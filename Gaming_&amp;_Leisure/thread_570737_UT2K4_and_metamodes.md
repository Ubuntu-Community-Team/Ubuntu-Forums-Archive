---
title: "UT2K4 and metamodes"
date: 2007-10-08
forum: Gaming &amp; Leisure
---

### Post by TwoOranges on 2007-10-08
I just installed UT2004 on my Ubuntu 7.10 Beta 64bit install. UT starts, but I've got a problem with my twinview setup. I configured some metamodes and when UT starts, one of my screens goes blank (as it should). The second screen switches to the correct resolution, but shows me a part of my first desktop. When I drag my mouse to the right, the UT game window "slides" into the visible area until it covers the entire screen area (I can't "slide" back to the desktop on the left). But then I've got problems with my mousepointer. Most of the time I can only drag the cursor half way the screen in one direction. This is really annoying as it makes the game unplayable :(
The relevant configuration in my xorg.conf
```
	Identifier	"nVidia Corporation NVIDIA Default Card"
	Driver		"nvidia"
	Busid		"PCI:1:0:0"
	Option		"NoLogo"	"True"
	Option "RenderAccel" "0"
	Option "ConnectedMonitor" "dfp, dfp"
	Option "TwinView" "True"
	Option "TwinViewOrientation" "LeftOf"
	Option "Metamodes" "1680x1050,1680x1050;1280x1024,NULL;1024x768,NULL;800x600,NULL;640x480,NULL"
	Option     "SecondMonitorHorizSync"   "UseEdidFreqs"
	Option     "SecondMonitorVertRefresh" "UseEdidFreqs"
```
I already tried to switch the screens in the metamodes configuration, but with the same result. Any help would be appreciated ;)

---

### Post by Eazy© on 2007-10-08
I never had any luck with TwinView and UT2004. I have to use separate X screens with Xinerama. With separate X screens and Xinerama you don't need to have metamodes to turn the other monitor off (I have IRC on my other monitor so I can follow what happens there, and beside, the point to use two monitors is to have them both active!? :) )The downside for this is I cant use my beloved Beryl/Compiz as it does not support Xinerama.

---

