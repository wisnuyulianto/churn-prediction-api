# Customer Churn Prediction API

![Python](https://img.shields.io/badge/Python-3.11-3776AB?style=for-the-badge&logo=python&logoColor=white)
![FastAPI](https://img.shields.io/badge/FastAPI-009688?style=for-the-badge&logo=fastapi&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white)
![Google Cloud Run](https://img.shields.io/badge/Google_Cloud_Run-4285F4?style=for-the-badge&logo=google-cloud&logoColor=white)


This project deploys a trained Scikit-learn churn prediction model as a REST API using FastAPI, containerizes it with Docker, and serves it on Google Cloud Run.

---

### 🌐 Live API Endpoint

The API is live and publicly accessible. You can interact with it using the automatically generated documentation (powered by Swagger UI).

* **Live API Base URL:** `https://churn-prediction-api-422038811496.asia-southeast1.run.app`
* **Interactive Docs:** **[/docs](https://churn-prediction-api-422038811496.asia-southeast1.run.app/docs)**

---

### 📦 1. Project Overview

This project demonstrates the full lifecycle of a machine learning model, from training and serialization to deployment and inference via REST API.

- ✅ Receives customer data in JSON format
- 🧠 Returns churn prediction (0 or 1) and probability score
- 🚀 Deployed using Docker & Google Cloud Run
- 📦 Model trained with RandomForestClassifier

---

### ⚙️ 2. Tech Stack & Architecture

| Component        | Tool / Framework                            |
| ---------------- | ------------------------------------------- |
| Model            | `RandomForestClassifier` via `scikit-learn` |
| API Framework    | `FastAPI`                                   |
| Serialization    | `joblib`                                    |
| Containerization | `Docker`                                    |
| Deployment       | `Google Cloud Run`                          |
| Image Hosting    | `Google Artifact Registry`                  |


---

### 🧲 3. How to Use the API

You can send a `POST` request to the `/predict` endpoint with a JSON body containing the 19 required customer features.

#### ✅ Example using `cURL` (Command Line)

```bash
curl -X 'POST' \
  'https://churn-prediction-api-422038811496.asia-southeast1.run.app/predict' \
  -H 'accept: application/json' \
  -H 'Content-Type: application/json' \
  -d '{
    "gender": "Female", "SeniorCitizen": 0, "Partner": "Yes", "Dependents": "No",
    "tenure": 1, "PhoneService": "No", "MultipleLines": "No phone service",
    "InternetService": "DSL", "OnlineSecurity": "No", "OnlineBackup": "Yes",
    "DeviceProtection": "No", "TechSupport": "No", "StreamingTV": "No",
    "StreamingMovies": "No", "Contract": "Month-to-month", "PaperlessBilling": "Yes",
    "PaymentMethod": "Electronic check", "MonthlyCharges": 29.85, "TotalCharges": 29.85
  }'
```

#### 📤 Expected Response
```
{
  "prediction": 1,
  "churn_probability": 0.6195
}
```
---

### 💻 4. How to Run Locally

#### 1. Clone the repository:
```
git clone https://github.com/wisnuyulianto/churn-prediction-api.git
cd churn-prediction-api
```
#### 2. Install dependencies:
```
pip install -r requirements.txt
```
#### 3. Run the API server:
```
uvicorn main:app --reload
```

Then open http://localhost:8000/docs

---

### 🐳 5. Run with Docker
```
# Build the image
docker build -t churn-api .

# Run the container
docker run -p 8080
```

API will be available at: http://localhost:8080/docs

---

### 📁 6. Project Structure
```
churn-prediction-api/
│
├── main.py                          # FastAPI app
├── churn_prediction_model.joblib    # Trained model pipeline
├── Dockerfile                       # Container configuration
├── requirements.txt                 # Python dependencies
├── LICENSE                          # MIT License
└── README.md                        # Project documentation
```

---

### 🧠 Author & Credits

Developed by Wisnu Yulianto
<br>Based on the [Telco Customer Churn](https://github.com/wisnuyulianto/customer-churn-prediction-model) dataset.
<br>Powered by FastAPI, Docker, and Google Cloud.

---

### 📜 License
This project is licensed under the MIT License - see the [LICENSE](./LICENSE) file for details.
