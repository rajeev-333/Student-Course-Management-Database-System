# Student Course Management System (SQL)

## Overview

This project is a **Student Course Management System** built using **MySQL**. It models a small college environment with students, courses, enrollments, and grades, and uses SQL for both transactional operations (CRUD) and analytical reporting. The goal is to demonstrate solid understanding of relational database design and data‑analysis‑oriented SQL.

## Database Design

The database `student_management` is normalized up to **Third Normal Form (3NF)** and contains 4 core tables:

### 1. students

- `student_id` INT PRIMARY KEY AUTO_INCREMENT  
- `full_name` VARCHAR(100) NOT NULL  
- `email` VARCHAR(100) UNIQUE  
- `department` VARCHAR(50)  
- `admission_year` INT  
- `phone` VARCHAR(15)  

### 2. courses

- `course_id` INT PRIMARY KEY AUTO_INCREMENT  
- `course_name` VARCHAR(100) NOT NULL  
- `course_code` VARCHAR(20) UNIQUE  
- `credits` INT  
- `department` VARCHAR(50)  

### 3. enrollments

Represents the many‑to‑many relationship between students and courses.

- `enrollment_id` INT PRIMARY KEY AUTO_INCREMENT  
- `student_id` INT NOT NULL  
- `course_id` INT NOT NULL  
- `enrollment_date` DATE  
- `semester` VARCHAR(20)  
- `FOREIGN KEY (student_id)` REFERENCES `students(student_id)`  
- `FOREIGN KEY (course_id)` REFERENCES `courses(course_id)`  

### 4. grades

Stores assessment details per enrollment.

- `grade_id` INT PRIMARY KEY AUTO_INCREMENT  
- `enrollment_id` INT NOT NULL  
- `marks_obtained` INT  
- `total_marks` INT  
- `letter_grade` VARCHAR(2)  
- `FOREIGN KEY (enrollment_id)` REFERENCES `enrollments(enrollment_id)`  

This structure avoids redundancy and ensures that every enrollment and grade references valid students and courses via foreign keys.

## Features

- **Normalized schema (3NF)** for clean, analysis‑ready data.
- **Primary and foreign keys** to enforce referential integrity.
- **CRUD operations** on students, courses, enrollments, and grades.
- **Analytical SQL** using JOIN, GROUP BY, and aggregate functions to:
  - Analyze student performance.
  - Count students per department.
  - Rank courses by enrollment.
- **View** for performance summarization.
- **Stored procedure** for per‑student transcript reports.

## SQL Scripts

A typical repo layout for this project:

- `01_schema.sql` – create database and tables  
- `02_sample_data.sql` – insert sample rows  
- `03_view_and_procedure.sql` – create view and stored procedure  
- `04_queries.sql` – example analytical queries  

You can run these sequentially in MySQL Workbench.

##How to Run
Install MySQL and open MySQL Workbench.

Run 01_schema.sql to create the database and tables.

Run 02_sample_data.sql to insert sample data.

Run 03_view_and_procedure.sql to create the view and stored procedure.

Use 04_queries.sql or write your own queries to explore the data:

  -SELECT * FROM vw_student_performance;

  -CALL get_student_transcript(1);

##Skills Demonstrated
Relational database design and normalization (3NF)

Use of primary and foreign keys for data integrity

Analytical SQL for reporting and trend analysis

Views and stored procedures for reusable data access patterns
