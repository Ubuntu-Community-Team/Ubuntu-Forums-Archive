---
title: "Display Settings - Followed Tutorials"
date: 2009-01-05
forum: General Help
---

### Post by Unforgiven247 on 2009-01-05
Hello  everyone, installed ubuntu on my laptop and desktop last week, and have been busy configuring and troubleshooting my hardware. But have met a snag
My hardware is
LG W2252 24" LCD
ATI Radion 3870

For the ATI 3870, followed the tutorial @ ([https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI))  for setting it up using ATI's downloadable driver, everything went well, fgrlxinfo gives me

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 3870
OpenGL version string: 2.1.8304 Release

lsmod shows the fgrlx driver is loaded.

I can fire up the ATI Catalyst, and it shows my monitor LG W2252(but as a 23"), also shows only one refresh rate and that is 75 Hz(I can't change this). But lets me change resolutions.

BUT the "Configure Display Settings" icon in my panel has a yellow triangle threw it, and when I click to configure, it says monitor "unknown" and only shows a refresh of 60 Hz. Also I should note, when I change the resolution with the Catalyst, the Display Settings icon adjusts accordingly.

So I open xorg.conf and it has this

Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

I have also read the 

[http://ubuntuforums.org/showthread.php?t=83973](http://ubuntuforums.org/showthread.php?t=83973)

But all that does is blow my ATI config out and the Catalyst doesn't work anymore

So basically I want to be able to change my refresh rate to at least 75 Hz, How I know it's at 60 Hz is I am using Cedega to play BF2142, and in game it only shows a 60 Hz refresh rate, and the game stutters a bit on the graphics end

Hope I gave enough info :-)

---

