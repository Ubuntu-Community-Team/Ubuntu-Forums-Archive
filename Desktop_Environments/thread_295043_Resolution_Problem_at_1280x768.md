---
title: "Resolution Problem at 1280x768"
date: 2006-11-07
forum: Desktop Environments
---

### Post by SRParda on 2006-11-07
Hi,

I have installed Ubuntu 6.10.

At first I was happy , for first time 1280x768 was available at Gnome's "Change Screen Resolution"

But when selected screen flash continuosly , and monitor gives and advice like a change of resolution. It's like the frequencies are a little different.

The graphic card is a X300 PCI express, in a G965 Intel motherboard.
The monitor is a 30" LCD VideoSeven with 1280x768 real resolution (and downscaled 1280x1024 that works fine, but looks blurry because of LCD interpolation)

I have tried to modify the modeline in xorg.conf, but no modelines are displayed. Here is the content.

[SIZE="1"][COLOR="Gray"]
Section "Device"
	Identifier	"ATI Technologies, Inc. RV370 5B60 [Radeon X300 (PCIE)]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
	Option		"UseFBDev"		"true"  # Added this for try
EndSection

Section "Monitor"
	Identifier	"Viewsonic LTV30C"
	Option		"DPMS"
	HorizSync	30-65   # Added this trying to solve
	VertRefresh	50-75   # Added this trying to solve
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. RV370 5B60 [Radeon X300 (PCIE)]"
	Monitor		"Viewsonic LTV30C"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x768" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x768" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x768" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x768" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x768" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x768" "1024x768"
	EndSubSection
EndSection
[/COLOR][/SIZE]

I tried with dpkg-reconfigure xserver-xorg but not worked selecting H&V frequencies nor monitor resolutions.


I also noticed, that resolutions displayed in "Change Screen Resolution" are more than listed here (I deleted 800x600 and 640x480, but they appear anyway). Is any other configuuration in some place for ATI cards ? 
With Intel integrated graphics 1280x768 was not available to select so I installed the ATI card. 


If it can help , this are the monitor's manual specifications for 1280x768:
Resolution 1280x768, Refresh: 60Hz,
H: 47.776, V: 59.870, D.C:79.5Mhz, Pol.H: N, Pol.V: P
HORIZ: Sync With: 128, Back Porch: 192, Front Porch: 64, Total: 1664
VERT: Sync With: 7, Back Porch: 20, Front Porch: 3, Total: 798


Thank You for your help.

---

### Post by CatKiller on 2006-11-07
> **SRParda said:**
> Is any other configuuration in some place for ATI cards ? 

Yes. The Ati card.

You could try ```
 HorizSync 31-64 
 VertRefresh 56-85
``` per the manual, but I don't know if it will work. I've never tried to run a computer display exclusively through a TV - well, except for my BBC model B, but I don't suppose that counts ;)

You could also try the fglrx driver, but again, I don't know that it will work, particularly.

---

### Post by SRParda on 2006-11-08
I'm using Beryl with aixgl extensions , so for now, I can't install fglrx drivers.

I will try with the H & V freqs that you say.

Thank You

---

### Post by SRParda on 2006-11-09
Problem fixed. Now I have working my Videoseven LTV30C (reported as NEXGEN NL30) with a resolution of 1280x768.

Here is the solution for other persons looking for it.

In /etc/X11/xorg.conf:

[COLOR="Gray"][SIZE="1"]
Section "Monitor"
	Identifier	"Videoseven LTV30C"
        DisplaySize	643 386
        HorizSync	30-64
        VertRefresh	56-75
        Option	"DPMS"
        ModeLine	"1280x768" 81.00 1280 1344 1472 1664 768 771 778 798
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. RV370 5B60 [Radeon X300 (PCIE)]"
	Monitor		"Videoseven LTV30C"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1280x768"
	EndSubSection
EndSection
[/SIZE][/COLOR]

(only data for 1280x768 24bits, can have more resolutions of course) 

The route for a generic solution (instead of a try and error method) is in:
[http://xorg.freedesktop.org/wiki/FAQVideoModes](http://xorg.freedesktop.org/wiki/FAQVideoModes)
In that page explains how to obtain additional video modes supported by your monitor, reading the X log.

So you can construct the exact modeline for your monitor.

What I don't understand, is why the driver don't use this info OK, if the info about monitor capabilities is reported by the monitor and received by X (and work if it is specified manually).

---

