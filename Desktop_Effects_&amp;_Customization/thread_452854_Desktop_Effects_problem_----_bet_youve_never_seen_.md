---
title: "Desktop Effects problem ---- bet youve never seen this problem before"
date: 2007-05-23
forum: Desktop Effects &amp; Customization
---

### Post by stuck on 2007-05-23
I tried to enable desktop effects but with no joy. I have tried looking through various posts and doing things but no joy. 

Its a fresh install of Ubuntu (I keep killing it trying to get things to work) with all the updates.So time to ask for help before I kill it again.

I tried to System>Preferences>DesktopEffect and it wouldnt work. It hopped around a little bit then gave up.

So first I tried the "official" link  Installing Ubuntu 7.04: ATI X**** Cards 
[http://ubuntuforums.org/showthread.php?t=414194](http://ubuntuforums.org/showthread.php?t=414194)

Now System>Preferences>DesktopEffect gives the result The Composite extension is not available. When I change the xorg.conf  to "composite"  "enable" I can now select the effects but they still wont work, so I changed the log back to as below. (I rebooted where needed)

Will I need to follow this link and install beryl?
[http://ubuntuforums.org/showthread.php?t=399643](http://ubuntuforums.org/showthread.php?t=399643)

I hope this is enough info, it seem what most people are asked for, if it wrong, sorry, let me know what is needed.

Graphics card, Mobility Radeon X1600

fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1600
OpenGL version string: 2.0.6334 (8.34.8)

fgl_glxgears
Using GLX_SGIX_pbuffer
3064 frames in 5.0 seconds = 612.800 FPS
3624 frames in 5.0 seconds = 724.800 FPS
3629 frames in 5.0 seconds = 725.800 FPS

Then I followed this link, I wasnt sure what I needed to replace in LINK #6
[http://ubuntuforums.org/showthread.php?t=428313&highlight=mobility+x1600](http://ubuntuforums.org/showthread.php?t=428313&highlight=mobility+x1600)

last sectoin of xorg.conf, didnt think you needed the rest, but if you do please ask.

```
Section "Monitor"
	Identifier	"Generic Monitor"
	Horizsync	28.0	-	64.0
	Vertrefresh	43.0	-	60.0
	Option		"DPMS"
EndSection

Section "Monitor"
	Identifier	"aticonfig-Monitor[0]"
	Option		"VendorName"	"ATI Proprietary Driver"
	Option		"ModelName"	"Generic Autodetecting Monitor"
	Option		"DPMS"	"true"
EndSection

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"fglrx"
	Busid		"PCI:1:0:0"
EndSection

Section "Device"
	Identifier	"aticonfig-Device[0]"
	Driver		"fglrx"
	Option		"VideoOverlay"	"on"
	Option		"OpenGLOverlay"	"off"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	1
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth	4
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth	8
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth	15
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth	16
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth	24
		Modes		"1280x800"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"aticonfig-Screen[0]"
	Device		"aticonfig-Device[0]"
	Monitor		"aticonfig-Monitor[0]"
	Defaultdepth	24
	SubSection "Display"
		Viewport	0	0
		Depth	24
	EndSubSection
EndSection

Section "DRI"
	Mode	0666
EndSection

Section "Extensions"
	Option		"Composite"	"0"
EndSection
```

---

