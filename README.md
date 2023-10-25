# ESP8266-NodeMCU DHT11 Sensor Server

The DHT11 Sensor Server is a simple application running on an ESP8266 WiFi-capable controller that allows you to retrieve temperature and humidity data from a DHT11 sensor. This README file provides an overview of the code and how to use it.

## Introduction

The DHT11 Sensor Server is designed to provide a web-based interface to retrieve temperature and humidity data from a DHT11 sensor connected to an ESP8266 controller. It sets up a WiFi access point, and you can access the sensor data by making HTTP requests to the ESP8266.

## Code Overview

The code is divided into three main sections: WiFi configuration, sensor handling, and web server setup.

### WiFi Configuration

The WiFi configuration is handled by the `initWiFi` function. It sets up the ESP8266 to act as an access point with the SSID "DHT11-0000" and the password "12345678". You can modify these values to match your preferences.

### Sensor Handling

The DHT11 sensor is connected to GPIO pin D2, as defined by `#define GPIO_PIN D2`. The `initSensor` function initializes the sensor, and the `getTemperature` and `getHumidity` functions retrieve temperature and humidity data, respectively.

### Web Server Setup

The ESP8266 serves the sensor data using a simple web server. The `initServer` function initializes the server, sets up two endpoints ("/temperature" and "/humidity"), and defines how to handle incoming requests for these endpoints.

The server responds to requests with the current temperature and humidity values retrieved from the DHT11 sensor. These values are sent as plain text in the HTTP response body.

## Usage

1. Make sure you have the necessary libraries installed. This code uses the Adafruit DHT library, so ensure it's available in your Arduino IDE.

2. Modify the WiFi configuration in the `initWiFi` function to match your network settings if needed.

3. Upload the code to your ESP8266 controller.

4. Open the Arduino Serial Monitor to view the ESP8266's serial output.

5. Connect to the ESP8266 access point with the SSID "DHT11-0000" and password "12345678."

6. Once connected, open a web browser or use a tool like `curl` to make HTTP GET requests to the ESP8266. For example:
   - To get the temperature: `http://192.168.4.1/temperature`
   - To get the humidity: `http://192.168.4.1/humidity`

7. The ESP8266 will respond with the temperature and humidity values in plain text.
