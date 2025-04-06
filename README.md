# **eCommerce API Testing - Postman Collection**

#### 🔑 **1. Login**
- **Method:** POST  
- **URL:** `https://rahulshettyacademy.com/api/ecom/auth/login`  
- **Headers:**  
  - `Content-Type: application/json`  
- **Body (raw JSON):**  
```json
{
    "userEmail": "sharma9785sagar007@gmail.com",
    "userPassword": "Practice@123"
}
```
- **Expected Response:**  
  - **Status:** 201 Created  
  - **Body:**  
    ```json
    {
    "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJfaWQiOiI2N2YyNTA4M2ZjNzY1NDFhYWQyMTllMzIiLCJ1c2VyRW1haWwiOiJzaGFybWE5Nzg1c2FnYXIwMDdAZ21haWwuY29tIiwidXNlck1vYmlsZSI6Nzk3NjQzNTM2MywidXNlclJvbGUiOiJjdXN0b21lciIsImlhdCI6MTc0MzkzODg2MSwiZXhwIjoxNzc1NDk2NDYxfQ.2-SI7AIoicK0YC2efZZ-8AUTOYRMoTqCbtnhrm5x8dw",
    "userId": "67f25083fc76541aad219e32",
    "message": "Login Successfully"
}
    ```

---

#### 🛒 **2. Create Product**
- **Method:** POST  
- **URL:** `https://rahulshettyacademy.com/api/ecom/product/add-product`  
- **Headers:**  
  - `Content-Type: application/json`  
- **Body (form-data):**  
```form-data
productName:{{productName}}
productAddedBy:{{userId}}
productCategory:fashion
productSubCategory:shirts
productPrice:11500
productDescription:Addias Originals
productFor:women
```
- **Expected Response:**  
  - **Status:** 200 OK  
  - **Body:**  
    ```json
    {
    "productId": "67f26530fc76541aad21bdc0",
    "message": "Product Added Successfully"
}
    ```

---

#### 📦 **3. Create Order**
- **Method:** POST  
- **URL:** `https://rahulshettyacademy.com/api/ecom/order/create-order`  
- **Headers:**  
  - `Authorization: Bearer {{token}}`  
- **Expected Response:**  
  - **Status:** 200 OK  
  - **Body:**  
    ```json
    [
      {
    "orders": [
        {
            "country": "India",
            "productOrderedId": "{{productId}}"
        }
    ]
    }
    ]
    ```

---

#### 👀 **4. View Order Details**
- **Method:** GET  
- **URL:** `https://rahulshettyacademy.com/api/ecom/order/get-orders-details?id={{orderId}}`  
- **Headers:**  
  - `Authorization: Bearer {{token}}`  
  - `Content-Type: application/json`  

- **Expected Response:**  
  - **Status:** 200 OK  
  - **Body:**  
    ```json
    {
    "data": {
        "_id": "67f26533fc76541aad21bdc4",
        "orderById": "67f25083fc76541aad219e32",
        "orderBy": "sharma9785sagar007@gmail.com",
        "productOrderedId": "67f26530fc76541aad21bdc0",
        "productName": "Automation",
        "country": "India",
        "productDescription": "Addias Originals",
        "productImage": "https://rahulshettyacademy.com/api/ecom/uploads/productImage_1743938864887.jpg",
        "orderPrice": "11500",
        "__v": 0
    },
    ```

---

#### ❌ **5. Delete Product**
- **Method:** DELETE  
- **URL:** `https://rahulshettyacademy.com/api/ecom/product/delete-product/{{productId}}`  
- **Headers:**  
  - `Authorization: Bearer {{token}}`  
  - `Content-Type: application/json`  

- **Expected Response:**  
  - **Status:** 200 OK  
  - **Body:**  
    ```json
    {
      "message": "Product Deleted Successfully"
    }
    ```
#### 🗑️ **5. Delete Order**
- **Method:** DELETE  
- **URL:** `https://rahulshettyacademy.com/api/ecom/order/delete-order/{{orderId}}`  
- **Headers:**  
  - `Authorization: Bearer {{token}}`  
  - `Content-Type: application/json`  

- **Expected Response:**  
  - **Status:** 200 OK  
  - **Body:**  
    ```json
    {
      "message": "Orders Deleted Successfully"
    }
    ```

---

### 🚀 **How to Import This in Postman**
1. Open Postman.  
2. Click on **"Import"** > **"Raw Text"**.  
3. Paste the JSON (if I generate it for you) or manually create requests.  
4. Hit **"Import"**.
