# CICOR — USB-HID (STM32F407)

USB HID **Mouse emulator** firmware for **STM32F407**, developed with **STM32CubeIDE / STM32CubeMX**.

This project turns an STM32F407 board into a **plug-and-play USB mouse**. After flashing, the board enumerates on a PC as a standard **HID Mouse** device, and the firmware continuously generates mouse movement based on **accelerometer (tilt / motion) input**. Because it uses the HID class, it works on Windows / Linux / macOS **without installing any driver**.

The repository follows the standard Cube-generated structure:

- `Core/` – main application logic, interrupts, HAL init, sensor read + report generation
- `Drivers/` – HAL/CMSIS + peripheral drivers
- `Middlewares/` – ST USB Device stack
- `USB_DEVICE/` – USB descriptors + HID interface layer used to send mouse reports

**Typical use cases**

- Motion/tilt-controlled cursor (accelerometer → USB mouse movement)
- USB HID learning/training project
- Prototyping a custom input device without writing a PC driver

> ⚠️ Safety note: This firmware can move your mouse cursor and click depending on implementation. Use on a test PC if possible.

---

## 1) What this project does

- Enumerates on a PC as a **USB HID device** (HID Mouse).
- Can send **mouse reports** (move/click).
- Moving using accelerometer
- No special driver is required on Windows/Linux/macOS (HID is built-in).

> It acts like a mouse, it can move the cursor on your PC. Use on your own machine/test setup.

---

## 2) Requirements

### Hardware

- Board: **STM32F407** (project configured for STM32F407VETx).
- **ST-LINK** (on-board or external) for flashing/debugging.
- A **USB data cable** connected to the board’s **USB FS Device** port.

### Software (Windows)

- **STM32CubeIDE** (recommended).
- ST-LINK USB driver (usually installed with CubeIDE / STM32CubeProgrammer).

---

## 3) Get the source code (Windows)

Open **PowerShell** in a folder where you want to store the project:

```powershell
git clone -b USB-HID https://github.com/robotanh/CICOR.git
cd CICOR
```
