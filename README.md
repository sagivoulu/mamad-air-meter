# Mamad Air Meter

## Backstory

Israel is under rocket threat, and many Israeli homes have a **mamad** (ממ"ד) — a reinforced safe room built into the apartment. When a missile alert sounds, the standard procedure is to take shelter in the mamad and seal the door.

The problem: with the door sealed, the mamad becomes an airtight room. No fresh air comes in, and the people inside exhale CO2 continuously. This raises an obvious question for anyone who wants to sleep through the night without waking up for every alert:

**Is it safe to sleep in the mamad with the door closed? For how long? With how many people?**

The CO2 buildup in a sealed room is a real constraint — at high enough concentrations it causes headaches, drowsiness, and eventually becomes dangerous. But the mamad is also typically small, and a family sheltering together amplifies the effect.

This tool was built to give a concrete, data-driven answer to that question.

## What It Does

The **Mamad Air Quality Calculator** is a single-page web app that models CO2 buildup in a sealed room over time.

Given your mamad's dimensions and how many people are sleeping inside, it calculates:

- **CO2 concentration** after a specified number of hours sealed
- **Time to reach safety thresholds** — when the air goes from comfortable to stuffy to unsafe to dangerous
- **What opening the door does** — how much CO2 drops depending on how long the door stays open (quick open/close vs. 1, 2, 5, or 10 minutes)

### Safety thresholds used

| Status   | CO2 level     | Effect                                                        |
|----------|---------------|---------------------------------------------------------------|
| Safe     | Below 1%      | Normal indoor air. No symptoms.                               |
| OK       | 1–2%          | Slightly stuffy. Mild drowsiness possible. No health risk.    |
| Caution  | 2–3%          | Headaches, drowsiness, reduced concentration.                 |
| Unsafe   | 3–5%          | Dizziness, elevated heart rate. Ventilate immediately.        |
| Danger   | Above 5%      | Nausea, confusion, impaired consciousness. Life-threatening.  |

### Key assumptions (worst case)

- Room is perfectly sealed (real mamads leak slightly, so reality is better)
- Sleeping metabolic rate (~0.8 MET), producing ~12 L/hr of CO2 per person
- Starting CO2 at outdoor levels (0.04% / 400 ppm)
- Standard Israeli residential ceiling height: 2.5m
- No wind (affects door-opening exchange estimates)

## Usage

Open `mamad-calc-html.html` in any browser. No server or dependencies needed — it's a single self-contained HTML file.

Adjust the sliders for:
- Room width and length
- Number of people
- Hours sealed

The calculator updates in real time.

## Sources

- Metabolic rates: ASHRAE Fundamentals Handbook
- Door air exchange estimates: buoyancy-driven single-sided ventilation research
