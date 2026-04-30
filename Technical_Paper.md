# SQL Report: Basics, Joins, and Aggregations

## Introduction

Structured Query Language is a standard language used to communicate with relational databases. It is used to create, manage, and manipulate data stored in tables. SQL allows users to insert, retrieve, update, and delete data efficiently. It plays a key role in software development, data analysis, and database management systems.

## SQL Basics

### Database and Table Creation

A database stores organized data, and tables store data in rows and columns.

```sql
CREATE DATABASE college;

USE college;

CREATE TABLE students (
    id INT PRIMARY KEY,
    name VARCHAR(50),
    age INT
);

CREATE TABLE marks (
    student_id INT,
    subject VARCHAR(50),
    score INT
);
```

### Basic Commands

#### Select

The SELECT statement retrieves data from a table.

```sql
SELECT * FROM students;
SELECT name FROM students WHERE age > 20;
```

#### Insert Into

The INSERT INTO statement adds new records to a table.

```sql
INSERT INTO students VALUES (1, 'Arjun', 20);
INSERT INTO students VALUES (2, 'Meena', 21);
```

#### Update

The UPDATE statement modifies existing records.

```sql
UPDATE students SET age = 22 WHERE id = 2;
```

#### Delete

The DELETE statement removes records from a table.

```sql
DELETE FROM students WHERE id = 1;
```

## Joins in SQL

Joins are used to combine data from multiple tables based on a common column. They help retrieve related information stored across tables.

### Inner Join

Returns only matching records from both tables.

```sql
SELECT students.name, marks.score
FROM students
INNER JOIN marks
ON students.id = marks.student_id;
```

### Left Join

Returns all records from the left table and matching records from the right table.

```sql
SELECT students.name, marks.score
FROM students
LEFT JOIN marks
ON students.id = marks.student_id;
```

### Right Join

Returns all records from the right table and matching records from the left table.

```sql
SELECT students.name, marks.score
FROM students
RIGHT JOIN marks
ON students.id = marks.student_id;
```

### Full Outer Join

Returns all records when there is a match in either table.

```sql
SELECT students.name, marks.score
FROM students
FULL OUTER JOIN marks
ON students.id = marks.student_id;
```

## Aggregations in SQL

Aggregation functions perform calculations on multiple rows and return a single value. They are useful for analyzing data.

### Common Aggregation Functions

* SUM calculates the total of a numeric column.
* MIN returns the smallest value in a column.
* MAX returns the largest value in a column.
* AVG calculates the average value of a column.

```sql
SELECT SUM(score) AS total_score FROM marks;
SELECT MIN(score) AS lowest_score FROM marks;
SELECT MAX(score) AS highest_score FROM marks;
SELECT AVG(score) AS average_score FROM marks;
```

### Group By

The GROUP BY clause groups rows with the same values.

```sql
SELECT student_id, AVG(score) AS average_score
FROM marks
GROUP BY student_id;
```

### Having

The HAVING clause filters grouped results.

```sql
SELECT student_id, AVG(score) AS avg_score
FROM marks
GROUP BY student_id
HAVING AVG(score) > 80;
```

## Conclusion

SQL is a powerful language for managing relational data. Basic commands help manipulate data, joins combine multiple tables, and aggregation functions help analyze data effectively. These concepts are essential for database management and application development.

## References

* https://www.w3schools.com/sql/  
* https://www.geeksforgeeks.org/sql-tutorial/  
