# The MCUmeter

The MCUmeter started as a gift for a "secret santa" round at my favourite electronics club, the [Boldport Club](https://www.boldport.com/). It was something I always wanted to do because it's useful, simple to build and can offers a nice learning experience for people who want to do microcontroller based themselves.

## What is it?

In a nutshell it’s a high performance voltage/current/power monitor which will render it’s voltags/current/power readings supplied by a Texas Instruments INA260 via a STM32F042 microcontroller onto a small OLED display.

It consists of two main ingredients:

* Custom made hardware, which is what this repository is all about
* Software which is written in Rust and can be found [here](https://github.com/therealprof/MCUmeter-software) or directly on [crates.io](https://crates.io/crates/mcumeter)

The hardware design was done in KiCad and this repository contains both the KiCad 5 design files as well as the Gerber files which can be sent directly to a fabhouse to build the project.

## Hardware connections

The [INA260](http://www.ti.com/lit/ds/symlink/ina260.pdf) allows sensing voltages (DC and positive values only!) up to 36V and high-side as well as low-side currenty (polarity not relevant). It can also do the power calculations, although at reduced precision.

The connections (from left to right) are
* V_IN:  Positive voltage to be measured. Important! This power meter does not like negative voltages so watch the polarity!
* I_IN+/I_IN-: High-side (i.e. connected between the power supply and DUT) or Low-side (i.e. connected between ground and the DUT) current measuring. Polarity irrelevant.
* GND: Ground of voltage measurement, common with the rest of the circuit

It also provides a 4-pin header to connect a SSD1306 OLED display with I2C interface using the following pinout:
* VCC
* Ground
* SCL
* SDA

The connectors can be either soldered onto the board or screwed on, good results have been achieved with e.g. MC/Stäubli XUB-G

## Can I reuse the hardware for my own ideas?

Absolutely, everything is licensed under the BSD license so please go ahead and use it however you'd like. 
