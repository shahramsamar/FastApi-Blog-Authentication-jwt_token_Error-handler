# FastAPI Blog Authentication with JWT and Error Handling

This repository demonstrates how to build a blog application using **FastAPI**, focusing on implementing JWT-based authentication and custom error handling. The project showcases secure user authentication and robust error management for API endpoints.

## Features

- JWT-based user authentication for secure access control.
- Custom error handling for improved API usability.
- CRUD operations for blog posts.
- User registration and login functionalities.
- Structured and modular FastAPI project.

## Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/shahramsamar/FastApi-Blog-Authentication-jwt_token_Error-handler.git
   ```

2. Navigate to the project directory:
   ```bash
   cd FastApi-Blog-Authentication-jwt_token_Error-handler
   ```

3. Create and activate a virtual environment:
   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   ```

4. Install the dependencies:
   ```bash
   pip install -r requirements.txt
   ```

5. Run the application:
   ```bash
   uvicorn main:app --reload
   ```

6. Access the API documentation:
   - Interactive API docs: `http://127.0.0.1:8000/docs`
   - Alternative API docs: `http://127.0.0.1:8000/redoc`

## API Endpoints

### User Authentication

- **POST** `/register/`: Register a new user.
- **POST** `/login/`: Login and receive a JWT token.

### Blog Posts

- **GET** `/posts/`: Retrieve all posts.
- **GET** `/posts/{post_id}/`: Retrieve a specific post by ID.
- **POST** `/posts/`: Create a new post (requires authentication).
- **PUT** `/posts/{post_id}/`: Update a post (requires authentication).
- **DELETE** `/posts/{post_id}/`: Delete a post (requires authentication).

### Error Handling

Custom error responses ensure clarity and consistency in error messages, improving the client experience when interacting with the API.

## Example Code

### JWT Token Creation Example
```python
from datetime import datetime, timedelta
from jose import jwt

SECRET_KEY = "your_secret_key"
ALGORITHM = "HS256"


def create_access_token(data: dict):
    to_encode = data.copy()
    expire = datetime.utcnow() + timedelta(minutes=30)
    to_encode.update({"exp": expire})
    return jwt.encode(to_encode, SECRET_KEY, algorithm=ALGORITHM)
```

## Usage

1. Register a user by sending a POST request to `/register/` with user details.
2. Login with the registered credentials to receive a JWT token.
3. Use the JWT token in the `Authorization` header as `Bearer <token>` to access protected endpoints.

Example request:
```bash
curl -X POST "http://127.0.0.1:8000/login/" -H "Content-Type: application/json" -d '{"username": "user1", "password": "password123"}'
```

## Requirements

- Python 3.7+
- FastAPI
- Uvicorn
- PyJWT (jose)
- SQLAlchemy

## Contributing

Contributions are welcome! Please follow these steps:

1. Fork the repository.
2. Create a new branch for your feature or bugfix.
3. Commit your changes with clear messages.
4. Push your branch and create a pull request.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for more details.

## Contact

- **Author**: Shahramsamar
- **Email**: [shahramsamar2010@gmail.com](mailto:shahramsamar2010@gmail.com)
- **GitHub**: [Shahramsamar](https://github.com/shahramsamar)

![Alt](https://repobeats.axiom.co/api/embed/eabe6508a91fa38b4ace0060919094363916f544.svg "Repobeats analytics image")
