# AXI4-Protocol

This project demonstrates a **single AXI4 Master–Slave interface** implemented in Verilog, along with a testbench to validate **read and write transactions**. It is designed as a learning resource for understanding the **AXI4 protocol**, its **VALID/READY handshake mechanism**, and **burst transfers**.

---

## 📘 Functionality
- **AXI Master**  
  Issues write and read requests, generates burst data, and manages responses.  

- **AXI Slave**  
  Provides memory-mapped storage, accepts burst writes, returns stored data on reads, and generates write responses (`BRESP`).  

- **Testbench**  
  Drives clock/reset, initiates transactions, and verifies correctness by comparing written and read data.  

---

## 🔧 Features
- Burst transfers with configurable length (`AWLEN`, `ARLEN`).  
- Handshake mechanism across all channels (`VALID/READY`).  
- Write response handling (`BRESP=00` for OKAY).  
- Memory-based slave storage for verification.  
- Simulation logs for transaction tracing and debugging.  

---

## 📊 Results (Simulation Output)
The following log shows the sequence of write and read transactions between the AXI Master and Slave:
```
[45000] MASTER -> SLAVE : WRITE ADDR = 00000020 LEN=3 BURST=01
[65000] MASTER -> SLAVE : WRITE DATA = a0000000 WLAST=0
[75000] MASTER -> SLAVE : WRITE DATA = a0000001 WLAST=0
[85000] MASTER -> SLAVE : WRITE DATA = a0000002 WLAST=0
[95000] MASTER -> SLAVE : WRITE DATA = a0000003 WLAST=1
[105000] SLAVE  -> MASTER: WRITE RESP = 00
[135000] MASTER -> SLAVE : READ ADDR = 00000020 LEN=3 BURST=01
[155000] SLAVE  -> MASTER: READ DATA = a0000000 RLAST=0
[165000] SLAVE  -> MASTER: READ DATA = a0000001 RLAST=0
[175000] SLAVE  -> MASTER: READ DATA = a0000002 RLAST=0
[185000] SLAVE  -> MASTER: READ DATA = a0000003 RLAST=1

```
---

## 🎯 Purpose
This project serves as a **reference model** for AXI4 transactions and as an **educational tool** to understand protocol fundamentals. It can be extended into more complex SoC or interconnect designs.

---

## 🔮 Future Extensions
Multiple Masters and Slaves  
Extend the design to support multiple masters and slaves with arbitration logic and interconnect fabric.

AXI4-Lite Implementation  
Add a simplified AXI4-Lite version for control/status register access, commonly used in SoC designs.

---
