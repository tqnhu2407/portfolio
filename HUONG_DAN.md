# Hướng dẫn portfolio và triển khai Vercel cho người mới

## 1. Bạn đang có gì?

Thư mục này là một website portfolio hoàn chỉnh theo concept Ocean Bloom, không cần database và không cần cài framework phức tạp.

Website gồm:

- Phần giới thiệu ngắn về vai trò AI Engineer và AI Highlight Detection.
- Hành trình nghề nghiệp qua Eklipse, Katalon và chương trình thạc sĩ tại JAIST.
- Năm nhóm năng lực tổng quát và thông tin liên hệ.
- Giao diện responsive cho máy tính, tablet và điện thoại.
- Hiệu ứng cuộn nhẹ và hỗ trợ người dùng giảm chuyển động.
- Ảnh social preview khi chia sẻ link trên LinkedIn hoặc mạng xã hội.

Nội dung được giữ ở mức portfolio tổng quát. Website không công khai số liệu benchmark, code nội bộ, dữ liệu riêng, prompt, endpoint hoặc ID hệ thống.

## 2. Hiểu cấu trúc thư mục bằng ngôn ngữ đơn giản

```text
portfolio/
├── index.html          Nội dung và cấu trúc của trang
├── ocean-bloom.css     Giao diện chính Ocean Bloom
├── rosewave.html       Concept Rosewave được giữ để tham khảo
├── pink-editorial.html Concept Pink Editorial được giữ để tham khảo
├── script.js           Hiệu ứng xuất hiện khi cuộn trang
├── vercel.json         Cấu hình triển khai Vercel
├── .gitignore          Không đưa cấu hình máy cá nhân lên Git
└── assets/
    ├── favicon.svg     Biểu tượng nhỏ trên tab trình duyệt
    └── og.png          Ảnh khi chia sẻ link trên mạng xã hội
```

Có thể hình dung như sau:

- `index.html` là phần nội dung và khung nhà.
- `ocean-bloom.css` là phần màu sắc, hình khối và bố cục Ocean Bloom.
- `script.js` là các công tắc và chuyển động nhỏ.
- Vercel là dịch vụ đưa ngôi nhà đó lên Internet.

## 3. Xem website trên máy của bạn

### Cách dùng Terminal

1. Mở Terminal.
2. Đi tới thư mục `portfolio`.
3. Chạy lệnh:

```bash
python3 -m http.server 4173
```

4. Mở trình duyệt và vào:

```text
http://localhost:4173
```

5. Khi xem xong, quay lại Terminal và nhấn `Control + C` để tắt.

Nếu cổng `4173` đang được dùng, thay bằng số khác, ví dụ `8080`, rồi mở `http://localhost:8080`.

## 4. Chỉnh nội dung mà không cần biết lập trình sâu

Mở `index.html` trong trình soạn thảo như Codex hoặc VS Code. Dùng chức năng tìm kiếm để tìm đúng câu cần đổi.

### Đổi câu giới thiệu chính

Tìm:

```text
AI with an eye for meaningful moments.
```

Thay phần chữ bằng thông điệp mới. Giữ nguyên các ký hiệu HTML bao quanh nếu bạn chưa quen chỉnh code.

### Đổi email, LinkedIn hoặc GitHub

Tìm lần lượt:

```text
tqnhu2407@gmail.com
https://www.linkedin.com/in/tqnhu2407/
https://github.com/tqnhu2407
```

Mỗi địa chỉ có thể xuất hiện nhiều lần. Nên thay tất cả các vị trí tìm được.

### Sửa hành trình nghề nghiệp

Trong `index.html`, tìm tên công ty hoặc trường học, ví dụ:

```text
Eklipse.gg
Katalon
JAIST · Japan
```

Mỗi mốc nằm trong một khối bắt đầu bằng `<article class="journey-card` và kết thúc bằng `</article>`. Chỉ nên dùng một hoặc hai câu để giới thiệu vai trò và hướng công việc.

### Sửa nhóm kỹ năng

Tìm các cụm sau trong `index.html`:

