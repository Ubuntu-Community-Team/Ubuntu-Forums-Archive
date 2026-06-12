---
title: "Changing screen resolution"
date: 2008-12-21
forum: General Help
---

### Post by Nitroware on 2008-12-21
Hey, Ive been working on this all day, and I cant seem to figure this out.  I have a hp2007 1680x1050 monitor, I have fedora 10 using Gnome.  Right now I have the highest the screen will go to is 1240x1024.  I want the screen at 1680x1050 however it refuses to let me.  I think I am using xrandr, however please advise if I'm not.  This is what I did (BTW. I have restarted the X server between each try):

```

[root@localhost ~]# gtf 1680 1050 60
  # 1680x1050 @ 60.00 Hz (GTF) hsync: 65.22 kHz; pclk: 147.14 MHz
  Modeline "1680x1050_60.00"  147.14  1680 1784 1968 2256  1050 1051 1054 1087  -HSync +Vsync

[root@localhost ~]# xrandr --newmode "1680x1050"  147.14  1680 1784 1968 2256  1050 1051 1054 1087  -HSync +Vsync
[root@localhost ~]# xrandr --addmode default 1680x1050
[root@localhost ~]# xrandr -s 1680x1050 --verbose
 SZ:    Pixels          Physical       Refresh
*0   1280 x 1024   ( 339mm x 271mm )  *61  
 1   1024 x 768    ( 339mm x 271mm )   61  
 2    800 x 600    ( 339mm x 271mm )   61  
 3    640 x 480    ( 339mm x 271mm )   60  
 4   1680 x 1050   ( 339mm x 271mm )   60  
Current rotation - normal
Current reflection - none
Rotations possible - normal 
Reflections possible - none
Setting size to 4, rotation to normal
Setting reflection on neither axis
Failed to change the screen configuration!

```

I saw that work before, but it doesnt want to now.  Here is my xorg.conf:
```
# Xorg configuration created by system-config-display

Section "ServerLayout"
	Identifier     "single head configuration"
	Screen      0  "Screen0" 0 0
	InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "InputDevice"
# keyboard added by rhpxl
	Identifier  "Keyboard0"
	Driver      "kbd"
	Option	    "XkbModel" "pc105+inet"
	Option	    "XkbLayout" "us"
EndSection

Section "Monitor"
	Identifier   "Monitor0"
	ModelName    "LCD Panel 1680x1050"
	HorizSync    31.5 - 65.5
	VertRefresh  56.0 - 65.0
	Modeline "1680x1050_60.00"  147.14  1680 1784 1968 2256  1050 1051 1054 1087  -HSync +Vsync
	Option	    "dpms"
EndSection

Section "Device"
	Identifier  "Videocard0"
	Driver      "vesa"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Videocard0"
	Monitor    "Monitor0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

```

This seems to be a common issue, I dont understand why the "X team" hasnt fixed it yet.


Thanks for any replies!

---

