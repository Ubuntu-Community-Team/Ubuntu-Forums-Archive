---
title: "Need help with hi resolution &amp; font's sharpness"
date: 2009-10-24
forum: Desktop Environments
---

### Post by viluve on 2009-10-24
Hi hi,

FYI: I've googled around, but still found no satisfying solutions.

I'm trying to use the native resolution from my large LCD, which is 1920x1200, but I can't find the 1920x1200 option in the Display Preference (I've added 1920x1200 in the xorg.conf, and I've tried using the xrandr --fbmm 1920x1200). The highest resolution available is 1920x1080.

Currently, the font looks very blurry.. and hurt my eyes after several minutes of use. I'm wondering, do I need a special fonts for large monitors, or what fonts DPI should I be using (at the moment is 96dpi).

Thanks in advance for your help.

Extract of xorg.conf:
Section "Monitor"
        Identifier      "Configured Monitor"
        Modeline        "1920x1200_60.00"  193.25  1920 2056 2256 2592  1200 1203 1209 1245 -hsync +vsync
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        SubSection "Display"
                Modes   "1920x1200" "1920x1080" "1280x768"
                Virtual 3200 1080
        EndSubSection
EndSection

Section "Device"
        Identifier      "Configured Video Device"
EndSection

Section "ServerFlags"
        Option  "DontZap"       "False"
EndSection


Other details:
- Monitor: 24" LCD (Phillips 240BW)
- Installed video driver: 01:05.0 VGA compatible controller: ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE)
- OS: Karmic Koala
- Laptop: Compaq Presario V2000

---

### Post by Zorael on 2009-10-24
You really want to get it to native resolution, changing font dpi won't make up for the fuzziness you get by having it set to any lower. Adding the modeline as you did seems to me should be enough to unlock it, but whatwith how X has moved away from xorg.conf-reliance I don't know anymore.

If the EDID is invalid, perhaps it will listen to the modeline if you disable it completely with Option "IgnoreEDID" "true" (or ["UseEDID" "false"](http://www.mythtv.org/pipermail/mythtv-users/2007-April/175756.html), not sure, refer to Xorg.0.log to see if it complains about not understanding the option). If you disable EDID you'd have to add modes to get any resolutions, obviously.

The [wiki entry on X resolution configuration](https://wiki.ubuntu.com/X/Config/Resolution) suggests doing something like the following might also help;

```
aa@aa-desktop:/$ cvt 1920 1200 60
# 1920x1200 59.88 Hz (CVT 2.30MA) hsync: 74.56 kHz; pclk: 193.25 MHz
Modeline "1920x1200_60.00"  193.25  1920 2056 2256 2592  1200 1203 1209 1245 -hsync +vsync
aa@aa-desktop:/$ cvt 1680 1050 60
# 1680x1050 59.95 Hz (CVT 1.76MA) hsync: 65.29 kHz; pclk: 146.25 MHz
Modeline "1680x1050_60.00"  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync
aa@aa-desktop:/$ xrandr --newmode "1920x1200_60.00"  193.25  1920 2056 2256 2592  1200 1203 1209 1245 -hsync +vsync
aa@aa-desktop:/$ xrandr --newmode "1680x1050_60.00"  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync
aa@aa-desktop:/$ xrandr --addmode DVI-1 "1920x1200_60.00"
aa@aa-desktop:/$ xrandr --addmode DVI-0 "1680x1050_60.00"
```
A neater solution (the driver still listens to your screen's EDID), but a per-session setting. If it works, make it persistent like so;
> Both KDM and GDM have startup scripts that are executed when X is initiated. For GDM, these are in /etc/gdm/, while for KDM this is done at /etc/kde4/kdm/Xsetup. In either case, you can paste in an xrandr command line string into one of these scripts.

This process requires root access and mucking around in system config files, but will take effect earlier in the startup process than using .xprofile, and will apply to all users including the login screen.

---

### Post by viluve on 2009-10-25
Thanks Zorael,

I've managed to add 1920x1200 using your method. 

But still doesn't resolve the fuzziness of the fonts. I hope Ubuntu will get better on this in future versions, this never an issue with Windows.

FYI: 1920x1200 is the native resolution for my LCD monitor.

---

### Post by Zorael on 2009-10-25
In what way do you feel they are fuzzy? Since it's an LCD, have you set up subpixel rendering with hinting? It should be in the font section of whatever environment you're using. (System Settings -> Appearance in KDE)

Setting it to RGB subpixel rendering with full hinting should make them more... precise. Some like it set to "best shapes" though (in GNOME).

See [http://newtoubuntu.wordpress.com/tag/subpixel-smoothing](http://newtoubuntu.wordpress.com/tag/subpixel-smoothing).

---

