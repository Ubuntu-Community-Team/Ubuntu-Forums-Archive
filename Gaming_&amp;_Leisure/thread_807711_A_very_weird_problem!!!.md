---
title: "A very weird problem!!!"
date: 2008-05-26
forum: Gaming &amp; Leisure
---

### Post by FlyinRedneck on 2008-05-26
While attempting to play any of the FPS games offered in the Ubuntu repositories I have come across an issue with mouse and keyboard lag. It is not graphical problems, my FPS is upward of 60. When i attempt to move the mouse it is very slow and does not complete my motions, then i switch to the keyboard and it is unresponsive. It is as if the commands are delayed a few frames... it is really hard to explain.

Please help me!!!

---

### Post by Sockerdrickan on 2008-05-26
Native games?

---

### Post by FlyinRedneck on 2008-05-26
Yes... I have tried Nexuiz, Warsow, OpenArena, Saurbraten they all have the same problem.

---

### Post by Sockerdrickan on 2008-05-26
Ok because I have that problem with some games with WINE. Perhaps you should set your DPI to something different in xorg.conf

---

### Post by FlyinRedneck on 2008-05-26
I have looked at my Xorg.conf there is no such value as DPI...

This is what it reads...

```
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"fglrx"
	Option 		"XAANoOffscreenPixmaps"		"on"
	Option 		"TexturedVideo"		"on"
	Option 		"VideoOverlay"		"off"
	Option 		"OpenGLOverlay"		"off"
	Option 		"Textured2D"		"on"
	Option		"TexturedXrender"	"on"
	Option		"UseFastTLS"		"1"
	Option		"BackingStore"		"on"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Option		"AIGLX"		"on"
  screen "Default Screen"
	Inputdevice	"Synaptics Touchpad"
EndSection
Section "Module"
	Load		"glx"
EndSection
```

---

### Post by |{urse on 2008-05-26
this is a laptop right>? Try disabling the touchpad in the bios, sounds like something is double polling.

---

### Post by FlyinRedneck on 2008-05-26
That helped quite a bit, thank you. But I am still suffering from slow mouse movement in menu and jerky in game movement. My FPS is still 50+

---

### Post by |{urse on 2008-05-26
are you using a ball mouse (olschool lol) or an optical mouse?

---

### Post by FlyinRedneck on 2008-05-26
I am using a generic logitech optical mouse.

---

### Post by |{urse on 2008-05-26
hm you may want to try 

sudo dpkg-reconfigure xserver-xorg

*warning If you had to do any special stuff like install proprietary ati/Nvidia drivers etc, for 3d acceleration you may have to repeat those steps again.

---

### Post by FlyinRedneck on 2008-05-28
Thank you very much.... that completely erased the problem... now could someone go into detail about what happened there, I like to know how things work, so i can better fix problems in the future.

---

