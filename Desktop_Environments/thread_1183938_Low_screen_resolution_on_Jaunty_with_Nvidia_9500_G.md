---
title: "Low screen resolution on Jaunty with Nvidia 9500 GT"
date: 2009-06-10
forum: Desktop Environments
---

### Post by Cordate on 2009-06-10
I have a fresh install of Jaunty and am attempting to use the v. 180 nvidia proprietary driver (v. 173 only offered me two choices of resolution, both under 800x600). The monitor is a ViewSonic G90fB with a maximum resolution up above 1600x1200 somewhere, I've never sought to go higher.

Unlike previous versions of Ubuntu which tended to start me at 640 x 400 pixels (or lower >.<) this time I start out at a somewhat-reasonable 1024 x 786. But I still can't seem to get anything higher than 1152 x 864 and under Intrepid I had this system comfortably at 1600x1200. I've been mucking about with xorg.conf for a few days without getting even 1280x1024 to work, and xrandr commands seem to only succeed in getting the screen to quickly blink- the resolution never changes.

Here is a copy of my current xorg.conf, with modelines added, though the system seems to be ignoring them completely. The nvidia x server settings app doesn't seem to recognize the monitor.

```
Section "Monitor"
	Identifier	"Configured Monitor"
	Modeline "1600x1200@73" 235.58 1600 1632 2520 2552 1200 1223 1237 1261
	Modeline "1280x1024@85" 188.40 1280 1312 2024 2056 1024 1043 1057 107
	Modeline "1024x768@85" 100.94 1024 1056 1432 1464 768 782 793 807
	Option          "PreferredMode" "1600x1200@73"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
    SubSection "Display"
        Depth           24
        Modes   "1600x1200@73" "1280x1024@85" "1024x768@85"
    EndSubSection
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection

```

Hopefully someone can help! I am considering going back to Intrepid, though it's a lot of lost hours in setting things back up again.

---

### Post by gasco on 2009-06-10
Don't know if this will help you, but I had a problem with an old LCD monitor that only uses RGB.
I have an 9800 GT and two LCD monitors conected: one 1920x1080 HDMI that works perfect when I installed Ubuntu 9.04, but the other a 1280x1024 (only RGB) worked at 1024x768.

I think (not sure), the problem was that the Graphics card read the EDID by the HDMI, but the older monitor don't comunicate its Refresh rate to the graphics card, and the driver uses a lower resolution and frequency to prevent damages.

I only had to add this lines to the xorg.conf

```

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "CRT-1"
    HorizSync       30.0 - 80.0
    VertRefresh     55.0 - 75.0
EndSection

```Of course, if you try this, _You have to modify H - V rates with your monitor rates_.
...
I found your Monitor Specs, 
Frequency     Fh: 30 &#8211; 97kHz Fv: 50 &#8211; 160Hz
So, your lines would be
```

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Viewsonic"
    ModelName      "G90fB"
    HorizSync       30.0 - 97.0
    VertRefresh     50.0 - 160.0
EndSection

```
but please, Check that in your manual

Javier

---

### Post by Cordate on 2009-06-10
Thanks for the tip, gasco. I had tried specifying the Horiz and Vert sync rates previously but without luck. I settled down to some slow (and sensible :/) change-one-thing-and-reboot poking at xorg and found that specifying the horizsync was causing the monitor to switch off when I got to the login. Thinking that might indicate a modeline that wasn't quite to the monitor's liking, I commented out a few till I found one it liked. Now nvidia settings seems to understand what to do and offers me the proper host of resolutions all the way up to 2048x1536. If I ever get bionic eyes, I might give that a go. :p

I also added 

```
Option "IgnoreEDID" "true" 
```

to my device section, but I'm not sure if that helped or not. Maybe I'll fiddle with it later, but right now I am very happy to have things sorted out and I can go work on getting actual work done!

---

