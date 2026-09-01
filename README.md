# RFID-Based Attendance System

An Arduino-based RFID attendance system designed to automate student attendance recording using RFID cards/tags. The system reads a unique RFID UID, checks whether the card is authorized, and provides the result through a 16x2 LCD and LED indicators.

## Project Overview

The traditional manual attendance process requires lecturers to spend time calling names and maintaining attendance registers. This project uses Radio Frequency Identification (RFID) technology to automate the process.

When an RFID card is placed near the RFID reader, the reader obtains the card's unique identification number. The Arduino processes the UID and determines whether the card is authorized. The result is displayed on the LCD and indicated using LEDs.

The project report states that attendance data can be stored in an Excel worksheet/database.

## Objectives

- Automate the attendance-taking process.
- Reduce the time required for manual attendance.
- Reduce human errors in attendance records.
- Identify students using unique RFID cards.
- Display authorization/attendance status on an LCD.
- Provide visual indication using LEDs.
- Provide a foundation for storing attendance records digitally.

## Components Used

1. Arduino UNO (ATmega328P)
2. RFID module
3. RFID tag/card
4. Breadboard
5. Jumper wires
6. 16x2 LCD display with I2C interface
7. Resistors
8. LED lights

## System Architecture

```text
RFID Card/Tag
      |
      v
RFID Reader (MFRC522)
      |
      v
Arduino UNO
   /       \
  v         v
LCD       LED Indicators
  |
  v
Attendance / Authorization Status
  |
  v
Data Storage
(Excel worksheet / database)
```

## Working Principle

1. Each student is assigned a unique RFID card/tag.
2. The RFID reader emits radio waves to detect a nearby RFID card.
3. The RFID card responds with its unique identification number (UID).
4. The Arduino receives and processes the UID.
5. The received UID is compared with the stored authorized UID.
6. If the UID matches, the system displays **Authorized access** and activates the access LED.
7. If the UID does not match, the system displays **Access denied** and activates the denied LED.
8. The system resets and waits for the next RFID card.

The project report describes an approximate RFID detection range of **10 cm** for the implemented setup.

## Software and Libraries

The program in the project uses:

- Arduino IDE
- SPI library
- MFRC522 library
- Wire library
- LiquidCrystal_I2C library

### Pin Configuration

| Component | Arduino Pin |
|---|---|
| MFRC522 SS/SDA | D10 |
| MFRC522 RST | D9 |
| Access LED | D6 |
| Denied LED | D7 |
| RFID communication | SPI |
| LCD communication | I2C |

## Program Logic

The Arduino program:

- Initializes serial communication at 9600 baud.
- Initializes the SPI bus.
- Initializes the MFRC522 RFID reader.
- Initializes the 16x2 I2C LCD.
- Waits for a new RFID card.
- Reads and displays the card UID.
- Compares the UID with the stored authorized UID.
- Displays the authorization result.
- Controls the access/denied LEDs.
- Resets the display for the next scan.

## Example Output

### Authorized Card

```text
Show your card:)
        ↓
Tag UID: XX XX XX XX
        ↓
Authorized access
```

### Unauthorized Card

```text
Show your card:)
        ↓
Tag UID: XX XX XX XX
        ↓
Access denied
```

## Advantages

- Accurate attendance identification.
- Faster than manual attendance.
- Reduces human errors.
- Provides automated operation.
- Can support real-time tracking.
- Can be integrated with other software systems.
- Suitable for educational institutions and workplaces.

## Limitations

- Initial hardware and software setup cost.
- RFID tags may need replacement.
- Requires technical knowledge for installation and maintenance.
- RFID signals may be affected by interference.
- Improper implementation can create security risks.
- RFID-based tracking can raise privacy concerns.

## Applications

- Schools and universities
- Colleges and laboratories
- Employee attendance systems
- Access-control systems
- Conferences and seminars
- Event attendance management

## Future Scope

The project report identifies the following future improvements:

- Directly adding attendance information to an Excel spreadsheet.
- Improving the security of stored attendance records.
- Integrating the RFID function into the college ID card so a separate tag does not have to be carried.
- Adding biometric/fingerprint authentication to reduce unauthorized scans.

## Project Structure

A suggested software/project structure is:

```text
RFID-Attendance-System/
├── README.md
├── src/
│   └── RFID_Attendance.ino
├── circuit/
│   └── circuit-diagram.png
└── documentation/
    └── project-report.pdf
```

## Requirements

### Hardware

- Arduino UNO
- MFRC522 RFID reader
- RFID card/tag
- 16x2 I2C LCD
- LEDs
- Resistors
- Breadboard
- Jumper wires
- Suitable 5V DC power supply

### Software

- Arduino IDE
- MFRC522 Arduino library
- LiquidCrystal_I2C Arduino library

## Getting Started

1. Assemble the Arduino, MFRC522 RFID reader, LCD, and LEDs according to the circuit diagram.
2. Install the required Arduino libraries.
3. Open the Arduino program in Arduino IDE.
4. Set the authorized RFID UID in the program.
5. Connect the Arduino UNO to the computer.
6. Upload the program.
7. Open the Serial Monitor at **9600 baud**.
8. Place an RFID card near the reader.
9. Check the UID and authorization status on the LCD/Serial Monitor.

## Note

The current project implementation described in the report compares the scanned RFID UID with a UID stored directly in the Arduino program. The report describes Excel/database storage as part of the attendance system and future scope; a complete network-connected automatic Excel/database implementation would require additional software/hardware integration.

## Author

**K. Tharak Prabath**  
**ID:** 221FE05003  
Diploma in Electronics & Communication Engineering  
Vignan's Foundation for Science, Technology and Research (VFSTR), Vadlamudi, Guntur

## Reference

This README is prepared from the supplied project report **“ATTENDENCE SYSTEM USING RFID”**, which describes the project's components, circuit, Arduino program, working principle, advantages, limitations, applications, conclusion, and future scope. 
