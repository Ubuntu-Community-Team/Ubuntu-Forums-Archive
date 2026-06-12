---
title: "Dell PowerEdge 1600SC or Similar ATI RAGE XL 8MB Video xorg.conf X11 Resolutions"
date: 2009-03-04
forum: Dell Ubuntu Support (CLOSED)
---

### Post by betterthanya on 2009-03-04
Running 8.10 Ubuntu on a Dell Poweredge 1600SC. To get higher than standard 800x600 resolution, custom xorg.conf is necessary

Below is my config and allows me up to 1280x1024 which is my Dell 19" CRT Max. Hope this helps anyone who has had similar issue.

```


Section "Device"
	Identifier	"ATI Technologies, Inc. Rage XL"
	Driver		"ati"
	BusID		"PCI:0:14:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	HorizSync	22.0 - 82.0
	VertRefresh	50.0 - 76.0


EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Rage XL"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	
EndSection





```

---

### Post by converted on 2009-07-31
Thanks very much!  You just saved me a bit of fiddling.  I couldn't believe that googling 1600SC Ubuntu brought up this thread!

---

