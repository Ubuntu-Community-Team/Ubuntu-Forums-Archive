---
title: "1680x1050 resolution and intel driver"
date: 2008-06-14
forum: Desktop Environments
---

### Post by deeflex on 2008-06-14
Hi

I recently bought a LG L222WS (22 inch widescreen monitor) but I can't get it configured right in Ubuntu Hardy.

Resolution 1680x1050 @ 60Hz is fine, but the desktop width is greater than the size of the monitor (height is OK).The auto-button doesn't resize it so I guess it has something to do with the modelines?

Text also appear a bit blurry, see the attachment.

This is my current xorg.conf


```
Section "Device"
	Identifier	"Intel Corporation 82865G Integrated Graphics Controller"
	Driver		"intel"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"LG L222WS"
	Option		"DPMS"
	HorizSync	30-83
	Modeline "1680x1050@60.0"  146.25  1680 1784 1960 2240  1050 1053 
1059 1089 +hsync -vsync
	Option "PreferredMode"	"1680x1050@60.0"
	VertRefresh 56-75
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82865G Integrated Graphics Controller"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Modes	 "1680x1050@60"	"1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
EndSection
```

Any help appreciated!

---

### Post by deeflex on 2008-06-15
Here's an interesting observation.

When I locked my screen and came back the problem with the blurry fonts was solved. I tried to auto resize the monitor and this time it worked. 

If someone got a better idea than putting my monitor to sleep for 10 min, I'd like to hear it :).

---

