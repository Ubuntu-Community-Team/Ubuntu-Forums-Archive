---
title: "Mouse scroll isn't working"
date: 2005-10-14
forum: Desktop Environments
---

### Post by helloyo on 2005-10-14
How do i fix this? First time i've had the problem with Ubuntu. Aptitude also stopped downloading during the installation, so i had to do it manually.

---

### Post by Ampersand on 2005-10-14
```
sudo gedit /etc/X11/xorg.conf
``` 
and add the line 
```
Option		"ZAxisMapping"		"4 5"
```
at the bottom of the 'Section "InputDevice"' for your mouse.

---

### Post by BLTicklemonster on 2005-10-14
Speaking of mice...  I have a logitech with buttons all over the place, and I'd sure like to make use of them. How can I do this?

---

### Post by BLTicklemonster on 2005-10-14
[http://ubuntuforums.org/showthread.php?t=65471&highlight=mouse+buttons](http://ubuntuforums.org/showthread.php?t=65471&highlight=mouse+buttons) :D

---

### Post by mikesmind on 2005-11-26
I'm also having problems with my scroll mouse.  Here is the section out of my xorg.conf file.

> Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
	Option		"EmulateWheel"		"true"
	Option		"EmulateWheelButton"	"2"
EndSection


Any idea what I should do?

---

### Post by mikesmind on 2005-11-27
OK, I got it working.  All I needed to do was shutdown and restart.  It then picked up the correct mouse.

---

