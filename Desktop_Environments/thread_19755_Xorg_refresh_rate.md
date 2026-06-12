---
title: "Xorg refresh rate"
date: 2005-03-13
forum: Desktop Environments
---

### Post by twistor on 2005-03-13
Upgraded to Hoary and Xorg decided to change my refresh rate to 85 Hz.  I can change the setting in Gnome, but GDM still looks like crap.  It happened with Xfree but I could fix it with dpkg-reconfigure xsession-xfree86.  I do not, however have the same luck with Xorg.  Here are the jucy parts of my xorg.conf:

Section "Module"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"type1"
	Load	"vbe"
EndSection

Section "Device"
	Identifier	"Silicon Integrated Systems (SiS) 86C326 5598/6326"
	Driver		"sis"
	BusID		"PCI:1:0:0"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"MAG DJ717"
#	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Silicon Integrated Systems (SiS) 86C326 5598/6326"
	Monitor		"MAG DJ717"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection

---

### Post by cutOff on 2005-03-13
Hi

Try with

```
dpkg-reconfigure xserver-xorg
``` 
Regards!

---

### Post by twistor on 2005-03-13
I tried that about 10 different ways and couldn't get it to do anything different.

---

### Post by rosslaird on 2005-03-13
I don't see your refresh rate specified in the file you posted. Here's what mine says:

Section "Monitor"
	Identifier	"SyncMaster"
	Option		"DPMS"
	HorizSync	56-75
	VertRefresh	30-81
EndSection

---

