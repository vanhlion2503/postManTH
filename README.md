# Thực Hành Postman Cơ Bản
## Cài đặt Postman
- Truy cập: [https://www.postman.com/downloads/](https://www.postman.com/downloads/)
- Chọn phiên bản phù hợp: Windows / macOS / Linux
- Tải và cài đặt như phần mềm thông thường
- Đăng nhập bằng tài khoản Google hoặc tạo tài khoản mới
## Thực hành cơ bản với API công khai
**API sử dụng**: [https://jsonplaceholder.typicode.com](https://jsonplaceholder.typicode.com)

### Bài 1: Gửi Request `GET` - Lấy danh sách bài post

- Method: `GET`
- URL: `https://jsonplaceholder.typicode.com/posts`
- Bấm **Send**
- Xem kết quả JSON trong phần **Body**

![Screenshot 2025-06-19 163116](https://github.com/user-attachments/assets/24ae6849-8a61-4936-a637-e8af4dfbf0d4)

### Bài 2: Gửi Request `GET` - Lấy chi tiết bài post

- Method: `GET`
- URL: `https://jsonplaceholder.typicode.com/posts/1`
- Bấm **Send**

![Screenshot 2025-06-19 163138](https://github.com/user-attachments/assets/5e099863-c0d0-46b4-9179-1a7f952e76db)

### Bài 3: Gửi Request `POST` - Tạo bài viết mới

- Method: `POST`
- URL: `https://jsonplaceholder.typicode.com/posts`
- Tab **Body** → Chọn **raw** → **JSON**
- Dán nội dung:
```json
{
  "title": "Hello Postman",
  "body": "This is my first API post",
  "userId": 1
}
```
- Bấm **Send**

![Screenshot 2025-06-19 163222](https://github.com/user-attachments/assets/84340817-b117-44b8-ae98-883f78b6c815)

### Bài 4: Gửi Request PUT - Cập nhật bài viết

- Method: `PUT`
- URL: `https://jsonplaceholder.typicode.com/posts/1`
- Tab **Body** → Chọn **raw** → **JSON**
```json
{
  "id": 1,
  "title": "Updated Title",
  "body": "Updated Body",
  "userId": 1
}
```

![Screenshot 2025-06-19 163332](https://github.com/user-attachments/assets/d246bbc3-de5c-43ac-b317-e0da861b22ec)

### Bài 5: Gửi Request DELETE - Xoá bài viết

- Method: `DELETE`
- URL: `https://jsonplaceholder.typicode.com/posts/1`
- Bấm **Send**

![Screenshot 2025-06-19 163409](https://github.com/user-attachments/assets/854c029a-4f0e-4869-b7dc-1b78a28cf104)

### Bài 6: Gửi Request DELETE - Xoá bài viết

- Method: `GET`
- URL: `https://jsonplaceholder.typicode.com/posts`
- Bấm **Script**
```
let posts = pm.response.json();

// Kiểm tra tổng số bài viết là 100
pm.test("Số lượng bài viết là 100", function () {
    pm.expect(posts.length).to.eql(100);
});

// Kiểm tra không có ID nào trùng nhau
let ids = posts.map(p => p.id);
let uniqueIds = new Set(ids);
pm.test("Không có ID bị trùng", function () {
    pm.expect(uniqueIds.size).to.eql(ids.length);
});
```
- Bấm **Send**

![Screenshot 2025-06-19 163738](https://github.com/user-attachments/assets/ea1230b0-d272-4855-96e4-6eaba3bc8ad8)
