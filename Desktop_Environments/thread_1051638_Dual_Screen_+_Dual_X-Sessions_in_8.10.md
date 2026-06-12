---
title: "Dual Screen + Dual X-Sessions in 8.10"
date: 2009-01-26
forum: Desktop Environments
---

### Post by techman83 on 2009-01-26
Hi All,

I have an IBM T60 with an Intel GMA 943 and a Docking Station. Now since 6.06 I have been running Dual X sessions, as I like to separate my work spaces. Now with 8.04 It was pretty straight forward, comment out the Xinerama option and Hey presto, 2 separate sessions. Now with more Automation in Intrepid, my old xorg.conf fails and no matter what I do by hand, it doesn't seem to honour my Xinerama False setting.

Any ideas would be much appreciated as 8.10 seems very snappy compared to 8.04 and I've grown fond of it over the weekend!

```
Section "Device"
	Identifier	"Configured Video Device"
	Screen 0
	Option		"UseFBDev"		"true"
        Option          "MonitorLayout" "CRT,LFP"
EndSection

Section "Device" # 
        Identifier      "device1"
        Screen  1
        Option          "MonitorLayout" "CRT,LFP"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "InputDevice"
        Identifier      "Keyboard0"
        Driver          "kbd"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
        Option          "CoreKeyboard"
EndSection

Section "InputDevice"
        Identifier      "Mouse0"
        Driver          "mouse"
        Option          "CorePointer"
EndSection


Section "Monitor"
        Identifier      "External Monitor"
        Vendorname      "Samsung"
        Modelname       "Samsung SyncMaster 204T/204Ts/214T,SyncMaster Magic CX201Ts(Digital)"
        Horizsync       30-81
        Vertrefresh     56-75
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
        SubSection "Display"
        Depth 24
        Virtual 2624 1200
	EndSubSection
EndSection

Section "screen" # 
        Identifier      "External Monitor"
        Device          "device1"
        Defaultdepth    24
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
	screen 0 "Default Screen" 
#	screen 1 "External Monitor" 
	screen 1 "External Monitor" rightof "Default Screen"
	InputDevice "Keyboard0" "CoreKeyboard"
	InputDevice "Mouse0" "CorePointer"
EndSection

Section "ServerFlags"
	Option "Xinerama" "0"
EndSection

```

---

### Post by pnutzh4x0r on 2009-02-05
You were probably using the old i810 (xserver-xorg-video-i810) driver which supported dual xsessions (aka zaphoid mode).  The new intel driver (xserver-xorg-video-intel) does NOT support this mode and this is why your old configuration does not work.  It may be possibe to still use the old driver by setting 

Driver          "i810"

under the Device section options. 

The following page may give you more information:

[http://www.thinkwiki.org/wiki/Xorg_RandR_1.2](http://www.thinkwiki.org/wiki/Xorg_RandR_1.2)

---

### Post by techman83 on 2009-02-10
Unfortunately using the i810 driver doesn't work, which from memory is probably why the old config doesn't work.

Quite a shame, I will probably have to revert back to 8.04 at this rate. Pity 8.10 is lightning fast in comparison. :(

---

### Post by techman83 on 2009-02-10
Noted that the package wasn't installed, but still no good. Attached log, seems that it doesn't detect the device with that driver. Quite annoying that a feature gets dropped.

---

### Post by techman83 on 2009-02-11
Well for the moment, I'll have to suffer with the Giant desktop it seems. But at least I'm not wasting screen real estate now. Got a script that can tell when I'm at work and will map certain shares, so just added:

```

        xrandr --output LVDS --auto --output VGA --auto --right-of LVDS
        gconftool --type int --set /apps/panel/toplevels/top_panel_screen0/monitor 1
        gconftool --type int --set /apps/panel/toplevels/bottom_panel_screen0/monitor 1

```

Which enables the external screen and moves the Panels back to the internal LCD.

I also cut the xorg.conf back to:
```
ection "Screen"
	Identifier	"Configured Screen Device"
	Device	"Configured Video Device"
	SubSection "Display"
		Virtual	2624 1200
	EndSubSection
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

```

Here's hoping 9.04 will have some better drivers. It seems the October releases are the test ground for the April releases, if 8.10 is anything to go by, 9.04 is really gunna kick serious butt.

---

