---
title: "Screen Resolution"
date: 2005-11-12
forum: Desktop Environments
---

### Post by klemens on 2005-11-12
Can't get my screen resolution higher then 1024*768

what must i change in my xorg.conf pls to get it up to 1600*1200 (22" screen).

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV35 [GeForce FX 5900XT]"
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

thanks

---

### Post by nszabolcs on 2005-11-12
[http://www.ubuntuforums.org/showthread.php?t=83973](http://www.ubuntuforums.org/showthread.php?t=83973)

---

