---
title: "xorg.conf and &quot;Screen Resolution&quot;"
date: 2008-09-07
forum: Desktop Environments
---

### Post by jem on 2008-09-07
Using the "System -> Preferences -> Screen Resolution" utility, I've set my screen to 1400x1050, which works well for me on my big old CRT monitor.

Oddly enough, though, this resolution does not appear in my xorg.conf file, and the available resolutions under the "Screen Resolution" utlity bear little resemblancs to those listed in the "Screen" section of my xorg.conf.

Do "Screen Resolution" and xorg.conf have any relationship at all?


Jim McCauley

---

### Post by cdtech on 2008-09-07
Yes they do. What do you have in your config file:
```
Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Option		"AddARGBGLXVisuals"	"True"
	Option          "NoLogo" "True"
	Defaultdepth	24
	SubSection     "Display"
        Virtual     **1440 900**
        Depth       24
        Modes      "**1440x900**" "1920x1440" "1920x1200" "1856x1392" "1680x1050" "1440x900@60" "1400x1050"
    EndSubSection
EndSection
```
The first listed should be your default resolution.

---

