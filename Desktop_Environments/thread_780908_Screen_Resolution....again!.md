---
title: "Screen Resolution....again!"
date: 2008-05-03
forum: Desktop Environments
---

### Post by rayj00 on 2008-05-03
I had this problem on 6.10 Edgy but forgot how I fixed it.

I got the Gateway 22" LCD model FPD2275W. I take it the 75 is refresh rate?
Anyway, the max resolution should be 1680x1050 but when I change the Monitor Resolution Settings to this, I am missing the left 5" of display. The screen is shifted right for some reason. 

I had this same problem with 6.10. I vaguely remember adding this resolution to a file but I can't remember which file it was. I recall the file had a list of resolutions in it....

Help!!!

Ray

---

### Post by z0mbie on 2008-05-03
You can try manually entering the refresh rates in */etc/X11/xorg.conf*:

Under **"Monitor"** section add this before **EndSection**:

```
    HorizSync       64.674 - 67.8
    VertRefresh     59.883 - 60.0
    Option         "DPMS"
```

-Please make sure these specs are correct with your monitor's model number. Then restart Xorg by pressing **Ctrl+Alt+Backspace**.

---

### Post by rayj00 on 2008-05-04
The specs say Max Sync Rate (V X H) 60 Hz X 64.8 KHZ

What do I put in xorg.conf?

---

### Post by rayj00 on 2008-05-04
Ok, here's what I did to xorg.conf:

Under Section Monitor I added the results of doing the gtf command:

ModeLine "1680x1050_60.00" 147.14 1680 1784 1968 2256  1050 1051 1054 1087 -HSync +Vsync

Rebooted, the screen flashes a bunch of garbage horizontal lines then shows the Ubuntu 8.04 window with the bird. Also, the screen is shifted right about 5 inches.

Went to preferences and it shows 1680 x 1050 60 Hz is selected. 
Had to change to 1280 x 1024 to get the whole screen.

Went back to xorg.conf and did this:

Section "Screen"
Identifier "Default Screen"
Device "Configured Video Device"
Monitor "Configured Monitor"
DefaultDepth 24
SubSection "Display"
Depth 24
Modes "1680x1024"
EndSubSection
EndSection

Rebooted.

I no longer have 1680x1050 as a choice in preferences.
The highest is 1400x1050? At this resolution, the screen is shifted right
by 5 inches.

Also if I pick any of the other resolutions in preferences, I get full screen, but verticle lines every inch and a half or so....from top to bottom. 

This is driving me nuts! I know it works....

Why can't an update or even new install grab the existing xorg.conf and use it? That would eliminate these types of problems???

Anyway...HELP!!!!!

Thanks

Ray

---

