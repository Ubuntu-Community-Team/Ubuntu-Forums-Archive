---
title: "Incorrect virtual desktop size"
date: 2007-03-08
forum: Desktop Environments
---

### Post by FooSoft on 2007-03-08
I'm trying to manually set up my screen resolution by editing /etc/X11/xorg.conf for fluxbox. I've had success in scaling resolution down to 1280x1024 from 1600x1200, but unfortunately even though the monitor resolution is now correct, the desktop size is not. When I move my cursor to the edges of windows I scroll around the desktop (which is bigger than my resolution). How would I go about making the desktop have the same size as my screen resolution (I have no idea where this preference is stored)?

Here's my xorg.conf

```

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	FontPath	"/usr/share/fonts/X11/misc"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
        Option             "ButtonMapping" "1 2 3 6 7"
EndSection

Section "Device"
	Identifier	"NVIDIA Corporation NV40 [GeForce 6800 Ultra/GeForce 6800 GT]"
	Driver		"nvidia"
	BusID		"PCI:5:0:0"
	Option          "NoLogo"
EndSection

Section "Monitor"
	Identifier	"DELL P1130"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV40 [GeForce 6800 Ultra/GeForce 6800 GT]"
	Monitor		"DELL P1130"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1600x1200" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1600x1200" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1600x1200" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1600x1200" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1600x1200" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1600x1200" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

---

### Post by chewearn on 2007-03-08
No sure if this will work; I'm just guessing. :-\"

I see that your resolutions are not in order from largest to smallest.  Maybe you try to reorder it.

from:
"1280x1024" "1600x1200" "1152x864" "1024x768" "800x600" "640x480"

to:
"1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "640x480"

---

### Post by FooSoft on 2007-03-08
No, that much doesn't work (that's how you set up your resolution in the first place, the first entry is the preferred resolution)

I'm kind of suspecting it has something to do w/ my dual head video card, but not sure.

---

### Post by RedSquirrel on 2007-03-08
I'm not sure if this is what you mean, but are you saying there's a few pixels of desktop showing on the right-hand side of your screen?

If that's the case, there's an empty Slit sitting there.

Go into your Fluxbox menu:

[B]fluxbox menu -> Configuration -> Slit -> Maximize Over


EDIT:

[/B]I just re-read your initial post and I see that this is *not* what you mean.

Have you experienced the same effect of the virtual desktop being larger than your resolution in other environments (GNOME, KDE, etc.)? I wonder if something is missing from your video card settings in xorg.conf....

**EDIT 2:**

From the man page for xorg.conf:

> **        Virtual    xdim ydim**
          This optional entry specifies the virtual screen    resolution  to
          be  used.   xdim    must  be a multiple of either 8 or 16 for most
          drivers, and a multiple of 32 when running in  monochrome  mode.
          The  given  value  will be rounded down if this is not the case.
          Video modes which are too large for the specified  virtual  size
          will  be    rejected.   [COLOR=Red]If    this entry is not present, the virtual
          screen resolution will be set to accommodate all the valid video
          modes  given in the Modes entry.[/COLOR]    Some drivers/hardware combina
          tions do not support virtual screens.  Refer to the  appropriate
          driver-specific documentation for details.
So I would just add

```
Virtual 1280 1024 
```to the section for 24-bit, or if you don't plan to ever use 1600 by 1200, you could delete than entry in the Modes line.

There may be some extra settings for your "nvidia" driver that you could put in xorg.conf to deal with your dual-head card. I came across a way for radeon users to specify in xorg.conf what monitor(s) is connected (CRT, LCD, NONE, etc.).  You might want to look into that as well.

---

### Post by FooSoft on 2007-03-08
That worked perfectly! Thanks a lot :)

---

