---
title: "New ATI Graphics Card Issues"
date: 2009-11-15
forum: Desktop Environments
---

### Post by teufelhundst on 2009-11-15
Hey all, first of all i'm running Ubuntu 9.10 and i'm having a couple issues with my new ATI 4890.  I basically want two things from it:
[LIST]
[*]To be able to drag windows between both of my mointors
[*]Have 3D acceleration for some basic gaming (EVE Online)
[/LIST]
Also, it would be great if I could get compiz working on top of this.

Now, to be able to drag screens between my monitors, it seems I would need to use Xinerama or use "Big Desktop" as provided from the ATI binary drivers (which I need to use to have 3D acceleration).  Now, if I use Xinerama I lose support for Compiz (I get issues with "Composite extension not found" which upon many google searches people seemed to fix with a package called xserver-xgl, however that is no longer available in the Ubuntu repositories, which is because I imagine is because of xserver switching over to AIGLX instead of xgl in 2008).  Also, even without Compiz I have 3D issues, upon starting EVE I get the black screen of no return and have to hard reboot my system (ctrl+alt+f# doesn't work, along with ctrl+alt+bksp).

Trying Big Desktop gives me issues too, Compiz works but my settings aren't saved so I have to configure my graphics everytime I restart my xserver, which I wouldn't even care about, but trying to run EVE simply fails (crashes after splash screen with no helpful errors).

I don't understand why, because glxinfo tells me I have direct rendering.  Although, running comipz-check says this:

```
Gathering information about your system...

 Distribution:          Ubuntu 9.10
 Desktop environment:   GNOME
 Graphics chip:         ATI Technologies Inc RV790 [Radeon HD 4800 Series]
 Driver in use:         fglrx
 Rendering method:      None

Checking if it's possible to run Compiz on your system...  [SKIP]

 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: No rendering method in use (AIGLX, Xgl or Nvidia) 

```

The compiz-check is strange, because even though it said I can't run compiz I can when I use "Big Desktop" mode, and it says I don't have rendering even though glxinfo says I do.

I have tried a number of different binary drivers from ATI, including the ones from the restricted drivers repository.  Currently I am using 9.11 which was just leaked a couple days ago.  So far, I have had the least lock-ups, and it has been easier to configure then previous drivers.  However, its still not working.

Here is my xorg.conf:

```

Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "Main Screen" 0 0
	Option	    "Xinerama" "off"
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "ServerFlags"
	Option	    "Xinerama" "off"
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
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	Option	    "DDCMode" "True"
	Option	    "MonitorLayout" "TMDS,TMDS"
	BusID       "PCI:3:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-1"
	Driver      "fglrx"
	Option	    "DDCMode" "True"
	Option	    "MonitorLayout" "TMDS,TMDS"
	BusID       "PCI:3:0:0"
	Screen      1
EndSection

Section "Screen"
	Identifier "Main Screen"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
		Modes    "1920x1080"
	EndSubSection
EndSection

Section "Screen"
	Identifier "Second Screen"
	Device     "aticonfig-Device[0]-1"
	Monitor    "aticonfig-Monitor[0]-1"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
		Modes    "1440x900"
	EndSubSection
EndSection
```

You can see I don't have the second screen in the serverlayout section, I was only using it when I was using Xinerama, which you can see I turned off.  I had Option "Composite" "1" in there for awhile, but it didn't make a difference.  If you need more info, just ask!  Please help!

---

### Post by teufelhundst on 2009-11-16
*bump*

Please Ubuntu community!  I come to you on my knees, I don't know what to do at this point.  Google has failed me, as has searching thru this forum (unless I missed something, very possible!).  I feel I have given sufficient information, but if not let me know!

:confused:

---

### Post by teufelhundst on 2009-11-16
*solved*

turns out it was wine/fglrx not playing nicely.  Some regedits in wine fixed my issues! (and there was a different issue with Ubuntu 9.10 and eve for whatever reason too... but we are all fixed!)

Of course this all only works with big desktop, but I don't care.  It works.

---

