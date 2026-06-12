---
title: "mouse middle button"
date: 2006-07-23
forum: Desktop Environments
---

### Post by harveyfly on 2006-07-23
how can I get mouse middle button work in ubuntu?

---

### Post by wieman01 on 2006-07-25
I assume you have a PS/2 mouse... you need to change the settings in '/etc/X11/xorg.conf":

> Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection

Replace your mouse section with these lines and restart the x-server. This should also work with a simple USB mouse. So it did in my case.

---

