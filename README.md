# Thiên (ThienDevAI) — Profile cá nhân

Trang profile chính thức của **Thiên (ThienDevAI)**: Web Developer, IT Support và tư vấn Digital Marketing tại Việt Nam.

🔗 **Website:** https://info.devthien.com/

Trang tĩnh viết bằng một file HTML duy nhất, không cần build, không phụ thuộc framework, deploy bằng GitHub Pages.

---

## Nội dung trang

| Khu vực | Nội dung |
|---|---|
| **Header** | Banner, avatar, tên, `@ThienDevAI · devthien.com`, chức danh, thống kê (khách hàng, theo dõi, kinh nghiệm) |
| **Giới thiệu** | Đoạn giới thiệu, địa điểm, chức danh, email |
| **Kỹ năng & Dịch vụ** | Danh sách thẻ kỹ năng |
| **Mạng xã hội** | Zalo, WhatsApp, Telegram, Facebook, TikTok, YouTube |
| **Dịch vụ** | 8 dịch vụ, mỗi dịch vụ một màu icon riêng |
| **Liên kết nhanh** | Các website mẫu kèm giá (Spa, Profile, Gia Phả, Tử Vi, Shop…), tư vấn, liên hệ |
| **Hành trình** | Các mốc làm việc từ 2021 đến 2026 |
| **Câu hỏi thường gặp** | 6 câu hỏi dạng mở/đóng, khớp với schema `FAQPage` |
| **Nút nổi** | Nút tròn Facebook và Zalo cố định ở góc phải. Trên điện thoại, bấm vào sẽ mở thẳng app |

## Tính năng

- **Responsive**: 2 cột trên máy tính; trên điện thoại còn 1 cột và các thẻ được sắp xếp lại thứ tự.
- **Giao diện tím** `#6938ef`. Mọi màu đều khai báo bằng biến CSS trong `:root`.
- **Hiệu ứng nhẹ**: các thẻ hiện dần khi cuộn tới. Tự tắt khi người dùng bật chế độ giảm chuyển động (`prefers-reduced-motion`).
- **Trợ năng**: có `aria-label`, `alt` cho ảnh, focus rõ ràng khi dùng bàn phím, link "Bỏ qua điều hướng".
- **SEO**: meta, Open Graph, Twitter Card, JSON-LD (`ProfilePage`, `Person`, `ProfessionalService`, `FAQPage`).
- **GEO** (tối ưu cho công cụ tìm kiếm bằng AI): `llms.txt`, `robots.txt` cho phép bot AI, FAQ trả lời ngắn gọn.
- **Hiệu năng**: preload banner, Font Awesome tải không chặn hiển thị, ảnh trang trí được hạ ưu tiên tải.

## Cấu trúc thư mục

```
profile-thien/
├── index.html                              # Toàn bộ trang: HTML + CSS + JS
├── robots.txt                              # Quy tắc cho bot tìm kiếm & bot AI
├── sitemap.xml                             # Sitemap (kèm ảnh)
├── llms.txt                                # Tóm tắt nội dung cho AI (GEO)
├── CNAME                                   # Tên miền cho GitHub Pages: info.devthien.com
└── README.md
```

## Chạy trên máy

Không cần cài đặt gì. Mở thư mục dự án trong terminal rồi chọn một trong các cách sau:

```bash
# Python
python -m http.server 8000      # mở http://localhost:8000

# Node.js
npx serve .                     # mở địa chỉ được in ra (thường là http://localhost:3000)
```

Hoặc dùng extension **Live Server** trong VS Code: chuột phải `index.html` → **Open with Live Server**.

> Nên chạy qua server local thay vì mở thẳng file, để đường dẫn và tài nguyên hoạt động giống trên web thật.

## Chỉnh sửa nội dung

Tất cả nằm trong `index.html`. Mỗi khối đều có comment tiêu đề để dễ tìm.

| Muốn sửa | Tìm tới |
|---|---|
| Màu giao diện | `/* ══ TOKENS ══ */`, biến `--pr`, `--pr-d`, `--pr-l` |
| Ảnh banner / avatar | `class="banner-img"` và `class="av"` (sửa luôn link trong `og:image`, JSON-LD, `sitemap.xml`) |
| Dịch vụ | `<!-- Dịch vụ -->`, mỗi dịch vụ là một `<li class="svc-item">`, màu icon là các class `.sv-*` |
| Website mẫu & giá | `<!-- Liên kết -->`, mỗi website là một `<a class="lk-card lk-priced">` |
| Hành trình | `<ol class="tl">`, mỗi mốc là một `<li class="tl-item">` |
| Câu hỏi thường gặp | `<!-- Câu hỏi thường gặp -->` |
| Nút nổi FB / Zalo | `<!-- ══ FLOATING CONTACT ══ -->` |
| Số điện thoại, email, mạng xã hội | Tìm và thay thế toàn file: `0383777823`, `ThienDevAI@gmail.com`, `ThienDevAI` |

> ⚠️ Khi sửa **dịch vụ, giá hoặc FAQ** trên trang, nhớ sửa cùng nội dung trong khối `<script type="application/ld+json">` ở `<head>` và trong `llms.txt`. Google yêu cầu dữ liệu schema phải khớp với nội dung hiển thị.

## Deploy

Trang chạy trên **GitHub Pages** với tên miền riêng `info.devthien.com` (khai báo trong file `CNAME`).

1. Push lên nhánh `main`.
2. GitHub → **Settings → Pages** → Source: `Deploy from a branch` → `main` / `(root)`.
3. Ở nhà cung cấp tên miền, tạo bản ghi DNS:

   | Loại | Tên | Giá trị |
   |---|---|---|
   | `CNAME` | `info` | `thiendevai.github.io` |

4. Bật **Enforce HTTPS** sau khi GitHub cấp chứng chỉ.

## SEO: việc cần làm sau mỗi lần cập nhật

1. Sửa `<lastmod>` trong `sitemap.xml` và `"dateModified"` trong JSON-LD của `index.html` thành ngày cập nhật.
2. **Google Search Console** → Kiểm tra URL → **Yêu cầu lập chỉ mục**.
3. **Bing Webmaster Tools** → Gửi URL (URL Submission) để Bing / Edge cập nhật nhanh.

### Thiết lập một lần

- **Google Search Console**: thêm `info.devthien.com`. Dán mã xác minh vào thẻ `google-site-verification` (đang để trong comment ở `<head>`), rồi gửi `sitemap.xml`.
- **Bing Webmaster Tools**: dùng *Import from Google Search Console*. Edge dùng kết quả tìm kiếm của Bing.
- **Cốc Cốc**: bot `coccocbot-web` tự thu thập trang và đã được cho phép trong `robots.txt`.
- **Kiểm tra dữ liệu cấu trúc**: [Rich Results Test](https://search.google.com/test/rich-results) và [Schema Validator](https://validator.schema.org/).

## Công nghệ

- HTML5, CSS3 (biến CSS, Grid, Flexbox), JavaScript thuần (`IntersectionObserver`)
- [Google Fonts](https://fonts.google.com/): Plus Jakarta Sans, Space Mono
- [Font Awesome 6.5.1](https://fontawesome.com/) qua cdnjs
- Icon mạng xã hội: [Icons8](https://icons8.com/)

## Liên hệ

- 🌐 https://info.devthien.com/
- 💬 Zalo: [0383777823](https://zalo.me/0383777823)
- ✉️ ThienDevAI@gmail.com
- Facebook · TikTok · YouTube · Telegram: **@ThienDevAI**
