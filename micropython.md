

## Introduction to MicroPython

#### These slides: [slides.cuban.tech/micropython.html](http://slides.cuban.tech/micropython.html)

----------------

### Wifi Info

Network: cubantech

Password: meet-ups

--

- Slides are based on a [talk](http://todayispotato.github.io/micropython-talk/#/25) by [Lars de Ridder](https://github.com/todayispotato)
- The workshop is based heavily on [Nodebots with CubanTech workshop](http://slides.cuban.tech/nodebots.html)
- ... which is based heavily on a workshop by [NY-Javascript](http://www.meetup.com/NY-Javascript) (see [bit.ly/nyjs-nodebots](http://bit.ly/nyjs-nodebots))
- ... which is based heavily on a workshop by [Francis Gulotta](https://twitter.com/reconbot) and [Rick Waldron](https://twitter.com/rwaldron)
- You can find the slides for that workshop at [gul.ly/3tjj](http://gul.ly/3tjj)
- You can sign up for one of their workshops on the [Nodebots NYC Meetup page](http://www.meetup.com/nodebots/)

---

## Our community guidelines

[Be excellent to each other](https://github.com/nodeschool/havana/blob/master/Code_of_Conduct.md)

---

Upcoming CubanTech Events

- [CubanTech meetups](http://meetup.cuban.tech)
- [Docker Cuba meetups](http://docker.cuban.tech)
- [Blockstack Cuba meetups](http://blockstack.cuban.tech)
- [SciPyLA 2017](http://scipyla.org/conf/2017)
  * ##### Universidad de Sancti Spiritus, November 22nd - 25th 2017

---

# Huge thanks to our host

---

## So, MicroPython

Who had heard of it before?

And who used it before?

For something serious?

For something that is running right now?

---

## Microcontrollers + Python = MicroPython

![](img/micropython.png)

MicroPython is a lean and fast implementation of the Python (version 3) programming language that is optimised to run on a microcontroller.

--

## Really ... ?

- Kickstarted in November 2013
- Original kickstarter ended April 2015
  *  &pound;97,803 first campaign
  * +&pound;200,000 in total
- Code open source : [github.com/micropython](https://github.com/micropython)

---

## But why?

- Existing community (that includes you)
- Easy to learn, with powerful features
- Good separation between int and float (unlike JS/Lua)
- Native bitwise operations on 1's and 0's (unlike Lua)
- Ideal for rapid prototyping
- Bridge between web-world and IoT world
- Lots of opportunities for optimization!

--

## ... and why not CPython?

Mainly due to RAM usage. Examples:

- Preallocation of 257 + 5 ints = 4k RAM
- Method calls: led.on() creates a bound method object = 20 bytes RAM

--

## Theoretical minimum system requirements

128kb ROM / 8kb RAM (after subtracting other software)

##### UNIX port around 280kb flash

---

# How so Micro ?

--

## Mainly RAM optimizations

- Many strings predefined in ROM (led, on, read, ...)
- Optimised method calls
- Everything that can be in ROM, is in ROM
- Garbage collection: Mark-and-sweep (no reference counts)

--

## Tagged pointers

A tagged pointer is a pointer (concretely a memory address) with additional data associated with it

- Integer - xxxx xxxx xxxx xxx1
- String - xxxx xxxx xxxx xx10
- Object - xxxx xxxx xxxx xx00

---

# Some supported boards

---

## The PyBoard

![](img/pyboard.small.png)

- Reference implementation
- Initially only on the pyboard, now on multiple chips
- ARM 32bit Cortex M4 @ 168Mhz, 1Mb flash, 192kb RAM
- Accerelometer, RTC, 4 LEDs, 2 switches, 30 GPIO

---

## BBC Micro:Bit

![](img/microbit.small.png)

16kb RAM, 256kb flash, Cortex M0 @ 16 MHz

--

## BBC Micro:Bit

Supplied to *1 million* school children

- 25 LEDs
- Two programmable buttons
- Accelerometer & magnetometer
- Bluetooth
- 5 GPIO

--

### ... comes with:

- Online Python editor
- Mobile app to upload code
- Tons of documentations, teaching material, etc.

--

### ... comes with:

![](img/microbit.pxt.small.png)

- Graphical drag-and-drop editor

--

## Buy it now ! ... :)

![](img/microbit.amazon.png)

Shipping is free for orders in the UK \o/

---

## The WiPy

![](img/wipy.small.png)

256kb RAM, 2Mb flash, 25 GPIO, Cortex M4 @ 80 MHz

#### "Small and light to fit in any cavity"

---

## LoPy

![](img/lopy.small.png)

LoRa + Python

--

## LoRa ... hmmm ?

[![](img/lora.logo.white.png)](https://www.lora-alliance.org/)

- Long range, low power wireless platform 
- Prevailing technology choice for building IoT networks worldwide.
- +500 members
- LoRaWAN<sup>&#153;</sup> Protocol Deployments
  * Low Power WAN (LPWAN) specification for wireless battery operated Things

---

## Feather M0 Express

[![](img/feather.m0.express.png)](https://www.adafruit.com/product/3403)

--

## Feather M0 with radio

|                                    |                                                                       |
|------------------------------------|-----------------------------------------------------------------------|
| ![](img/feather.m0.lora.png) | ![](img/feather.m0.rfm69hcw.png) |
| <small> RFM59 LoRA - [900 MHz](https://www.adafruit.com/product/3178) </small> | <small> Packet Radio [433 MHz](https://www.adafruit.com/product/3177), [868 or 915 MHz](https://www.adafruit.com/product/3176) </small> |

--

## Feather M0 wireless

|                                    |                                                                       |
|------------------------------------|-----------------------------------------------------------------------|
| ![](img/feather.m0.atwinc1500.png) | ![](img/feather.m0.bluefruit.png) |
| <small> [WiFi](https://www.adafruit.com/product/3010) </small> | <small> [Bluetooth](https://www.adafruit.com/product/2995) |

--

## Feather M0 Express - specs

- ATSAMD21G18 @ 48MHz with 3.3V logic/power
- 256KB of FLASH + 32KB of RAM
- 32.768 KHz crystal for clock generation & RTC
- 3.3V regulator with 500mA peak current output
- USB native support (USB bootloader, serial port debugging)
- USB storage key [UF2 bootloader](https://learn.adafruit.com/adafruit-feather-m0-express-designed-for-circuit-python-circuitpython/uf2-bootloader)

--

## Feather M0 Express - specs

- 20 GPIO pins (PWM outputs for all)
- Hardware Serial, I2C, SPI support
- 6 x 12-bit analog inputs
- 1 x 10-bit analog ouput (DAC)
- Built in 100mA lipoly charger (with LED)
- Pin #13 red LED

---

## Circuit Playground Express

![](img/circuitpython.small.png)

--

## CircuitPython

|                             |                        |
|-----------------------------|------------------------|
| ![](img/circuitpython.logo.png) | ![](img/adafruit.logo.jpg) |

--

### Circuit Playground Express board - features

- ATSAMD21 ARM Cortex M0 Processor
  * 3.3V and 48MHz
- 2 MB of SPI Flash storage
- MicroUSB port
  * Programming and debugging
  * serial port
  * keyboard, mouse
  * joystick or MIDI

--

### Circuit Playground Express board - other features

- 10 x mini NeoPixels
- 1 x Motion sensor (LIS3DH)
  * Triple-axis accelerometer
  * Tap and free-fall detection
- 1 x Temperature sensor (thermistor)
- 1 x Light sensor (phototransistor).
  * Color sensor and pulse sensor.

--

### Circuit Playground Express board - more features

- 1 x MEMS microphone
- 1 x Mini speaker with class D amplifier
- 2 x Push buttons
- Infrared receiver and transmitter
  * Receive and transmit any remote control codes
  * Send messages between Circuit Playground Expresses
  * Proximity sensor.

--

### Circuit Playground Express board - even more features

- 8 x alligator-clip friendly input/output pins

--

### ... comes with

- Online Python and Javascript editor
- Tons of [documentations](http://adafru.it/wpE), teaching material, etc.

--

### ... comes with:

![](img/makecode.circuitpython.small.png)

- Graphical drag-and-drop editor

---

## ESP8266 and NodeMCU

![](img/feather.huzzah.small.png)

... also runs on ESP8266 (i.e. a lot of) chips 

---

## NodeMCU devkit - DOIT

![](img/nodemcu.doit.png)

---

## NodeMCU devkit - Makerfocus D1 mini

![](img/nodemcu.d1mini.png)

--

## NodeMCU devkit pinout

![](img/nodemcu.doit.pinout.png)

---

## LoLin pinout

![](img/nodemcu.lolin.pinout.png)

---

## Adafruit Feather Huzzah ESP8266

![](img/feather.huzzah.png)

--

## Feather HUZZAH ESP8266 - specs

- ESP8266 @ 80MHz or 160 MHz 
- 3.3V logic/power, 500mA peak current output
- 4MB of FLASH (32 MBit)
- CP2104 USB-Serial converter onboard
  * 921600 max baudrate for uploading
- 9 GPIO pins
  * can also be used as I2C and SPI
- 1 x analog inputs 1.0V max

--

## Feather HUZZAH - 100mA lipoly charger

![](img/feather.huzzah.lipoly.png)

--

## Feather HUZZAH ESP8266 - [pinout](https://learn.adafruit.com/adafruit-feather-huzzah-esp8266/pinouts)

![](img/feather.huzzah.pinout.png)

---

## Adafruit HUZZAH ESP8266 Breakout

![](img/huzzah.breakout.png)

--

## HUZZAH ESP8266 Breakout - specs

- 1 x Analog input (1.0V max)
- 9 x GPIO (3.3V logic)
  * Also used for I2C or SPI
- 2 x UART pins
- 2 x 3-6V power inputs
  * reset, enable, LDO-disable
  * 3.3V output

--

## HUZZAH ESP8266 Breakout - power pins

![](img/huzzah.breakout.pinout.power.png)

- voltage regulator (stick to 4V to 6V)
  * [Schottky diodes](https://en.wikipedia.org/wiki/Schottky_diode) for variable voltages
- **VBat** : Lipoly battery
- **V+** : 5V ( FTDI/serial header )

--

## HUZZAH ESP8266 Breakout - serial pins

![](img/huzzah.breakout.pinout.serial.png)

- TX ( 3.3V ) and RX ( 5V )

--

## HUZZAH ESP8266 Breakout - GPIO pins

![](img/huzzah.breakout.pinout.gpio.png)

- No pull-up in **#0**
- 3.3V logic 
  * max current drawn : 12mA.
- [Full spec sheet](http://www.adafruit.com/datasheets/ESP8266_Specifications_English.pdf)

--

## HUZZAH ESP8266 Breakout - other pins

![](img/huzzah.breakout.pinout.analog.png)

- **A** : analog input ( 0 - 1.0V )
- **LDO** : connect to **GND** to turn 3.3V regulator off
- **RST** ( 5V ) **EN** ( 3.3V )
  * down to **GND** to reset ESP8266

---

## MakerFocus D1 mini ESP8266

![](img/d1mini.png)

--

## MakerFocus D1 mini - specs

TODO

--

## MakerFocus D1 mini - pinout

TODO

---

## LoLin

![](TODO)

--

## LoLin - specs

TODO

--

## LoLin - pinout

TODO

---

# Excuse me ... 

# What is MicroPython ?

---

## It's Python! (3.4-ish)

```python

>>> print('Hello world!')
Hello world!

>>> with open('pygrunn.txt', 'w') as f:
>>>     f.write('Hello PyGrunn!')

>>> try:
>>>     1/0
>>> except ZeroDivisionError as e:
>>>     print("Oh, you!")
Oh, you!
```

---

## ... but not all of it

```python

>>> import functools
Traceback (most recent call last):
    File "<stdin>", line 1, in <module>
ImportError: no module named 'functools'
>>> import this
Traceback (most recent call last):
    File "<stdin>", line 1, in <module>
ImportError: no module named 'this'
```

---

## Supported modules

- `sys`
- `time`
- `struct`
- `machine` - functions related to the board
- `micropython` - internals
- Specific ports provides specific hooks, REPL and custom modules

---

## Supports async / await syntax

```python

async def ping_pygrunn():
    return await ping_server('pygrunn.org')
```

---

## External Standard Library

Written in Python (remember PyPy?)

```sh

$ micropython -m upip install micropython-functools
$ ./micropython 
MicroPython v1.7-116-g8dd704b on 2016-04-19; linux version
Use Ctrl-D to exit, Ctrl-E for paste mode
>>> import functools
>>> dir(functools)
['__name__', 'reduce', 'partial', 'update_wrapper', '__file__', 'wraps']
https://github.com/micropython/micropython-lib
```

---

# Hardware APIs

--

## Your Micro-superpowers include:

- Disable interrupts
- Trigger and disable GC
- Write inline assembler
- Emit bytecode or machine code

--

## Inline assembler - Returning a value

```python

>>> @micropython.asm_thumb
... def fun():
...     movw(r0, 42)
...
>>> print(fun())
42
```

--

## Inline assembler - peripherals

```python

@micropython.asm_thumb
def led_on():
    movwt(r0, stm.GPIOA)
    movw(r1, 1 << 13)
    strh(r1, [r0, stm.GPIO_BSRRL])
```

Turn on the red LED in the PyBoard (i.e. PA13 high)

--

## Inline assembler - Arguments

```python

>>> @micropython.asm_thumb
... def asm_add(r0, r1):
...     add(r0, r0, r1)
...
>>> asm_add(1, 2)
3
```

- Up to 4 arguments
- They must be named `r0`, `r1`, `r2` and `r3`

--

## Inline assembler - Flash LED r0 times

```python

@micropython.asm_thumb
def flash_led(r0):
    # get the GPIOA address in r1
    movwt(r1, stm.GPIOA)

    # get the bit mask for PA14 (the pin LED #2 is on)
    movw(r2, 1 << 14)
    b(loop_entry)
    label(loop1)

    # turn LED on
    strh(r2, [r1, stm.GPIO_BSRRL])

    # delay for a bit
    movwt(r4, 5599900)
    label(delay_on)
    sub(r4, r4, 1)
    cmp(r4, 0)
    bgt(delay_on)

    # turn LED off
    strh(r2, [r1, stm.GPIO_BSRRH])

    # delay for a bit
    movwt(r4, 5599900)
    label(delay_off)
    sub(r4, r4, 1)
    cmp(r4, 0)
    bgt(delay_off)

    # loop r0 times
    sub(r0, r0, 1)
    label(loop_entry)
    cmp(r0, 0)
    bgt(loop1)
```

- `label(x)` - assign label
- `b(x)` unconditional branch
- `bgt(x)`, `blt(x)`, ... conditional branch

--

## Native code emitter

```python

@micropython.native
def foo(self, arg):
    # code
```

Roughly twice as fast, but larger binary

--

## Viper is Python embedded in realtime

```python

@micropython.viper
def foo(self, arg: int) -> int:
    # code
```

- Now actually called Zerynth and kind of confusing
- Not fully standards-compliant Python code
- Produces machine instructions

---

# Current state of MicroPython

---

## Development

- One full time developer, two core contributors
- Partly funded by the European Space Agency
- Kickstart in May 2016 for proper ESP8266 sockets support
- Feels like it's maturing

---

## Is it production ready?

It depends on your board

But it's amazing for prototyping!

Or for embedding in games and apps

--

## Embedding Python in games ?

![](img/civ.iv.jpg)

... has happened before, not MicroPython though ...

--

### Embedded Python for video games

##### Civilization IV

![](img/civ.iv.jpg)

All internal logic, including AI. The API is available .

--

### Embedded Python for video games

##### The Temple of Elemental Evil

![](img/toee.small.jpg)

Almost everything except the rendering engine , [according to Steve Moret](http://www.pygame.org/interview/stevemoret.shtml)

--

### Embedded Python for video games

##### Star Trek Bridge Commander

![](img/BridgeCommander.small.jpg)

Scripts of the missions

--

### Embedded Python for video games

##### Crystal Space

![](img/crystal.space.small.jpg)

All internal logic, including AI. The API is available .

--

### Embedded Python for video games

##### Battlefield 2

![](img/battlefield.4.small.jpeg)

Gameplay , scores , team stats

---

# Let's get started!

---

## Our hardware

[![](img/hardware-kit-closed.jpg)](http://www.seeedstudio.com/depot/ARDX-The-starter-kit-for-Arduino-p-1153.html)

---

## Our hardware

[![](img/hardware-kit-open.jpg)](http://www.seeedstudio.com/depot/ARDX-The-starter-kit-for-Arduino-p-1153.html)

---

## Kits may be missing equipment

------------

If you have trouble finding a component, let us know and we'll get you a replacement

---

## Not working?

## Probably hardware!

---

## Components We are Covering

- Network programming with ESP8266
- LEDs (Light Emitting Diodes)
- Buttons
- Servos

---

Feel free to select the components you like most and complete the challenges that most interest you

--

## Adafruit HUZZAH ESP8266 Breakout - pinout

---

# Getting started

---

## Getting started PyBoard

Zero conf

![](img/pyboard.small.png)

---

## Getting started ESP8266

```sh

pip install esptool
```

Since Version 1.3 supports both Python 2.7 and 3.4 <br/> (or higher)

--

### Identify USB - GNU/Linux

```sh
$ udevadm monitor --udev
monitor will print the received events for:
UDEV - the event which udev sends out after rule processing

UDEV  [1504678146.578976] add      /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2 (usb)
UDEV  [1504678146.746860] add      /module/usbserial (module)
UDEV  [1504678146.747288] add      /bus/usb-serial (bus)
UDEV  [1504678146.747855] add      /bus/usb/drivers/usbserial (drivers)
UDEV  [1504678146.748149] add      /bus/usb/drivers/usbserial_generic (drivers)
UDEV  [1504678146.748241] add      /bus/usb-serial/drivers/generic (drivers)
UDEV  [1504678146.772466] add      /module/ch341 (module)
UDEV  [1504678146.772783] add      /bus/usb-serial/drivers/ch341-uart (drivers)
UDEV  [1504678146.774556] add      /bus/usb/drivers/ch341 (drivers)
UDEV  [1504678146.774614] add      /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2:1.0 (usb)
UDEV  [1504678146.775507] add      /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2:1.0/ttyUSB0 (usb-serial)
UDEV  [1504678146.803046] add      /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2:1.0/ttyUSB0/tty/ttyUSB0 (tty)

```

--

### Identify USB - Mac OS X

```sh

$ ls /dev/cu*serial*
/dev/cu.wchusbserial1410

```

--

## Erase and deploy firmware

```sh

esptool.py --port /dev/ttyUSB0 erase_flash
esptool.py --port /dev/ttyUSB0 --baud 460800 write_flash --flash_size=detect 0 esp8266-20170526-v1.9.bin
```

- Specify the device name identified earlier after `--port`
- Reduce the baudrate if you get errors when flashing (e.g. down to 115200)

--

## ... if it still does not work ...

For some NodeMCU boards specify `-fm dio` option

```sh
esptool.py --port /dev/ttyUSB0 --baud 460800 write_flash --flash_size=detect -fm dio 0 esp8266-20170526-v1.9.bin
```

---

## REPL over the serial port

- Plug mini-USB (board) to USB (laptop) cable
- Identify USB device
- Connect over serial connection

--

### Identify and connect over USB - GNU/Linux

<small>
```sh
$ udevadm monitor --udev
monitor will print the received events for:
UDEV - the event which udev sends out after rule processing

UDEV  [1504678146.578976] add      /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2 (usb)
UDEV  [1504678146.746860] add      /module/usbserial (module)
UDEV  [1504678146.747288] add      /bus/usb-serial (bus)
UDEV  [1504678146.747855] add      /bus/usb/drivers/usbserial (drivers)
UDEV  [1504678146.748149] add      /bus/usb/drivers/usbserial_generic (drivers)
UDEV  [1504678146.748241] add      /bus/usb-serial/drivers/generic (drivers)
UDEV  [1504678146.772466] add      /module/ch341 (module)
UDEV  [1504678146.772783] add      /bus/usb-serial/drivers/ch341-uart (drivers)
UDEV  [1504678146.774556] add      /bus/usb/drivers/ch341 (drivers)
UDEV  [1504678146.774614] add      /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2:1.0 (usb)
UDEV  [1504678146.775507] add      /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2:1.0/ttyUSB0 (usb-serial)
UDEV  [1504678146.803046] add      /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2:1.0/ttyUSB0/tty/ttyUSB0 (tty)

$ picocom /dev/ttyUSB0 -b115200
```
</small>

... not always `ttyUSB0` e.g. `ttyACM0` 

--

### Identify and connect over USB - Mac OS X

```sh

$ ls /dev/cu*serial*
/dev/cu.wchusbserial1410

$ screen /dev/cu.wchusbserial1410 115200 -L
MicroPython v1.9-8-gfcaadf92 on 2017-05-26; ESP module with ESP8266
Type "help()" for more information.
>>>

```

... The device name might not be `/dev/cu.wchusbserial1410`

---

## Components We're Covering

- <span style="color:yellow"> Network programming with ESP8266 </span>
- LEDs (Light Emitting Diodes)
- Buttons
- Servos

---

## Network config (MicroPython on ESP8266)

- WiFi access point (AP)
  * ESSID is of the form MicroPython-xxxxxx (MAC address of your device)
  * Factory reset Password `micropythoN`
  * IP address `192.168.4.1`
- Station interface

---

## Install WebREPL if you haven't already

```sh
git clone https://github.com/micropython/webrepl
```

[Download WebREPL from the Internet](https://github.com/micropython/webrepl)

[Download WebREPL from LAN](ftp://qnap01.local/Public/soft/micropython/webrepl)

---

## Setup WebREPL access (over USB)

```python

import webrepl_setup
```

- Follow the on-screen instructions and prompts
- Reboot your MicroPython device.

---

## WebREPL

![](img/webrepl.png)

- Connect to the ESP8266's access point
- Launch WebREPL
  * Open `webrepl.html` in your browser
- Click the "Connect" button
- Type the password set with `webrepl_setup` when prompted 

---

## Network module

```python

>>> import network
>>> sta_if = network.WLAN(network.STA_IF)
>>> ap_if = network.WLAN(network.AP_IF)

```

---

## (Network) interface activation status

```python

>>> sta_if.active()
False
>>> ap_if.active()
True
>>> ap_if.ifconfig()
('192.168.4.1', '255.255.255.0', '192.168.4.1', '8.8.8.8')
```

Returned values are: IP address, netmask, gateway, DNS.

---

## Network configuration

```python

>>> sta_if.active(True)
>>> sta_if.connect('cubantech', 'meetups')
>>> sta_if.isconnected() # Might take a while
True
>>> sta_if.ifconfig()
('192.168.0.2', '255.255.255.0', '192.168.0.1', '8.8.8.8')

```

---

## We have WiFi ?

```python

>>> import socket
```

We have sockets !!!

---

## Simple HTTP server

State of all GPIO pins

```python

import machine
pins = [machine.Pin(i, machine.Pin.IN) for i in (0, 2, 4, 5, 12, 13, 14, 15)]
html = """<!DOCTYPE html>
<html>
    <head> <title>ESP8266 Pins</title> </head>
    <body>
        <h1>ESP8266 Pins</h1>
        <table border="1"> <tr><th>Pin</th><th>Value</th></tr> %s </table>
    </body>
</html>
"""

import socket
addr = socket.getaddrinfo('0.0.0.0', 80)[0][-1]
s = socket.socket()
s.bind(addr)
s.listen(1)
print('listening on', addr)
while True:
    cl, addr = s.accept()
    print('client connected from', addr) cl_file = cl.makefile('rwb', 0)
    while True:
        line = cl_file.readline()
        if not line or line == b'\r\n':
            break
    rows = ['<tr><td>%s</td><td>%d</td></tr>' % (str(p), p.value()) for p in pins] response = html % '\n'.join(rows)
    cl.send(response)
    cl.close()
```

---

## Components We're Covering

- Network programming with ESP8266
- <span style="color:yellow"> LEDs (Light Emitting Diodes) </span>
- Buttons
- Servos

---

## LEDs

#### <span class="red-led">LIGHT</span> <span class="green-led">EMITTING</span> <span class="blue-led">DIODES</span>

![](img/leds.jpg)

---

## Identifying LED Pins

- Long pin is positive (and goes to power)
- Short pin is negative (and goes to ground)

![](img/led-pin-diagram.png)

---

## Build This - Feather HUZZAH ESP8266

![](img/feather.huzzah.led.png)

--

## Alternative - PyBoard

![](img/pyboard.led.png)

---

Run this in (USB or web) REPL

```python
import machine
import time

pin_id = 15 # Huzzah Feather
            # PyBoard = 'A14'
led = machine.Pin(pin_id, machine.Pin.OUT)
while True:
    led.high()
    time.sleep(0.5)
    led.low()
    time.sleep(0.5)
```

Exit loop with `Ctrl-c`

--

## Built-in LEDs (PyBoard)

| Physical name | CPU name | LED description |
|---------------|----------|-----------------|
| P2            | B4       | blue LED        |
| P3            | A15      | yellow LED      |
| P4            | A14      | green LED       |
| P5            | A13      | red LED         |

--

## Built-in LEDs (Huzzah)

- Red LED at pin 0
- Blue LED at pin 2

---

## If successful, you should see this

![](img/huzzah.blinking-led.gif)

---

## Changing the Blink Rate

- You probably noticed the light blinks about every .5 seconds
- Change the code to blink at a different rate and then rerun it to make sure it works
- If you're stuck, press &darr; to see a potential solution

--

```js
var five = require("johnny-five");
var board = new five.Board();

board.on("ready", function() {

  var led = new five.Led(11);

  // "blink" the led in 3000ms on-off phase periods
  led.blink(3000);
});
```

`node blinky.js`

---

## The REPL

- Stands for Read Evaluate Print Loop
- Allows us to type code in our terminal and see it affect our robots

---

## Write and run this. Then, go on to the next slide.

```js
var five = require("johnny-five");
var board = new five.Board();

board.on("ready", function() {
  var led = new five.Led(11);

  this.repl.inject({
    led: led
  });
});
```

`node led-boss.js`

---

## Type these commands in the REPL and watch how the LED changes

```
> led.on();

> led.off();

> led.blink();

> led.stop();

> led.pulse();
```

---

## REPL Inject

The reason we're able to access the led object in the REPL is because of this bit of code in the previous example. It exposes the led object to our REPL session.

```js
this.repl.inject({
  led: led
});
```

---

## Breadboards: Solderless wiring

#### Breadboards allow us to quickly wire components together for prototyping

![](img/breadboard.small.png)

---

## Breadboards: Electrical Connections

- #### Here you can see how the different rows and columns are connected.
- #### If unclear, don't hesitate to do some Googling or ask a volunteer to explain them further.

![](img/breadboard-diagram.small.jpg)

## Use your breadboard and a couple of wires (color doesn't matter) to build this

![](img/arduino-led-breadboard.png)

---

Now run one of your programs from before and make sure the LED still blinks

---


## LED Challenges

Now that you've got the basics of LEDs, you can either move on to the next component, or work on some LED challenges

- Press &rarr; to move on to the next component
- Press &darr; to scroll through the LED challenges

--

## LED Challenges

*Try to solve them yourself before looking at the solution!*

Press &darr; to scroll through the following challenges (and potential solutions)

1. Multiple Lights
2. Holiday Lights
3. Binary Counter

--

### 1. Multiple Lights

Have 2 (or more) lights alternate blinking

![](img/alternate-blinking.gif)

--

### Potential Multiple Lights Solution - Hardware

![](img/alternate-blinking-hardware.png)

--

### Potential Multiple Lights Solution - Code

```js
var five = require("johnny-five");
var board = new five.Board();

board.on("ready", function() {

  var led1 = new five.Led(10);
  var led2 = new five.Led(11);
  var flag = false;

  setInterval(function() {
    if (flag) {
      led1.on();
      led2.off();
    } else {
      led1.off();
      led2.on();
    }

    flag = !flag;
  }, 500);
});
```

--

### 2. Holiday Lights

#### Make an LED (or multiple LEDs) go through different settings like some holiday lights do. It should change the setting every few seconds. Below are some example settings. You can see an example on the next slide.

- Off
- Solid
- Blinking
- Pulsing (fading in and out)
- Different speeds of blinking, pulsing, or alternating
- Alternating which lights are on

--

### 2. Holiday Lights

![](img/holiday-lights.gif)

--

### Potential Holiday Lights Solution - Hardware

![](img/holiday-lights-hardware.gif)

--

### Potential Holiday Lights Solution - Code

```js
var five = require("johnny-five");
var board = new five.Board();

board.on("ready", function() {
  var led = new five.Led(11);
  var setting = 0;

  setInterval(function() {
    led.stop();  // If we call pulse, we need to stop it
    switch (setting) {
      case 0:
        led.pulse();
        break;
      case 1:
        led.off();
        break;
      case 2:
        led.on();
        break;
    }
    setting = (setting + 1) % 3;
  }, 3000);
});
```

--


### 2. Holiday Lights (Bonuses)

1. Expose a function to the REPL that allows you to switch to the next setting from the REPL
2. Add a button that when pressed will go to the next setting (N.B: you should complete the Button Component slides before attempting this)

--

### Potential Holiday Lights Bonus 1 Solution - Hardware

![](img/holiday-lights-hardware.gif)

--

### Potential Holiday Lights Bonus 1 Solution - Code

```js
var five = require("johnny-five");
var board = new five.Board();

board.on("ready", function() {
  var led = new five.Led(11);
  var setting = 0;

  function changeSetting() {
    led.stop();  // If we call pulse, we need to stop it
    switch (setting) {
      case 0:
        led.pulse();
        break;
      case 1:
        led.off();
        break;
      case 2:
        led.on();
        break;
    }
    setting = (setting + 1) % 3;
  }

  this.repl.inject({
    cs: changeSetting  // Now we can call cs() from the REPL
  });
});
```

--

### Potential Holiday Lights Bonus 2 Solution

You're on your own for this one!

--

### 3. Binary Counter

Using 3 LEDs, count from 0 to 7 in binary as shown below. On represents 1 and off repesents 0.

![](img/binary-counter.gif)

--

### Potential Binary Counter Solution - Hardware

![](img/binary-counter-hardware.png)

--

### Potential Binary Counter Solution (alt 1) - Code

```js

var five = require("johnny-five");
var board = new five.Board();

board.on("ready", function() {
  var led1 = new five.Led(9);
  var led2 = new five.Led(10);
  var led3 = new five.Led(11);
  var num = 0;

  setInterval(function() {
    var binary = (num).toString(2);

    binary.slice(-1)     === "1" ? led1.on() : led1.off();
    binary.slice(-2, -1) === "1" ? led2.on() : led2.off();
    binary.slice(-3, -2) === "1" ? led3.on() : led3.off();

    num = (num + 1) % 8;
  }, 1000);
});
```

--

### Potential Binary Counter Solution (alt 2) - Code

```js

var five = require("johnny-five");
var board = new five.Board();

board.on("ready", function() {
  var leds = [new five.Led(9), new five.Led(10), new five.Led(11)];
  var num = 0;

  setInterval(function() {
    var mask = 1;

    for (var i = 0; i < leds.length; ++i, mask <<= 1) {
      var led = led[i];
      num & mask? led.on() : led.off();
    }

    num = (num + 1) % 8;
  }, 1000);
});
```

--

### 3. Binary Counter (Bonus)

Allow the user to enter a number through the REPL and display it in binary on the LEDs

--

### Potential Binary Counter Bonus Solution

You're on your own for this one!

---

## Components We're Covering

- Network programming with ESP8266
- LEDs (Light Emitting Diodes)
- <span style="color: yellow">Buttons</span>
- Servos

---

## Buttons

![](img/buttons.jpg)

---

## Build This

![](img/button-hardware.png)

---

## Save this to a file and run it

```js
var five = require("johnny-five");
var board = new five.Board();

board.on("ready", function() {
  var button = new five.Button(2);

  button.on("press", function() {
    console.log("Button Pressed!");
  });

  button.on("hold", function() {
    console.log("Button Held!");
  });

  button.on("release", function() {
    console.log("Button Released!");
  });
});
```

`node button.js`

---

Try pressing, releasing, and holding the button

You should see some output like this in the REPL

```

>> Button Pressed!
Button Released!
Button Pressed!
Button Released!
Button Pressed!
Button Held!
Button Held!
Button Released!
```

---

## Let's add an LED!

![](img/button-led-hardware.png)

---

## Save this to a file and run it

```js
var five = require("johnny-five");
var board = new five.Board();

board.on("ready", function() {
  var led = new five.Led(11);
  var button = new five.Button(2);

  button.on("press", function() {
    led.on();
  });

  button.on("hold", function() {
    led.blink(50);
  });

  button.on("release", function() {
    led.stop().off();
  });
});
```

`node button_led.js`

---

The LED should go on when you press, off when you release, and blink when you hold

---

## Button Challenges

Now that you've got the basics of buttons, you can either move on to the next component, or work on some button challenges

- Press &rarr; to move on to the next component
- Press &darr; to scroll through the button challenges

--

## Button Challenges

*Try to solve them yourself before looking at the solution!*

Press &darr; to scroll through the following challenges (and potential solutions)

1. Light Switch
2. Passcode
3. Holiday Lights

--

### 1. Light Switch

Have pressing a button alternate turning an LED on and off

--

### Potential Light Switch Solution - Hardware

![](img/light-switch-hardware.png)

--

### Potential Light Switch Solution - Code

```js
var five = require("johnny-five");
var board = new five.Board();

board.on("ready", function() {
  var led = new five.Led(11);
  var button = new five.Button(2);
  var on = false;

  button.on("press", function() {
    if (on) {
      led.off();
    } else {
      led.on();
    }

    on = !on;
  });
});
```

--

### 2. Passcode

Have 2 buttons and 1 LED. Make it so you have to press the buttons in a certain order to turn the LED on.

--

### Potential Passcode Solution - Hardware

![](img/passcode-hardware.png)

--

### Potential Passcode Solution - Code

```js
var five = require("johnny-five");
var board = new five.Board();

board.on("ready", function() {
  var led = new five.Led(11);
  var button1 = new five.Button(2);
  var button2 = new five.Button(4);

  var passcode = "12112";
  var presses = "";

  button1.on("press", function() {
    presses += "1";
    if (presses.indexOf(passcode) > -1) {
      led.on();
    }
  });

  button2.on("press", function() {
    presses += "2";
    if (presses.indexOf(passcode) > -1) {
      led.on();
    }
  });
});
```

--

### 3. Holiday Lights

#### Make an LED (or multiple LEDs) go through different settings like some holiday lights do. It should change the setting every time the button is pressed. Below are some example settings.

- Off
- Solid
- Blinking
- Pulsing (fading in and out)
- Different speeds of blinking, pulsing, or alternating
- Alternating which lights are on

--

### Potential Holiday Lights Solution

You're on your own for this one!

---

## Components We're Covering

- Network programming with ESP8266
- LEDs (Light Emitting Diodes)
- Buttons
- <span style="color: yellow"> Servos </span>

---

## <span class="spin">S</span><span class="spin">E</span><span class="spin">R</span><span class="spin">V</span><span class="spin">O</span><span class="spin">S</span>

![](img/servo.jpg)

---

Take your servo and add one of the attachments to it

![](img/servo.jpg)

---

## Build This

![](img/servo-hardware.png)

---

## Save this to a file and run it

```js

var five = require("johnny-five");
var board = new five.Board();

board.on("ready", function() {

  var servo = new five.Servo(11);

  this.repl.inject({
    servo: servo
  });
});
```

`node servo.js`

---

Type these commands in the REPL and watch how the servo reacts

```js

> servo.to(10);   // Move to 10 degrees

> servo.to(200);  // Move to 200 degrees

> servo.value;    // Get current position

> servo.min();

> servo.max();

> servo.range;

> servo.center();

> servo.sweep();
```

---

## Servo Challenges

Now that you've got the basics of servos, you can either move on to the next component, or work on some servo challenges

Press &rarr; to move on to the next component
Press &darr; to scroll through the servo challenges

--

## Servo Challenges

*Try to solve them yourself before looking at the solution!*

Press &darr; to scroll through the following challenges (and potential solutions)

1. Sprinkler
2. Arrows
3. Button

--

### 1. Sprinkler

Make the servo rotate back and forth like a sprinkler

![](img/sprinkler.gif)

--

### Potential Sprinkler Solution - Hardware

![](img/sprinkler-hardware.png)

--

### Potential Sprinkler Solution - Code

```js
var five = require("johnny-five");
var board = new five.Board();

board.on("ready", function() {

  var servo = new five.Servo(11);
  var min = servo.range[0];
  var max = servo.range[1];
  var value = min;

  function step() {
    servo.to(value);
    value = (value + 45) % max;
    setTimeout(step, 500);
  }

  step();
});
```

--

### 2. Arrows

Make pressing the left arrow button rotate the servo one way and pressing the right arrow button rotate the other way

![](img/servo-arrows.gif)

--

### Potential Arrows Solution - Hardware

![](img/servo-arrows-hardware.png)

--

### Potential Arrows Solution - Code

```js

var five = require("johnny-five");
var keypress = require("keypress");
var board = new five.Board();

board.on("ready", function() {

  var servo = new five.Servo(11);

  process.stdin.on("keypress", function(ch, key) {
    if (key && key.name === "left") {
      servo.min();
    } else if (key && key.name === "right") {
      servo.max();
    }
  });

  process.stdin.setRawMode(true);
  process.stdin.resume();
});
```

--

### 3. Button

Have the servo sweep while a button is held down

![](img/servo-sweep.gif)

-- 

### Potential Button Solution - Hardware

![](img/servo-sweep-hardware.png)

--

### Potential Button Solution - Code

```js

var five = require("johnny-five");
var board = new five.Board();

board.on("ready", function() {
  var servo = new five.Servo(11);
  var button = new five.Button(2);

  button.on("press", function() {
    servo.sweep();
  });

  button.on("release", function() {
    servo.stop();
  });
});
```

---

Uh oh! We ran out of slides! Feel free to try out some of the other components in your kit while we add more!

---

## Wrapping Up

- Thank you for coming!
- We'd love your feedback: [bit.ly/nodebots-feedback](http://bit.ly/nodebots-feedback)
- Please put away kits (you can buy your own [here](http://www.seeedstudio.com/depot/ARDX-The-starter-kit-for-Arduino-p-1153.html))


