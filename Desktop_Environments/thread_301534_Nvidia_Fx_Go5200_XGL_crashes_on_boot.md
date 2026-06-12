---
title: "Nvidia Fx Go5200: XGL crashes on boot"
date: 2006-11-17
forum: Desktop Environments
---

### Post by hokutonoken on 2006-11-17
I already tried posting elsewhere this problem, but got no answer, so I'll try starting a new thread.

I have a Nvidia fx go5200 on an Acer aspire laptop.

I followed xgl+compiz how-to on the Ubuntu Guide and tried many times but I haven't managed to start an Xgl session.

Whenever I reboot in Xgl mode I get a black screen and the following error message

NVIDIA(0): Failure reading maximum pixel clock value for display device
NVIDIA(0): TV-0


Please note I successfully installed all nvidia driver packages, and xgl packages (I also tried compiz, compiz-vanilla and beryl but they can't start if xgl isn't loaded)

I correctly set the following lines:

>>in gdm.conf-custom

[server-Xgl]
name=Xgl server
command=/usr/bin/Xgl :0 -fullscreen -ac -accel glxbuffer -accel xv:fbo
flexible=true

>>in xorg.conf

Section "Module"
Load "i2c"
Load "bitmap"
Load "ddc"
# Load "dri"   (note: dri is correctly uncommented; I don't have Glcore either)
Load "extmod"
Load "freetype"
Load "glx"     (note: glx is correctly loaded)
Load "int10"
Load "type1"
Load "vbe"
EndSection


...

Section "Device"
	Identifier	"NVIDIA Corporation NV34M [GeForce FX Go5200]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Option		"RenderAccel"		"true"
	Option		"AllowGLXWithComposite" "true"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	Option "NoLogo" "1"
	Option "NvAGP" "1"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV34M [GeForce FX Go5200]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
EndSection

....

#Section "DRI"  (note: DRI is disabled in the last section, too)
#	Mode	0666
#EndSection


>>
Please note also Nvidia drivers are correctly installed and working.
(e.g. glxgears works ok)

On loading of gdm login screen, I get a black screen and the error message:
NVIDIA(0): Failure reading maximum pixel clock value for display device
NVIDIA(0): TV-0

When I revert to default gdm.conf-custom, I get no warning message and x server starts correctly.. without xgl however, sadly.

Any advice?
Many thanks

---

### Post by hokutonoken on 2006-11-17
Any advice? 


I guess it depends on "Monitor" or "screen" section of my xorg.conf

Please help me,..

---

### Post by hokutonoken on 2006-11-18
Hoped someone would be so kind to send me a piece of advice..
Also the most trivial suggestion is well accepted..sadly, no one has answered yet. 
And I'm still wondering what's keeping XGL from loading.

I'll continue then with my monologue.

I considered there are two other warnings which may be causing XGL crashes.

The XKEYBOARD keymap compiler (xkbcomp) reports:
 > Warning:            Type "ONE_LEVEL" has one level, but <RALT> has 2 simbols
 >                              Ignoring extra simbols

and the next (and last) is:

FreeFontPath: FPE "usr/share/fonts/misc" refcount is 2, should be 1; fixing.

I think they have something to do with fonts folder loading.


I already tried googling and found many other people have the same problem, which isn't fatal to Gnome and KDE, but apparently keeps XGL from running.

Unfortunately I haven't found any solution.And there seem to be none out there.

Here is an example.
[http://forums.kororaa.org/viewtopic.php?t=700&postdays=0&postorder=asc&start=0](http://forums.kororaa.org/viewtopic.php?t=700&postdays=0&postorder=asc&start=0)

Many people complain Koroora doesn't start.
The symptoms are the same: three flashes on the screen an then Blue Scrren Of Death-

I also set a longer gdm load time (in gdm.conf), but it continues crashing.

What do you suggest?

---

### Post by Yaamboo on 2006-11-24
I have a similar problem with a GF4Ti4200 on Edgy. I can use Gnome without xgl, but if I try to run it with it, it crashes and returns to the welcome screen and hangs. I don't understand where the problem could be.

---

