---
title: "Gnome Login Screen Resolution"
date: 2006-08-02
forum: Desktop Environments
---

### Post by ncrypto on 2006-08-02
The problem I'm having has already been answered here:

[http://www.ubuntuforums.org/showthread.php?t=225339&highlight=login+resolution](http://www.ubuntuforums.org/showthread.php?t=225339&highlight=login+resolution)

I'm just having a little problem understanding the answer.
Being a "newb" I get nervous editing config files.
Here is what my xorg.config looks like (forgive the big post area thought it would be helpful if you could see the entries).
xorg.config:

Section "Device"
	Identifier	"NVIDIA Corporation NV11DDR [GeForce2 MX 100 DDR/200 DDR]"
	Driver		"nv"
	BusID		"PCI:0:3:0"
EndSection

Section "Monitor"
	Identifier	"A90f+"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV11DDR [GeForce2 MX 100 DDR/200 DDR]"
	Monitor		"A90f+"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1792x1344" "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1792x1344" "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1792x1344" "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1792x1344" "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1792x1344" "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1792x1344" "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

If the answer is deleting or adding a line thats ok just not sure were to start with this.
Thanks so much ..Charles

---

