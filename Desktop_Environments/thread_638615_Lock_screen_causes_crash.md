---
title: "Lock screen causes crash"
date: 2007-12-12
forum: Desktop Environments
---

### Post by simonrobinson on 2007-12-12
Installed 7.10 on a HP nx8220 with the Compiz extensions, I thought I had it configured correctly, but if I select "Lock Screen" from the logout dialog it closes the desktop manager and resumes at the Ubuntu login screen.  Also happens if the machine's screensaver comes on.

Output of xorg.conf is

```
# Fallback X.org config file
# FIXME: include the wacom devices (would only add noise at the current
#        development stage)

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
  screen 0 "screen1" 0 0
EndSection
Section "Module"
	Load		"dri"
	Load		"v4l"
	Load		"glx"
EndSection
Section "device" #  
	Identifier	"device1"
	Boardname	"ATI Radeon (fglrx)"
	Busid		"PCI:1:0:0"
	Driver		"fglrx"
	Screen	0
	Vendorname	"ATI"
	Option		"MergedFB"	"off"
EndSection
Section "screen" #  
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	24
	Monitor		"monitor1"
EndSection
Section "monitor" #  
	Identifier	"monitor1"
	Gamma	1.0
EndSection
Section "ServerFlags"
EndSection
Section "Extensions"
	Option		"Composite"	"0"
EndSection
```

---

