# Phần A

## A1
Ba cách nhúng CSS vào HTML
1. Inline CSS (CSS nội tuyến)
<p style="color: red; font-size: 18px;">
  Đây là đoạn văn màu đỏ
</p>
Ưu điểm:
Nhanh, đơn giản, dùng ngay trên element
Phù hợp khi test nhanh hoặc chỉnh sửa nhỏ
Nhược điểm:
Khó bảo trì (viết lặp lại nhiều)
Không tái sử dụng được
Làm HTML bị rối
Khi nào nên dùng:
Khi cần chỉnh sửa nhanh 1 phần tử duy nhất
Debug hoặc demo nhanh

2. Internal CSS (CSS nội bộ)
<!DOCTYPE html>
<html>
<head>
  <style>
    p {
      color: blue;
      font-size: 18px;
    }
  </style>
</head>
<body>
  <p>Đây là đoạn văn màu xanh</p>
</body>
</html>
Ưu điểm:
Quản lý CSS trong cùng 1 file HTML
Dễ đọc hơn inline
Nhược điểm:
Không tái sử dụng giữa nhiều trang
File HTML sẽ dài hơn
Khi nào nên dùng:
Website nhỏ, 1 trang
Khi không cần tách file CSS riêng

3. External CSS (CSS bên ngoài)
<link rel="stylesheet" href="style.css">
<p>Xin chào</p>

File style.css:

p {
  color: green;
  font-size: 18px;
}
Ưu điểm:
Tái sử dụng cho nhiều trang
Dễ bảo trì, chuyên nghiệp
Giúp HTML gọn gàng
Nhược điểm:
Cần thêm file riêng
Phải load file CSS (có thể chậm hơn chút)
Khi nào nên dùng:
Hầu hết mọi dự án thực tế
Website nhiều trang

* Câu hỏi thêm
 Nếu cùng một element có cả 3 cách CSS thì thứ tự ưu tiên là:
    Inline CSS > Internal CSS > External CSS
Inline CSS thắng vì nó được viết trực tiếp trên element nên có độ ưu tiên cao nhất.
        Ngoài ra, nếu dùng !important thì CSS đó có thể ghi đè các CSS khác.

## A2
Câu 1

Selector: h1
→ Chọn element có text: “ShopTLU”

Câu 2

Selector: .price
→ Chọn các element có text:

“25.990.000đ”
“45.990.000đ”
Câu 3

Selector: #app header
→ Chọn toàn bộ phần header chứa:

“ShopTLU”
“Home”
“Products”
“About”
Câu 4

Selector: nav a:first-child
→ Chọn element có text: “Home”

Câu 5

Selector: .product.featured h2
→ Chọn element có text: “MacBook Pro”

Câu 6

Selector: article > p
→ Chọn các element có text:

“25.990.000đ”
“Mô tả sản phẩm...”
“45.990.000đ”
“Mô tả sản phẩm...”
Câu 7

Selector: a[href="/"]
→ Chọn element có text: “Home”

Câu 8

Selector: .top-bar.dark h1
→ Chọn element có text: “ShopTLU”

## A3
*TH1
Chiều rộng hiển thị = 400 + 20*2 + 5*2 = 450px
Không gian chiếm trên trang =450 + 10*2 = 470px

Giải thích:
width chỉ tính phần content
padding và border được cộng thêm bên ngoài
margin làm tăng khoảng trống xung quanh element

*TH2
Chiều rộng hiển thị =400px
Kích thước content thực tế = 400 - 20*2 - 5*2 = 350px
Không gian chiếm trên trang = 400 + 10*2 = 420px

Giải thích:
Khi dùng border-box, width đã bao gồm:
content
padding
border
Vì vậy content sẽ bị giảm lại

*TH3
Khoảng cách giữa box-a và box-b = 40px
Giải thích tại sao KHÔNG PHẢI 65px:
    Trong CSS có hiện tượng margin collapse.
    Khi 2 margin dọc chạm nhau:
        Browser KHÔNG cộng 2 margin lại
        Browser chỉ lấy margin lớn hơn
