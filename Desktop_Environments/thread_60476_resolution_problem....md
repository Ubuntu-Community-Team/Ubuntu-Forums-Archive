---
title: "resolution problem..."
date: 2005-08-27
forum: Desktop Environments
---

### Post by otero on 2005-08-27
how do a chage the resolution so the browser, new windows, and oter programs look much smaller so they can fit in the screen... 
thanks...

---

### Post by otero on 2005-08-28
the screen resolution wont give more choise than just 640*480

my xorg.conf

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "800x600" "720x400" "640x480"

---

### Post by Perfect Storm on 2005-08-28
[http://ubuntuforums.org/showthread.php?t=27029](http://ubuntuforums.org/showthread.php?t=27029)

---

