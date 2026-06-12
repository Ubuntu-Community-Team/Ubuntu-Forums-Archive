---
title: "Labview + FTDI + Ubuntu"
date: 2011-04-15
forum: Education &amp; Science
---

### Post by flakifero on 2011-04-15
Hi, what I'm trying to do is to communicate from Labview to a board with a PIC through a FT232 adapter. 
I'm using the visa function in labview, in VI that I made that works right in windows. Thing is that I can't configure the serial port.

Using LabView 8.6 under Ubuntu 10.04.

The result of a dmesg is: 

>dmesg | grep FTDI
[  141.382347] USB Serial support registered for FTDI USB Serial Device
[  141.382586] ftdi_sio 4-3:1.0: FTDI USB Serial Device converter detected
[  141.384084] usb 4-3: FTDI USB Serial Device converter now attached to ttyUSB0
[  141.384099] ftdi_sio: v1.5.0:USB FTDI Serial Converters Driver
[  343.307147] ftdi_sio ttyUSB0: FTDI USB Serial Device converter now disconnected from ttyUSB0
[  382.936053] ftdi_sio 4-3:1.0: FTDI USB Serial Device converter detected
[  382.939101] usb 4-3: FTDI USB Serial Device converter now attached to ttyUSB0
[ 2526.843115] ftdi_sio ttyUSB0: FTDI USB Serial Device converter now disconnected from ttyUSB0
[ 2591.256061] ftdi_sio 4-3:1.0: FTDI USB Serial Device converter detected
[ 2591.259102] usb 4-3: FTDI USB Serial Device converter now attached to ttyUSB1
[ 3862.445018] ftdi_sio ttyUSB1: FTDI USB Serial Device converter now disconnected from ttyUSB1
[B][ 3864.240089] ftdi_sio 4-3:1.0: FTDI USB Serial Device converter detected
[ 3864.243105] usb 4-3: FTDI USB Serial Device converter now attached to ttyUSB1[/B]

I'm lost.

I'll appreciate any idea. 
Thanks!
flakifero

---

### Post by [woodstock] on 2011-04-24
Seems that the device is recognized properly and attached to /dev/ttyUSB1.

If your device allows it, try to communicate with it via some other tools. Despising labview, we use python, so no labview specific help here (sorry).


```

import serial

f = serial.open('/dev/ttyUSB1')
f.write('some command')
#some waiting for processing might be necessary
f.readline() #read the answer
f.close()

```

---

### Post by flakifero on 2011-04-24
Thanks for the reply... the communication between the PIC18 and the pc works fine, I tried it with a terminal. The problem was that the VISA module of labview wasn't properly installed. After lots of tries I have it working now!

---

