---
title: "ATI 4870 Dual Monitor Jaunty, Maximize Problem"
date: 2009-04-26
forum: Desktop Environments
---

### Post by Rywern on 2009-04-26
Well I have searched and googled and looked.. but since I cant find anything im posting here.

I own an ATI 4870 card that I use with my two monitors, both 19" screens, one TFT and one CRT

The total resolution I use is 2560x1024@60

Everything works wonders in Jaunty, except one thing that keeps me from switching cause its incredibly important to me.
Every time I maximize a window, it spans over both screens, I hate it, since I often look at movies on my CRT monitor and surf on the TFT.

This all worked awesomely in Intrepid (8.10), so it has to be something with Jaunty.

Also in Intrepid i was able to change monitor positions resolutions and "Big desktop to the right of screen 1" in the "ATI Catalyst Control center" now that program is more of a waste since i cant use it to manage my monitors. the build in and edited "Display" tool seems to be the one prioritized.

thanks in advance =)
Rywern

---

### Post by Trab on 2009-05-02
Hello! I was wondering if you could explain how you were able to get dual monitors working? Since upgrading to Jaunty, I cannot get the monitors to Span, only to clone (how annoying!).

The only answer I can think of is that you must have done dual monitors not using the ATICCC, which is what allows you to have it only maximize on just one screen.

---

### Post by Nausser on 2009-05-03
Similar problem here. I have dual independent displays after doing a fresh install to Jaunty, however, each monitor has it's own full desktop. I have a separate mouse on each screen that I can switch between just by moving my mouse from left to right across the boarder. The mouse on my left screen stays at the edge of the boarder and a new mouse pointer picks up from there on the right screen and vise versa. 
I have separate menus on the tops and bottoms of each screen including apps, places, system, default icons, volume, clock and power. The only thing which is not duplicated on my right screen is the network manager icon.
I've also tried running these commands:
```
sudo aticonfig --initial=dual-head --screen-layout=right
```
and
```
sudo aticonfig --dtop=horizontal --overlay-on=1
```

I'm curious if I'm the only one or if someone else has a similar problem.

I've been running Hardy and then Intrepid consistently for some time now on the same computer in a dual screen configuration. (spanned)
I'm also running an older graphics card slot. Its AGP and not PCI-X.

Here is my current xorg file after running the above two commands:

```
Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
	Screen         "aticonfig-Screen[0]-1" RightOf "aticonfig-Screen[0]-0"
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "Monitor"
	Identifier   "Configured Monitor"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-1"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "Configured Video Device"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	Option	    "DesktopSetup" "horizontal"
	Option	    "OverlayOnCRTC2" "1"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-1"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
	Screen      1
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "Configured Video Device"
	Monitor    "Configured Monitor"
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

Section "Screen"
	Identifier "aticonfig-Screen[0]-1"
	Device     "aticonfig-Device[0]-1"
	Monitor    "aticonfig-Monitor[0]-1"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection
```

Cool if you can help. If not, I'll figure it out eventually.

-Nausser

---

### Post by luxor on 2009-05-08
For the 4870, if you have to use the fglrx driver which either allows 3d effects with Independent Desktops or you can disable the 3d effects and use the 'big desktop' (like xinerama) feature of the driver.  When ATI releases new drivers, you might want to try the new drivers to see if your widow maximizes correctly instead of across both screens.  I believe this was a known bug as of 3/2009.  

If you are using older hardware (agp), and you don't need 3d effects, then you don't need to use the fglrx driver.  You probably wan to use the ati or radeon driver.  These are open source drivers, and you will want to use the xinerama feature with these drivers.  There is plenty of information on the ubuntu forums and google on how to set this up.

For those of you using multiple independent displays with fglrx, are any of you experiencing the following bug:  When I try to open some applications in my secondary/tertiary display, they open on my primary display.  It doesn't happen with all apps.  It is pretty annoying, and if anyone has a fix, please post.  I know I can open up a terminal, and set the DISPLAY variable to the appropriate screen and run the app to have it open in the appropriate screen.  Is there some other way to set this when each desktop starts up?  I've opened a bug report here:  [https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/354880](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/354880)

---

### Post by nnl on 2009-05-19
Ati Catalyst 9.5 solves the maximizing problem download here: [http://ati.amd.com/support/driver.html](http://ati.amd.com/support/driver.html)

---

### Post by Fac51 on 2009-06-02
> **nnl said:**
> Ati Catalyst 9.5 solves the maximizing problem download here: [http://ati.amd.com/support/driver.html](http://ati.amd.com/support/driver.html)

Can anyone out there confirm this for ATI 3100 in Jaunty?

---

### Post by chome4 on 2009-06-17
If you have two monitors that have identical views, ie, two mouse pointers, it's called 'mirroring'.

To have one desktop instead of two, simply go to preferences, choose display and untick (uncheck) the 'Mirror' box. Done

I'm not sat in front of my Ubuntu pc so I'm working blind but it's under the 'display' icon.

This is for Jaunty, 9.04.

---

### Post by GSZX1337 on 2009-07-09
> **Nausser said:**
> Similar problem here. I have dual independent displays after doing a fresh install to Jaunty, however, each monitor has it's own full desktop. I have a separate mouse on each screen that I can switch between just by moving my mouse from left to right across the boarder. The mouse on my left screen stays at the edge of the boarder and a new mouse pointer picks up from there on the right screen and vise versa. 
I have separate menus on the tops and bottoms of each screen including apps, places, system, default icons, volume, clock and power. The only thing which is not duplicated on my right screen is the network manager icon.

This is the problem I have with the latest Catalyst drivers and a Radeon 4850. Anyone have an answer?

---

