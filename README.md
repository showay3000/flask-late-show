# flask-late-show
Late Show API - Heroes and Superpowers Tracking
Overview
This is a Flask-based API for tracking episodes, guests, and their appearances on a late show. The API allows you to manage and query information about show episodes, celebrity guests, and their appearances with ratings.

Features
CRUD operations for episodes, guests, and appearances

Relationship management between episodes and guests through appearances

Data validation for appearance ratings

Detailed serialization of related data

Database Schema
The database consists of three main models:

Episode

id: Integer (Primary Key)

date: String

number: Integer

Guest

id: Integer (Primary Key)

name: String

occupation: String

Appearance (Join Table)

id: Integer (Primary Key)

rating: Integer (1-5)

episode_id: Integer (Foreign Key)

guest_id: Integer (Foreign Key)

API Endpoints
Episodes
GET /episodes - Get all episodes

GET /episodes/:id - Get a specific episode with appearances

Guests
GET /guests - Get all guests

Appearances
POST /appearances - Create a new appearance record

Setup Instructions
Prerequisites
Python 3.x

PostgreSQL

pip

Installation
Clone the repository:

bash
Copy
git clone <repository-url>
cd lateshow-firstname-lastname
Create and activate a virtual environment:

bash
Copy
python -m venv venv
source venv/bin/activate  # On Windows use `venv\Scripts\activate`
Install dependencies:

bash
Copy
pip install -r requirements.txt
Set up the database:

Create a PostgreSQL database

Update the database URI in config.py

Run migrations:

bash
Copy
flask db init
flask db migrate
flask db upgrade
Seed the database:

bash
Copy
python seed.py
Start the server:

bash
Copy
python app.py
Usage
After starting the server, the API will be available at http://localhost:5000. You can test the endpoints using Postman or any HTTP client.

Example Requests
Get all episodes:

bash
Copy
GET http://localhost:5000/episodes
Get a specific episode:

bash
Copy
GET http://localhost:5000/episodes/1
Get all guests:

bash
Copy
GET http://localhost:5000/guests
Create an appearance:

bash
Copy
POST http://localhost:5000/appearances
Content-Type: application/json

{
  "rating": 5,
  "episode_id": 1,
  "guest_id": 1
}
Error Handling
The API returns appropriate HTTP status codes along with JSON error messages when something goes wrong.

Example error response:

json
Copy
{
  "error": "Episode not found"
}
Validation Rules
Appearance rating must be between 1 and 5 (inclusive)

All required fields must be provided when creating records

Testing
To test the API:

Import the provided Postman collection

Run the tests in the collection

Verify all endpoints return the expected responses