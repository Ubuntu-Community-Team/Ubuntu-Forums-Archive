---
title: "Lenny-Testing on AMD64 w/22&quot; widescreen xorg.conf"
date: 2008-11-26
forum: Debian
---

### Post by stream303 on 2008-11-26
Wow - just installed Lenny Testing after having been away from it since Sarge.  Nice work!

Running an HP Pavilion Slimline AMD64 with 22" Viewsonic VX2235wm monitor at 1680x1050.  The only thing I had to do was force my xorg.conf to recognize the larger screen since it just came up as 800x600.

Using the 2D nvidia "nv" driver and loving it.  I used to have to mess around with fonts in Debian, but now - man what an improvement using the Liberty sans font.

Anyway, here's my manually-edited /etc/X11/xorg.conf to force 1680x1050 with the open-source 2D nv driver for the ViewSonic VX2235wm:

```

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"nv"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
	HorizSync	30-82
	VertRefresh	50-85
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
		SubSection	"Display"
		Depth		24
		Modes		"1680x1050"
		EndSubSection
EndSection

```

About the only other major thing I did was change the font dpi to 100 in appearances, since that calculates out better than the default of 96 for the larger screen before I made any small adjustments to the fonts themselves.  Way to go Debian!

---

