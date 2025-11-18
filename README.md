# FemtoKVM

> **FemtoKVM** is a minimal-cost, incremental IP-KVM platform developed by **Sanctus**.  
> It starts as a $5 remote power controller and scales up to a complete remote-console solution.

FemtoKVM is designed for real homelabs, field-deployed nodes, edge servers, and low-budget remote machines where you **mostly SSH**, but occasionally need **power control, BIOS access, or rescue-mode visibility**.

The philosophy is simple:

> **Build the smallest thing that works. Then layer capabilities only when they matter.**

---

## 🧩 Why FemtoKVM Exists

Full IP-KVM units (PiKVM, TinyPilot, Dell iDRAC, HP iLO, Supermicro IPMI) are excellent — and expensive.

Most hobbyist or small-scale deployments don’t need:

- full H.264 interactive desktop,
- encrypted hardware keyboard injection,
- KVM-over-IP enterprise features.

But they *do* need:

- **Reliable remote power control**  
- **A way to see BIOS / bootloader output**  
- **A low-cost toolchain that can grow with needs**

FemtoKVM is an **incremental open platform** for exactly that.

---

## 🔧 Project Phases

FemtoKVM grows in three layers. Each phase is fully usable on its own.

---

### **Phase 1 — Remote Power Control (Current)**  
**Cost:** ~$5–8  
**Hardware:** ESP8266 (NodeMCU/Wemos D1 Mini) + 5V relay

**Capabilities**

- Web-based “power switch” with configurable press durations  
- Parallel wiring with existing case power button  
- Static IP / local-only operation  
- No cloud dependencies  
- Safe: only switching low-voltage motherboard header  

**Directory:**  
`hardware/phase1-power-control/`  
`firmware/esphome/`  
`firmware/arduino/`

---

### **Phase 2 — Basic Emergency Video (Planned)**  
**Cost:** ~$40 incremental  
**Hardware:** Raspberry Pi Zero 2W + USB HDMI capture

**Capabilities**

- Low-resolution rescue video for BIOS/bootloader  
- Occasional use only (not intended for full desktop streaming)  
- Basic keyboard injection for recovery scenarios  

**Directory:**  
`hardware/phase2-basic-video/`

---

### **Phase 3 — Full IP-KVM (Future)**  
**Cost:** ~$80–100 total  
**Hardware:** Raspberry Pi 4 + HDMI→CSI bridge

**Capabilities**

- Low-latency video pipeline  
- Full keyboard/mouse injection  
- Authenticated access  
- Optional VPN integration  
- Production-ready remote console stack  

**Directory:**  
`hardware/phase3-full-ip-kvm/`

---

## 📁 Repository Structure

```
FemtoKVM/
├── hardware/
│ ├── phase1-power-control/
│ ├── phase2-basic-video/
│ └── phase3-full-ip-kvm/
│
├── firmware/
│ ├── esphome/
│ └── arduino/
│
├── software/
│ └── controller/ # optional CLI/UI tools
│
├── docs/
│ ├── quickstart.md
│ ├── configuration.md
│ ├── assembly.md
│ ├── roadmap.md
│ └── faq.md
│
├── LICENSE-HARDWARE # (CERN-OHL-S v2)
├── LICENSE-FIRMWARE # (AGPLv3)
├── LICENSE-SOFTWARE # (AGPLv3)
├── LICENSE-DOCS # (CC-BY-SA 4.0)
└── README.md
```


*(Your repo currently has only a single AGPL file. Instructions for multi-license setup follow below.)*

---

## 🚀 Getting Started (Phase 1)

1. **Assemble hardware** (ESP8266 + 5V relay wired in parallel to the PWR_SW header)  
2. **Flash firmware** using ESPHome or Arduino  
3. **Connect to device’s web interface**  
4. **Trigger power, reset, or forced shutdown**  

See:  
`docs/quickstart.md` and `docs/configuration.md`.

---

## 🤝 Contributing

FemtoKVM is an **incremental open-hardware platform**.  
Contributions are welcome in:

- Hardware validation / alternative parts  
- Firmware improvements  
- Enclosure designs  
- Documentation (assembly photos, wiring, etc.)  

PRs and issues are encouraged.

---

## 📜 Licensing

FemtoKVM uses a **multi-license model** appropriate for open hardware:

- **Hardware** (schematics, PCB, mechanicals): **CERN-OHL-S v2**  
- **Firmware** (ESPHome + Arduino): **AGPLv3**  
- **Software** (controller tools): **AGPLv3**  
- **Documentation**: **CC-BY-SA 4.0**

Commercial licensing and OEM arrangements are available — contact **Sanctus**.

---

## 🏛️ About Sanctus

**Sanctus** is a technology company for human beings. We builds simple, accessible, transparent, & open infrastructure tools — from micro-scale hardware to agentic software systems.  
FemtoKVM is one of several composable primitives in this ecosystem.

