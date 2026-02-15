# VL53L0X Laser Distance Sensor with Raspberry Pi Pico

This repository contains a C project to use the VL53L0X Time-of-Flight (ToF) laser distance sensor with the Raspberry Pi Pico board.

## ✨ Features

-   Integration with the VL53L0X laser distance sensor.
-   Continuous distance reading in millimeters.
-   I2C communication with the Raspberry Pi Pico.
-   Project configured for easy compilation with the Raspberry Pi Pico SDK and CMake.

## 🛠️ Required Hardware

-   **Raspberry Pi Pico** or **Pico W**
-   **VL53L0X Laser Distance Sensor**
-   **Cables/Jumper wires** for connection

## 📦 Software and Dependencies

-   **Visual Studio Code**
-   **Raspberry Pi Pico/W Extension for VS Code**
-   **Raspberry Pi Pico SDK**, **ARM GCC Compiler**, and **CMake**

## 🔌 Connections

Connect the VL53L0X sensor to the Raspberry Pi Pico using the I2C0 interface, as defined in the `src/sensor-distancia-laser.c` file:

| VL53L0X Pin | Raspberry Pi Pico Pin     | Description      |
| :---------- | :------------------------ | :--------------- |
| **VIN** | **3V3 (OUT)** | Power Supply     |
| **GND** | **GND** | Ground           |
| **SCL** | **GP1 (I2C0 SCL)** | I2C Clock        |
| **SDA** | **GP0 (I2C0 SDA)** | I2C Data         |

## 🚀 How to Compile and Run

### Using VS Code with the Raspberry Pi Pico Extension (Recommended)

This project is already configured for the official extension, making the process very simple.

1.  **Open the Project:** Open the project root folder in Visual Studio Code.
2.  **Prepare the Board:** Put the Raspberry Pi Pico into **BOOTSEL** mode (press and hold the BOOTSEL button while connecting the USB cable).
3.  **Upload the Code:** Click the **`Run`** button in the status bar or use the shortcut. The extension will automatically compile the code and flash it to the board using `picotool`.
4.  **View Output:** Open the integrated serial monitor in VS Code to view distance measurements.

### Using the Command Line

If you prefer not to use VS Code, you can compile manually.

1.  **Clone the repository:**
    ```bash
    git clone <YOUR_REPOSITORY_URL>
    cd <FOLDER_NAME>
    ```
2.  **Create and configure the build:**
    * Ensure the `PICO_SDK_PATH` environment variable points to your SDK directory.
    ```bash
    mkdir build
    cd build
    cmake ..
    ```
3.  **Compile:**
    ```bash
    make
    ```
4.  **Load the firmware (`.uf2`):**
    -   Put the Pico into **BOOTSEL** mode.
    -   Copy the `build/sensor-distancia-laser.uf2` file to the drive mounted by the Pico on your system.

## 📂 Project Structure

```
.
├── .vscode/               # Visual Studio Code configuration files for the extension
├── build/                 # Directory (ignored) where build files are generated
├── inc/                   # Header files (.h)
│   └── tof.h
├── src/                   # Source code files (.c)
│   ├── sensor-distancia-laser.c
│   └── tof.c
├── .gitignore             # Files and folders ignored by Git
├── CMakeLists.txt         # CMake configuration file for the project
├── LICENSE                # Project license
└── pico_sdk_import.cmake  # Script to import the Pico SDK
```
## 📄 License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for more details.
