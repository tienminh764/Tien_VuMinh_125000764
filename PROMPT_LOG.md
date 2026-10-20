# NHẬT KÝ PROMPT ENGINEERING (VIBE CODING LOG)
- **Họ và tên:** Vũ Minh Tiến
- **MSSV:** 125000764
- **Lớp / Trường:** Đại học Lạc Hồng (LHU)
- **Tên đề tài Website:** Sneaker C&S (Website Cửa Hàng Giày Thể Thao & Sneaker Chính Hãng)
- **Công cụ AI đã sử dụng:** Claude / Gemini (Antigravity)

---

## 1. Yêu cầu ban đầu (System / Initial Prompt)

> *"Đóng vai trò là một Senior Front-end Developer và UI/UX Designer chuyên về phong cách Neo-Brutalist & Streetwear hiện đại. Hãy giúp tôi xây dựng một website bán giày sneaker tên là **'Sneaker C&S'** với bộ sưu tập đặc biệt **'Shark Teeth Series'** bằng HTML/CSS/JS thuần (Vanilla Web).*
> 
> *Yêu cầu kỹ thuật bắt buộc:*
> 1. *Cấu trúc HTML5 chuẩn Semantic (header, nav, main, section, article, aside, footer, address), tuyệt đối không lạm dụng thẻ div vô nghĩa.*
> 2. *Quản trị giao diện bằng CSS Variables trong `:root` (khai báo bảng màu, spacing, radius, fonts, box-shadow dạng neo-brutalist 5px 5px 0px #000).*
> 3. *Phát triển 2 hệ phối màu cốt lõi chuyên nghiệp:*
>    - **Colorway 01 - Ice Glacial (Băng Bắc Cực):** Phối màu Đen Phantom - Trắng Tinh Khiết - Đỏ Thể Thao - Xanh Băng Glacial.
>    - **Colorway 02 - Neon Pulse (Hồng Neon Đêm):** Phối màu Hồng Neon Pulse - Đen Huyền Bí - Trắng Thể Thao - Viền Đỏ Thể Thao.
> 4. *Chi tiết sản phẩm độc bản theo chuẩn giày sneaker thể thao:*
>    - Đế giày đúc họa tiết **răng cưa nhọn (Shark Teeth Traction Sole)** từ cao su Gum non tự nhiên tăng ma sát bám đường tối đa.
>    - Hộp giày thiết kế mô phỏng **Hộp Đựng Giày Collector Box (Tactical Packaging)** đúc nguyên khối chống va đập kết hợp họa tiết khóa lục giác trợ lực khí động học.
> 5. *Phân loại danh mục rõ ràng: Cổ Thấp (Low-Top), Cổ Lửng & Cao (Mid & High-Top), Giày Chạy & Slip-On (Runner).*
> 6. *Tích hợp thư viện hiệu ứng Animate.css và AOS (Animate On Scroll).*
> 7. *Tự viết hiệu ứng tương tác: :hover, :focus-visible, bộ chọn size giày, drawer giỏ hàng lưu localStorage, menu hamburger trên mobile và hỗ trợ prefers-reduced-motion.*
> 8. *Giao diện phải có cá tính mạnh mẽ, đậm chất streetwear cho Gen Z và Sneakerhead, không dùng template thương mại chung chung."*

---

## 2. Quá trình tinh chỉnh & Giải quyết sự cố (Iteration)

### Lần 1: Dựng khung Semantic HTML & Hệ thống CSS Variables theo chuẩn Sneaker Shop
- **Prompt đã dùng:**
  > *"Hãy tạo cấu trúc khung HTML5 chuẩn ngữ nghĩa semantic và file `style.css` thiết lập toàn bộ biến `:root`. Hãy chia rõ 2 palette màu thiết kế giày: Colorway Ice Glacial (`--phantom-black`, `--pure-white`, `--sport-red`, `--ice-blue`) và Colorway Neon Pulse (`--neon-pink`, `--jet-black`, `--athletic-white`, `--crimson-trim`), cùng các biến chung như `--gum-sole`, `--caution-yellow`. Dựng layout header cố định (sticky), hero section chia 2 cột với CSS Grid, section concept banner, section danh sách sản phẩm phân loại theo kiểu dáng giày (Low-top, Mid-top, Runner), section hộp đựng Collector Box, section vì sao chọn và footer có thông tin sinh viên."*

- **Kết quả AI tạo ra:**
  - Khung HTML với đầy đủ thẻ ngữ nghĩa `<header>`, `<nav>`, `<main>`, các `<section>` có id neo đậu liên kết, thẻ `<article>` cho card giày, `<address>` ở chân trang.
  - File CSS khai báo hệ thống biến `:root` bài bản với phong cách Neo-Brutalist (viền đen dày, bóng đổ lệch cứng cáp `5px 5px 0 #000`).

- **Nhận xét & Tinh chỉnh của SV:**
  - AI ban đầu dùng thẻ `<div class="card">` thay vì thẻ ngữ nghĩa; tôi đã yêu cầu đổi toàn bộ sang `<article class="product-card">`.
  - Chuẩn hóa thuật ngữ sang ngôn ngữ thiết kế sneaker chuyên nghiệp (Low-Top, High-Top, Runner, Outsole, Traction, Colorway).
  - Kiểm tra độ tương phản màu (WCAG Contrast): Điều chỉnh màu nền `--bg-main` tối sâu hơn (`#0b0c10`) để các màu neon (Xanh Băng `#2be4ff` và Hồng Neon `#ff2a85`) phát sáng nổi bật trên màn hình.

---

### Lần 2: Tích hợp thư viện Animate.css, AOS và Thiết kế Vector SVG Đế Răng Cưa & Hộp Collector Box
- **Prompt đã dùng:**
  > *"Website cần thể hiện rõ tính năng kỹ thuật của sneaker: 'Đế giày có họa tiết răng cưa nhọn tăng độ bám đường (Shark Teeth Traction)' và 'Hộp giày thiết kế đúc nguyên khối chống va đập (Collector Box) với nẹp góc kim loại và cấu trúc khóa lục giác trợ lực'.*
  > *Hãy nạp Animate.css và AOS qua CDN. Đồng thời, thay vì dùng ảnh ngoài dễ vỡ link, hãy tự vẽ trực tiếp bằng mã SVG Symbol các đôi giày mang đế răng cưa nhọn (sawtooth profile), dải vây kéo gót thể thao, cấu trúc lục giác trợ lực và một hộp đựng Tactical Collector Box hoàn chỉnh."*

- **Kết quả AI tạo ra:**
  - Nạp CDN Animate.css v4.1.1 và AOS v2.3.4.
  - Gắn class `animate__animated animate__fadeInUp`, `animate__delay-1s` cho Hero text.
  - Gắn thuộc tính `data-aos="fade-up"`, `data-aos-delay="..."` so le cho 6 card sản phẩm và các khối nội dung.
  - Thiết kế 3 bộ SVG symbols: `#shoe-low-shark`, `#shoe-mid-neon` và `#collector-crate-svg`.

- **Thách thức gặp phải:**
  - Ban đầu phần đế giày SVG chỉ là hình chữ nhật phẳng lì (`rect`), chưa thể hiện được đặc trưng "răng cưa nhọn" chống trượt.
  - Hiệu ứng cuộn AOS trên màn hình hẹp dễ làm người dùng bị giật khung hình do offset mặc định quá lớn.
  - Hộp đựng ban đầu thiếu chi tiết chuyên dụng cho dân sưu tầm sneaker (nẹp kim loại chống móp, khóa lục giác thông khí và mã hiệu sản phẩm).

- **Cách sửa prompt (Debug prompt):**
  > *"Sửa lại mã SVG của đôi giày: phần outsole dưới cùng phải dùng thẻ `<path>` vẽ zíc-zắc hình tam giác nhọn liên tục (răng cá mập) từ gót đến mũi giày. Với hộp đựng Collector Box, thêm pattern sọc an toàn thể thao (`#hazard`), nẹp 4 góc gia cố và mã hiệu 'C&S-01'. Về AOS, chỉnh lại cấu hình `AOS.init({ duration: 700, once: true, offset: 60 })` để cuộn mượt và không bị giật lặp lại khi lướt ngược lên."*

---

### Lần 3: Tối ưu Trải nghiệm Tương tác (Cart Drawer, Size Selector, Bộ lọc Phân loại Giày, Mobile Menu & Reduced Motion)
- **Prompt đã dùng:**
  > *"Hãy hoàn thiện toàn bộ tầng tương tác JavaScript và CSS UX:*
  > 1. *Làm chức năng chọn Size giày (38-43) ngay trên từng card sản phẩm.*
  > 2. *Nút 'Thêm vào giỏ' khi bấm sẽ hiển thị thông báo Toast góc màn hình, tăng số đếm badge giỏ hàng có hiệu ứng rung lắc (bump animation), và lưu dữ liệu vào `localStorage`.*
  > 3. *Khi click vào nút Giỏ hàng trên header, mở một Drawer trượt từ bên phải ra, hiển thị danh sách sản phẩm đã chọn, kích cỡ, cho phép tăng/giảm số lượng, xóa món, và tính tổng tiền tự động.*
  > 4. *Thêm bộ lọc danh mục giày theo kiểu dáng: Tất cả (All) / Cổ Thấp (Low-Top) / Cổ Lửng & Cao (Mid & High) / Giày Chạy & Slip-On (Runner).*
  > 5. *Viết form Đặt hàng / Pre-order hộp Collector Box với validation và thông báo xác nhận.*
  > 6. *Tối ưu responsive hoàn chỉnh trên thiết bị di động với nút menu Hamburger, và bổ sung media query `@media (prefers-reduced-motion: reduce)` chuẩn Accessibility."*

- **Kết quả AI tạo ra & SV tinh chỉnh:**
  - Xây dựng thành công Drawer giỏ hàng trượt mượt mà với nền mờ backdrop blur.
  - Hàm format tiền tệ Việt Nam `formatVND()` chuẩn `Intl.NumberFormat('vi-VN', { style: 'currency', currency: 'VND' })`.
  - Bộ chọn size trực quan với class `.selected`, lưu chính xác size người dùng đã chọn khi cho vào giỏ hàng.
  - Bộ lọc sản phẩm chuyển đổi mượt mà giữa các kiểu dáng giày (Low-top, Mid-top, Runner) thông qua thuộc tính `data-category`.
  - Hỗ trợ đầy đủ menu di động và kiểm soát chuyển động cho người dùng nhạy cảm với hiệu ứng động.

---

### Lần 4: Tái cấu trúc giao diện sáng E-commerce (phong cách EGO Sport / Biti's Hunter), tích hợp ảnh chụp Sneaker thật & Hoàn thiện nhận diện thương hiệu Sneaker C&S
- **Bối cảnh & Yêu cầu thay đổi:**
  - Giảng viên / Khách hàng cung cấp ảnh mẫu thiết kế thực tế từ website thương mại điện tử chuyên nghiệp (EGO Sport / Biti's Hunter) với tone màu sáng thanh lịch, tinh tế.
  - Loại bỏ hoàn toàn các đường viền đen thô cứng, đổi tên thương hiệu thống nhất thành **Sneaker C&S**.
  - Loại bỏ triệt để 100% tất cả các từ khóa anime/game (*Ellen Joe, Kurona, Zenless Zone Zero, Blue Lock...*) và chuyển sang ngôn ngữ thiết kế giày thể thao thương mại thực thụ (*Biti's Hunter Street Dark, Adidas Valstripes 2 ADV Classic, Hunter Green Trail, Just Do It Orange, Classic Leather, Ocean Air...*).
  - Thay thế toàn bộ hình vẽ vector bằng **ảnh chụp sneaker thực tế** chất lượng cao từ nhiếp ảnh thương mại.
  - Đồng bộ màu sắc giao diện theo đúng ảnh mẫu: Nền sáng `#f9fafb`, điểm nhấn Đỏ Coral `#e53935`, Hero banner Hồng pastel `#fce4ec` với slogan *"Tưng bừng khai trương Giảm ngay 50%"*, thanh 8 danh mục icon bo tròn viền đỏ, con dấu tròn đỏ răng cưa (`BEST SELLER`, `HOT DEAL`, `SALE 50%`) và banner phụ *"BÙNG NỔ SẮC CAM"*.

- **Prompt đã dùng:**
  > *"Hãy chuyển đổi toàn diện website Sneaker C&S sang phong cách E-commerce hiện đại, sáng sủa dựa trên ảnh chụp mẫu website EGO Sport / Biti's Hunter:*
  > *1. Tái cấu trúc toàn bộ CSS Variables trong `:root`: Màu nền sáng `--bg-main: #f9fafb`, thẻ card trắng tinh khôi `--bg-card: #ffffff`, màu chủ đạo Đỏ Coral `--primary-red: #e53935`, gradient Hero hồng pastel `--hero-pink-start: #fce4ec`.*
  > *2. Bỏ hoàn toàn các đường kẻ viền dày thô cứng, thay bằng border mỏng nhẹ `#e5e7eb` và box-shadow mềm mại nhiều tầng.*
  > *3. Dựng Hero section với hiệu ứng giày bay bồng bềnh, chữ 'Tưng bừng khai trương Giảm ngay 50%' và nút Mua ngay.*
  > *4. Thiết kế thanh Category Bar bo tròn với viền đỏ/hồng chứa 8 danh mục: Bộ sưu tập, Boots, Cổ Thấp, Thể thao, Cổ Cao, Đế bệt, Slip-on, Sneaker.*
  > *5. Thay thế tất cả ảnh sản phẩm bằng URL ảnh chụp sneaker thật chất lượng cao (Unsplash CDN). Bổ sung con dấu tròn đỏ dập nổi 'BEST SELLER', 'HOT DEAL', 'SALE 50%' ở góc trên bên trái từng card.*
  > *6. Thiết kế thêm banner phụ 'BÙNG NỔ SẮC CAM' rực rỡ với ảnh giày thể thao cam.*
  > *7. Tối ưu giỏ hàng Drawer, bộ chọn size, thông báo Toast và form đặt hàng hoạt động trơn tru trên nền sáng mới."*

- **Kết quả AI tạo ra & SV tinh chỉnh:**
  - Layout sáng sủa, thanh lịch, mang lại cảm giác tin cậy của một shop thời trang thể thao chính hãng.
  - 10 mẫu giày được trang bị ảnh chụp thật cực kỳ sắc nét, hiển thị rõ form dáng, chất liệu và màu sắc.
  - Con dấu tròn đỏ `.stamp-badge` được tạo hình tỉ mỉ bằng CSS với viền răng cưa chấm bi, góc xoay nghiêng nhẹ tự nhiên như tem chứng nhận cao cấp.
  - Toàn bộ nội dung chữ, tên sản phẩm, mô tả cam kết được Việt hóa chuẩn mực, không còn bất kỳ dấu vết từ ngữ hoạt họa/game nào.
  - Đảm bảo trọn vẹn thông tin sinh viên Vũ Minh Tiến - MSSV: 125000764 - ĐH Lạc Hồng ở chân trang web.

---

## 3. Đánh giá cá nhân về quá trình Vibe Coding

### 1. AI giúp tiết kiệm thời gian nhất ở phần nào?
- **Khởi tạo Boilerplate & CSS Variables:** Thiết lập một Design System nhất quán cho thương hiệu Sneaker C&S chỉ trong vài giây.
- **Vẽ vector SVG tọa độ phức tạp:** Tự động tính toán các điểm tọa độ `L x y` và `Q x y` cho họa tiết răng cưa nhọn trên đế giày và vẽ hộp đựng giày Collector Box bằng SVG thuần cực kỳ sắc nét.
- **Xử lý logic giỏ hàng & LocalStorage:** Viết khung code Javascript quản lý trạng thái giỏ hàng, tính toán tổng tiền và format số tiền chuẩn xác.

### 2. Bài học rút ra khi đặt prompt cho AI trong thiết kế web:
- **Chuẩn hóa ngôn ngữ chuyên ngành (Domain Terminology):** Trong thương mại điện tử giày dép, việc dùng đúng thuật ngữ (Low-Top, Mid-Top, High-Top, Traction Sole, Colorway, Insole, Outsole) giúp trang web toát lên sự chuyên nghiệp và đáng tin cậy như các thương hiệu hàng đầu.
- **Vibe Coding đòi hỏi sự định hướng thẩm mỹ:** Không phó mặc hoàn toàn cho AI; lập trình viên cần làm chủ các kỹ năng kiểm tra Semantic HTML, tối ưu Accessibility, và liên tục tinh chỉnh các chi tiết tương tác để mang lại trải nghiệm người dùng hoàn hảo nhất.
