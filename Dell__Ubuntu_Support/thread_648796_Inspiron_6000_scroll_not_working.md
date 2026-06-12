---
title: "Inspiron 6000 scroll not working"
date: 2007-12-24
forum: Dell  Ubuntu Support
---

### Post by tom_alexander89 on 2007-12-24
the scroller on the touchpad has stopped working. any suggestions?

---

### Post by Rocket2DMn on 2007-12-24
Do you have an external mouse plugged in?  Also, please post the contents of your xorg.conf file:
```
cat /etc/X11/xorg.conf
```
I have a 600m model (very similar)

---

### Post by wormser on 2007-12-25
I have an Inspiron 6000.  Here are the details for the Mouse and Synaptics Touchpad.

> Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Let me know if you need anything else.

---

