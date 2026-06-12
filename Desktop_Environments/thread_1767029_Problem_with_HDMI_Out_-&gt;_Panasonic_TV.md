---
title: "Problem with HDMI Out -&gt; Panasonic TV"
date: 2011-05-25
forum: Desktop Environments
---

### Post by dtuza on 2011-05-25
Hi all,

I've reinstalled Ubuntu 11.04 after not having Ubuntu since Gutsy, and in general I really like the new Unity desktop; very polished and professional looking.  I'm having some trouble, however, with HDMI output to a Panasonic Viera TV.

With the vanilla installation of 11.04 I was having no display issues whatsoever - dual screen was working perfectly with my 22" monitor and the TV in question.  However, I was having trouble with sound via HDMI, so I installed the latest drivers for my card (ATI Radeon HD 5450) from the ATI site.  After installing, sound via HDMI is working like a dream, and the display on the 22" monitor is perfect, but the display on the TV is all wrong.

First of all, the display doesn't fill the entire screen.  Second of all, the ATI Catalyst Control Center seems to regularly change its mind about the TV's resolution, refresh rate, and even what the thing is - it seems to intermittently say it's a projector, then a TV, and back and forth.

The problem seems (to my untrained eye) to lie with the ATI drivers, but I'm not sure whether it's something I will be better off to try and fix, or whether it would be more beneficial to uninstall the ATI Catalyst Control Center and try to fix the HDMI sound on the vanilla install.

Any help or advice would be greatly appreciated.  Thanks!

---

### Post by Grenage on 2011-05-25
You can 'hard-set' the resolution in /etc/X11/xorg.conf.  If the file exists, could you post its contents?  It's also worth posting your desired TV res, and the output of:

```
xrandr -q
```
and
```
lspci | grep VGA
```

---

### Post by dtuza on 2011-05-25
Thanks so much for the quick reply.  My preferred resolution for the 22" monitor is 1680x1050, and for the TV it's 1920x1080.  Outputs for those commands follow:

```
$ cat /etc/X11/xorg.conf
Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Module"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Monitor"
	Identifier   "0-DFP1"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	Option	    "PreferredMode" "1920x1080"
	Option	    "TargetRefresh" "60"
	Option	    "Position" "1680 0"
	Option	    "Rotate" "normal"
	Option	    "Disable" "false"
EndSection

Section "Monitor"
	Identifier   "0-DFP2"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	Option	    "PreferredMode" "1680x1050"
	Option	    "TargetRefresh" "60"
	Option	    "Position" "0 0"
	Option	    "Rotate" "normal"
	Option	    "Disable" "false"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	Option	    "Monitor-DFP1" "0-DFP1"
	Option	    "Monitor-DFP2" "0-DFP2"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Virtual   3600 1920
		Depth     24
	EndSubSection
EndSection
```


```
$ xrandr -q
Screen 0: minimum 320 x 200, current 3600 x 1080, maximum 3600 x 1920
DFP1 connected 1920x1080+0+0 (normal left inverted right x axis y axis) 698mm x 392mm
   1920x1080      60.0*+   50.0     59.9     30.0     25.0     24.0     30.0     24.0  
   1280x720       50.0 +   60.0     59.9  
   1776x1000      50.0     59.9     25.0     24.0     30.0  
   1680x1050      60.0     50.0     59.9     24.0     24.0  
   1400x1050      60.0     50.0     59.9     24.0     24.0  
   1600x900       60.0     50.0     59.9     24.0     24.0  
   1360x1024      60.0     50.0     59.9     24.0     24.0  
   1280x1024      60.0     50.0     59.9     24.0     24.0  
   1440x900       60.0     50.0     59.9     24.0     24.0  
   1280x960       60.0     50.0     59.9     24.0     24.0  
   1280x768       60.0     50.0     59.9     24.0     24.0  
   1024x768       60.0     50.0     59.9     24.0     24.0  
   1152x648       50.0     59.9  
   800x600        50.0     59.9  
   720x576        59.9     50.0  
   720x480        50.0     60.0     59.9  
   640x480        50.0     60.0     59.9  
DFP2 connected 1680x1050+1920+0 (normal left inverted right x axis y axis) 470mm x 300mm
   1680x1050      60.0*+
   1400x1050      60.0  
   1600x900       60.0  
   1360x1024      60.0  
   1280x1024      75.0     60.0  
   1440x900       75.0     59.9  
   1280x960       60.0  
   1280x800       60.0  
   1152x864       60.0     75.0  
   1280x768       60.0  
   1280x720       60.0  
   1024x768       75.0     70.1     72.0     60.0  
   800x600        72.2     75.0     60.3     56.2  
   640x480        75.0     72.8     66.8     59.9  
CRT1 disconnected (normal left inverted right x axis y axis)
CRT2 disconnected (normal left inverted right x axis y axis)
```

