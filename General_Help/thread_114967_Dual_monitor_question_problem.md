---
title: "Dual monitor question problem"
date: 2006-01-09
forum: General Help
---

### Post by pjman on 2006-01-09
Hello,

I have a dual monitor setup, laptop with crt monitor. Everytime I boot my machine I have to Ctrl+Alt+Backspace to restart my X session so that my second monitor shows up in 1024x768. On bootup looks like it's 640x480... 

Any idea why my xorg.conf file isn't being read properly on bootup?

Thanks!

```

Section "Device"
	Identifier	"ati0"
	Driver		"ati"
	BusID		"PCI:1:0:0"
	Screen		0
EndSection

Section "Device"
	Identifier	"ati1"
	Driver		"ati"
	BusID		"PCI:1:0:0"
	Screen		1
EndSection

Section "Monitor"
	Identifier	"monitor0"
	Option		"DPMS"
EndSection

Section "Monitor"
	Identifier	"monitor1"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"screen0"
	Device		"ati0"
	Monitor		"monitor0"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1024x768"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"screen1"
	Device		"ati1"
	Monitor		"monitor1"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1024x768"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Multihead"
	Screen		"screen0"
	Screen		"screen1" RightOf "screen0"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
	Option		"Xinerama"
EndSection

Section "DRI"
	Mode	0666
EndSection


```

---

### Post by bannerboy on 2006-01-09
first off, a little more information in your "Monitor" section might be helpful, for the laptop screen it may not be nescisary, but for the CRT monitor it would be advised, in fact, lack of monitor specification alone may be causeing your problem.

---

### Post by pjman on 2006-01-13
Running fglrxconfig fixed the problem.

---

