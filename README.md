# 📚 Library Management System (DBMS Project)

> A relational database management system designed to automate library operations, book indexing, member registrations, issuing/returning workflows, and fine management.

---

## 📌 Table of Contents
- [Overview](#-overview)
- [Key Features](#-key-features)
- [Database Schema & Architecture](#-database-schema--architecture)
  - [Core Entities](#core-entities)
  - [ER Diagram & Relations](#er-diagram--relations)
- [Tech Stack](#-tech-stack)
- [Getting Started](#-getting-started)
  - [Prerequisites](#prerequisites)
  - [Database Setup](#database-setup)
- [Key SQL Operations & Stored Procedures](#-key-sql-operations--stored-procedures)
- [Future Roadmap](#-future-roadmap)
- [Contributing](#-contributing)
- [License & Contact](#-license--contact)

---

## 📖 Overview

The **Library Management System** is a structured database project built to manage the daily administrative tasks of a modern library. It provides a reliable structure for tracking book inventories, managing student/staff memberships, monitoring borrowing and return dates, and automatically calculating overdue fines while maintaining strict relational integrity.

---

## ✨ Key Features

* 📖 **Catalog & Book Management:** Organize books by categories, genres, authors, publishers, and ISBNs.
* 👨‍🎓 **Member Management:** Maintain records for students, faculty, and general members with active membership statuses.
* 🔄 **Issue & Return Tracking:** Track active book loans, due dates, renewal histories, and return confirmations.
* 💰 **Fine & Penalty Calculation:** Automated tracking of overdue books and fine calculations based on return delays.
* 🔍 **Search & Indexing:** Optimized queries for finding books by title, author, category, or availability status.

---

## 🏗️ Database Schema & Architecture

### Core Entities
* **Books:** `Book_ID`, `ISBN`, `Title`, `Author_ID`, `Category_ID`, `Publisher`, `Publication_Year`, `Total_Copies`, `Available_Copies`
* **Authors:** `Author_ID`, `First_Name`, `Last_Name`, `Biography`
* **Categories / Genres:** `Category_ID`, `Category_Name`, `Description`
* **Members / Users:** `Member_ID`, `First_Name`, `Last_Name`, `Email`, `Phone`, `Membership_Date`, `Status`
* **Loans / Issue Records:** `Loan_ID`, `Book_ID`, `Member_ID`, `Issue_Date`, `Due_Date`, `Return_Date`, `Status`
* **Fines:** `Fine_ID`, `Loan_ID`, `Fine_Amount`, `Payment_Status`, `Paid_Date`

### ER Diagram & Relations
```text
 +--------------+       1:N       +--------------+       1:N       +--------------+
 |   Authors    | ───────────────> |    Books     | <─────────────── |  Categories  |
 +--------------+                  +--------------+                  +--------------+
                                          │
                                     1:N  │
                                          ▼
 +--------------+       1:N       +--------------+       1:1       +--------------+
 |   Members    | ───────────────> |    Loans     | ───────────────> |    Fines     |
 +--------------+                  +--------------+                  +--------------+
