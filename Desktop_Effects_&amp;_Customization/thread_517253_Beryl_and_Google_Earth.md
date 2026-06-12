---
title: "Beryl and Google Earth"
date: 2007-08-04
forum: Desktop Effects &amp; Customization
---

### Post by Grimgoil on 2007-08-04
Hi,

New to Ubuntu (very pleased), anyways, started using Beryl, only for window style and closing opening minimizing and so fading animations. Non of the heavy effects.

Google on it's own works just fine for me but:

Found that now when opening up Google Earth with beryl as the windows manager on i get allot of display problems, it's really jumpy and buggy having the display part of it getting stuck and blacking out, also crashing sometimes when i try to use the side panel, no slowdown though,

I'm using a Thinkpad R52 laptop and seems my display driver is i810

here is some info from xorg.conf:

Section "Device"
	Identifier	"Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768"
	EndSubSection

Does anyone know of a option or fix i could do to get them work together other than disabling beryl when i want to use Google Earth.
Thanks for taking a look.

---

