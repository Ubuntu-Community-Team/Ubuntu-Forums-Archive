---
title: "Acer X183h 1366x768 custom resolution"
date: 2010-06-25
forum: Desktop Environments
---

### Post by A Zenful Person on 2010-06-25
so, ive been searching for days and days trying to get this monitor to output in 1366x768 on Ubuntu 10.04. I knew it was possible, i did it late one night about a month back, but my system became unstable (not due to the resolution, i had setup a firewall to block all incoming till i unlock it, then another application to connect before i log in, and somehow it managed to lock out my keyboard on the login screen AND the recovery console, so i decided to just reinstall it :P)

Anyways, i found out exactly how to do it (for the Acer 183h that is). Ive spent about 48 hours total pouring through documents and found the documentation for nvidia-settings (easy find, i know, i was hoping to find an easy solution like what im typing up)

So, i figured out I could use Nouvaeu to get the proper settings (since all the modeline calcs dont do 1366, only 1360.) What i did was i went into the log file for the xorg,conf right after i installed, and in there somewhere near the middle it says what the timings are. 

```

mine were  ModeLine    "1366x768_60_0" 85.9 1366 1438 1626 1798 768 769 772 795 +hsync +vsync ) 

```
and i inputed that modeline into the monitor section, like so:
```

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Acer"
    ModelName      "x183h"
    HorizSync       30.0 - 80.0
    VertRefresh     55.0 - 75.0
    Option         "DPMS"
ModeLine    "1366x768_60_0" 85.9 1366 1438 1626 1798 768 769 772 795 +hsync +vsync
Option "IgnoreEDID" "True"
Option "UseEDID" "FALSE"
EndSection

```One of the two EDID commands is an old one, i just left it in there so when i was searching throught the xorg log i could find the section really quickly. 

(BTW, im not sure if these timings are 100 accurate until i reboot my livecd and check, but im sure thier pretty damn close, and my monitor hasent exploded yet :D if your worried bout it, grab your livecd, open your xorg.conf, and it "should" be in the monitor section)

Next, i had to input all the Options to not search for different modes into the device section:

```

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
Option      "ModeValidation"  "NoWidthAlignmentCheck, NoDFPNativeResolutionCheck"
Option "ExactModeTimingsDVI" "TRUE"
EndSection

```And finally, i had to set the screen to output the 1366x768, entering Modes "1366x768_60_0"

```


Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes       "1366x768_60_0"
    EndSubSection
EndSection


```in the Modeline and Modes section, its VERY important that you have it in the format i have it in. The Modeline name MUST be completely custom, by adding either letters or extra  _0.

And thats it!

Reboot, restart X, whatever (I prefer reboot, gives me time to ponder :) ) and you should be good to go. :)

(((((I know this may seem like a beginners knowledge type of thing, but im a beginner, pretty damn bright, and it still took me 4 days :D So, if this helps just one other person, ive done my part :))))))

Im also pretty sure this method will work with other wide screen monitors, as long as you get the timings off Nouveou via LiveCD or installing the driver.

---

### Post by roland_mai on 2010-06-29
Thank you so much. I bought a 185h yesterday and I couldn't get the resolution right with the nvidia cards. While I used whatever driver ubuntu recommended, your config works great!

---

### Post by 1366guy on 2010-12-17
Thank you so much for this post.  I've spent hours trying to get the nvidia driver to work with my monitor (a Dell IN1910N) at 1366x768 and this finally did the trick (I got the ModeLine off nouveau too).  I've registered in these forums just to say thanks and put this monitor model number here so Google can find this!

---

### Post by culkan82 on 2011-03-26
Thank You so much. I was trying 2 days to get my screen resolution and your post helped me.

---