Ở đây:
25px
40px
→ Browser lấy 40px

*Nâng Cao
Khoảng cách giữa 2 box = 40 + (-10) = 30px
Giải thích:
    Margin âm sẽ làm giảm khoảng cách
    Browser cộng margin dương và margin âm lại với nhau
→ Kết quả cuối cùng là 30px

*A4
Rule A
p { color: black; }
→ Specificity: (0,0,1)

Rule B
.price { color: blue; }
→ Specificity: (0,1,0)

Rule C
#main-price { color: red; }
→ Specificity: (1,0,0)

Rule D
p.price { color: green; }
→ Specificity: (0,1,1)

Element sẽ có màu gì?
<p class="price" id="main-price">
→ Element có màu red
Vì Rule C có specificity cao nhất.

Nếu thêm inline style
style="color: orange;"
→ Element có màu orange
Vì inline style ưu tiên cao hơn ID, class và element.

Nếu Rule A thêm !important
p { color: black !important; }
→ Element có màu black
Vì !important ưu tiên cao hơn các rule CSS thông thường.

# Phần C
## C1
Sidebar có chiều rộng thực tế:
300 + 20*2 + 1*2 = 342px

Content có chiều rộng thực tế:
660 + 30*2 + 1*2 = 722px

Tổng chiều rộng:
342 + 722 = 1064px

Container chỉ rộng 960px nên content bị đẩy xuống dòng mới.

Cách sửa 1: dùng box-sizing: border-box; để width bao gồm cả padding và border.

Cách sửa 2: giảm width của sidebar và content để tổng kích thước không vượt quá 960px.

Tạo file:

debug_layout.html
debug_layout.css

## C2
Sản phẩm A (h2)

→ font-size: 20px
→ color: green

Vì .card .title đặt font-size 20px và .highlight { color: green !important; } mạnh hơn #featured .title.

Mô tả sản phẩm (p trong featured)

→ color: blue

Vì p { color: inherit; } nên kế thừa màu từ .card.

Sản phẩm B (h2)

→ font-size: 20px
→ color: blue

Vì .card .title đặt font-size 20px và h2 kế thừa màu từ .card.

Mô tả sản phẩm B (p.highlight)

→ color: green

Vì .highlight có green !important nên ưu tiên cao nhất.

Tạo file:
index.html
style.css

## CSS Specificity Answers

### 1. Danh sách 10 rules + specificity score

| Rule | Specificity |
|------|-------------|
| p | 0,0,1 |
| .text | 0,1,0 |
| .highlight | 0,1,0 |
| p.text | 0,1,1 |
| p.highlight | 0,1,1 |
| .text.highlight | 0,2,0 |
| p.text.highlight | 0,2,1 |
| #demo | 1,0,0 |
| p#demo | 1,0,1 |
| p#demo.text.highlight | 1,2,1 |

---

### 2. Element cuối cùng hiển thị màu gì? Tại sao?

Element cuối cùng hiển thị màu GOLD.

Lý do:
Rule:

p#demo.text.highlight {
    color: gold;
}

có specificity cao nhất là:

1,2,1

Nó mạnh hơn tất cả các rules còn lại nên trình duyệt sẽ áp dụng màu gold.

---

### 3. Screenshot kết quả

(Chèn ảnh screenshot tại đây)

---

### 4. Thay đổi thứ tự rules trong CSS file. Kết quả có đổi không? Giải thích.

Kết quả KHÔNG đổi nếu rule có specificity cao nhất vẫn tồn tại.

Trong CSS:
- Rule có specificity cao hơn sẽ được ưu tiên.
- Thứ tự chỉ quan trọng khi specificity bằng nhau.

Ví dụ:
.text và .highlight đều có specificity:
0,1,0

Khi đó rule viết sau sẽ thắng.

Nhưng:
p#demo.text.highlight có specificity:
1,2,1

nên dù đặt ở đầu file hay cuối file thì nó vẫn thắng tất cả rules khác.
