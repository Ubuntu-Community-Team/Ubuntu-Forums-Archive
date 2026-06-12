---
title: "Configuring Dual Monitors"
date: 2009-04-04
forum: General Help
---

### Post by ant2ne on 2009-04-04
Physical Setup.
I have 1 21&1/2 inch monitor and 1 19inch monitor. Video card is (from lspci) 01:00.0 VGA compatible controller: nVidia Corporation NV44 [GeForce 6200 LE] (rev a1). I have the 21&1/2 inch connected via the VGA and the 19inch connected via the DVI. On boot, both monitors display post information, so I know that they are physically functional.

I'm assuming I have a missing line in the xorg.conf or someother simple configuration setting.  Or maybe there is a nifty GUI app to simplify this whole process.

Here is my working xorg.conf with only 1 monitor.
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
	Option		"Emulate3Buttons"	"true"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Option		"UseFBDev"	"true"
	Option		"NoLogo"	"True"
	Driver		"nvidia"
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
  screen "Default Screen"
EndSection
Section "Module"
	Load		"glx"
EndSection
```

Here is my xorg.conf attempt at dual monitors.
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
	Option		"Emulate3Buttons"	"true"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Option		"UseFBDev"	"true"
	Option		"NoLogo"	"True"
	Driver		"nvidia"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
	Option 		“RenderAccel” “true”.
	##This turns on NVidia’s TwinView
		Option “TwinView”
	##Here I’m setting the resolution to the individual monitors.
		Option “MetaModes” “1680×1024 1280×1024&#8243;
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
EndSection
Section "Module"
	Load		"glx"
EndSection
```Of course it fails miserably. With no output to either monitor

---

### Post by kanikilu on 2009-04-04
Sorry, I'm useless trying to edit xorg.conf by hand. However, since you said you have Nvidia, have you tried installing and using the **nvidia-settings** package? It's what I used to get dual monitors setup at work...

---

### Post by ShaunG on 2009-04-04
I did the same as kanikilu.

I used envyng-gtk to install my nvidia bits for me. 

Then I run nvidia-settings and configure my monitors in there.

---

### Post by ant2ne on 2009-04-04
> **kanikilu said:**
> Sorry, I'm useless trying to edit xorg.conf by hand. However, since you said you have Nvidia, have you tried installing and using the **nvidia-settings** package? It's what I used to get dual monitors setup at work...
That is what I was looking for THANKS. Worked great! Very awesome. Dual monitors in XP just extends the desktop. Here it creates its own session. Very neat. Is it possible to drag or move a window from screen to screen?

---

### Post by ant2ne on 2009-04-04
I noticed now that I've got them both working, My windows load slower and the drop down menus aren't as fast. Am I now overtaxing my GPU?

---

