#Fake Currency Detection 


📖 About the Project
The Fake Currency Detection project is a mobile application designed to help users identify counterfeit Indian banknotes (100, 200, and 500 denominations). By taking a picture of a currency note using the mobile app, the system processes the image using advanced Computer Vision algorithms to determine its authenticity.

The project bridges a user-friendly Flutter mobile interface with a robust Python Flask backend, analyzing 10 distinct security features per banknote to ensure high accuracy.

✨ Key Features
Supported Denominations: Automatically tests and verifies 100, 200, and 500 currency notes.

10-Point Security Check: Analyzes 10 specific features of a banknote, including:

7 distinct regional template matches (using ORB feature matching and SSIM).

Left and Right bleed line counts (verifying the exact number of tactile lines).

Serial number panel verification (ensuring exactly 9 characters are detected).

Computer Vision Processing: Utilizes classical image processing techniques like Homography, Gaussian Blurring, and binary thresholding instead of heavy ML models, making it fast and lightweight.

Cross-Platform: Built with Flutter, ensuring smooth performance on both iOS and Android devices.

REST API Integration: The app communicates with a Flask backend via lightweight API calls, parsing JSON results for each of the 10 features.

🛠️ Tech Stack
Frontend: Flutter (Dart)

Backend: Python (Flask)

Computer Vision & Image Processing: OpenCV (cv2), scikit-image (for SSIM and I/O), NumPy

Core Algorithms: * ORB (Oriented FAST and Rotated BRIEF) for feature detection.

SSIM (Structural Similarity Index) for template matching.

Homography & Perspective Transform for aligning currency features.

Contour Detection for serial number extraction.

⚙️ System Architecture
Client Side (Flutter): The user selects or captures an image. The image is uploaded (e.g., to Firebase), and the app sends a GET request to the Flask server's /api endpoint containing the currency denomination type and the image URL parameters.

Server Side (Python/Flask): * Fetches the image from the provided URL.

Resizes, converts to grayscale, and applies Gaussian blur for noise reduction.

Runs the specific algorithm (testing_100(), testing_200(), or testing_500()) based on the selected option.

Feature Verification: The backend cross-references the scanned image against known templates and physical geometries (like bleed line dimensions and locations).

Response: The Flask API returns a detailed JSON array containing the success status (true/false) and details for all 10 analyzed features back to the Flutter app.

🚀 Getting Started
Prerequisites
Flutter SDK installed on your machine

Python 3.x installed

Virtual Environment (recommended for Python)

Installation
1. Clone the repository

Bash
git clone https://github.com/yourusername/fake-currency-detection.git
cd fake-currency-detection
2. Setup the Python Backend

Navigate to the backend directory.

Create and activate a virtual environment.

Install the required Python dependencies:

Bash
pip install Flask opencv-python numpy scikit-image matplotlib Pillow
Ensure you have the proper dataset folder structure (Dataset/100_Features_Dataset, Dataset/200_Features_Dataset, Dataset/500_Features_Dataset) in the backend environment as referenced in the code.

Run the Flask server:

Bash
python app.py  # or the specific name of your flask file
3. Setup the Flutter Frontend

Navigate to the flutter app directory.

Run flutter pub get to install all dependencies.

Ensure your backend IP/URL is correctly configured in the Flutter API service file to hit the /api endpoint.

Run the app on an emulator or physical device using flutter run.

🤝 Contributing
Contributions are welcome! If you have ideas to optimize the ORB feature matching, reduce noise in the contour detection, or enhance the UI, feel free to fork the repository and submit a pull request.
