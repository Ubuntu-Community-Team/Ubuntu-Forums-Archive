---
title: "xserver setup on a dell 'studio hybrid'"
date: 2011-01-14
forum: Dell Ubuntu Support (CLOSED)
---

### Post by necco on 2011-01-14
greetings.

i am evaluating the use of ubuntu 10.10 on a dell "hybrid studio". the video card has a 256Mb VRAM and (i think) is an integrated i810.

gnome panel proposes a max 4/3 resolution of 1024*768@60Hz, my good old trinitron screen goes up to 2048 and is otimized for a 1600*1200@85Hz resolution.

i have tried to run as root dpkg-reconfigure xserver-xorg on tty1 but nothing happens and i have my "#" back. ctrl-alt backspace does not work to kill gnome and when stopping Xorg through /etc/init.s/stop gdm the procedure freezes trying to check the battery level.

does anybody has a clue on how i can get a decent workspace?

thanks in advance.

necco

---

### Post by fibble on 2011-01-18
Hi,

I hit what seems to be the same problem today. Ill guess your using a VGA monitor via an adapter or DVI to vga cable?

Anyway ive resolved it here by:

Generating a custom modeline at: [http://xtiming.sourceforge.net/cgi-bin/xtiming.pl](http://xtiming.sourceforge.net/cgi-bin/xtiming.pl)

I only bothered with visible resolution and refresh rate and left the rest blank. I then created /etc/X11/xorg.conf with the following content (do this as root!)



```

Section "ServerLayout"
	Identifier     "X.org Configured"
	Screen      0  "Screen0" 0 0
	InputDevice    "Mouse0" "CorePointer"
	InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
	ModulePath   "/usr/lib/xorg/modules"
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/usr/share/fonts/X11/cyrillic"
	FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/Type1"
	FontPath     "/usr/share/fonts/X11/100dpi"
	FontPath     "/usr/share/fonts/X11/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath     "built-ins"
EndSection


Section "Module"
       Load  "record"
       Load  "extmod"
       Load  "dri"
       Load  "dbe"
       Load  "glx"
       Load  "xtrap"
       Load  "GLcore"
EndSection 

Section "InputDevice"
	Identifier  "Keyboard0"
	Driver      "kbd"
EndSection

Section "InputDevice"
	Identifier  "Mouse0"
	Driver      "mouse"
	Option	    "Protocol" "auto"
	Option	    "Device" "/dev/input/mice"
	Option	    "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
	Identifier   "Monitor0"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
	Modeline "1280x1024@60" 114.98 1280 1312 1744 1776 1024 1045 1055 1076
EndSection

Section "Device"
       ### Available Driver options are:-
       ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
       ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
       ### [arg]: arg optional
       #Option     "NoAccel"                   # [<bool>]
       #Option     "SWcursor"                  # [<bool>]
       #Option     "ColorKey"                  # <i>
       #Option     "CacheLines"                # <i>
       #Option     "Dac6Bit"                   # [<bool>]
       #Option     "DRI"                       # [<bool>]
       Option     "NoDDC"                   "true"  # [<bool>]
       #Option     "ShowCache"                 # [<bool>]
       #Option     "XvMCSurfaces"              # <i>
       #Option     "PageFlip"                  # [<bool>]
       Option     "NoAccel"    "false"                 # [<bool>]
       Option    "AccelMethod" "XAA" 
       Identifier  "Card0"
       Driver      "intel"
       VendorName  "Intel Corporation"
       BoardName   "Mobile GM965/GL960 Integrated Graphics Controller"
       BusID       "PCI:0:2:0"
EndSection 

Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "Monitor0"
	SubSection "Display"
		Viewport   0 0
		Depth     24
		#
	EndSubSection
EndSection


```


Replace the Modeline you genrated with the one in that example. Then when i went to Preferences > Monitors the desired 1280x1024 was in the list

Hope this helps

Andy

---

