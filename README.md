# Student Database Project

## Introduction
This project builds a **student database** using PostgreSQL, allowing you to:
- Store information about **students, majors, and courses**.
- Automatically import data from CSV files.
- Run SQL queries through Bash scripts to analyze data (GPA, course lists, majors, etc.).

## Project Structure
```
.
├── students.sql        # SQL file to create schema and sample data for the database
├── insert_data.sh      # Bash script to import data from CSV files into the database
├── student_info.sh     # Bash script to run analytical queries on the database
├── data/courses.csv         # Data file for courses and majors
├── data/students.csv        # Data file for students
└── README.md           # Documentation
```

## Requirements
- PostgreSQL (>= 12)
- Bash Shell
- PostgreSQL user `freecodecamp` (can be changed in the scripts)

## Setup
1. Create the database and schema from the SQL dump:
   ```bash
   psql -U freecodecamp -f students.sql
   ```
   > This file creates the `students` database with the tables `students`, `majors`, `courses`, and `majors_courses`.

2. Import data from CSV files:
   ```bash
   bash insert_data.sh
   ```
   - This script will:
     - Truncate old data (`TRUNCATE`).
     - Insert data from `courses.csv` into **majors**, **courses**, and **majors_courses**.
     - Insert data from `students.csv` into the **students** table.

3. Run the query script:
   ```bash
   bash student_info.sh
   ```
   - This script runs multiple SQL queries, such as:
     - List of students with a 4.0 GPA.
     - Courses whose first letter comes before "D" in the alphabet.
     - Average GPA of all students.
     - Majors with no students enrolled or with a student whose name contains "ma".
     - Courses with only one student enrolled.

## Notes
- You can edit the database connection in the `PSQL` variable inside the scripts:
  ```bash
  PSQL="psql -X --username=freecodecamp --dbname=students --no-align --tuples-only -c"
  ```
- To reset the entire database, run:
  ```bash
  psql -U freecodecamp -f students.sql
  bash insert_data.sh
  ```
