---
title: "dual monitor issue after jaunty upgrade, plz help."
date: 2009-06-09
forum: General Help
---

### Post by ubuscout on 2009-06-09
hi people,

let me say first, I tried many way and threads before post this, so plz I need really help :)

My hardware setup is a notebook Asus X53S with an Ati Radeon HD2600 plus an external monitor Philips lcd 19"

I need to setup my external lcd as default monitor in clone mode (with laptop res 1280x800 and external lcd 1280x1024), plz note that I have working with this setup until before the upgrade with ubuntu 8.10, I tried to paste my previous copy of xorg.con, but it seem that i t  doesn't work now... :( 

Actually the system is almost going fine, I'm meaning that in laptop the display is working fine with 1280x800 resolution but in external monitor the cloned display is not right. It show fine the horiz res 1280 but the vertical res is not 1024 as expected but is little bit stretched, and bottom of desktop is little bit cutted ...

For the rest everything seem fine compiz work fine etc... Only he external monitor is really annoying me :(

Any help is really appreciated :)

I post the actual code of my xorg.conf

```

Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "ServerFlags"
	Option	    "Xinerama" "off"
EndSection

Section "Monitor"
	Identifier  "lcdext"
	DisplaySize 376 301
	Modeline    "1280x1024_60.00"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
	Option	    "PreferredMode" "1280x1024_60.00"
	Option	    "DPMS" "true"
EndSection

Section "Monitor"
	Identifier  "laptop"
	DisplaySize 331 207
	Option	    "DPMS" "true"
EndSection


Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	Option	    "Monitor-LCD" "laptop"
	Option	    "Monitor-CRT1" "lcdext"
#	Option	    "DesktopSetup" "clone"
#	Option	    "Capabilities" "0x00000800"
#	Option	    "PairModes" ""
#	Option	    "EnableMonitor" "CRT1,LCD"
#	Option	    "Mode2"         "1280x1024" #Resolution for second
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "laptop"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
#		Mode "1280x1024" "1024x768" "800x600"
#		Virtual 1280 1024
	EndSubSection
EndSection


```

---

### Post by ubuscout on 2009-06-10
...a polite  toc toc ... 

PS. I've forgotten to write I'm using last version of restricted drive of Ati. 

Plz. note also, that once login, if I type from console:
"xrandr --output CRT1 --mode 1280x1024 --refresh 75" ...it give some message error in console due to some call, but everything is work fine...

thx in advance :-)

---

### Post by ubuscout on 2009-06-24
Hi people,

maybe it seems I solved this problem :-)

Essentially fglrx (ati closed driver) "doesn't work" for me fine due to RandR12 was enable.

If I did aticonfig --query-monitor  it gave me error due to RandR enable. This explain (I think) why from ati catalyst manager I wasn't ebable to see all "good" option for set my configuration. Follow this post

[http://ubuntuforums.org/showthread.php?t=1137576](http://ubuntuforums.org/showthread.php?t=1137576)

I solved Randr problem and consequently also ati dual configuration.

---

