# ECU Calibration Study — EDC-16C9/C39 (Z19DTH)

**BEng Thesis | ASPAITE — Department of Mechanical Engineering Educators | 2020**

Analysis and optimization of an automotive Electronic Control Unit (ECM) 
using WinOLS calibration software, covering ECU architecture, sensor 
characterization, fuel and ignition modeling, and live parameter optimization 
on a Z19DTH diesel engine.

---

## Overview

Modern automotive ECUs manage complex interactions between hundreds of 
parameters — fuel injection timing, boost pressure, torque limiting, 
idle control — all derived from real-time sensor inputs processed through 
lookup tables (maps). This study analyzes the full ECM signal chain and 
demonstrates practical ECU calibration on a production diesel engine.

**Engine:** Opel/Vauxhall Z19DTH (1.9L CDTI diesel)  
**ECU:** Bosch EDC-16C9 / C39  
**Calibration Tool:** WinOLS

---

## Technical Scope

### 1. ECM Architecture
- Microprocessor fundamentals — RAM, ROM, EEPROM, Flash memory
- Analog-to-digital signal conversion pipeline
- Input/output channel organization and bus communication

### 2. Sensor Analysis
Full characterization of ECM input sensors:

| Sensor | Type | Signal Range |
|--------|------|-------------|
| Throttle Position (TPS) | Potentiometer | 0.5–5V |
| Mass Air Flow (MAF) | Bosch Hot-Wire | 0.4–5V |
| Manifold Absolute Pressure (MAP) | Diaphragm pressure | Variable |
| Knock Sensor (KS) | Piezoelectric | Frequency-based |
| Lambda / O2 Sensor | Narrowband / Wideband | 0–1V / 0–5V |
| Exhaust Gas Temperature (EGT) | Thermocouple | Temperature-based |
| Crank / Cam Position | Hall effect / VR | Digital pulse |

### 3. Fuel System Modeling
- Electronic Fuel Injection (EFI) operating principles
- Injector flow rate and pressure characterization
- Injector electrical characteristics — opening time, duty cycle
- Fuel supply system architecture

### 4. Combustion and Ignition
- Burn rate modeling and MBT (Minimum spark for Best Torque)
- Mass Fraction Burned (MFB) analysis
- Knock detection and spark advance management
- Forced induction — turbocharger and supercharger dynamics

### 5. Airflow Modeling
- Speed-density systems (MAP-based)
- Mass airflow modeling (MAF-based)
- MAF scaling for modified airflow applications

### 6. Volumetric Efficiency (VE) Tables
- VE table theory and physical interpretation
- Calibration methodology for accuracy at all operating points
- Target lambda selection for calibration (stoichiometric vs enrichment)
- Idle speed calibration and dashpot behavior
- Wide Open Throttle (WOT) calibration procedure

---

## ECU Remap — Z19DTH Diesel Parameters

Practical calibration performed on EDC-16C9/C39 ECU using WinOLS:

| Map | Description | Modification |
|-----|-------------|-------------|
| Driver's Wish Map | Pedal-to-torque request curve | Optimized response |
| Torque Limiter | Maximum torque ceiling | Adjusted for performance |
| Nm to IQ Conversion | Torque to fuel quantity mapping | Recalibrated |
| IQ Limiter Map | Injection quantity ceiling | Increased within safe limits |
| Gear-Dependent Torque Limiter | Per-gear torque cap | Optimized per gear |
| IQ Limit by Coolant Temperature | Cold-start fuel limiting | Verified |
| Start of Injection (SOI) Map | Injection timing | Advanced for efficiency |
| Injection Duration Map | Fuel quantity per cycle | Recalibrated |
| CRS Rail Pressure | Common rail fuel pressure | Optimized |
| EGR vs MAF Map | EGR valve control | Adjusted |
| Boost Request Map | Turbo target pressure | Increased within limits |

---

## Key Concepts Demonstrated

- **Closed-loop vs open-loop** fuel control using Short Term / Long Term 
  Fuel Trim (STFT/LTFT)
- **Lambda target selection** — stoichiometric (λ=1.0) for gasoline, 
  lean operation for diesel efficiency
- **Forced induction calibration** — turbocharger boost control, 
  boost pressure vs. RPM mapping
- **Transients and modifiers** — acceleration enrichment, 
  deceleration fuel cut strategies

---

## Tools and Technologies

- **WinOLS** — ECU map extraction, editing, and checksum correction
- **Bosch EDC-16** platform — automotive diesel engine management
- **OBD-II diagnostics** — fault code reading and live data monitoring
- Automotive sensor measurement and validation

---

## Context

This work was completed as a BEng thesis in Mechanical Engineering at ASPAITE 
(School of Pedagogical and Technological Education), Athens, Greece.

The practical ECU calibration was performed on a real production vehicle, 
applying theoretical sensor and combustion models to actual map adjustments 
and verifying outcomes against engine behavior.

This hands-on automotive ECU experience, combined with subsequent MSc research 
in deep learning for battery State of Health prediction, forms the foundation 
of a profile at the intersection of mechanical engineering and applied AI 
for automotive and industrial systems.

---

## Related Work

[Battery State of Health Prediction API](https://github.com/YOUR_USERNAME/battery-soh-api) — 
MSc thesis implementation: LSTM-based multi-step SOH forecasting, 
deployed as a REST API using FastAPI and PyTorch.
