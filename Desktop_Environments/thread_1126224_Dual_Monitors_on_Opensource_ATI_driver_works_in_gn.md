---
title: "Dual Monitors on Opensource ATI driver works in gnome not KDE/XFCE (9.04 beta)"
date: 2009-04-15
forum: Desktop Environments
---

### Post by brendan.lefoll on 2009-04-15
My problem is simple, I can get dual head working fine on my fanless ATI HD4550 if I use gnome.

My card has a DVI, a HDMI and a VGA. I use the VGA and DVI, but on KDE both screens are seen as the same. SO when i click detect screens it shows VGA-0/DVI-0 on both screens.

So its pretty confused.

XFCE only sees one screen. and basically clones them.

here is my xorg.conf file

Section "Screen"
	Identifier	"Configured Screen Device"
	Device	"Configured Video Device"
	SubSection "Display"
		Virtual	3840 1200
	EndSubSection
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "ServerFlags"
	Option	"DontZap"	"False"
EndSection

And the output of xrandr -q

Screen 0: minimum 320 x 200, current 1920 x 1200, maximum 3840 x 1200
VGA-0 connected 1920x1200+0+0 (normal left inverted right x axis y axis) 518mm x 324mm
   1920x1200      60.0*+
   1600x1200      60.0  
   1280x1024      75.0     60.0  
   1152x864       75.0  
   1024x768       75.0     60.0  
   800x600        75.0     60.3  
   640x480        75.0     59.9  
   720x400        70.1  
HDMI-0 disconnected (normal left inverted right x axis y axis)
DVI-0 connected 1920x1200+0+0 (normal left inverted right x axis y axis) 518mm x 324mm
   1920x1200      60.0*+
   1600x1200      60.0  
   1280x1024      75.0     60.0  
   1152x864       75.0  
   1024x768       75.0     60.0  
   800x600        75.0     60.3  
   640x480        75.0     59.9  
   720x400        70.1  

Any help would be appreciated!

edit : I have tried 
xrandr --output DVI-0 --right-of VGA-0 --auto
but It does nothing.

---

### Post by markbuntu on 2009-04-15
I have the same problem with KDE on Jaunty with my HD3650 using the radeonhd driver.  There is a very excellent explanation for setting multiple monitors in the KDE help but the actual place to do it is missing from the system settings.

Is this a bug or a feature?

---

### Post by yourexhalekiss on 2010-01-25
Any luck? I'm having the same problem - dual 1920x1200 monitors appearing as clones instead of separate. I have a Radeon HD 4830.

---

