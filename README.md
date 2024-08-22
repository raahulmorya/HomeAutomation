# Home Automation with ESP8266 and SinricPro API

This project is a smart home automation system that allows you to control relays (connected to home appliances) via tactile buttons or remotely through the SinricPro platform. The system is based on an ESP8266 microcontroller, which connects to Wi-Fi and communicates with the SinricPro cloud service to receive commands and update the state of connected devices.

## Features

- **Remote Control:** Control your home appliances remotely through the SinricPro platform.
- **Manual Control:** Use tactile buttons to manually control the relays connected to your appliances.
- **Wi-Fi Connectivity:** Connects to your home Wi-Fi network for seamless integration with SinricPro.
- **State Synchronization:** Ensures that the state of appliances is always synchronized between the physical buttons and the SinricPro app.

## Hardware Requirements

- ESP8266 Microcontroller (e.g., NodeMCU)
- Relays (connected to GPIO pins)
- Tactile buttons or toggle switches
- Wi-Fi network

## Libraries Required

Ensure you have the following libraries installed in your Arduino IDE:

- **SinricPro by Boris Lovosevic**: For communication with the SinricPro platform.
- **ESP8266WiFi**: For Wi-Fi connectivity.

## Pin Configuration

| **Pin**   | **Connected Device**       | **Function**     |
|-----------|----------------------------|------------------|
| D1 (GPIO5)| Relay 1                    | Controls Device 1|
| D2 (GPIO4)| Relay 2                    | Controls Device 2|
| D3 (GPIO0)| Tactile Button 1           | Controls Relay 1 |
| D7 (GPIO13)| Tactile Button 2          | Controls Relay 2 |
| D0 (GPIO16)| Wi-Fi Status LED           | Shows Wi-Fi Status|

## Setup Instructions

1. **Install Dependencies**: Ensure the SinricPro library and its dependencies are installed in the Arduino IDE.
   
2. **Connect to Wi-Fi**: Set up your Wi-Fi credentials by modifying the following lines in the code:
    ```cpp
    #define WIFI_SSID "Your_WiFi_SSID"
    #define WIFI_PASS "Your_WiFi_Password"
    ```
   
3. **Configure SinricPro**: Replace the `APP_KEY`, `APP_SECRET`, and `Device IDs` with your own SinricPro credentials:
    ```cpp
    #define APP_KEY "Your_App_Key"
    #define APP_SECRET "Your_App_Secret"
    #define device_ID_1 "Your_Device_ID_1"
    #define device_ID_2 "Your_Device_ID_2"
    ```

4. **Upload the Code**: Upload the provided code to your ESP8266 using the Arduino IDE.

5. **Test the System**: After uploading, the system should connect to Wi-Fi, and you can control the relays via the SinricPro app or the connected tactile buttons.

## Code Overview

The code is organized as follows:

- **setup()**: Initializes the Wi-Fi connection, relays, and tactile buttons. Also sets up communication with SinricPro.
  
- **loop()**: Handles incoming commands from SinricPro and manages the state of the relays based on tactile button input.

- **setupRelays()**: Configures the relays as output and sets them to an initial state.
  
- **setupFlipSwitches()**: Configures the tactile buttons (flip switches) as input with pull-up resistors.
  
- **handleFlipSwitches()**: Detects the state change of the tactile buttons and updates the relay state accordingly.

- **onPowerState()**: Callback function that handles power state changes received from SinricPro.

## Debugging

To enable debug output over the serial monitor, uncomment the following line:
```cpp
//#define ENABLE_DEBUG
