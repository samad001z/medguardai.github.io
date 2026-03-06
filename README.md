# README - MedGuard AI

## 🏥 MedGuard AI – Patient Safety Intelligence

A production-ready AI-powered clinical triage system built for the **AI Innovation Hackathon 2026** at the College of Engineering, Osmania University, Hyderabad.

### 📋 Overview

MedGuard AI screens unstructured patient intake records, uses Google Gemini API to extract structured medical data, applies intelligent triage classification rules, and stores results in Firebase Firestore with a real-time responsive dashboard.

**Status**: ✅ Ready for Hackathon Submission

---

## 🚀 Quick Start

### 1. Clone/Download Project
```bash
# All files are in: d:\Medic\medguard-ai\
```

### 2. Configure APIs (2 minutes)
- **Firebase**: Get config from [console.firebase.google.com](https://console.firebase.google.com) → Paste into `firebase.js`
- **Gemini API**: Get key from [aistudio.google.com/app/apikey](https://aistudio.google.com/app/apikey) → Paste into `app.js`

### 3. Test Locally (2 minutes)
```bash
# Open index.html in browser
# Paste test case (see below)
# Click "Screen Patient"
# Watch results and submit
```

### 4. Deploy (5 minutes)
```bash
npm install -g firebase-tools
firebase login
firebase init hosting
firebase deploy --only hosting
```

### 5. Submit (Before 120-min deadline)
Fill Google Form with:
- Live URL
- System Prompt
- Firestore Screenshot (PT-001)
- AI Agent Log (one sentence)

---

## 📁 Project Files

| File | Purpose |
|------|---------|
| **index.html** | Main UI layout (intake form + dashboard) |
| **style.css** | Responsive medical-themed styling |
| **firebase.js** | Firebase initialization |
| **app.js** | Core application logic (LLM, triage, Firestore) |
| **SETUP_GUIDE.md** | Detailed setup instructions (read this!) |
| **QUICK_REFERENCE.md** | Quick lookup for configs and test cases |
| **TECHNICAL.md** | Full technical documentation |
| **DEPLOYMENT_CHECKLIST.md** | Pre-deployment verification checklist |
| **README.md** | This file |

---

## 🧪 Test Cases

### PT-001: CRITICAL ✓
```
PATIENT ID: PT-001
Name: Ravi Shankar
Age: 58 | Gender: Male
Symptoms: Severe chest pain, shortness of breath
Vitals: BP 180/110, Pulse 102, SpO2 94%
Allergies: Penicillin, Aspirin
```
→ Expected: 🔴 **CRITICAL**

### PT-002: SAFE ✓
```
PATIENT ID: PT-002
Name: Priya Mehta
Age: 29 | Gender: Female
Symptoms: Mild seasonal cough
Vitals: BP 118/76, Pulse 72, SpO2 99%
Allergies: None
```
→ Expected: 🟢 **SAFE**

### PT-003: MODERATE ✓
```
PATIENT ID: PT-003
Name: [Not Provided]
Age: ?
Symptoms: Dizziness and pain
Vitals: Not recorded
```
→ Expected: 🟡 **MODERATE**

---

## 🎯 Key Features

✅ **Patient Intake UI** - Clean form with textarea for raw intake text
✅ **Gemini LLM Integration** - Extracts structured data with intelligent prompting
✅ **Triage Classification** - CRITICAL/MODERATE/SAFE logic
✅ **Firestore Database** - Real-time storage with server timestamps
✅ **Live Dashboard** - Real-time updates using onSnapshot()
✅ **Color Coding** - Red/Amber/Green for status
✅ **Responsive Design** - Works on desktop, tablet, mobile
✅ **Error Handling** - Graceful error messages
✅ **Retry Logic** - Automatic retry for API failures
✅ **Filter System** - Filter dashboard by risk status

---

## 📊 Triage Rules

### CRITICAL if ANY:
- Symptoms include "chest pain"
- Symptoms include "shortness of breath"
- SpO2 < 96%
- BP systolic > 160
- Known allergies present

### MODERATE if ANY:
- Name missing
- Age missing
- Vitals not recorded

### SAFE otherwise

---

## 🛠️ Tech Stack

| Component | Technology |
|-----------|-----------|
| Frontend | HTML5, CSS3, Vanilla JavaScript |
| LLM | Google Gemini API |
| Database | Firebase Firestore |
| Hosting | Firebase Hosting / Vercel / Netlify |
| Browser SDKs | Firebase JS SDK v10.7.0 |

---

## 📖 Documentation

- **[SETUP_GUIDE.md](SETUP_GUIDE.md)** - Start here! Complete setup instructions
- **[QUICK_REFERENCE.md](QUICK_REFERENCE.md)** - Cheat sheet for configs and APIs
- **[TECHNICAL.md](TECHNICAL.md)** - Deep dive into architecture and code
- **[DEPLOYMENT_CHECKLIST.md](DEPLOYMENT_CHECKLIST.md)** - Pre-submission verification

---

## ⏱️ Hackathon Timeline

```
0:00-0:20  → Setup & Planning (Firebase + API keys)
0:20-0:55  → Intake UI & LLM Integration
0:55-1:25  → Triage Logic & Firestore
1:25-1:55  → Live Dashboard
1:55-2:20  → Deployment
2:20-2:30  → Submission (Google Form)
```

---

## 🔧 Configuration

### firebase.js
```javascript
const firebaseConfig = {
    apiKey: "YOUR_API_KEY",
    authDomain: "YOUR_PROJECT_ID.firebaseapp.com",
    projectId: "YOUR_PROJECT_ID",
    // ... (get from Firebase Console)
};
```

### app.js
```javascript
CONFIG = {
    GEMINI_API_KEY: 'YOUR_GEMINI_API_KEY'  // Get from Google AI Studio
}
```

---

## 🚀 Deployment Options

Choose one:

### 1. Firebase Hosting (Recommended)
```bash
firebase login
firebase init hosting
firebase deploy --only hosting
# Live at: https://PROJECT_ID.web.app
```

### 2. Vercel
Upload folder to [vercel.com](https://vercel.com)
Live at: `https://your-project.vercel.app`

### 3. Netlify
Drag & drop to [netlify.com](https://app.netlify.com)
Live at: `https://your-project.netlify.app`

---

## 📝 System Prompt

The LLM is instructed with this prompt (included in `app.js`):

```
You are a clinical triage assistant for City General Hospital.

Extract the following fields from the patient intake record:
- patientId, name, age, symptoms, allergies, medications
- bp, pulse, spo2, doctorNotes

Then apply triage rules:
- CRITICAL if: chest pain OR shortness of breath OR SpO2<96 OR BP>160 OR allergies present
- MODERATE if: name/age/vitals missing
- SAFE otherwise

Return ONLY valid JSON with status field.
No explanations or markdown.
```

---

## 🎨 UI/UX Highlights

- **Medical Theme**: Hospital-inspired blue/white/green color scheme
- **Real-Time Updates**: Firestore onSnapshot() for instant dashboard refresh
- **Color Coding**: CRITICAL=Red, MODERATE=Amber, SAFE=Green
- **Responsive Grid**: Auto-wraps cards for mobile/tablet/desktop
- **Loading Spinner**: Shows during API calls
- **Error Handling**: User-friendly error messages
- **Filter System**: View all records or filter by status

---

## 🔐 Security Notes

### For Hackathon ✓
- API keys in frontend code (acceptable with restrictions)
- Firestore in Test Mode (open for demo)

### For Production (Use Later)
- Move APIs to backend
- Use environment variables
- Enable Firestore Authentication
- Implement restrictive security rules

---

## 📊 Firestore Collection Schema

```
Collection: patients
Document: {
  patientId: "PT-001",
  name: "Ravi Shankar",
  age: 58,
  symptoms: ["chest pain", "shortness of breath"],
  allergies: ["Penicillin", "Aspirin"],
  medications: ["Warfarin 5mg"],
  bp: "180/110",
  pulse: 102,
  spo2: 94,
  doctorNotes: "Possible acute MI...",
  status: "CRITICAL",
  timestamp: [Server Timestamp],
  rawInput: "[Original text]"
}
```

---

## ✅ Pre-Submission Checklist

- [ ] Firebase configured
- [ ] Gemini API key obtained
- [ ] All 3 test cases pass
- [ ] PT-001 shows CRITICAL ✓
- [ ] PT-002 shows SAFE ✓
- [ ] PT-003 shows MODERATE ✓
- [ ] Firestore screenshot taken (PT-001)
- [ ] System prompt copied
- [ ] AI Agent Log written
- [ ] App deployed to public URL
- [ ] Mobile view tested
- [ ] Google Form submitted before deadline

---

## 🆘 Quick Troubleshooting

| Issue | Solution |
|-------|----------|
| Firebase not initialized | Check config in firebase.js |
| Gemini API error | Verify API key is correct |
| JSON parse error | Check system prompt syntax |
| Records not saving | Verify Firestore rules |
| Dashboard not updating | Check Firestore listener |

See **DEPLOYMENT_CHECKLIST.md** for detailed troubleshooting.

---

## 🏆 Evaluation Criteria (100 Points)

| Criterion | Points |
|-----------|--------|
| Data Extraction | 20 |
| CRITICAL Logic | 20 |
| MODERATE Logic | 15 |
| Live Dashboard | 15 |
| Deployment | 15 |
| Prompt Quality | 10 |
| AI Agent Log | 5 |

---

## 📱 Browser Support

✅ Chrome 90+
✅ Firefox 88+
✅ Safari 14+
✅ Edge 90+
✅ Mobile browsers (iOS Safari, Chrome Mobile)

---

## 📞 Support Resources

- [Firebase Documentation](https://firebase.google.com/docs)
- [Google Gemini API Docs](https://ai.google.dev/)
- [MDN Web Docs](https://developer.mozilla.org/)

---

## 📄 License

Educational project for AI Innovation Hackathon 2026
College of Engineering, Osmania University, Hyderabad

---

## 🚀 Ready to Build?

1. **Start**: Read [SETUP_GUIDE.md](SETUP_GUIDE.md)
2. **Configure**: Get API keys (~5 min)
3. **Test**: Run with test cases (~10 min)
4. **Deploy**: Push to public URL (~5 min)
5. **Submit**: Fill Google Form (before deadline)

**Total time: ~2 hours within the hackathon window**

---

**Good luck! May your triage logic be accurate and your Firestore queries return instantly! 🏥✨**
