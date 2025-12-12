# Gas-Leakage-Detection

Gas Leakage Detection System — ESP32 & IoT

A smart IoT-based Gas Leakage Detection System built using ESP32, MQ Gas Sensor, Buzzer, LED, and cloud notifications.
This project ensures early gas leak detection, instant alerts, and remote monitoring, making it ideal for homes, industries, and kitchens.

📌 Features

✅ Real-time gas monitoring

✅ Audible alert using buzzer

✅ Visual alert using LED

✅ Wi-Fi–enabled cloud notifications

✅ Threshold-based gas detection

✅ Low-cost & easy to deploy

✅ Supports calibration & testing

🛠️ Hardware Requirements

ESP32 Development Board

MQ Gas Sensor (e.g., MQ-2)

Buzzer

LED (with resistor)

Power Supply / USB Cable

Connecting wires

Breadboard / PCB

💻 Software Requirements

Thonny IDE / Arduino IDE

ESP32 Board Support

Required sensor libraries

Wi-Fi configuration

Cloud notification service (IFTTT / MQTT / Webhooks)

🔌 Circuit Connections
ESP32 ↔ MQ Gas Sensor
MQ Sensor Pin	ESP32 Pin
VCC	5V / 3.3V
GND	GND
A0	GPIO (example: GPIO34)
D0	Not Used
Buzzer
Buzzer Pin	ESP32 Pin
+ (Long)	GPIO pin (example: GPIO15)
- (Short)	GND
LED
LED Pin	ESP32 Pin
Positive (+)	Any GPIO (example: GPIO2)
Negative (-)	GND
🧠 Working Principle

ESP32 reads gas concentration from the MQ sensor.

If the reading crosses a preset threshold, it triggers:

🔔 Buzzer alert

💡 LED indicator

📲 Wi-Fi alert to mobile/cloud

System runs continuously and logs data if enabled.

You can calibrate the threshold for better accuracy.

📡 IoT Notifications

You can send alerts via:

IFTTT Webhooks (Email/SMS/Push notification)

MQTT broker

Custom cloud API

Example triggers:

"GAS LEAK DETECTED – Take action immediately!"

🧪 Testing & Calibration

Test the sensor using a safe gas source (lighter gas, without flame).

Observe readings in serial monitor.

Set an accurate threshold using trial & error.

📷 Snapshots

(Add your project images here)

/images/circuit.jpg
/images/output.jpg

📄 Code Snippet (Example)
import machine
import network
import time

gas_sensor = machine.ADC(machine.Pin(34))
buzzer = machine.Pin(15, machine.Pin.OUT)
led = machine.Pin(2, machine.Pin.OUT)

THRESHOLD = 2000

while True:
    value = gas_sensor.read()
    print("Gas Reading:", value)

    if value > THRESHOLD:
        led.on()
        buzzer.on()
        # send_notification()  # If using cloud
    else:
        led.off()
        buzzer.off()

    time.sleep(1)

📈 Future Scope

AI-based gas prediction

Multi-gas detection

Building automation integration

Portable/wearable detectors

Cloud dashboard monitoring

🎯 Conclusion

This project is a reliable and cost-effective IoT-based gas leakage detection system using ESP32. It enhances safety, prevention, and remote monitoring, ensuring a safer environment at homes and industries.

📚 References

ESP32 Documentation — Espressif

MQ Gas Sensor Datasheet

Pushbullet / IFTTT API Docs
