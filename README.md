# Flask URL Shortener

A simple URL shortener application built with Flask, featuring a clean and modern UI. This project allows users to shorten URLs and view statistics about their shortened links.

## Features

- Shorten long URLs into short and manageable links.
- View statistics for each shortened URL, including clicks and creation date.
- User-friendly web interface with Bootstrap for responsive design.

## Table of Contents

- [Installation](#installation)
- [Usage](#usage)
- [Technology Stack](#technology-stack)
- [Contributing](#contributing)
- [License](#license)

## Installation

To get started with this project, follow these steps:

### 1. Set Up Python Virtual Environment

#### Create a Virtual Environment

Navigate to your project directory:

```bash
cd /path/to/your/project/directory
```

Create the virtual environment:

```bash
python -m venv env
```

#### Activate the Virtual Environment

Activate the virtual environment using the appropriate command for your operating system:

- **Windows (cmd.exe or PowerShell):**

  ```bash
  env\Scripts\activate
  ```

- **Git Bash on Windows:**

  ```bash
  source env/Scripts/activate
  ```

- **Unix or macOS:**

  ```bash
  source env/bin/activate
  ```

### 2. Install Necessary Packages

Make sure you are in the virtual environment and install the required packages:

```bash
pip install flask hashids
```

### 3. Create and Initialize the SQLite Database

#### Create a SQL Schema File

Create or open `schema.sql` in a text editor and add the following SQL commands:

```sql
DROP TABLE IF EXISTS urls;

CREATE TABLE urls (
    id INTEGER PRIMARY KEY AUTOINCREMENT,
    created TIMESTAMP NOT NULL DEFAULT CURRENT_TIMESTAMP,
    original_url TEXT NOT NULL,
    clicks INTEGER NOT NULL DEFAULT 0
);
```

#### Initialize the Database

Create a Python script `init_db.py` with the following content:

```python
import sqlite3

connection = sqlite3.connect('database.db')

with open('schema.sql') as f:
    connection.executescript(f.read())

connection.commit()
connection.close()
```

Run the script to initialize the database:

```bash
python init_db.py
```

### 4. Set Up and Run the Flask Application

#### Set Environment Variables

Set the environment variables for Flask (replace `app` with the name of your Flask app):

```bash
export FLASK_APP=app
export FLASK_ENV=development
```

#### Run the Flask Application

Start the Flask development server:

```bash
flask run
```

With these steps, your Python environment and Flask application should be correctly set up and running. You can now access your application in the browser at `http://127.0.0.1:5000`.

## Usage

1. **Shorten a URL:**

   - Navigate to the home page.
   - Enter the URL you want to shorten and click "Submit."
   - The shortened URL will be displayed, which you can use to redirect to the original URL.

2. **View statistics:**

   - Navigate to the "Stats" page to view statistics for all shortened URLs, including the number of clicks and creation date.

## Technology Stack

- **Flask**: Web framework for building the application.
- **Bootstrap**: CSS framework for responsive design.
- **SQLite**: Lightweight database for storing URLs and statistics.

## Output Images
![Screenshot 2024-08-14 172954](https://github.com/user-attachments/assets/a819eec1-2ac3-489e-a7a4-ce9c5fb6b939)


![Screenshot 2024-08-14 173021](https://github.com/user-attachments/assets/e65c68a4-1e01-45a0-948a-d8e2cdbb2f7b)


![Screenshot 2024-08-14 173039](https://github.com/user-attachments/assets/cf78196e-cd85-43df-976c-2a56a160abe7)


## Output Video


https://github.com/user-attachments/assets/5cd90936-def5-4e23-887d-ba35a15ae6fc




## Contributing

Contributions are welcome! If you'd like to contribute to this project, please follow these guidelines:

1. Fork the repository.
2. Create a new branch for your feature or bug fix.
3. Commit your changes and push them to your branch.
4. Open a pull request with a description of your changes.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Acknowledgments

- Thanks to the Flask and Bootstrap communities for providing excellent frameworks and tools.
- Special thanks to anyone who contributed to the development and improvement of this project.
