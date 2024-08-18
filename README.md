# Books_Buzz

# Setup Instructions

1. Clone the Repository:
  git clone https://github.com/ravilla7032/books_project_by_anilravilla.git
  cd google_books

2. Create and Activate Virtual Environment:
  python -m venv venv
  On Windows use : source venv/bin/activate // On Windows use `venv\Scripts\activate`

3. Install Dependencies:
  pip install -r requirements.txt

4. Create the PostgreSQL Database:
  Create a PostgreSQL database named books_buzz and a user named admin1 with the password admin@123. Grant all privileges on the database to this user.
  Save the database details for later use in a .env file with the following entries: DB_NAME=books_buzz, DB_USER=admin1, and DB_PASSWORD=admin@123.
  
5. Configure Environment Variables:
   Create a .env file in the project root and add the following:
   ```plaintext
    DEBUG=1
    SECRET_KEY='django-insecure-fgi*9*)xsd=p=^d)$a*5b%ms^9efm4e*(7ybwk65xl3!u4+g1)'
   
    DB_ENGINE='django.db.backends.postgresql'
    DB_NAME= # DB name
    DB_USER= # DB user
    DB_PASSWORD= # password
    DB_HOST='localhost'
    DB_PORT='5432'
    
    DEFAULT_FROM_EMAIL= # your mail
    EMAIL_HOST_USER= # your mail
    EMAIL_HOST_PASSWORD= # your App password
    EMAIL_PORT=587
    EMAIL_USE_TLS=True

7. Apply Migrations:

  • python manage.py makemigrations
  • python manage.py migrate


# Api Endpoints

Access all API endpoints through the Postman collection link below. This collection provides comprehensive API documentation, including details on requests, responses, exceptions, and additional notes for each endpoint.
This collection provides comprehensive API documentation, including details on requests, responses, exceptions, and additional notes for each endpoint.

Postman Collection Link: https://documenter.getpostman.com/view/37485860/2sA3rxrtna


# Google Books API Integration

The BooksConfigurations API endpoint is designed to search for books using the Google Books API. It allows users to search for books based on different criteria such as keyword, title, author, and categories. The results from the Google Books API are fetched, processed, and stored in the local database for further querying and retrieval.

Key Features:

1. Book Search
   
  --> The API accepts a search key and a search type as query parameters. The search type can be one of the following: "keyword", "title", "author", or "categories".
  --> The search key is used to query the Google Books API to retrieve a list of books that match the criteria.
  
2. Book Retrieval

  --> The API fetches book data from the Google Books API using the service.volumes().list(q=search_key).execute() method.
  --> The retrieved data includes information such as title, authors, categories, ISBN, cover picture, published date, and description.

3. Data Processing and Storage

  --> The API processes the retrieved book data to ensure it is in the correct format.
  --> Books and authors are saved to the local database. If an author or book already exists, it updates the existing record with the new information.

4. Display of Search Results

  --> After processing and storing the data, the API searches the local database based on the provided search type and key.
  --> It filters the results and returns a list of books that match the search criteria, including additional details such as the number of recommendations, comments, and average   rating.

5. Error Handling

  --> The API includes error handling to manage potential exceptions during data retrieval, processing, and storage, returning appropriate error messages if something goes wrong.
