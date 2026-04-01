# 📚 Online Book Store — SQL Analysis Project

A structured SQL project that models and analyzes an online book store database. It covers database design, data exploration, and business insights using MySQL — ranging from beginner-friendly queries to advanced multi-table analytics.

---

## 📁 Project Structure

```
online-book-store/
│
├── Books.csv                              # Book catalog dataset (500 records)
├── Customers.csv                          # Customer dataset (500 records)
├── Orders.csv                             # Orders dataset (500 records)
└── Online Book store project.sql          # All SQL queries (basic + advanced)
```

---

## 🗃️ Database Schema

### `Books`
| Column           | Type    | Description                        |
|------------------|---------|------------------------------------|
| Book_ID          | INT     | Primary key                        |
| Title            | TEXT    | Book title                         |
| Author           | TEXT    | Author name                        |
| Genre            | TEXT    | Genre (Fiction, Fantasy, etc.)     |
| Published_Year   | INT     | Year of publication                |
| Price            | DECIMAL | Book price (USD)                   |
| Stock            | INT     | Units available in inventory       |

### `Customers`
| Column      | Type | Description              |
|-------------|------|--------------------------|
| Customer_ID | INT  | Primary key              |
| Name        | TEXT | Full name                |
| Email       | TEXT | Email address            |
| Phone       | TEXT | Contact number           |
| City        | TEXT | City of residence        |
| Country     | TEXT | Country of residence     |

### `Orders`
| Column       | Type    | Description                         |
|--------------|---------|-------------------------------------|
| Order_ID     | INT     | Primary key                         |
| Customer_ID  | INT     | Foreign key → Customers             |
| Book_ID      | INT     | Foreign key → Books                 |
| Order_Date   | DATE    | Date the order was placed           |
| Quantity     | INT     | Number of copies ordered            |
| Total_Amount | DECIMAL | Total value of the order (USD)      |

---

## 🔍 SQL Queries Overview

### 🟢 Basic Queries (10)

| # | Question |
|---|----------|
| 1 | Retrieve all books in the "Fiction" genre |
| 2 | Find books published after the year 1950 |
| 3 | List all customers from Canada |
| 4 | Show orders placed in November 2023 |
| 5 | Retrieve the total stock of books available |
| 6 | Find the details of the most expensive book |
| 7 | Show all customers who ordered more than 1 quantity |
| 8 | Retrieve all orders where total amount exceeds $20 |
| 9 | List all distinct genres in the Books table |
| 10 | Find the book with the lowest stock |

### 🔴 Advanced Queries (9)

| # | Question |
|---|----------|
| 1 | Total number of books sold per genre |
| 2 | Average price of books in the "Fantasy" genre |
| 3 | Customers who placed at least 2 orders |
| 4 | Most frequently ordered book |
| 5 | Top 3 most expensive Fantasy books |
| 6 | Total quantity of books sold per author |
| 7 | Cities where customers spent over $30 |
| 8 | Customer who spent the most on orders |
| 9 | Remaining stock after fulfilling all orders |

---

## 🚀 Getting Started

### Prerequisites
- MySQL 8.0+ (or any MySQL-compatible client like MySQL Workbench, DBeaver, etc.)

### Setup Instructions

1. **Clone the repository**
   ```bash
   git clone https://github.com/parth-visualize/Online-Book-Store-SQL-Analysis.git
   cd online-book-store
   ```

2. **Create the database and tables**
   ```sql
   CREATE DATABASE online_book_store;
   USE online_book_store;
   ```

3. **Create the tables**
   ```sql
   CREATE TABLE Books (
     Book_ID INT PRIMARY KEY,
     Title TEXT,
     Author TEXT,
     Genre TEXT,
     Published_Year INT,
     Price DECIMAL(10,2),
     Stock INT
   );

   CREATE TABLE Customers (
     Customer_ID INT PRIMARY KEY,
     Name TEXT,
     Email TEXT,
     Phone TEXT,
     City TEXT,
     Country TEXT
   );

   CREATE TABLE Orders (
     Order_ID INT PRIMARY KEY,
     Customer_ID INT,
     Book_ID INT,
     Order_Date DATE,
     Quantity INT,
     Total_Amount DECIMAL(10,2),
     FOREIGN KEY (Customer_ID) REFERENCES Customers(Customer_ID),
     FOREIGN KEY (Book_ID) REFERENCES Books(Book_ID)
   );
   ```

4. **Import the CSV data** using MySQL Workbench's Table Data Import Wizard, or via CLI:
   ```bash
   mysqlimport --local --fields-terminated-by=',' --lines-terminated-by='\n' \
     --ignore-lines=1 online_book_store Books.csv Customers.csv Orders.csv
   ```

5. **Run the queries**
   Open `Online Book store project.sql` in your SQL client and execute the queries.

---

## 📊 Key Insights (Sample)

- **Total revenue** can be calculated by summing all `Total_Amount` values in the Orders table.
- **Stock analysis** — the remaining stock query joins Books and Orders to show real-time inventory after sales.
- **Customer segmentation** — identify high-value customers by grouping total spend.
- **Genre performance** — aggregate order quantities by genre to find best-selling categories.

---

## 🛠️ Tools Used

- **MySQL** — Database management and query execution
- **MySQL Workbench** — SQL development environment
- **CSV** — Raw data format for importing records

---

## 📌 Notes

- All 3 datasets contain **500 records** each.
- The SQL file contains both **DDL** (database creation) and **DML** (select queries) statements.
- Queries use `JOIN`, `GROUP BY`, `HAVING`, `ORDER BY`, `COALESCE`, and aggregate functions.

---

## 🙋‍♂️ Author
**Parth**  


If you like this project, feel free to ⭐ the repository.
