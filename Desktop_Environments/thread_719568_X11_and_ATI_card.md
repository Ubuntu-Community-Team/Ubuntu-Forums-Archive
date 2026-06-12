---
title: "X11 and ATI card"
date: 2008-03-09
forum: Desktop Environments
---

### Post by mr.propre on 2008-03-09
Hi,

I just tried to install the latest ATI driver using Envy and all whent well exept when I run "glxinfo | grep" I get: "rendering direct rendering: No "

My ati driver is active and compize workes. But I would like to run WOW on my linux box and for that I need to get renering on.

I don't really know what the problem could be but I think its my xorg.conf file:
```
Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Monitor"
	Identifier	"aticonfig-Monitor[0]"
	Option		"VendorName"	"ATI Proprietary Driver"
	Option		"ModelName"	"Generic Autodetecting Monitor"
	Option		"DPMS"	"true"
EndSection

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"fglrx"
	Busid		"PCI:1:0:0"
	Option		"VideoOverlay"	"on"
	Option		"OpenGLOverlay"	"off"
EndSection

Section "Device"
	Identifier	"aticonfig-Device[0]"
	Driver		"fglrx"
	Option		"Capabilities"	"0x00000800"
	Option		"UseFastTLS"	"off"
	Option		"KernelModuleParm"	"locked-userpages=0"
	Option		"VideoOverlay"	"on"
	Option		"OpenGLOverlay"	"off"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	1
		Modes		"1400x1050"	"(pitch"	"1400)"
	EndSubSection
	SubSection "Display"
		Depth	4
		Modes		"1400x1050"	"(pitch"	"1400)"
	EndSubSection
	SubSection "Display"
		Depth	8
		Modes		"1400x1050"	"(pitch"	"1400)"
	EndSubSection
	SubSection "Display"
		Depth	15
		Modes		"1400x1050"	"(pitch"	"1400)"
	EndSubSection
	SubSection "Display"
		Depth	16
		Modes		"1400x1050"	"(pitch"	"1400)"
	EndSubSection
	SubSection "Display"
		Depth	24
		Modes		"1400x1050"	"(pitch"	"1400)"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"aticonfig-Screen[0]"
	Device		"aticonfig-Device[0]"
	Monitor		"aticonfig-Monitor[0]"
	Defaultdepth	24
	SubSection "Display"
		Viewport	0	0
		Depth	24
	EndSubSection
EndSection
```

Can somebody look into this please?
Thanks :-)

---

### Post by luisromangz on 2008-03-09
Have you tried running WoW without Compiz?

---

### Post by mr.propre on 2008-03-16
I'm sorry for the late answer, getting wow to run on my laptop isn't a prior manor but it would be fun for the boring moments ;-)

When I put of compiz, there is no change  and i still get a "direct rendering: No"

---

