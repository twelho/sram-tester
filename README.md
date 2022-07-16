# sram-tester

The Universal Static RAM Tester (`sram-tester`) is an Arduino-based testing tool for TTL (5 volt) compatible SRAM modules, such as the 2114 or 6116. I wrote it to help in debugging old computer hardware (e.g. a 1541) in a versatile and fast way.

`sram-tester` is loosely derived from the [2114 SRAM tester](https://github.com/skjerk/Arduino-2114-SRAM-tester) by Carsten Skjerk, but has seen major rework to make it faster and more reliable as well as enable support for SRAM modules with very wide buses and/or large capacities.

# Usage

`sram-tester` should run on most 8-bit Arduino hardware with sufficient pins to communicate with the SRAM module of your choice, but I have only verified its functionality on an Arduino Mega 2560.

Before flashing the sketch to your Arduino, create a profile for your configuration by editing the following constants defined in the beginning of the file:

- `addressPins`: The Arduino pins that correspond to the address pins of the SRAM in the order expected by the SRAM (starting from e.g. `A0`, check the datasheet for your SRAM).
- `dataPins`: The Arduino pins that correspond to the data pins of the SRAM in the order expected by the SRAM (starting from e.g. `D0`, check the datasheet for your SRAM).
- `writePins`: The Arduino pins that correspond to the SRAM pins that must be pulled `HIGH` (normal) or `LOW` (inverted) in order to *write* data. The per-pin boolean states if the pin should be inverted.
- `addressCount`: The number of addressable memory locations in your SRAM model (i.e. its capacity at its native data bus width).

There is an example configuration for testing a 6116 with a Mega 2560 already in place.

Connect your SRAM module to the Arduino and flash the sketch using the Arduino IDE. The test begins automatically, and can be followed over serial at a baud rate of 115200. A summary of the results will be output after the test has finished. You can reset the Arduino (e.g. via the button) to start a new test (e.g. after swapping SRAM modules).

# Authors

- Dennis Marttinen ([@twelho](https://github.com/twelho))

# License

[MIT](LICENSE)
