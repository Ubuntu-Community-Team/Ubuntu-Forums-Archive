---
title: "Compiz effects without xserver-xgl?"
date: 2007-11-04
forum: Desktop Effects &amp; Customization
---

### Post by Nick Payne on 2007-11-04
Gutsy AMD64 with an nVidia 7600 digital dual head video card. I can enable the nVidia restricted driver and get the desktop across both monitors no problem, but when I try to enable visual effects (System / Preferences / Appearance), I get a dialog after a few seconds saying that effects could not be enabled. If I install xserver-xgl, then I can enable effects, but I also get the problem that windows maximize across both monitors, and centered dialogs/windows open split half and half between the two monitors. Is it possible to get desktop effects without xserver-xgl? The maximized window problem happens as soon as X is restarted after installing xserver-xgl and before desktop effects are enabled.

I also have the wierd problem that Restricted Drivers shows me that the niVidia accelerated graphics driver is in use, But when I try to run nvidia-settings, I get an error dialog saying "You do not appear to be using the NVIDIA X driver". xorg.conf clearly shows that I am:

[B]Section "Device"
	    Identifier	"nVidia Corporation G70 [GeForce 7600 GT]"
	    Boardname	"nv"
	    Busid		"PCI:1:0:0"
	    Driver		"nvidia"
	    Screen	0
EndSection[/B]

---

