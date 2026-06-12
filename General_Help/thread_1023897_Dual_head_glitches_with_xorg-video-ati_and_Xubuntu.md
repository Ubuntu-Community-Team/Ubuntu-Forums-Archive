---
title: "Dual head glitches with xorg-video-ati and Xubuntu 8.10?"
date: 2008-12-28
forum: General Help
---

### Post by Digiku on 2008-12-28
I'm trying to work dual head support on the open source "ati" driver using Xubuntu 8.10 and my ATI Radeon x1300 (r515) card. Dual head works perfectly on radeonhd, but when I try it on ati, the secondary display is unusable. It shows the mouse pointer fine, but the desktop is garbled and windows aren't displayed. Here's a screenshot of my problem:

[[IMG]http://img511.imageshack.us/img511/3928/opensourceatidualheadgltu6.th.jpg[/IMG]](http://img511.imageshack.us/my.php?image=opensourceatidualheadgltu6.jpg)

Any idea of what's going on, and how I can fix this?

My Xorg.conf:
```

Section "Device"
	Identifier	"Configured Video Device"
	Driver "ati"
	Option "AccelMethod" "exa"
EndSection

Section "Monitor"
	# Only the primary monitor, DVI-0, is defined here; Xrandr recognizes the other.
	Identifier	"DVI Digital Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"DVI Digital Monitor"
	Device		"Configured Video Device"
	SubSection "Display"
		Depth 24
		Modes "1680x1050" "1280x1024" "1024x768" "800x600"
		Virtual 2960 1050 # For combined 1680x1050 + 1280x1024 desktop -- otherwise, Xrandr complains.
	EndSubSection
EndSection

```

My Xrandr commands, which do the actual dual head stuff:
```

xrandr --output DVI-0 --mode 1680x1050
xrandr --output VGA-0 --mode 1280x1024
xrandr --output VGA-0 --right-of DVI-0

```

---

### Post by CHaoSlayeR on 2009-01-10
Hi there,

for your card the ati driver is not the best choice. At work I have a machine with an X1350 up and running with the radeon driver. I also struggled a bit to get it up but I could post my xorg.conf in case you have no luck.

On that machine I even have KDE4 up and running with all effects available and running smoothly. Also X-Video is accelerated nicely. As I never saw any glitches give it a try.

C]-[aoZ

---

