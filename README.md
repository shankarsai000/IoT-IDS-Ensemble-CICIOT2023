# 🛡️ IoT Intrusion Detection System (IDS) using Ensemble Learning + Session Aggregation

An end-to-end **IoT Intrusion Detection System (IDS)** pipeline built using the **CICIOT2023 dataset**, leveraging **Ensemble Machine Learning (ExtraTrees + XGBoost)** and **Session/Window-level aggregation** for highly accurate attack detection.

This project performs both:
✅ **Flow-level classification** (per network flow)  
✅ **Session-level detection** (using rolling probability window aggregation)

---

## 🚀 Key Highlights

- 📌 Dataset: **CICIOT2023**
- 🧠 Model: **Soft Voting Ensemble**
  - `ExtraTreesClassifier`
  - `XGBoostClassifier`
- 🎯 Flow-level Accuracy: **~99.60%**
- 🔥 Session-level Accuracy: **Up to 100%** (window size ≥ 7)
- 💾 Model Export: `joblib` `.pkl` files for deployment-ready use

---

## 🧩 Problem Statement

IoT environments are highly vulnerable to cyber-attacks due to:
- large number of connected devices
- limited device security
- high traffic volume
- unknown/unstructured attack patterns

This project aims to build a **robust IDS** that automatically detects whether IoT traffic is:
✅ Benign (Normal)  
❌ Malicious (Attack)

---

## 📂 Dataset Used

**CICIOT2023 Dataset** loaded from Kaggle environment:

- `train.csv`
- `test.csv`
- `validation.csv`

Example path used in notebook:

/kaggle/input/ciciot2023/CICIOT23/


---

## ⚙️ Feature Set Used

A robust set of top IoT traffic features:

- Header_Length, Protocol Type, Duration
- Rate, Srate, Drate
- TCP Flags: fin, syn, rst, psh, ack
- Flow Stats: AVG, Std, Tot sum, Tot size, IAT, Magnitue
- Weight, Data_length, etc.

✅ Missing feature handling included to prevent runtime crashes.

---

## 🧠 Model Architecture

### ✅ Flow-Level Detection
Predicts attack vs benign for each flow using Ensemble model:

- ExtraTreesClassifier (fast, strong baseline)
- XGBoostClassifier (high accuracy, complex pattern learning)

Both are combined using:

✅ **Soft Voting** (probability-based voting)  
✅ **Weighted voting** giving higher influence to XGBoost

---

## 🔥 Session-Level Detection (Window Aggregation)

Real IDS systems often detect attacks at a **session level** rather than individual flows.

This project aggregates predictions using:

✅ Mean attack probability over a fixed window size:

- window = 3, 5, 7, 11, 15
- Best found: **window = 7** (100% session accuracy)

---

## 📊 Results

### ✅ Flow-Level Evaluation
- Accuracy: **~99.60%**
- Classification report generated (Precision, Recall, F1-score)

### ✅ Session-Level Evaluation
- Accuracy improves further with window aggregation
- Achieved **100%** with window size ≥ 7

---

## 💾 Saved Files (Model + Config)

The project exports trained model and configuration files:

- `voting_ids_model.pkl`
- `session_config.pkl`
- `session_config_window11.pkl`
- `session_config_best.pkl`

These files can be used for:
✅ real-time prediction  
✅ deployment in a web/app/IoT gateway environment

---

## 🏃 How to Run

### ✅ On Kaggle
1. Open the notebook
2. Attach dataset: **CICIOT2023**
3. Run all cells
4. Output model files will be stored under:

/kaggle/working/



### ✅ Run Locally (optional)
Install dependencies:

```bash
pip install numpy pandas scikit-learn xgboost joblib matplotlib

📌 Future Enhancements

✅ Multi-class classification (detect specific attack type)

✅ Real-time inference API using Flask/FastAPI

✅ Stream traffic integration (ESP32 / Wireshark / MQTT)

✅ Confusion Matrix + ROC-AUC & PR-AUC reporting

✅ Feature importance visualization

👨‍💻 Author

Shankar Sai N
Engineer Student | ML + IoT | Cybersecurity Enthusiast
📌 Kaggle Notebook: Final IoT Thread (CICIOT IDS)


⭐ If you like this project

Give it a ⭐ on GitHub — it motivates me to build more!


---

# ✅ How to Push This Project to GitHub (Step-by-Step)

## ✅ 1) Create a GitHub Repo
1. Go to GitHub
2. Click **New Repository**
3. Repo name example:
   - `IoT-IDS-Ensemble-CICIOT2023`
4. ✅ Tick: **Add README** (optional)  
5. Click **Create repository**

---

## ✅ 2) Upload Files from Kaggle (Model/Notebook)
If you want to upload your notebook/code:

### Option A: Download notebook from Kaggle
- Kaggle Notebook → **File → Download Notebook**
- You’ll get `.ipynb`

### Option B: Download output `.pkl` files
From Kaggle:
- Go to **Output**
- Download:
  - `voting_ids_model.pkl`
  - `session_config_best.pkl` etc.

---

## ✅ 3) Push using Git (BEST METHOD 🔥)

### ✅ Step 1: Install Git (if not installed)
- Windows: install Git SCM

### ✅ Step 2: Open terminal inside your project folder
Example:

```bash
cd path/to/your/project

✅ Step 3: Initialize git
git init

✅ Step 4: Add all files
git add .

✅ Step 5: Commit
git commit -m "Initial commit: IoT IDS ensemble + session aggregation"

✅ Step 6: Connect to GitHub repo

Copy your repo link from GitHub (example):

git remote add origin https://github.com/YOUR_USERNAME/IoT-IDS-Ensemble-CICIOT2023.git

✅ Step 7: Push to GitHub
git branch -M main
git push -u origin main


✅ Done ✅ Your project is live on GitHub.
