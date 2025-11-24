# Jobs80 — The Daily Signal:Noise Engine

Jobs80 is a ruthless, Steve-Jobs–style daily prioritization tool. It forces an **80:20 signal-to-noise day** by helping you identify the **3–4 mission‑critical outcomes** you must accomplish and showing you exactly what to **skip**.

Minimal. Outcome‑focused. Brutally honest.

---

## 🚀 Purpose

Most productivity tools track tasks. **Jobs80 makes decisions.**

It takes all tasks you think you want to do today, analyzes them against your long-term mission and weekly focus, and filters the day down to:

* **Signal (Top 3–4 outcomes)** — moves your mission forward.
* **Noise (Everything else)** — optional or explicitly skipped.
* **80:20 ratio visualization** — clear and simple.

The goal: Ensure that **80% of your day is mission-aligned output** and 20% is discretionary noise.

---

## 🧩 Core Features

### **1. Drop‑Zone Input**

A clean input area where you:

* Enter all tasks you want to do today.
* Add today’s focus ("What outcome matters today?").
* Push "Analyze".

### **2. AI-Based Daily Prioritization**

Tasks are automatically scored using:

* **Impact** (mission movement)
* **Urgency** (deadline proximity)
* **Energy cost**
* **Relevance to weekly focus**
* **Mission alignment** (stored from your profile)

### **3. Signal Extraction**

The engine picks **3–4 tasks** that:

* Have high impact
* Fit today’s available time
* Match energy levels
* Serve this week’s direction

### **4. Noise Budgeting**

You get a max allowed noise time (e.g., 90 minutes).
Jobs80 shows:

* Noise tasks
* Expected cost
* What to skip entirely

### **5. Day Simulation**

A small simulation predicts:

* Expected progress score for the week
* Energy load
* Risk of task spillover

### **6. Visuals**

Clean, Apple-like UI with:

* Signal/Noise donut chart
* Task impact bars
* Skipped-list module

---

## 🏗️ Architecture Overview

### **Frontend (Next.js)**

* Next.js App Router
* TailwindCSS
* shadcn/ui components
* Framer Motion animations
* Minimal white-space design (Jobs-like focus mode)

### **Backend**

You can choose either:

* **Next.js Server Actions** (recommended for simplicity)
* OR Express API server

### **Datastore**

* **Supabase / Postgres** for:

  * User mission & weekly focus
  * Daily task logs
  * Skip history

### **AI Engine (Hosted API)**

Use any hosted reasoning API:

* OpenAI GPT‑5‑mini or 4.1‑mini
* Qwen 2.5 (backup free option)

Tasks go through a scoring algorithm, then the LLM refines the final ranking & reasoning.

---

## 🔧 API Flow (Simplified)

### **1. Client → /analyze-day**

```
POST /analyze-day
{
  "tasks": [...],
  "today_focus": "...",
  "energy": "high|med|low",
  "time_available": 6
}
```

### **2. Backend Pipeline**

1. Run local scoring (impact, urgency, relevance)
2. Feed into model prompt
3. Model returns:

   * signal tasks (3–4)
   * noise tasks
   * reasoning
   * chart-friendly values

### **3. Client renders results**

* signal box
* noise box
* skip box
* 80:20 donut

---

## 🎛️ Scoring Algorithm (Draft)

Each task gets:

* `impact: 0–10`
* `urgency: 0–10`
* `energy_cost: 0–10`
* `weekly_relevance: +3`
* `mission_alignment: +5`

Final score = weighted sum.

Signal tasks = highest-scoring **3–4 tasks** within time + energy constraints.

---

## 🎨 Design Philosophy

* Extreme minimalism (inspired by Steve Jobs' 2008 keynote slides)
* No clutter
* No calendars or multi-day views
* One screen: "Today only"
* Two binary categories:

  * **Do this**
  * **Skip this**

Focus is a feature.

---

## 🛣️ Roadmap

**Phase 1 — Core Engine (MVP)**

* Task dump → AI analysis → Signal/Noise output

**Phase 2 — Simulation + Noise Budgeting**

* Predict score for the day
* Enforce noise time cap

**Phase 3 — User Mission Memory**

* Weekly focus
* Long-term mission
* Skip patterns

**Phase 4 — Analytics Dashboard**

* Weekly signal:noise trend
* Skip habit heatmap

---

## 📦 Folder Structure (Proposed)

```
/jobs80
  ├── app/
  ├── components/
  ├── lib/
  ├── styles/
  ├── api/
  ├── README.md
  └── package.json
```

---

## 📜 License

MIT (free to copy/use/build on).

---

## 🤝 Contribute

Pull requests welcome once the stable MVP is out.

---

## ✨ Vision

Jobs80 is designed to help you live a **mission-driven life**, not a task-driven one.
It acts like a personal "No Machine," cutting out noise and amplifying what truly matters.
