# 🏥 HealthLog — Family Health Management Ecosystem

> A comprehensive, AI-powered family health management system built with Android (Jetpack Compose), Next.js, and Flask.

[![Android](https://img.shields.io/badge/Android-Jetpack%20Compose-brightgreen)](https://github.com/palurupravalika/Healthlog-App)
[![Web](https://img.shields.io/badge/Web-Next.js%2015-black)](https://github.com/palurupravalika/Healthlog-Web)
[![Backend](https://img.shields.io/badge/Backend-Flask-blue)](https://github.com/palurupravalika/Healthlog-Backend)
[![Firebase](https://img.shields.io/badge/Firebase-Firestore%20%7C%20Auth%20%7C%20Storage-orange)](https://firebase.google.com)
[![AI](https://img.shields.io/badge/AI-Groq%20Llama%203.1-purple)](https://groq.com)

---

## 📋 Project Overview

**HealthLog** is a cross-platform family health management application that allows users to:

- 👨‍👩‍👧‍👦 **Manage family member profiles** with health metrics (blood group, height, weight, age)
- 🗂️ **Store and view digital medical records** with report uploads
- ⏰ **Set medicine and appointment reminders**
- 🤖 **AI-powered medical report summarizer** using OCR + Groq Llama 3.1
- 💊 **Explain medical terms** in patient-friendly language
- 🔬 **Identify medicine purpose** via AI
- 🔐 **Secure authentication** via Firebase + JWT

---

## 🏗️ Architecture Diagram

```
┌─────────────────────────────────────────────────────────────────────┐
│                        HealthLog Ecosystem                          │
│                                                                     │
│  ┌───────────────┐    ┌───────────────┐    ┌──────────────────────┐ │
│  │  Android App  │    │   Web App     │    │    Flask Backend     │ │
│  │  (Kotlin +    │    │  (Next.js 15  │    │   (Python 3.13 +     │ │
│  │   Compose)    │    │   React 19)   │    │    REST API)         │ │
│  └───────┬───────┘    └───────┬───────┘    └──────────┬───────────┘ │
│          │                    │                        │             │
│          └────────────────────┴────────────────────────┘             │
│                               │                                     │
│                    ┌──────────▼──────────┐                          │
│                    │   Firebase Platform │                          │
│                    │  ┌────────────────┐ │                          │
│                    │  │ Authentication │ │                          │
│                    │  ├────────────────┤ │                          │
│                    │  │   Firestore    │ │                          │
│                    │  ├────────────────┤ │                          │
│                    │  │    Storage     │ │                          │
│                    │  └────────────────┘ │                          │
│                    └──────────┬──────────┘                          │
│                               │                                     │
│                    ┌──────────▼──────────┐                          │
│                    │  Groq AI (Llama 3.1)│                          │
│                    │  OCR: EasyOCR +     │                          │
│                    │       pypdf         │                          │
│                    └─────────────────────┘                          │
└─────────────────────────────────────────────────────────────────────┘
```

---

## 🛠️ Technology Stack

| Layer | Technology |
|---|---|
| **Android App** | Kotlin, Jetpack Compose, Material3, Retrofit2, Firebase SDK |
| **Web App** | Next.js 15, React 19, TypeScript, Tailwind CSS, Axios |
| **Backend** | Python 3.13, Flask 3.0, Firebase Admin SDK, Groq AI |
| **Database** | Firebase Firestore |
| **Authentication** | Firebase Authentication + JWT (Flask-JWT-Extended) |
| **File Storage** | Firebase Storage |
| **AI / OCR** | Groq Llama 3.1, EasyOCR, pypdf |
| **CI/CD** | GitHub (3 repositories + 1 main with submodules) |

---

## 📁 Repository Structure

This is the **main repository** that links all three sub-repositories as Git submodules.

```
Healthlog/                          ← This repository
│
├── backend/          ──────────────► Healthlog-Backend (Flask REST API)
│
├── healthLog App/    ──────────────► Healthlog-App (Android Jetpack Compose)
│
└── healthLog Web/    ──────────────► Healthlog-Web (Next.js Web Application)
```

### 🔗 Linked Repositories

| Repository | URL | Description |
|---|---|---|
| **Main** | [Healthlog](https://github.com/palurupravalika/Healthlog) | Master repo with submodules |
| **Android** | [Healthlog-App](https://github.com/palurupravalika/Healthlog-App) | Jetpack Compose Android app |
| **Web** | [Healthlog-Web](https://github.com/palurupravalika/Healthlog-Web) | Next.js 15 web application |
| **Backend** | [Healthlog-Backend](https://github.com/palurupravalika/Healthlog-Backend) | Flask REST API + AI/OCR |

---

## ⚙️ Setup Instructions

### Prerequisites

- Android Studio Hedgehog+ (for Android)
- Node.js 18+ and npm (for Web)
- Python 3.13+ (for Backend)
- Firebase project with Firestore, Auth, and Storage enabled
- Groq API Key from [console.groq.com](https://console.groq.com)

---

### 1. Clone with Submodules

```bash
git clone --recurse-submodules https://github.com/palurupravalika/Healthlog.git
cd Healthlog
```

If already cloned without submodules:
```bash
git submodule update --init --recursive
```

---

### 2. Backend Setup

```bash
cd backend
cp .env.example .env
# Edit .env and fill in your actual secrets
pip install -r requirements.txt
# Place your Firebase service account key at: config/firebase-key.json
python run.py
```

**Backend runs at:** `http://localhost:5000`

---

### 3. Web App Setup

```bash
cd "healthLog Web"
npm install
# Create .env.local with your Firebase config
npm run dev
```

**Web runs at:** `http://localhost:3000`

---

### 4. Android App Setup

1. Open `healthLog App/` in Android Studio
2. Place `google-services.json` in `app/` directory
3. Update `RetrofitClient.BASE_URL` with your backend server IP
4. Run on emulator or physical device

---

## 🔐 Sensitive Files — Do NOT Commit

| File | Repository | Action |
|---|---|---|
| `backend/config/firebase-key.json` | Backend | Add manually after cloning. Never commit. |
| `backend/.env` | Backend | Copy from `.env.example`, fill secrets. Never commit. |
| `healthLog App/app/google-services.json` | Android | Download from Firebase Console. Never commit. |
| `healthLog App/local.properties` | Android | Auto-generated by Android Studio. Never commit. |

---

## 📱 Screenshots

> *(Add screenshots here after deployment)*

| Login | Dashboard | AI Summarizer |
|---|---|---|
| ![Login](#) | ![Dashboard](#) | ![AI](#) |

---

## 🤝 Contributors

| Name | Role |
|---|---|
| Paluru Pravalika | Full Stack Developer, Android, Web, Backend, Firebase, AI |

---

## 📄 License

This project is licensed under the MIT License. See [LICENSE](LICENSE) for details.

---

*Built with ❤️ using Kotlin, Next.js, Flask, Firebase, and Groq AI*