```
$ lspci | grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc Cedar PRO [Radeon HD 5450]
```

---

### Post by Grenage on 2011-05-25
I never deal with ATI configs, but that looks good to me.  Try adding the modeline (I added it in bold); hopefully that will set your desired res to always be an option, so that the preferred mode can be utilised.

```
Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Module"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Monitor"
	Identifier   "0-DFP1"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	Option	    "PreferredMode" "1920x1080"
	Option	    "TargetRefresh" "60"
	Option	    "Position" "1680 0"
	Option	    "Rotate" "normal"
	Option	    "Disable" "false"
EndSection

Section "Monitor"
	Identifier   "0-DFP2"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	Option	    "PreferredMode" "1680x1050"
	Option	    "TargetRefresh" "60"
	Option	    "Position" "0 0"
	Option	    "Rotate" "normal"
	Option	    "Disable" "false"
**Modeline "1680x1050_60.00"  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync**
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	Option	    "Monitor-DFP1" "0-DFP1"
	Option	    "Monitor-DFP2" "0-DFP2"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Virtual   3600 1920
		Depth     24
	EndSubSection
EndSection
```

---

### Post by dtuza on 2011-05-25
Thanks, that will be an excellent start.  Is there a way I can specify in my X config for the screen to fill the TV?  I mentioned briefly in the OP - right now, I can't actually get the display to fill the screen, it's got about a 1-2" bar on all sides, which seems completely arbitrary.

---

### Post by Grenage on 2011-05-25
> **dtuza said:**
> Thanks, that will be an excellent start.  Is there a way I can specify in my X config for the screen to fill the TV?  I mentioned briefly in the OP - right now, I can't actually get the display to fill the screen, it's got about a 1-2" bar on all sides, which seems completely arbitrary.

Does the ATI Control Centre have any Underscan/Overscan options?  I may be listed under Administrative tasks as 'scaling'.  I am going to assume that there is an EDID whoops here, which would explain why the resolution also varies.  A fix could be as simple as checking the TV-PC cable connection, or swapping the cable; failing that, look for scaling options.

If there isn't an option or it simply doesn't work, there appear to be a few Catalyst commands which others have had success with - [like here]("http://phoronix.com/forums/showthread.php?10073-black-border&p=35481#post35481").

---

### Post by dtuza on 2011-05-25
Thanks again - that thread looks like exactly what I'm after.  Though it may be a workaround, I'll take a workaround over silly looking black borders any day :)

---

### Post by dtuza on 2011-05-25
Sorry for the double post, but I just wanted to confirm for anyone having the same problem - from the thread given above, [this]("http://phoronix.com/forums/showthread.php?10073-black-border&p=36734#post36734") post was the one that did it for me.  Though there's no option in the ATI Control Centre to directly turn off underscanning, that does seem like the issue.

Will set this thread to solved!  Grenage, thanks again for your help - greatly appreciated :)

---

### Post by Grenage on 2011-05-25
Outstanding, glad to hear that it's sorted.

---

