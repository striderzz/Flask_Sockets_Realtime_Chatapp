# Flask WebSocket Chat App

A real-time chat room web application built with **Flask** and **Flask-SocketIO**.  
Users can create or join chat rooms using unique room codes and exchange messages instantly without refreshing the page.

---

## What is Flask?

**Flask** is a lightweight Python web framework used to build web applications quickly.  
It helps create routes, render HTML pages, handle forms, manage sessions, and connect backend logic with frontend pages.

In this project, Flask is used for:

- Rendering the home page and chat room page
- Handling user names and room codes
- Managing sessions
- Creating and joining chat rooms
- Running the backend server

---

## What are WebSockets?

**WebSockets** allow two-way real-time communication between the browser and the server.  
Unlike normal HTTP requests, where the browser must refresh or send repeated requests, WebSockets keep a live connection open.

This makes WebSockets useful for:

- Real-time chat apps
- Live notifications
- Multiplayer games
- Collaboration tools
- Live dashboards

In this project, WebSockets are implemented using **Flask-SocketIO**.

---

## Project Overview

This project is a simple real-time chat application where users can:

- Enter a username
- Create a new chat room
- Join an existing room using a room code
- Send and receive messages instantly
- See when users enter or leave the room

Each chat room is assigned a unique room code. Multiple users can join the same room and communicate in real time.

---

## Features

- Real-time messaging using WebSockets
- Create private chat rooms
- Join rooms using unique room codes
- User join and leave notifications
- Session-based username and room tracking
- Clean dark-themed user interface
- Message timestamps
- Simple and beginner-friendly Flask structure

---

## Tech Stack

- Python
- Flask
- Flask-SocketIO
- HTML
- CSS
- JavaScript
- WebSockets

---

## Project Structure

```bash
Flask_Sockets_Chatapp/
│
├── app.py
├── templates/
│   ├── home.html
│   └── room.html
│
├── static/
│   ├── css/
│   │   └── style.css
│   └── js/
│       └── script.js
│
└── README.md
```

---

## How It Works

The user first enters their name on the home page.

They can either:

1. Create a new room
2. Join an existing room using a room code

When a room is created, the backend generates a random unique room code.

```python
def generate_unique_code(length):
    while True:
        code = ""
        for _ in range(length):
            code += random.choice(ascii_uppercase)

        if code not in rooms:
            break

    return code
```

The room code is stored on the server, and users who enter the same code are connected to the same chat room.

---

## WebSocket Events

This app uses Socket.IO events to manage real-time communication.

### User Joins Room

When a user joins a room, they are added to the Socket.IO room.

```python
join_room(room)
```

A message is sent to everyone in that room saying the user has entered.

Example:

```text
Hasan has entered the room
```

---

### User Sends Message

When a user sends a message, the message is emitted to everyone connected to the same room.

Example:

```text
Hasan: Hello
Tom: Hey
```

---

### User Leaves Room

When a user disconnects, they are removed from the room.

```python
leave_room(room)
```

The app then notifies the remaining users.

Example:

```text
Tom has left the room
```

---

## Installation

Clone the repository:

```bash
git clone https://github.com/your-username/flask-websocket-chat-app.git
cd flask-websocket-chat-app
```

Create a virtual environment:

```bash
python -m venv venv
```

Activate the virtual environment.

On Windows:

```bash
venv\Scripts\activate
```

On macOS/Linux:

```bash
source venv/bin/activate
```

Install dependencies:

```bash
pip install flask flask-socketio
```

---

## Running the App

Run the Flask app:

```bash
python app.py
```

Then open your browser and go to:

```bash
http://127.0.0.1:5000
```

---

## Usage

1. Open the app in your browser.
2. Enter your username.
3. Click **Create Room** to generate a new room code.
4. Share the room code with another user.
5. The other user enters their name and the room code.
6. Both users can now chat in real time.

---

## Example Chat Room

```text
Chat Room: SJBP

Hasan has entered the room
Hasan: Hello
Hasan: how are you?
Tom has entered the room
Tom: hey
Tom: i am good not much
Tom has left the room
```

---

## Screenshots

### Chat Room Interface

![Chat Room Screenshot](screenshot.png)

---

## Key Concepts Learned

This project demonstrates important backend and real-time web development concepts:

- Flask routing
- HTML template rendering
- Form handling
- User sessions
- WebSocket communication
- Socket.IO rooms
- Real-time event handling
- Client-server communication
- Dynamic chat updates without page refresh

---

## Why This Project is Useful

This is a good beginner-to-intermediate Flask project because it teaches how real-time communication works in web applications.

It can also be extended into more advanced applications such as:

- Group chat app
- Private messaging system
- Online multiplayer lobby
- Live classroom chat
- Customer support chat system
- Real-time notification system

---

## Future Improvements

- Add user authentication
- Store chat messages in a database
- Add private one-to-one messaging
- Add typing indicators
- Add online user list
- Add file/image sharing
- Improve mobile responsiveness
- Add message delete/edit feature
- Add persistent chat history
- Deploy the app online using Render, Railway, or Heroku

---

## Requirements

```txt
Flask
Flask-SocketIO
```

You can also create a `requirements.txt` file:

```bash
pip freeze > requirements.txt
```

Then install dependencies using:

```bash
pip install -r requirements.txt
```

---

## Author

Developed by Hasan as a Flask WebSocket real-time chat application project.

---

## License

This project is open-source and available under the MIT License.