```text
Applied AI
AI Engineering
Research to Production
Multimodal Models
Communication
```

Mỗi kỹ năng chỉ có một câu giải thích ngắn. Nếu thêm kỹ năng mới, sao chép một khối `<article class="pool-card` và thay nội dung bên trong.

Trước khi thêm chi tiết về Eklipse, hãy kiểm tra:

- Có văn bản cho phép công bố từ công ty chưa?
- Có dữ liệu, screenshot, prompt, endpoint, ID hoặc code nội bộ không?
- Có số liệu hoặc kết quả chưa được phê duyệt không?
- Chi tiết đó có thực sự cần thiết cho một portfolio giới thiệu tổng quát không?

Nếu chưa chắc, hãy giữ nội dung ở mức vai trò và lĩnh vực phụ trách như phiên bản hiện tại.

### Đổi màu giao diện

Mở `ocean-bloom.css` và tìm phần đầu file:

```css
:root {
  --foam: #eafcff;
  --ink: #173f58;
  --ocean: #4a9fd4;
  --aqua: #8ddedc;
  --pink: #f1a3c2;
}
```

- `--foam`: màu nền xanh rất nhạt.
- `--ink`: màu chữ xanh navy.
- `--ocean`: màu xanh biển chính.
- `--aqua`: màu xanh ngọc phụ.
- `--pink`: màu hồng san hô làm điểm nhấn.

Chỉ cần thay mã màu sau dấu `#`. Nếu giao diện khó đọc, khôi phục các màu ban đầu.

## 5. Triển khai trực tiếp bằng Vercel CLI

Đây là cách ngắn nhất khi website đang nằm trên máy và chưa cần GitHub.

### Bước 1 — Tạo tài khoản Vercel

