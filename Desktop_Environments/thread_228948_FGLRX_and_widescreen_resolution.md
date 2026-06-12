---
title: "FGLRX and widescreen resolution"
date: 2006-08-03
forum: Desktop Environments
---

### Post by Slourte on 2006-08-03
Hey,

Just installed the FGLRX driver for my Radeon x800 card and it seems I can't get a decent 1680x1050 resolution on my widescreen monitor. I either lose the top panel or the bottom panel each time I auto-adjust the monitor.  Everything worked fine the default ATI driver though. So I'm starting to guess that it may be something I wrote in xorg.conf but I can't get my finger on it :
> 
Section "Device"
	Identifier	"ATI Technologies, Inc. R420 JK [Radeon X800]"
	Driver		"fglrx"
	BusID		"PCI:1:0:0"
	Option "DPMS"
EndSection

Section "Monitor"
	Identifier	"FPD2185W"
	Option		"DPMS"
        Modeline "1680x1050@60" 154.20 1680 1712 2296 2328 1050 1071 1081 1103 -HSync +Vsync
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. R420 JK [Radeon X800]"
	Monitor		"FPD2185W"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1680x1050" "1440x1440" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1680x1050" "1440x1440" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1680x1050" "1440x1440" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1680x1050" "1440x1440" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1680x1050" "1440x1440" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1680x1050" "1440x1440" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection


Thanks!

---

### Post by Pauan on 2006-10-26
I'm not sure if this will work or not, but I remember reading that if you remove the refresh rate and add .1 to the dot clock (in the modeline generator), then run it through the modeline generator again, replacing in the old numbers with the new (in the xorg.conf), that it might work. I'm not sure if it does or not, since I never tested it myself.

---

