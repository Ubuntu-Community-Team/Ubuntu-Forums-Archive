---
title: "lines all over screen"
date: 2008-03-05
forum: Dell  Ubuntu Support
---

### Post by Papa-san on 2008-03-05
I re-booted and this time I have a thousand little 'unerscore' looking lines all over the screen. I'm trying to install 7.10 on my daughters new Dell 1525. Got the boot-grub issue handled (I think), and now, I get this... 
I tried to do a screenshot, but it doesn't show the clutter... It's BAD too... I can hardly read this page...
the (seemingly) relavent lines in /etc/X11/xorg.conf are:
```
Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1280x800"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"


```Edit: OK... that's messed up...
Re-booted once, got it again. Was going to boot into Vista but was busy, so it defaulted to Ubuntu, and this time they are gone...
I'll have her let me know if it happens again, and I'll check this thread.

---

### Post by natehall on 2008-03-05
I had the same problem once on my 1420N. It went away after i rebooted so who knows what was happening.

---

### Post by gpilkay on 2008-03-06
On my own dell I had this once, I went to the display settings and chose the Dell Laptop LCD display of as close to the right side as I could get, then I added to the xconf.  I'm not that familiar with x, so it took a few tries...most of the troubles went away with the choosing of the Dell LCD, though.  For some reason Ubuntu chose a generic plug n play monitor, which was inadequate.

---

