---
title: "fullscreen, maximized white titles / borders with desktop fx enabled (compiz)"
date: 2007-06-19
forum: Desktop Effects &amp; Customization
---

### Post by jon.reeve on 2007-06-19
With desktop effects enabled (and, I've noticed on beryl too) everything runs smooth as silk until one tries to maximize anything, then the top of the window where the title and buttons are goes white. Strangely, it still works, it's just white. Also, fullscreen video doesn't work. 

I've done a little searching around the forums found a previous post about this same problem, where the poster was directed to the beryl thread [here]("http://forum.beryl-project.org/viewtopic.php?f=35&t=1500"), but I'm a bit of a n00b and can't find the /etc/drirc, plus something tells me changing my xconf video driver to radeon isn't the best idea. 

I'm lost. I'm sure this is a relatively common problem. Any ideas?

This is the video card I'm using: 00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)

And here's a dump of what I think might be relevant from my xorg.conf entry:

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"i810"
	BusID		"PCI:0:2:0"
	VideoRam	32000
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
EndSection

& This is all on a P4 2.4GHz / 256 M RAM

---

### Post by mizzikee on 2007-06-28
I'm having the same problem...  everything works until I maximize.  The frame just goes white.  I'm using 7.04 with beryl/emerald and I just configured my xorg file.  Any help?

---

### Post by iloman on 2007-07-06
I've been having the same problem and was able to resolve it by following the recommendation here:

[http://ubuntuforums.org/showthread.php?t=326173&highlight=drirc]("http://ubuntuforums.org/showthread.php?t=326173&highlight=drirc")

I added Option "AGPSize" "32" to my xorg.conf file and verified it works.

---

