# SpeedSpy

SpeedSpy is aimed at correcting (or monitoring) one of the most common driver habits: excessive speeding. The project consists of a Particle Photon configured with an Adafruit Ultimate GPS Breakout and external antenna, a 4-ohm speaker, external LED, and an Adafruit Mono 2.5W Class D Audio Amplifier. Together, along with a Blynk app integration, SpeedSpy monitors your vehicle's location and speed, pushes that information to the Blynk app, and emits a shrill alert via the speaker when the speed limit for the current road is exceeded.

A demo of SpeedSpy can be viewed [here](https://www.youtube.com/watch?v=IyeKg0UlMBg).

### Overview

The core of SpeedSpy lies in the Adafruit Ultimate GPS. The GPS unit interfaces with GPS satellites via the external antenna, providing the Photon with the approximate latitude, longitude, altitude, and speed of the device. The latitude and longitude provided by the GPS are used to determine the speed limit of the current road. If the current speed reported by the GPS exceeds this speed limit, a tone is emitted from the speaker and the Blynk app gets a notification. The tone's note denotes the degree to which the current speed limit is exceeded. Each increase in 5 miles per hour _over_ the speed limit results in the tone going up a note on the C-major scale.

The hardware components of SpeedSpy are fully integrated with the vehicle. The Photon, speaker, antenna, and external LED are designed to sit within the console of a vehicle. The Photon is powered via a USB connected to the vehicle's stereo (a cigarette lighter DC socket would also work). Internet connectivity is achieved via tethering to a mobile phone. The external LED indicates whether or not the GPS has acquired enough satellites. A steady flashing LED indicates that the GPS is currently acquiring satellites while an occasional flash indicates satellite acquisition (a "fix").

The SpeedSpy Blynk app includes a map widget for plotting locations where readings were taken along with the speed at the time of the reading. The below image depicts the interface of the Blynk app with a GPS coordinate selected, showing a speed of 43 miles per hour for that reading.

[Blynk](images/blynk.png?raw=true)

The SpeedSpy Blynk app also includes a mute button for silencing the speeding alarm, a speedometer for visualizing the current GPS speed, and two indicators that respectively signal speeding and a GPS fix.

## Wiring diagram

[Wiring diagram](images/wiring.png)

## Hardware

The [Particle Photon](https://store.particle.io/products/photon) runs SpeedSpy's firmware, connects to the internet and interfaces with [Blynk](http://www.blynk.cc/), and handles reading from the GPS and driving the speaker. The Photon is powered by the vehicle's stereo power via a USB plug. WiFi connectivity and Blynk functionality is provided via a tethered cell phone.

The [Adafruit Ultimate GPS](https://www.adafruit.com/product/746) is a GPS breakout board that is powered by the Photon and delivers data about location and speed. Its ability to acquire a satellite fix is enhanced through connection to an [external antenna](https://www.adafruit.com/product/960) via a [SMA to uFL](https://www.adafruit.com/product/851) adapter.

The [speaker](https://www.adafruit.com/product/1314) is driven by an [amplifier](https://www.adafruit.com/product/2130) that allows for volume control via an onboard trim potentiometer.

Lastly, an external LED light is connected to the `FIX` pin of the GPS board to allow easy visualization of satellite connectivity from the console of the vehicle. Without it, it would be impossible to know if the GPS had acquired a fix without opening up the console of the vehicle.

Shown below are the connected hardware components of SpeedSpy outside of the vehicle console enclosure.

[Hardware](hardware.jpg)

The main breadboard with the Photon, amplifier, and GPS unit is show below.

[Breadboard](breadboard.jpg)
