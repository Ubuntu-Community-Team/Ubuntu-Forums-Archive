---
title: "why do usb items not show up in device notifier"
date: 2009-09-02
forum: Desktop Environments
---

### Post by gatorbrit on 2009-09-02
Hi, using KDE, I have  various usb devices plugged in...here is the output of lsusb

```
Bus 001 Device 009: ID 0bc2:0500 Seagate RSS LLC 
Bus 001 Device 008: ID 13fe:1a00 Kingston Technology Company Inc. 512MB/1GB Flash Drive
Bus 001 Device 006: ID 05ac:1291 Apple, Inc. 
Bus 001 Device 004: ID 03f0:3e17 Hewlett-Packard 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 046d:c016 Logitech, Inc. M-UV69a/HP M-UV96 Optical Wheel Mouse
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 413c:2010 Dell Computer Corp. 
Bus 002 Device 003: ID 413c:1003 Dell Computer Corp. 
Bus 002 Device 002: ID 051d:0002 American Power Conversion Uninterruptible Power Supply
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```


But none show up in device notifier
Should I just delete this widget and not worry about it?

---

### Post by krazyd on 2009-09-02
the device notifier is only for storage devices.. flash drives etc. so you can safely eject them and easily mount them.

---

