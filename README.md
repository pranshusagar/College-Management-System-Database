# College-Management-System-Database
This project is a basic implementation of a relational database schema for a College Management System using SQL. It covers the creation of tables for students, courses, and enrollments, along with appropriate keys and relationships.

📚 Project Overview
The main goal of this project is to design a well-structured schema that demonstrates:

Student records
Courses offered by the college
Enrollment details (which student enrolled in which course)
The goal is to build a well-structured, normalized schema using SQL with clearly defined primary and foreign keys.

This project is part of my learning and internship submission, aimed at demonstrating my understanding of database design concepts.

📌 Domain: College Management
Entities:
Students: Stores student details
Courses: Contains course information
Enrollments: Records which students are enrolled in which courses

💻 SQL Script
```

-- Create the database
CREATE DATABASE College;
USE College;

-- Create Students table
CREATE TABLE Students (
    StudentID INT PRIMARY KEY,
    Name VARCHAR(50) NOT NULL,
    Email VARCHAR(60) UNIQUE,
    DOB DATE
);

-- Create Courses table
CREATE TABLE Courses (
    CourseID INT PRIMARY KEY,
    CourseName VARCHAR(50) NOT NULL,
    Credits INT CHECK (Credits > 0)
);

-- Create Enrollments table
CREATE TABLE Enrollments (
    EnrollmentID INT PRIMARY KEY,
    StudentID INT,
    CourseID INT,
    EnrollmentDate DATE,
    FOREIGN KEY (StudentID) REFERENCES Students(StudentID),
    FOREIGN KEY (CourseID) REFERENCES Courses(CourseID)
);


📊 ER Diagram
[Students]           [Courses]
+------------+       +-------------+
| StudentID  |       | CourseID    |
| Name       |       | CourseName  |
| Email      |       | Credits     |
| DOB        |       +-------------+
+------------+             |
        |                  |
        |                  |
        |                  |
        |      [Enrollments]
        |      +------------------+
        +----> | EnrollmentID     |
               | StudentID (FK)   |
               | CourseID  (FK)   |
               | EnrollmentDate   |
               +------------------+
