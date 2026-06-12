---
title: "[SOLVED] Logitech Cordless Duo (MX700 Mouse) - Erratic Mouse Behavior"
date: 2006-07-29
forum: Desktop Environments
---

### Post by wieman01 on 2006-07-29
Hello Everybody, 

I have been struggling to get my Cordless MX Duo with a MX700 working for weeks now but it's all to no avail. The problem is that my mouse starts behaving erratically after a few minutes although the buttons and the mousewheel work fine in the first place. 

Has anybody a solution for this? 

Here is my configuration (I followed a guide in this forum):

**_xorg.conf:_**
> Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"gb"
EndSection

Section "InputDevice"
    	Identifier      "Configured Mouse"
    	Driver          "evdev"
	Option          "CorePointer"
	Option          "Dev Name"	"Logitech USB Receiver"
	Option          "Dev Phys"      "usb-*/input1"
	Option          "Device"        "/dev/input/mx700"
EndSection

**_.Xmodmap:_**
> pointer = 1 3 2 4 5 8 9 6 7 10 11 12 13 14 15 16 17 18 19 20 21 22 23 24 25 26 27 28 29 30 31 32

Anybody with a similar problem? Batteries are fully charged.

---

### Post by wieman01 on 2006-07-30
I managed to solve this problem a few minutes ago. After my keyboard had given up on me, I smashed both keyboard & mouse and will get myself a new (wired) set next week.

This solution may not sound appealing to everybody, but it did the trick for me.

---

