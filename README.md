# 300W Pure Sine Wave Inverter - Final Project Repository


## 📋 Table of Contents
1. [Project Overview](#project-overview)
2. [Team Members](#team-members)
3. [Problem Statement & Motivation](#problem-statement--motivation)
4. [Technical Architecture](#technical-architecture)
5. [PCB Design & Schematics](#pcb-design--schematics)
6. [Simulations & Verification](#simulations--verification)
7. [Enclosure & Mechanical Design](#enclosure--mechanical-design)
8. [Bill of Quantities (BOQ) & Costing](#bill-of-quantities-boq--costing)
9. [Manufacturing Considerations](#manufacturing-considerations)
10. [Marketing & Competitor Landscape](#marketing--competitor-landscape)
11. [Future Improvements](#future-improvements)

---

## 🏛️ Project Overview
This repository contains the complete documentation, design files, schematics, simulations, and manufacturing reports for the **300W Pure Sine Wave Inverter** developed by **Group Forge** for the module **EN2160 - Electronic Design Realization** at the Department of Electronic and Telecommunication Engineering, **University of Moratuwa, Sri Lanka**.

The device is engineered to provide clean, grid-quality AC power (230V, 50Hz) from a 12V battery source during power outages, specifically tailored for low-wattage sensitive electronics (such as Wi-Fi routers, laptops, and monitors) without introducing the harmonic distortion, noise, or overheating characteristic of budget-friendly modified sine wave inverters.

---

## 👥 Team Members (Group Forge)

| # | Name | Index Number | Role / Core Responsibilities |
|---|---|---|---|
| 1 | **Athukorala U.R.** | 230063B | Schematics, Hardware Testing, and System Assembly |
| 2 | **De Mel D.J.** | 230121D | Power Stage (12V-400V) Design, Simulation, PCB Design, Assembly & Testing |
| 3 | **Fernando W.H.D.** | 230186E | Enclosure Design, Physical Integration, Testing & Validation |
| 4 | **Rahul B.** | 230508V | Controller Design, Schematics, PCB Routing, Component Selection & Testing |
| 5 | **Ratheeshan A.R.** | 230539P | Controller Schematics, H-Bridge & Filter Simulation, PCB Routing & Testing |

---

## ⚡ Problem Statement & Motivation

### Problem Statement
In Sri Lanka, frequent grid power interruptions severely disrupt day-to-day activities and remote work. While cheap backup solutions exist, budget modified sine wave inverters cause electrical noise, overheating, and long-term degradation in sensitive equipment. There is an urgent need for a cost-effective, highly efficient 300W pure sine wave inverter delivering clean grid-equivalent power.

### Motivation & Statistics
* **Grid Vulnerability:** Over **1 million Sri Lankan households** lost power access during recent energy crunches (2023 data).
* **Daily Blackouts:** Extended load-shedding hours forced households to look for reliable local backup solutions for essential low-wattage devices (<300W).

---

## ⚙️ Technical Architecture

The inverter utilizes a high-frequency two-stage power conversion topology:

1. **DC-DC Boost Stage (12V to 350V DC):**
   * Driven by an **SG3525 PWM controller module** switching primary-side high-current Power MOSFETs.
   * Features a custom hand-wound center-tapped ferrite core transformer (1:40 winding ratio).
   * A full-bridge fast-recovery diode rectifier converts high-frequency AC to a stable 350V DC bus.

2. **DC-AC Inverter Stage (350V DC to 230V 50Hz AC):**
   * Built around the **EG8010 ASIC architecture (EGS002 module)** providing precise SPWM signal generation with hardware dead-time control to prevent shoot-through.
   * Full H-bridge high-voltage MOSFET configuration driven by high/low-side drivers.
   * **LC Low-Pass Output Filter:** Smooths out high-frequency switching edges to yield a pristine 50Hz pure sine wave.
   * **Real-time Feedback Loop:** Continuously monitors output voltage via a resistor divider and feeds data back to the controller to dynamically adjust duty cycles under varying loads.

---

## 🖨️ PCB Design & Schematics

To isolate noisy high-current switching paths from sensitive low-voltage control signals, the hardware is partitioned into **two distinct 2-layer FR4 PCBs (1.6mm thickness, 1oz copper weight, manufactured via JLCPCB)**:

* **Controller Board:** Houses the EG8010 module, 12V-to-5V buck regulators, protection comparator logic, and display headers.
* **Power Board:** Houses the 12V-400V push-pull boost converters, primary-side MOSFET arrays, bridge rectifiers, H-bridge switching stage, and output LC filters.

---

## 📈 Simulations & Verification

Design parameters and passive component selections were rigorously verified using industry-standard simulation tools:
* **LTspice:** Utilized for modeling the SG3525 push-pull boost converter, transformer winding ratios, current draws, and snubber circuits.
* **MATLAB Simulink:** Employed to simulate unipolar SPWM generation, H-bridge switching behavior, and LC filter attenuation to guarantee total harmonic distortion (THD) remains minimal.

---

## 📦 Enclosure & Mechanical Design

* **Material:** Formed from durable **zinc-coated steel**, chosen over mild steel for superior bendability, corrosion resistance, structural rigidity, and natural Faraday cage shielding against electromagnetic interference (EMI).
* **Thermal Management:** Optimized interior layout featuring custom aluminum heat sinks attached to power MOSFETs and a temperature-controlled cooling fan triggered via thermistors.
* **I/O Integration:** Equipped with a 30A mounting post for low-voltage high-current battery inputs, standard 3-pin AC sockets for output appliances, a power toggle switch, and a front-mounted LCD readout screen.

---

## 💰 Bill of Quantities (BOQ) & Costing

### Prototype Cost Breakdown (LKR)
| Item Description / Part Number | Qty | Unit Cost (Rs.) | Total (Rs.) |
|---|---|---|---|
| EG8010 SPWM controller module | 1 | 1,200 | 1,200 |
| SG3525 PWM controller | 1 | 250 | 250 |
| IR2110 high/low-side driver | 2 | 300 | 600 |
| Power MOSFETs (H-bridge + push-pull) | 6 | 350 | 2,100 |
| Ferrite core transformer (custom wound) | 1 | 1,200 | 1,200 |
| LM2678SX-5.0 buck regulator | 1 | 350 | 350 |
| TPS55289 buck-boost converter | 1 | 500 | 500 |
| Bridge rectifier + filter capacitors | 1 set | 850 | 850 |
| LCD display module | 1 | 650 | 650 |
| Connectors, resistors, passives, PCB fabrication | 1 set | 6,000 | 6,000 |
| **Total Prototype Cost** | | | **Rs. 13,700** |

* **Prototype Marginal Cost:** Rs. 14,000.00
* **Absorption Cost (incl. transport):** Rs. 16,000.00
* **Projected Volume Production Cost:** Rs. 10,000.00 – Rs. 13,000.00 per unit (achieving ~20-30% savings on PCBs, enclosures, and bulk component sourcing).

---

## 📊 Market Positioning & Competitor Landscape

| Metric | Our Product (Forge Inverter) | Tier 1 Imported Inverters (Unitec, SAKO, Growatt) | Tier 2 Solar Hybrids (Goodwe, Victron) | Tier 3 Petrol/Diesel Generators |
|---|---|---|---|---|
| **Input** | 12V DC Battery | 12V DC Battery | Solar + Grid | Petrol / Diesel |
| **Advantages** | Clean output, affordable, locally serviceable, 230V/50Hz native | Readily available | Smart monitoring, high capacity | High raw power |
| **Disadvantages** | Early prototype stage | Import markups, 110V/60Hz mismatch issues | Overkill (3-10kW), highly expensive | Loud, heavy, toxic emissions, fuel costs |
| **Price Range** | **Rs. 25,000.00** | LKR 25,000 - 40,000 | LKR 200,000+ | LKR 40,000 - 400,000 |

---

## 🚀 Future Improvements
* **IoT Integration:** Transition from an ASIC-based design to a microcontroller-based architecture with Bluetooth/Wi-Fi telemetry for remote mobile monitoring.
* **Industrial Magnetic Optimization:** Outsource custom transformer winding to industrial facilities to reduce core losses and parasitic inductance.
* **Miniaturization:** Further optimize PCB layouts and surface-mount component placement to reduce weight and overall physical footprint.

---

## 📜 License
This project was developed as an academic submission for the **Department of Electronic and Telecommunication Engineering, University of Moratuwa**. All rights reserved to Group Forge.
README.md
Displaying README.md.
