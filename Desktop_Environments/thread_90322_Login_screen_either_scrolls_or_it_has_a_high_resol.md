---
title: "Login screen either scrolls or it has a high resolution and low refresh rate"
date: 2005-11-14
forum: Desktop Environments
---

### Post by olavi on 2005-11-14
The login screen had a too high resolution and a low refresh rate. I edited X configuration to have a maximum resolution of 1280x960. Now the darn thing scrolls around! How can I make it fit the resolution?

Or is there a cleaner way to do this?

The CRT screen is (fairly common) Samsung SyncMaster 959NF.

And here is the important part from xorg.conf:
```
Section "Device"
	Identifier	"NVIDIA Corporation NV11 [GeForce2 MX/MX 400]"
	Driver		"nv"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"SyncMaster"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV11 [GeForce2 MX/MX 400]"
	Monitor		"SyncMaster"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"2048x1536" "1920x1440" "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"2048x1536" "1920x1440" "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"2048x1536" "1920x1440" "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"2048x1536" "1920x1440" "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"2048x1536" "1920x1440" "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x960" "1024x768" "832x624" "800x600" "720x400" "640x480" "2048x1536" "1920x1440" "1600x1200" "1280x1024"
	EndSubSection
EndSection
```

---

### Post by thumbsoup on 2005-11-14
I am new to Linux, but perhaps your xorg.conf entries are allowing higher resolutions at 24 bit depth.

There is a "How To" on this topic.

[http://ubuntuforums.org/archive/index.php/t-83973.html](http://ubuntuforums.org/archive/index.php/t-83973.html)

---

