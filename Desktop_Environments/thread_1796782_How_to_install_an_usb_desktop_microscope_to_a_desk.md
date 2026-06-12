---
title: "How to install an usb desktop microscope to a desktop system using natty?"
date: 2011-07-04
forum: Desktop Environments
---

### Post by Geezanansa on 2011-07-04
Would really like to add a usb desktop microscope to my ubuntu natty machine. The microscope comes with a cd with drivers and image editing software the system requirements: DirectX, Windows XP sp3/vista sp2, .NET Framework 3.5



Any body want to give some pointers?

Thanks in advance.

---

### Post by Geezanansa on 2011-07-04
lsusb gives

user@user-desktop:~$ lsusb
Bus 002 Device 002: ID 045e:0734 Microsoft Corp. Wireless Optical Desktop 700
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
[COLOR=Red]Bus 001 Device 003: ID 1871:0101 Aveo Technology Corp. [/COLOR]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
user@user-desktop:~$ 

The microscope is at least detected.

Any help with drivers and image editing software would be appreciated.

Thanks in advance.

---

### Post by Geezanansa on 2011-07-04
Easy as pluggin it in and use cheese webcam booth to view!!!!

It just a webcam!!!

Ubuntu ROCKS:guitar::guitar:

---

### Post by mister_p_1998 on 2011-07-04
I tried this six months ago, using cheese, didnt work, I gave up and binned it..

---

### Post by piewie on 2011-07-04
ID 1871:0101 Aveo Technology Corp.

is detected by cheese, but the view seems not correct. The snapshot button is doing fine.
guvcview seems to give better results - but still not perfect.

---

### Post by gfx on 2011-07-04
Is it one of those Bresser ones from Lidl?
We bought one today, and it does work with cheese.

Haven't tried the Windows software yet.
At 20x it easiest to get an image from one of the supplied samples.

Searching for the vendorid:deviceid brought me here.

---

### Post by piewie on 2011-07-04
Yes, it's the one which is currently sold at lidl. Looks like it is fully supported. I have to do some test with the colour - but I have a lack of time.
Also guvcview is doing fine - probably more fine tuning.

---

