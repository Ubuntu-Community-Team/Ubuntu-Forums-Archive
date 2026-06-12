---
title: "3d desktop and ATI x1600...which driver"
date: 2007-01-18
forum: Desktop Environments
---

### Post by myname on 2007-01-18
Hello all,

I am running an AMD 3700+ with Ubuntu Edgy (non 64), and have a Radeon x1600 w/512 megs of RAM

I have installed the latest ATI drivers from ATI, and would like to run either Compiz or Beryl.  After reading the forum posts and the how-to's, I am unsure if I can run it, and when I tried, my X froze, had to roll back my xorg.conf file.

Here is a portion of my xorg.conf file.  notice, I have duplicate sections.  Can I combine/delete any sections?

Section "Monitor"
	Identifier   "Generic Monitor"
	HorizSync    28.0 - 64.0
	VertRefresh  43.0 - 60.0
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "ATI Technologies, Inc. ATI Default Card"
	Driver      "vesa"
	BusID       "PCI:5:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. ATI Default Card"
	Monitor    "Generic Monitor"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

Section "Extensions"
	Option	    "Composite" "Disabled"
EndSection

Per the How-to's they say I should have "Radeon" listed in the device section, but as you can see, I have 1 section with VESA and 1 section with fglrx.  When I change them to Radeon, X refuses to start, and my system freezes.

Can I run Beryl, or Compiz, and if so, which ones, and which lines should I remove/re-configure.  any help would be great.

With this change, I would also like to continue to play WoW, so hopefully any change I make won't mess up my framerates in WoW.

TIA

--Kevin

---

### Post by mcduck on 2007-01-18
yes, x1600 runs Beryl just fine. But the important thing to notice is that you need to use fglrx drivers to get 3D acceleration, and that means you also need to use XGL, not AIGLX..

This is pretty good guide for installing Beryl with fglrx&XGL: [http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_XGL]("http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_XGL")

---

### Post by tbeld on 2007-01-18
I had Dapper installed and tried repeatedly to get Beryl running but being a noob I probably took some wrong turns and hosed my system so that all the howtos wouldn't help. I upgraded to Edgy and still couldn't get it working. So, I did a clean install of Edgy.

I am now running Edgy and have Beryl SVN running with an ATI Radeon x1300. I am using the ATI proprietary drivers (fglrx). I have a dual-head setup with direct rendering apparently only on screen 0 but my system runs well and is quite stable. 
~$ fglrxinfo
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1300 Series Generic
OpenGL version string: 2.0.6011 (8.28.8)

After a clean install of Edgy, I used the following guide: [http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html](http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html)

It worked perfectly.  However, I didn't mess with xorg.conf. I followed all the other steps and then rebooted and logged in to trouble shooting mode and used the aticonfig tool to get a dual-head setup with fglrx in xorg.conf.

sudo aticonfig --dtop=horizontal --overlay-on=1

I suppose for a single-head setup the guide would work just fine.

---

