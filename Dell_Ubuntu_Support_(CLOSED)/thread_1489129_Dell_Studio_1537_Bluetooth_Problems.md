---
title: "Dell Studio 1537 Bluetooth Problems"
date: 2010-05-20
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Technicolour on 2010-05-20
I have recently installed Ubuntu 10.04 64bit on my Dell Studio 1537

Everything seems to work fine from a fresh install but for some reason my bluetooth adapter isn't working :S

My laptop has a Dell 370 Bluetooth minicard in it so I know that it is there and the lsusb seemingly shows that it is there but for some reason it fails to show as an adapter.

luke@laptopia:~$ lsusb
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 004: ID 413c:8158 Dell Computer Corp. Integrated Touchpad / Trackstick
Bus 003 Device 003: ID 413c:8157 Dell Computer Corp. Integrated Keyboard
**Bus 003 Device 002: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)**
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0c45:63fb Microdia 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

But both the default Bluetooth manager and Blueman fail to see it.

init.d bluetooth status constantly shows that the service is not running.

Help (I really need this feature to keep me needing windows to sync my phone)

---

