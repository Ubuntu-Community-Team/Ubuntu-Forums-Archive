---
title: "Trouble with VCP connection"
date: 2009-04-22
forum: General Help
---

### Post by beckon02 on 2009-04-22
I'm working with Medusa Research's 'Power Analyzer Pro'.  They use FTDI's FT232 chip for VCP support.  For some reason I'm having trouble detecting the device (it's not showing up in my /dev directory).  Medusa uses a customized product ID (PID) for their FTDI driver and I've made sure to update the driver on my system with their PID, but that didn't solve the problem.

When I execute the command 'dmesg|grep FTDI' I get this:

[	13.876089] usbserial: USB Serial support registered for FTDI USB serial Device
[	13.876129] ftdi_sio 1-4.1:1.0: FTDI USB Serial Device converter detected
[	13.876369] usb 1-4.1: FTDI USB Serial Device converter now attached to ttyUSB0
[	13.876400] ftdi_sio: v1.4.3:USB FTDI Serial Converters Driver
[	54.282256] ftdi_sio ttyUSB0: FTDI USB Serial Device converter now disconnected from ttyUSB0

It's correctly attaching the device to ttyUSB0 but, then it's doing something funny and removing it (I don't unplug the device).

Any ideas?

---

