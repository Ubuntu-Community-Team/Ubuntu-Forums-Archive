---
title: "display resolution stuck at 1024"
date: 2009-02-02
forum: Desktop Environments
---

### Post by caymahallesi on 2009-02-02
hi guys here is my xorg.conf and like to rewrite it so it will let me use 11xx and 1280x1024


Section "Monitor"  
	 # HorizSync source: edid, VertRefresh source: edid  
	 Identifier     "Monitor0"  
	 VendorName     "Norwood Micro"  
	 ModelName      "MT9ANK"  
	 HorizSync       30.0 - 83.0  
	 VertRefresh     56.0 - 76.0  
	 Option         "DPMS"  
	 Modeline        "1280x1024_60.00"  108.88  1280 1360 1496 1712  1024 1025 1028 1060  -HSync +Vsync
	 Option          "PreferredMode" "1280x1024_60.00"

EndSection  

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
            	SubSection "Display"
			Depth 24
			Modes   "1280x1024" "1024x768" "800x600"
		EndSubSection
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"nvidia"
	Option		"NoLogo"	"True"
	BusID		"PCI:1:0:0"

EndSection

all help will be appreciated.

---

