---
title: "iceWM resolution problem"
date: 2005-03-30
forum: Desktop Environments
---

### Post by neshaug on 2005-03-30
I've just installed Ubuntu 5.04 Preview "The Hoary Hedgehog" using the howto "http://www.binonabiso.com/en/Ubuntu-miniRAM-HOWTO.html".

The problem is that the only resolution I get is 640x480 and It's not using the whole screen either, so I get a little 640x480 window sentered on my screen.

It's a evercom laptop:
550mhz
194mb ram
grapics card: Silicon Motion

---

### Post by az on 2005-03-31
It does not have to do with icewm, but with the configuration of your xserver.

sudo dpkg-reconfigure xserver-xorg

Chage the capabilities of your monitor.  Change the color depth.  It depends on what your card can handle.

---

### Post by neshaug on 2005-03-31
Yeah, I know it doesnt have anything with iceWM now.. Sorry for a bad post :P

I`ve tried to reconfigure several times with no luck though.. 

I have a 12" LCD monitor capable of 1024x768 in windows XP.

I`ll paste my monitor and device sections in the xorg.conf when I can get the paste function to work...

---

### Post by neshaug on 2005-03-31
Here goes.

Probably weird that I have 800x600 in modelline and 1024 on the other depth modes  but this was the only way that I could get fullscreen. Though now I dont know if its 800x600 or 1024 :P

xorg.conf:

Section "Device"
	Identifier	"Silicon Motion, Inc. SM710 LynxEM"
	Driver		"siliconmotion"
	BusID		"PCI:0:2:0"
	VideoRam	16000
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"BuiltinLCD"
	VendorName	"Generic"
	ModelName	"Flat Panel 1024x768"
	Option		"DPMS"
	HorizSync	28-64
	VertRefresh	43-60
	Modeline	"800x600" 65 1024 1048 1208 1264 768 776 784 817 +hsync +vsync Interlace
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Silicon Motion, Inc. SM710 LynxEM"
	Monitor		"BuiltinLCD"
	DefaultDepth	16
	SubSection "Display"
		Depth		8
		Modes		"1024x768@60"
		ViewPort	0 0
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768@60"
		ViewPort	0 0
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768@60"
		ViewPort	0 0
	EndSubSection

---

### Post by lprofil on 2005-08-06
Hi,

this thread is quiet old, but i have the same prob as you had. 
Using Ubuntu 5.04 with the 2.6.10-5-386 kernel.
The graphic chipset in a "**Maxdata Stanford Pro**" Notebook i am maintaining at the moment with an **PentiumII 360 MHz and 192MB RAM** is the same. 
It's a **Silicon Motion SM710 Chipset**.

As your's my display is only running in the 640x400 mode which is quiet annoying.
Of course i did a **dpkg-reconfigure xserver-xorg** but nada.

When it come to the menue where i can define the resolution only 1024x768 is highlighted which means that only that resolution should be used. 

#####

After a lot of messing around here is finally a first **Solution**:

**Set the default desired color depth to 8 bit.**
The graphic chipset our notebooks are using cannot handle higher color depth i think. This is not very satisfying but at least you can use the full resolution of your screen. As this is not a final solution further help would be appreciated.
Here is a link which might also help:
**[http://www.die.net/doc/linux/man/man4/siliconmotion.4.html](http://www.die.net/doc/linux/man/man4/siliconmotion.4.html) **

/lprofil


ps:finally i can give some advises back to "the community" which satisfies me very much!  :)

---

