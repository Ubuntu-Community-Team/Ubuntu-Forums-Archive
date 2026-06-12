---
title: "Confusing error when trying to start beryl"
date: 2007-03-26
forum: Desktop Effects &amp; Customization
---

### Post by Doug11 on 2007-03-26
As far as I know, I have everything set up right. I posted a shot of my terminal. I have direct rendering. But when I try to start beryl, it says no composite extensions. In Xorg.conf,,I have extension set to disabled, like all the how-to's say, and even if I change it to "enable" I then lose my direct rendering. Here is also part of my   Xorg.conf   and what it looks like.



Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "ATI Technologies, Inc. Radeon Xpress 200M (RS482)"
	Driver      "fglrx"
        Option      "VideoOverlay" "on"
        Option	    "OpenGLOverlay" "off"
	BusID       "PCI:1:5:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. Radeon Xpress 200M (RS482)"
	Monitor    "Generic Monitor"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1280x800"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1280x800"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1280x800"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1280x800"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1280x800"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1280x800"
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
	Option	    "Composite" "Disable"
EndSection



Is there something out of place here. Baffled. I have been tryting to get this going for a couple days nows and it seems I'm against a brick wall. Thx

---

### Post by AtrejuT on 2007-03-26
IMHO you'll need to use the xgl server since you are using fglrx, which doesn't support AIGLX.
So you'll need to set up an xgl session as described e.g. on the beryl wiki page ([www.beryl-project.org)](www.beryl-project.org)).
If you're installing beryl from the ubuntu universe repositories it furthermore won't work right now (at least not for me, and I'm using xgl as well). So you'll need to add the repositories from beryl-project to your /etc/apt/sources.list and force all beryl packages back to version 0.2.0

If your card is supported by the opensource driver then that's a much easier solution since those work with aiglx - but if the OS drivers work with your card, I don't know.

The above is only a rough outline, let me know if you run into problems.

good luck

atreju

---

### Post by Doug11 on 2007-03-26
OK,,Will see what I can do when I get home from work.

---

### Post by Doug11 on 2007-03-26
Well, i tried that. Then logged into a XGL session, tried to start beryl again but it come up with a bunch of different errors and i lost my panels and icons and had to restart x. Will keep trying.

ok,,update,,when in an xgl session, i have no direct rendering,, but when in a gnome session, I do,,this is my out put when in xgl session


doug@doug-laptop:~$ glxinfo | grep direct
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
direct rendering: No


This is getting very frustrating

---

### Post by Doug11 on 2007-03-26
ok,,,finally go it working,,now though,,whenever i log into an xgl session, I lose my panel. Also, I've been reading around a bit about making beryl work and what it can do. The cube is a pretty cool thing. I read about all the commands on how to move it, unfold it etc. but I can't figure out to actually get it on the desktop. Is there a good wiki on how to work beryl somewhere?

---

