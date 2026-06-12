---
title: "Cannot get Nintendo Switch Pro Wired controllers to work on Ubuntu 18.04.1."
date: 2019-01-14
forum: Gaming &amp; Leisure
---

### Post by tsynkzzz on 2019-01-14
This has been a problem with me ever since I decided that I want to game on my Ubuntu 18.04 installation, I don't have Bluetooth on my laptop and USB is my only option. Ubuntu doesn't even detect my USB controller, however on my Windows side of my disk (I installed Ubuntu alongside Windows), it can be used. I just want to know why Ubuntu isn't detecting my USB controller, does it not have a driver of sorts for it? If there is a fix of sorts without the use of Bluetooth, I'd like to know.

---

### Post by oldrocker99 on 2019-01-14
Please post the output of this:
```
lsusb
```

There is also the very real possibility that your USB cable failed. I was doing a write operation, and suddenly it halted, and I got a "Cannot mount sdx" warning. Figuring the drive had gone bad, I set it aside. Then another cable failed; it was in a stable position, not wiggled around, and it still failed. Replaced the cable, and the drive came back to life. I used a new cable on the "broken" drive, and, voila, it worked.

The ironic thing is that my motto has been "always look at the connection.":cry:Cables fail. Keep one or two new cables around. Experience has taught me that it certainly does happen. Exactly why cables fail suddenly is something of a mystery.

---

### Post by tsynkzzz on 2019-02-15
I can assure that the cable is okay, the cable works on the Switch itself and on Windows, apparently Ubuntu 18.10 (I upgraded since this post) still can't detect it, at this point, I am pointing at Ubuntu for not being able to detect it. 

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 005: ID 0c45:651b Microdia 
Bus 001 Device 004: ID 05e3:0608 Genesys Logic, Inc. Hub
Bus 001 Device 003: ID 0a5c:21e8 Broadcom Corp. BCM20702A0 Bluetooth 4.0
Bus 001 Device 002: ID 0e8f:2517 GreenAsia Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

It's a PowerA wired only controller.

---

### Post by wsmith198729 on 2019-02-22
Can you run `lsusb` from the `usbutils` package and check that the vendor/product IDs match your controller.

---

### Post by tsynkzzz on 2019-07-01
tsynk@TsynkZZZ:~$ lsusb
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 005: ID 0c45:651b Microdia HP Webcam
Bus 001 Device 004: ID 05e3:0608 Genesys Logic, Inc. Hub
Bus 001 Device 003: ID 0a5c:21e8 Broadcom Corp. BCM20702A0 Bluetooth 4.0
Bus 001 Device 014: ID 20d6:a711  
Bus 001 Device 011: ID 0e8f:2517 GreenAsia Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub



I have no idea what you are talking about when you say "'usbutils' package" I need more information to even understand what you are talking about there, that literally gives me no idea what I am even to look for to begin with... Anyway, on Ubuntu 19.04 here, it shows when I use lsusb on the terminal, that the controller is plugged up, however, Ubuntu is the issue for not recognizing it as a PowerA Switch Pro controller or even what the vendor is. I just would like to know what I need to install to get Ubuntu to open its eyes to recognize this controller and to be used properly without the use of WINE.

---

