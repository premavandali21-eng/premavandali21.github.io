Welcome to My Blog

Hello! I am Prema B

This is my blog created using GitHub Pages. This blog presents my project on assistive communication technology, which focuses on enabling seamless interaction between hearing and deaf/mute individuals using Artificial Intelligence.

🚀 My Project
Bidirectional Indian Sign Language Recognition System
📌 Introduction

Communication is a fundamental part of human interaction. However, individuals who are deaf or mute rely on sign language, which many people do not understand. This creates a significant communication gap in everyday situations such as education, healthcare, and workplaces.

To address this challenge, this project introduces a real-time bidirectional translation system that converts:

✋ Indian Sign Language → Text
⌨️ Text/Speech → Sign Language

The system uses Computer Vision and Deep Learning to provide an accessible and inclusive communication solution.

💡 Project Overview

The system is designed as a web-based application that works in real time using a webcam. It captures hand gestures and processes them using advanced AI techniques.

Using MediaPipe, the system detects hand landmarks and extracts key features. These features are passed into a trained Deep Learning model to recognize gestures accurately.

For reverse communication, the system converts text or speech into ISL gestures using videos and images, allowing hearing individuals to communicate effectively with deaf users.

The project is lightweight, user-friendly, and does not require expensive hardware.

⚙️ Working Principle

The system works in two main phases:

🔹 Phase 1: Sign → Text

The webcam captures live video input. OpenCV processes each frame, and MediaPipe detects hand landmarks. These landmarks are converted into feature vectors and passed into a trained neural network model. The model predicts the gesture and displays the corresponding text in real time.

🔹 Phase 2: Text/Speech → Sign

The user enters text or uses voice input. The system processes the input and breaks it into words. Each word is matched with pre-stored gesture videos. If a word is not available, it is converted into individual letter gestures. The gestures are displayed sequentially for easy understanding.

🧠 Technologies Used
Python for backend development
OpenCV for video processing
MediaPipe for hand tracking
TensorFlow / Keras for deep learning
Flask for web framework
HTML, CSS, JavaScript for frontend
SQLite for database
🎯 Key Features
Real-time gesture recognition
Bidirectional communication (Sign ↔ Text)
Voice input support
User-friendly web interface
No need for special hardware
Designed for accessibility and inclusivity

🔄 Flowchart
https://github.com/premavandali21-eng/BIDIRECTIONAL-INDIAN-SIGN-LANGUAGE-RECOGNITION/blob/main/flowchart.png


🌍 Applications

This system can be used in various real-world scenarios. It is especially useful in education, where deaf students can communicate easily with teachers. In healthcare, it helps patients interact with doctors without needing interpreters.

It can also be used in public services, workplaces, and daily communication, promoting inclusivity and equal opportunities.

💻 Sample Code
from flask import Flask, Response
import cv2, mediapipe as mp
import numpy as np

app = Flask(__name__)
mp_hands = mp.solutions.hands
hands = mp_hands.Hands()

cap = cv2.VideoCapture(0)

def generate():
    while True:
        _, frame = cap.read()
        rgb = cv2.cvtColor(frame, cv2.COLOR_BGR2RGB)
        result = hands.process(rgb)

        if result.multi_hand_landmarks:
            cv2.putText(frame, "Gesture Detected", (50,50),
                        cv2.FONT_HERSHEY_SIMPLEX, 1, (0,255,0), 2)

        _, buffer = cv2.imencode('.jpg', frame)
        yield (b'--frame\r\nContent-Type: image/jpeg\r\n\r\n' +
               buffer.tobytes() + b'\r\n')
🔗 Source Code

Click here to view the project:
https://github.com/premavandali21-eng/BIDIRECTIONAL-INDIAN-SIGN-LANGUAGE-RECOGNITION

🚀 Conclusion

This project demonstrates how Artificial Intelligence and Computer Vision can be used to solve real-world communication problems.

It enables inclusive interaction between hearing and non-hearing individuals, reducing dependency on interpreters and improving accessibility.

Future improvements can include expanding the dataset, increasing accuracy, and developing mobile applications for wider usability.
