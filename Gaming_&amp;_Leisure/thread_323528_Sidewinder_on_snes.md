---
title: "Sidewinder on snes"
date: 2006-12-22
forum: Gaming &amp; Leisure
---

### Post by adam0509 on 2006-12-22
Hello


Can't find any thread/help/wikipost detailled about gamepad, so let's start a new one.


So I followed what to do from french wiki ( [http://doc.ubuntu-fr.org/materiel/joystick](http://doc.ubuntu-fr.org/materiel/joystick) ), and it works, I can calibrate the sidewinder and the 10 button with jscalibrator...


Unfortunately, I can't make things work under Zsnes or Visual boy advance : the buttons works without problems, but the X/Y axis do absolutely not work...


Thank you in advance ! :)

---

### Post by adam0509 on 2006-12-23
UP



sorry to insist, it's a very big trouble, and I can't really complete french'wiki about gamepads if I am stick to a stupid error like that... :[

---

### Post by adam0509 on 2006-12-24
Find it


**If you got an analog gamepad**


if you got an analog gamepad (gamepad that needs "sudo modprobe analog" to work), set the value like this (see ".joystick" file in your /home/user) :

Maximum (3421) - Center (1773) = 1648

set the value to a lower value, 1500 for example

joy_sensitivity=1500

**If you got a digital gamepad**

If you got a digital gamepad such as "Microsoft Sidewinder", set the value to 0 :

joy_sensitivity=0 


I will retest this on a clean installation (cause I made a download of the 1.50 from SVN and others settings, so not sure at all it will work on a default installation)

---

