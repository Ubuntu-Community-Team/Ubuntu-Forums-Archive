---
title: "Stellarium Installation problems"
date: 2005-11-11
forum: Desktop Environments
---

### Post by gregorian21 on 2005-11-11
I installed [Stellarium]("http://www.stellarium.org/") from the Ubuntu Universe repositories and got the following error message when trying to run it.
My video card is an nVidia 6600 running nVidia drivers.
Am I missing an essential package. Any help would be appreciated.
Thank you
---------------------------------------------------------------
[FONT=Courier New]
    -----------------------------------------
    | ## ### ### #   #   ### ###  #  # # # #|
    | #   #  ##  #   #   ### ##   #  # # ###|
    |##   #  ### ### ### # # # #  #  ### # #|
    |                       Stellarium 0.6.2|
    -----------------------------------------

Copyright (C) 2004 Fabien Chereau

Please check last version and send bug report & comments
on stellarium web page : [http://stellarium.free.fr]("http://stellarium.free.fr")

Loading configuration file /home/myHome/.stellarium/config.ini ...
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
sdl: Couldn't set 1024x768 video mode (Couldn't find matching GLX visual), retrying with stencil size 0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
sdl: Couldn't set 1024x768 video mode: Couldn't find matching GLX visual!
Fatal signal: Segmentation Fault (SDL Parachute Deployed)
*** glibc detected *** corrupted double-linked list: 0xb7d0a938 ***
Aborted[/FONT]

---

### Post by Ubuntist on 2005-11-11
Synaptic shows a package called libglitz-glx1 -- maybe that's what you need to install?

---

### Post by perspectoff on 2007-08-03
I installed Stellarium but it ran very slowly. (This same thing happened with Google Earth).

Then i found out that the Ubuntu installer had denoted "VESA" as my standard graphic card in /etc/X11/xorg.conf:

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"vesa"
	BusID		"PCI:0:2:0"
EndSection

However, my system has an Intel 865G chipset with Extreme Graphics 2.

The appropriate graphics driver is i810, not VESA.

I therefore substituted the section:

Section "Device"
	Identifier	"Intel Corporation 82945G/GZ Integrated Graphics Controller"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

and changed the section:

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
...

to
Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82945G/GZ Integrated Graphics
...

Now both Stellarium and Google Earth work fast and without problems.

The problem seems to be that the auto-detection of my graphics card by the Ubuntu Feisty installation did not accurately identify the graphics card driver needed. This was not a problem in Dapper; I don't know what changed.

---

