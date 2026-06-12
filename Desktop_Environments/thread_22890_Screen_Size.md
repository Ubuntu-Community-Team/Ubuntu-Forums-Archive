---
title: "Screen Size"
date: 2005-03-30
forum: Desktop Environments
---

### Post by Slalomsk8er on 2005-03-30
I have some Problems with the screen size.
My monitor is a acer al732 (LCD) on nvidia graphiccards.
On the analog connection (gforce 2mx) it works like it was intendet to work (1280x1024).
On the digital connection (gforce FX 5600) it is now on 1280x1024 (I had to comment all other resolutions out in xorg.conf) but gnome and gdm are running 1280x768 on 1280x1024 (the firefox icon looks like an easter egg). The maximum resolution in gnome-display-properties is 1280x768 and the lower resolution are still usable (not in xorg.conf).

```
Section "Device"
	Identifier      "NVIDIA Corporation NV31 [GeForce FX 5600]"
	Driver          "nvidia"
	BusID           "PCI:3:0:0"
	Option          "RenderAccel"   "true"
	Option          "NvAGP"         "3"
	Option          "NoLogo"        "true"
	Option          "IgnoreEDID"    "on"
	Option 		"ConnectedMonitor" "DFP"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS" "true"
	HorizSync	28-49
	VertRefresh	43-72
#	Modeline 	"1280x1024_60.00"  108.88  1280 1360 1496 1712  1024 1025 1028 1060
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV31 [GeForce FX 5600]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" 
# "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" 
# "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" 
# "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" 
# "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" 
# "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" 
# "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection
```

```
(II) NVIDIA(0): Not using mode "1280x1024" (no mode of this name)
(WW) NVIDIA(0): Not using mode "1152x768":
(WW) NVIDIA(0):   horizontal sync start (1178) not a multiple of 8
(WW) NVIDIA(0): Not using mode "576x384":
(WW) NVIDIA(0):   horizontal sync start (589) not a multiple of 8
(**) NVIDIA(0): Validated modes for display device DFP-0:
(**) NVIDIA(0):      Default mode "1280x768": 80.1 MHz, 47.7 kHz, 60.0 Hz
(**) NVIDIA(0):      Default mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz
(**) NVIDIA(0):      Default mode "800x600": 50.0 MHz, 48.1 kHz, 72.2 Hz
(**) NVIDIA(0):      Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(**) NVIDIA(0):      Default mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
(**) NVIDIA(0):      Default mode "640x480": 25.2 MHz, 31.5 kHz, 60.0 Hz
(**) NVIDIA(0):      Default mode "640x384": 40.1 MHz, 47.7 kHz, 60.1 Hz (D)
(**) NVIDIA(0):      Default mode "512x384": 32.5 MHz, 48.4 kHz, 60.0 Hz (D)
(**) NVIDIA(0):      Default mode "400x300": 25.0 MHz, 48.1 kHz, 72.2 Hz (D)
(**) NVIDIA(0):      Default mode "400x300": 20.0 MHz, 37.9 kHz, 60.3 Hz (D)
(**) NVIDIA(0):      Default mode "400x300": 18.0 MHz, 35.2 kHz, 56.3 Hz (D)
(**) NVIDIA(0):      Default mode "320x240": 12.6 MHz, 31.5 kHz, 60.1 Hz (D)
(II) NVIDIA(0): Virtual screen size determined to be 1280 x 768
```

How can I set the virtual screen size to 1280x1024?

Thanks, Dominik

---

### Post by Slalomsk8er on 2005-03-30
It looks like Xorg has some problems with DFPs. I fixed my problem with parts of the xorg.conf from my other PC on the same monitor but on the analog connection.

My Xorg config lokks now like this:
```
Section "Device"
	Identifier      "NVIDIA Corporation NV31 [GeForce FX 5600]"
	Driver          "nvidia"
	BusID           "PCI:3:0:0"
	Option          "RenderAccel"   "true"
	Option          "NvAGP"         "3"
	Option          "NoLogo"        "true"
	Option 		"IgnoreEDID" 	"true"
	Option 		"ConnectedMonitor" "DFP"
EndSection

Section "Monitor"
	Identifier	"Acer AL732"
	Option		"DPMS" "true"
	HorizSync	30-80
	VertRefresh	60-75
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV31 [GeForce FX 5600]"
	Monitor		"Acer AL732"
	DefaultDepth	24
	
	SubSection "Display"
		Depth		24
		Modes		"1280x1024"
		Virtual  	1280 1024
	EndSubSection
EndSection
```
I think   HorizSync    30-80    and     VertRefresh    60-75  did the trick.

---