Vào [vercel.com](https://vercel.com/) và đăng ký hoặc đăng nhập.

### Bước 2 — Mở Terminal tại đúng thư mục

Bạn phải đứng trong thư mục `portfolio`, không phải thư mục Career OS bên ngoài. Điều này giúp chắc chắn các tài liệu nghề nghiệp riêng tư không bị tải lên.

### Bước 3 — Đăng nhập Vercel

Chạy:

```bash
npx --yes vercel login
```

Vercel sẽ đưa một link xác nhận. Mở link, đăng nhập và cho phép.

### Bước 4 — Tạo bản xem trước

Chạy:

```bash
npx --yes vercel
```

Ở lần đầu, Vercel có thể hỏi:

- `Set up and deploy?` → chọn `Y`.
- `Which scope?` → chọn tài khoản cá nhân hoặc team bạn muốn dùng.
- `Link to existing project?` → chọn `N` nếu đây là lần đầu.
- `Project name?` → có thể dùng `tran-quynh-nhu-portfolio`.
- `In which directory is your code located?` → nhập `./`.
- `Want to modify settings?` → chọn `N`.

Sau khi xong, Terminal sẽ in ra một URL dạng `https://...vercel.app`. Đây là bản Preview.

### Bước 5 — Kiểm tra bản Preview

Mở URL và kiểm tra:

- Trang đầu tải được.
- Các nút Work, Expertise và About cuộn đúng vị trí.
- Nút email mở ứng dụng gửi thư.
- Link LinkedIn và GitHub đúng tài khoản.
- Giao diện điện thoại không tràn ngang.
- Nội dung công khai không có thông tin nội bộ.

### Bước 6 — Đưa lên Production

Khi Preview ổn, chạy:

```bash
npx --yes vercel --prod
```

Vercel sẽ gắn phiên bản này vào domain production của project.

Theo tài liệu chính thức, `vercel` tạo bản Preview và `vercel --prod` tạo bản Production: [Vercel CLI deployment guide](https://vercel.com/docs/projects/deploy-from-cli).

## 6. Triển khai bằng GitHub để tự động cập nhật

Cách này phù hợp nếu bạn muốn mỗi lần cập nhật code và push lên GitHub thì Vercel tự deploy.

### Quy tắc an toàn quan trọng

Chỉ tạo repository từ nội dung bên trong thư mục `portfolio`. Không đưa thư mục Career OS cha lên GitHub vì nó chứa hồ sơ và bằng chứng nghề nghiệp không dành cho công khai.

### Cách dễ cho người mới với GitHub Desktop

1. Cài GitHub Desktop và đăng nhập.
2. Chọn `File` → `Add Local Repository`.
3. Chọn đúng thư mục `portfolio`.
4. Nếu được hỏi tạo repository, chọn tạo repository tại chính thư mục này.
5. Viết commit đầu tiên, ví dụ `Initial portfolio`.
6. Chọn `Publish repository`.
7. Bạn có thể để repository ở chế độ Private; Vercel vẫn có thể import sau khi được cấp quyền.

### Import vào Vercel

1. Mở Vercel Dashboard.
2. Chọn `New Project`.
3. Chọn repository vừa tạo.
4. Ở phần Framework Preset, chọn `Other` nếu Vercel chưa tự nhận diện.
5. Vì repository chỉ chứa website, Root Directory để mặc định.
6. Không cần Build Command.
7. Output Directory để trống hoặc dùng `.` nếu giao diện yêu cầu.
8. Chọn `Deploy`.

Vercel cho phép chọn Root Directory khi import Git repository: [Vercel Git deployment guide](https://vercel.com/docs/git).

## 7. Cập nhật website sau này

### Nếu dùng Vercel CLI

1. Sửa file.
2. Xem lại trên máy.
3. Tạo Preview:

```bash
npx --yes vercel
```

4. Nếu ổn, đưa lên Production:

```bash
npx --yes vercel --prod
```

### Nếu dùng GitHub

1. Sửa file.
2. Commit và push lên GitHub.
3. Vercel tự tạo deployment mới.
4. Mở Vercel Dashboard để xem trạng thái và URL.

## 8. Gắn tên miền riêng

Tên miền riêng là tùy chọn; link `.vercel.app` vẫn dùng tốt.

Trong Vercel:

1. Mở project.
2. Vào `Settings` → `Domains`.
3. Nhập tên miền, ví dụ `tqnhu.dev`.
4. Làm theo bản ghi DNS mà Vercel hướng dẫn.
5. Chờ DNS cập nhật và HTTPS được cấp tự động.

Sau khi có domain chính thức, nên đổi `og:image` trong `index.html` thành URL đầy đủ, ví dụ:

```html
<meta property="og:image" content="https://tqnhu.dev/assets/og.png" />
```

## 9. Checklist trước khi chia sẻ với nhà tuyển dụng

- [ ] Tên, chức danh, email, LinkedIn và GitHub chính xác.
- [ ] Link website mở được ở cửa sổ ẩn danh.
- [ ] Website hiển thị tốt trên điện thoại.
- [ ] Không có code, dữ liệu, prompt, endpoint hoặc ID nội bộ.
- [ ] Không còn số liệu benchmark hoặc mô tả thử nghiệm quá chi tiết.
- [ ] Nội dung Eklipse chỉ giới thiệu vai trò và lĩnh vực phụ trách, hoặc đã có phê duyệt công bố.
- [ ] GitHub được kiểm tra nội dung trước khi đặt link công khai.
- [ ] Ảnh social preview hiển thị đúng khi chia sẻ link.

## 10. Nếu gặp lỗi

### `command not found: npx`

Cài Node.js bản LTS từ [nodejs.org](https://nodejs.org/), đóng và mở lại Terminal.

### Vercel hỏi đăng nhập lại

Chạy lại:

```bash
npx --yes vercel login
```

### Deploy xong nhưng trang trắng

Kiểm tra bạn đã chạy lệnh trong đúng thư mục `portfolio`. Thư mục này phải có file `index.html` ở cấp đầu tiên.

### Sửa code nhưng website chưa đổi

Tạo deployment mới bằng `npx --yes vercel --prod`, sau đó tải lại trang bằng `Command + Shift + R` trên macOS hoặc `Control + Shift + R` trên Windows.
