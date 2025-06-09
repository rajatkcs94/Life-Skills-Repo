# Life-Skills

Life Skills at Mountblue

# 1. Introduction to SQL
SQL is a structured query language used to interact with the database. It enables users to insert, delete, update, and retrieve data from the database.


## 2. SQL Basics

### 2.1 Creating a Table

CREATE TABLE employees (
    id INT PRIMARY KEY,
    name VARCHAR(100),
    department VARCHAR(50),
    salary DECIMAL(10,2)
);

### 2.2 Inserting data into tables

INSERT INTO employees (id, name, department, salary)
VALUES
(1, 'Alice', 'HR', 50000),
(2, 'Bob', 'Engineering', 70000),
(3, 'Charlie', 'Engineering', 75000),
(4, 'Diana', 'Marketing', 60000);

### 2.3 Basic select query
SELECT * FROM employees;

### 2.4 WHERE Clause

SELECT name, salary
FROM employees
WHERE department = 'Engineering';

## 3. SQL Joins

Joins are used to combine rows from two or more tables based on a related column.
### 3.1 Sample Tables

CREATE TABLE departments (
    dept_id INT PRIMARY KEY,
    dept_name VARCHAR(50)
);

INSERT INTO departments VALUES
(1, 'HR'), (2, 'Engineering'), (3, 'Marketing');

CREATE TABLE employees (
    emp_id INT PRIMARY KEY,
    emp_name VARCHAR(100),
    dept_id INT,
    FOREIGN KEY (dept_id) REFERENCES departments(dept_id)
);

INSERT INTO employees VALUES
(1, 'Alice', 1),
(2, 'Bob', 2),
(3, 'Charlie', 2),
(4, 'Diana', 3);

### 3.2 INNER JOIN

SELECT e.emp_name, d.dept_name
FROM employees e
INNER JOIN departments d
ON e.dept_id = d.dept_id;

Returns only matching rows from both tables.
### 3.3 LEFT JOIN

SELECT e.emp_name, d.dept_name
FROM employees e
LEFT JOIN departments d
ON e.dept_id = d.dept_id;

Returns all employees, including those without a department.
### 3.4 RIGHT JOIN

SELECT e.emp_name, d.dept_name
FROM employees e
RIGHT JOIN departments d
ON e.dept_id = d.dept_id;

Returns all departments, even if no employee belongs to them.
### 3.5 FULL OUTER JOIN (Simulated)

SELECT e.emp_name, d.dept_name
FROM employees e
LEFT JOIN departments d ON e.dept_id = d.dept_id

UNION

SELECT e.emp_name, d.dept_name
FROM employees e
RIGHT JOIN departments d ON e.dept_id = d.dept_id;

## 4. Aggregation Functions

Used for summarizing data.
### 4.1 COUNT

SELECT COUNT(*) AS total_employees FROM employees;

### 4.2 SUM

SELECT SUM(salary) AS total_salary FROM employees;

### 4.3 AVG

SELECT AVG(salary) AS avg_salary FROM employees;

### 4.4 MAX / MIN

SELECT MAX(salary) AS highest, MIN(salary) AS lowest FROM employees;

### 4.5 GROUP BY

SELECT department, COUNT(*) AS num_employees
FROM employees
GROUP BY department;

### 4.6 HAVING

SELECT department, AVG(salary) AS avg_salary
FROM employees
GROUP BY department
HAVING AVG(salary) > 60000;

## Resources
https://sqlbolt.com/
https://www.geeksforgeeks.org/sql-tutorial/
https://www.tutorialspoint.com/sql/index.htm&ved=2ahUKEwjj36qkqNWNAxVzfWwGHd5mH2gQFnoECAkQAQ&usg=AOvVaw22TQWVfr7Z6R9WtTfXuFSr
