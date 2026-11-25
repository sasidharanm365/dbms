# 📝 Notes Webpage – Database Management System

## 📌 Project Overview

The Notes Webpage is a database-driven web application designed to help users create, store, organize, update, and manage notes efficiently. It provides a centralized platform for managing notes digitally instead of relying on traditional paper-based methods.

The project uses MySQL as its primary database management system to maintain user details, notes, and categories in a structured relational database.

## 🎯 Objectives

- To develop an organized digital note management system.
- To store and manage user information and notes efficiently.
- To organize notes using different categories.
- To mark important notes using a pin feature.
- To perform CRUD operations using SQL queries.
- To maintain data integrity using primary keys and foreign keys.
- To retrieve information efficiently using SQL JOIN operations.

## 🛠️ Technologies Used

- **MySQL:** Database management system.
- **SQL:** Structured Query Language for database operations.
- **Relational Database Model:** To establish relationships between tables.

## ✨ Key Features

- **User Management:** Stores and manages user information.
- **Notes Management:** Create, view, update, and delete notes.
- **Category Management:** Organizes notes into categories such as Study, Personal, Work, Ideas, and Health.
- **Pin Important Notes:** Marks important notes for quick access.
- **Data Retrieval:** Retrieves information using SELECT queries.
- **JOIN Operations:** Combines data from multiple tables.
- **Data Integrity:** Uses primary keys, foreign keys, and constraints.

## 🗄️ Database Structure

Database Name: `notes_app`

The project consists of three main tables:

### 1. Users Table

| Column | Data Type | Description |
|---|---|---|
| user_id | INT | Primary Key, Auto Increment |
| name | VARCHAR(100) | User Name |
| email | VARCHAR(100) | Unique Email |

### 2. Categories Table

| Column | Data Type | Description |
|---|---|---|
| category_id | INT | Primary Key, Auto Increment |
| category_name | VARCHAR(100) | Category Name |

### 3. Notes Table

| Column | Data Type | Description |
|---|---|---|
| note_id | INT | Primary Key, Auto Increment |
| user_id | INT | Foreign Key |
| category_id | INT | Foreign Key |
| title | VARCHAR(200) | Note Title |
| content | TEXT | Note Content |
| is_pinned | BOOLEAN | Pin Status |
| created_at | TIMESTAMP | Creation Time |

## 🔗 Database Relationships

- One user can create multiple notes.
- One category can contain multiple notes.
- Each note belongs to a specific user.
- Each note can be associated with a category.
- Foreign keys maintain relationships between the tables.

### Referential Integrity

- `ON DELETE CASCADE` – Deleting a user automatically deletes their associated notes.
- `ON DELETE SET NULL` – Deleting a category sets the associated note's category ID to NULL.

## 💻 SQL Operations Implemented

The following SQL operations are implemented:

| Operation | SQL Command | Purpose |
|---|---|---|
| Create Database | CREATE DATABASE | Creates the database |
| Create Tables | CREATE TABLE | Creates database tables |
| Insert Records | INSERT | Adds users, categories, and notes |
| View Records | SELECT | Displays stored information |
| Join Tables | JOIN | Combines related table information |
| Filter Notes | WHERE | Displays pinned notes |
| Update Records | UPDATE | Modifies existing notes |
| Delete Records | DELETE | Removes unwanted notes |

## 🧩 Sample SQL Queries

### 1. Create Database

```sql
CREATE DATABASE IF NOT EXISTS notes_app;
USE notes_app;
```

### 2. Create Users Table

```sql
CREATE TABLE users (
    user_id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(100) NOT NULL,
    email VARCHAR(100) UNIQUE
);
```

### 3. Create Categories Table

```sql
CREATE TABLE categories (
    category_id INT AUTO_INCREMENT PRIMARY KEY,
    category_name VARCHAR(100)
);
```

### 4. Create Notes Table

```sql
CREATE TABLE notes (
    note_id INT AUTO_INCREMENT PRIMARY KEY,
    user_id INT,
    category_id INT,
    title VARCHAR(200),
    content TEXT,
    is_pinned BOOLEAN DEFAULT FALSE,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,

    FOREIGN KEY (user_id)
    REFERENCES users(user_id)
    ON DELETE CASCADE,

    FOREIGN KEY (category_id)
    REFERENCES categories(category_id)
    ON DELETE SET NULL
);
```

### 5. Insert Records

```sql
INSERT INTO users (name, email) VALUES
('Sasi', 'sasi@gmail.com'),
('Varsha', 'varshan@gmail.com'),
('Arun', 'arun@gmail.com'),
('Divya', 'divya@gmail.com'),
('Rahul', 'rahul@gmail.com');
```

### 6. Retrieve All Notes

```sql
SELECT * FROM notes;
```

### 7. JOIN Operation

```sql
SELECT
    n.note_id,
    u.name,
    n.title,
    c.category_name,
    n.is_pinned
FROM notes n
JOIN users u ON n.user_id = u.user_id
JOIN categories c ON n.category_id = c.category_id;
```

### 8. Display Pinned Notes

```sql
SELECT * FROM notes
WHERE is_pinned = TRUE;
```

### 9. Update Notes

```sql
UPDATE notes
SET title = 'Updated DBMS Notes'
WHERE note_id = 1;
```

### 10. Delete Notes

```sql
DELETE FROM notes
WHERE note_id = 2;
```

## 📸 Project Screenshots

### Notes Webpage
<!-- Add your Notes Webpage screenshot here -->

### Users Table
<!-- Add your Users Table screenshot here -->

### Categories Table
<!-- Add your Categories Table screenshot here -->

### Main Output Table
<!-- Add your Main Output screenshot here -->

### JOIN Output
<!-- Add your JOIN Output screenshot here -->

### UPDATE and DELETE Output
<!-- Add your UPDATE and DELETE screenshots here -->

## 🚀 Future Enhancements

- Implement user authentication and authorization.
- Add advanced search functionality.
- Introduce advanced filtering and sorting options.
- Integrate cloud storage for accessing notes across multiple devices.
- Implement automatic backup and data recovery.
- Add notifications and reminder systems.
- Support multimedia attachments such as images, audio, and documents.

## 🎓 Conclusion

The Notes Webpage project demonstrates the practical implementation of relational database concepts using MySQL and SQL. It provides an organized solution for managing users, notes, and categories through essential database operations.

The project demonstrates the use of CRUD operations, JOIN queries, primary keys, foreign keys, and referential integrity to ensure efficient data storage and retrieval.

## 👨‍💻 Project Team

- Niranjan S
- Pranav M
- Sasi Dharan M
- Vishnu Prasath S

## 📚 References

- Fundamentals of Database Systems – Elmasri & Navathe.
- Database Systems: Design, Implementation, & Management – Coronel & Morris.
- MySQL Reference Manual – https://dev.mysql.com/doc/
- W3Schools SQL Tutorial – https://www.w3schools.com/sql/