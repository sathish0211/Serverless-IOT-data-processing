# Serverless-IOT-data-processing

Welcome to the Serverless IoT Home Automation project! This repository contains the source code and documentation for a serverless IoT solution designed to make your home smarter and more efficient.

## Introduction

In today's world, home automation is becoming increasingly popular as it offers the convenience of controlling various home devices and systems remotely. Our Serverless IoT Home Automation system provides an open-source and highly customizable solution for automating your home. Whether you want to control your lights, temperature, security systems, or any other IoT devices, this project can help you achieve that.

## Features

- **Remote Control:** Control your home devices from anywhere using a web interface or a mobile app.

- **Scalability:** Easily add new IoT devices and sensors to your setup as your needs change.

- **Automation:** Create custom automation rules to trigger actions based on specific events or schedules.

- **Security:** Implement robust security measures to protect your home and data.

- **Energy Efficiency:** Monitor and optimize energy consumption to reduce utility bills.

- **Notifications:** Receive alerts and notifications about important events at your home.

- **Third-Party Integration:** Integrate with popular smart home platforms and services.

## Getting Started

### Prerequisites

To set up the Serverless IoT Home Automation system, you will need the following:

- Raspberry Pi or a similar single-board computer.
- IoT devices compatible with your chosen communication protocol (e.g., Zigbee, Z-Wave, Wi-Fi).
- AWS or another cloud provider for serverless functions and data storage.
- Web server for the user interface (optional).

### Installation

1. Clone this repository to your Raspberry Pi.
2. Follow the installation instructions in the [INSTALL.md](INSTALL.md) file.
3. Configure your IoT devices to connect to the system.
4. Set up your cloud environment and serverless functions as described in the [CloudSetup.md](CloudSetup.md) guide.

For detailed setup instructions and configuration options, please refer to our installation documentation.

## Usage

Once your Serverless IoT Home Automation system is up and running, you can start using it to manage your home devices. Access the web interface or mobile app to control your lights, thermostat, security cameras, and more. Set up automation rules to make your home work for you.

The system also provides APIs for developers to extend its functionality and integrate it with other services.

## Architecture

Our Serverless IoT Home Automation system follows a modern, scalable, and modular architecture. Here is an overview of the components:

- **IoT Devices:** These are the smart devices you want to control, such as smart plugs, lights, or sensors.

- **Raspberry Pi (Edge Device):** The Raspberry Pi acts as the central hub for your IoT devices, running local processing and serving as a bridge to cloud services.

- **Serverless Functions (Cloud):** We use serverless functions provided by AWS Lambda to execute custom logic, handle data storage, and send notifications.

- **Web Interface (Optional):** If desired, you can set up a web-based interface for managing your home devices and automation rules.

 ## Architecture flow

User says a command into the microphone, or sends a text to the Twilio SMS number

User input is captured and embedded in an HTTP POST request triggering an IBM Cloud Functions sequence

The first IBM Cloud Functions action in the sequence forwards the audio to Speech to Text service, and waits for the response

Transcription is forwarded to the second IBM Cloud Functions action

IBM Cloud Functions action 2 calls the Watson Assistant service to analyze the user's text input, again waits for the response

Watson Assistant service result is forwarded to final IBM Cloud Functions action

Final IBM Cloud Functions action publishes a entity/intent pair (fan/turnon for example) to the IoT MQTT broker

MQTT client subscribed on Raspberry Pi receives and interprets result

Raspberry Pi transmits corresponding RF signal to adjust outlet state


