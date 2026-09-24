# SHORT-CIRCUIT-SQUAD---HTH-IT-06-Peak-Shaving-Energy-Control-System-for-Multi-Device-Facilities-
# IoT-Based Smart Energy Management and Automatic Peak Load Control System

## 📌 Project Overview

This project is an IoT-based Smart Energy Management System designed to monitor electrical parameters and automatically control non-critical loads when the configured peak current limit is reached.

The system uses an **ESP32**, **current sensor**, **voltage sensor**, and **relay modules** to monitor and manage electrical loads. The ESP32 also provides real-time monitoring through a Wi-Fi dashboard.

---

## 🎯 Objectives

- Monitor real-time voltage and current.
- Calculate electrical power consumption.
- Set a configurable peak current limit.
- Detect when the peak current limit is reached.
- Automatically switch OFF non-critical loads.
- Keep critical loads operating.
- Provide manual control for non-critical loads.
- Display electrical parameters through an IoT dashboard.
- Reduce unnecessary peak power consumption.

---

## ⚙️ System Configuration

### Critical Loads

- 1 × 100 W Bulb
- 1 × AC Coolant Fan

Critical loads are given higher priority and are kept ON during peak-load control.

### Non-Critical Loads

- 2 × 100 W Bulbs
- Controlled using a relay module.
- Can also be controlled manually using a normal switch.

---

## 🔧 Components Required

| Component | Quantity |
|---|---:|
| ESP32 Development Board | 1 |
| ACS712 Current Sensor | 1 |
| AC Voltage Sensor | 1 |
| Relay Module | 2 |
| 100 W Bulb | 3 |
| AC Coolant Fan | 1 |
| Normal ON/OFF Switch | 1 |
| Connecting Wires | As required |
| Power Supply | 1 |
| IoT Dashboard | 1 |

---

## 🧩 Block Diagram

```text
                  ┌───────────────────┐
                  │    230 V AC       │
                  │      Supply       │
                  └─────────┬─────────┘
                            │
                ┌───────────┴───────────┐
                │                       │
        ┌───────▼───────┐       ┌──────▼───────┐
        │ Voltage Sensor│       │ Current Sensor│
        └───────┬───────┘       └──────┬───────┘
                │                       │
                └───────────┬───────────┘
                            │
                     ┌──────▼──────┐
                     │    ESP32    │
                     │ Processing &│
                     │   Control   │
                     └──────┬──────┘
                            │
             ┌──────────────┼──────────────┐
             │                             │
      ┌──────▼───────┐             ┌───────▼────────┐
      │ Relay Module │             │  Wi-Fi / IoT   │
      │              │             │    Dashboard   │
      └──────┬───────┘             └────────────────┘
             │
      ┌──────▼────────────┐
      │ Non-Critical Load │
      │ 2 × 100 W Bulbs  │
      └───────────────────┘

      Critical Loads:
      ┌──────────────────────────────┐
      │ 100 W Bulb + AC Coolant Fan │
      │        Priority Load        │
      └──────────────────────────────┘


---

🔄 Working Principle

Step 1: Power Supply

The system receives electrical power from the AC supply.

Step 2: Voltage Measurement

The voltage sensor continuously measures the supply voltage and provides the measurement to the ESP32.

Step 3: Current Measurement

The ACS712 current sensor measures the current consumed by the connected loads.

Step 4: ESP32 Processing

The ESP32 receives the voltage and current measurements and monitors the total electrical load.

Power can be calculated using:

Power = Voltage × Current

Step 5: Peak Limit

A maximum allowable current value is programmed in the ESP32.

For example:

Peak Current Limit = 5 A

The actual value can be configured according to the project requirement.

Step 6: Normal Operation

When the current is below the configured peak limit:

ESP32 → Normal Operation
        ↓
Critical Load → ON
Non-Critical Load → Available

Step 7: Peak Detection

When the measured current reaches the configured peak limit:

Current ≥ Peak Limit
          ↓
       ESP32
          ↓
   Peak Condition Detected

Step 8: Automatic Load Control

The ESP32 activates the relay controlling the non-critical loads.

Peak Condition
      ↓
Relay Activated
      ↓
2 × 100 W Non-Critical Bulbs OFF
      ↓
Total Current Reduced

Step 9: Critical Loads

The critical loads have higher priority:

Critical Loads
├── 100 W Bulb
└── AC Coolant Fan

These loads remain operational during automatic peak-load control.

Step 10: Manual Control

The two non-critical bulbs can also be controlled manually using the normal ON/OFF switch.

Step 11: IoT Dashboard

The ESP32 connects to Wi-Fi and sends real-time information to the dashboard.

The dashboard can display:

Voltage

Current

Power

Peak current limit

Critical load status

Non-critical load status

Relay status

Peak condition



---

🔁 Overall System Flow

START
  ↓
Initialize ESP32
  ↓
Initialize Sensors
  ↓
Connect to Wi-Fi
  ↓
Read Voltage
  ↓
Read Current
  ↓
Calculate Power
  ↓
Compare Current with Peak Limit
  ↓
 ┌───────────────────────┐
 │ Is Peak Limit Reached?│
 └───────────┬───────────┘
             │
       ┌─────┴─────┐
       │           │
      NO          YES
       │           │
       ↓           ↓
 Normal       Activate Relay
 Operation         ↓
       │       Non-Critical
       │       Loads OFF
       │           ↓
       │      Current Reduced
       │           │
       └─────┬─────┘
             ↓
       Update Dashboard
             ↓
          Repeat


---

🚀 Key Features

⚡ Real-time current monitoring

🔌 Voltage monitoring

📊 Power consumption monitoring

🔴 Peak current detection

🔄 Automatic load shedding

💡 Critical and non-critical load classification

📱 IoT dashboard monitoring

🎛️ Manual load control

📶 ESP32 Wi-Fi connectivity



---

💡 Innovation

The main innovation of this project is priority-based automatic load management.

Instead of switching OFF all loads when the current becomes high, the system identifies non-critical loads and disconnects them first.

This allows important loads such as the AC coolant fan and critical bulb to continue operating while reducing unnecessary electrical demand.


---

🛠️ Technologies Used

ESP32

IoT

Embedded Systems

Current Sensing

Voltage Sensing

Relay-Based Load Control

Wi-Fi Communication

Real-Time Monitoring



---

📈 Expected Result

The system continuously monitors electrical consumption and automatically reduces non-critical electrical loads when the configured peak current limit is reached.

This helps prevent unnecessary peak-load conditions and provides real-time visibility of the electrical system through an IoT dashboard.
