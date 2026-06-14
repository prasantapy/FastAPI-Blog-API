*FastAPI Blog API**

A robust, backend API built with FastAPI and SQLAlchemy for managing blog posts and users. This application features user authentication, database integration using PostgreSQL, and a complete set of CRUD (Create, Read, Update, Delete) operations.

---

## **Tech Stack**

| Technology | Purpose |
| :--- | :--- |
| **FastAPI** | Web framework for building the API endpoints. |
| **SQLAlchemy** | Object-Relational Mapping (ORM) for database interactions. |
| **PostgreSQL** | Relational database for storing users and posts. |
| **Pydantic** | Data validation and schema definition (via `schemas`). |
| **Uvicorn** | ASGI server to run the application. |

---

## **Features**

* **User Management:** Secure user registration with password hashing.
* **Authentication:** Dependency injection to ensure only authorized users can create, update, or delete posts.
* **Post Management:** Full CRUD capabilities for blog posts linked to specific users.
* **PostgreSQL Integration:** Pre-configured SQLAlchemy engine and session management.

---

## **API Endpoints**

### **Posts Router (`/posts`)**

| Method | Endpoint | Description | Requires Auth |
| :--- | :--- | :--- | :---: |
| `POST` | `/posts/` | Create a new blog post. | ✅ Yes |
| `GET` | `/posts/posts` | Check database connection / Retrieve posts. | ❌ No |
| `PUT` | `/posts/{post_id}` | Update an existing post. *(See Dev Notes)* | ✅ Yes |
| `DELETE` | `/posts/{post_id}` | Delete a post by its ID. | ✅ Yes |

---

## **Project Structure Overview**

Based on the provided snippets, the application is organized into the following modules:

* **`app/main.py`** *(Assumed)*: The entry point of the FastAPI application.
* **`app/database.py`**: Contains PostgreSQL connection URL (`DATABASE_URL`), SQLAlchemy `engine`, and `SessionLocal`.
* **`app/deps.py`**: Contains FastAPI dependencies like `get_db` for database session management.
* **`app/models.py`**: Defines SQLAlchemy ORM models (`User`, `Post`).
* **`app/schemas.py`**: Defines Pydantic models for request/response validation (`PostCreate`).
* **`app/crud.py`**: Contains reusable database interaction functions (`create_user`, `update_post`, etc.).
* **`app/auth.py`**: Handles password hashing (`hash_password`) and retrieving the current user (`get_current_user`).

---

## **Getting Started**

### **1. Prerequisites**
* Python 3.8+
* PostgreSQL installed and running.

### **2. Database Setup**
Ensure you have a PostgreSQL database created that matches the configuration in your `database.py` file:
> `postgresql://postgres:admin@localhost:5432/blog_api_db`

### **3. Installation**
Clone the repository and install the required dependencies:
