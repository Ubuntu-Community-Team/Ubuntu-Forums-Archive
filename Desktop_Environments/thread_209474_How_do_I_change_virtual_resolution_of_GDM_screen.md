---
title: "How do I change virtual resolution of GDM screen?"
date: 2006-07-05
forum: Desktop Environments
---

### Post by jonboy99 on 2006-07-05
Hi all, 
am having problems with gdm screen resolution have a high res monitor (up to 2048 by1536) but only use 1152x864 for day to day use when not gaming.

Initially had problems with gdm running at the max resolution in xorg.conf and being unreadable, but fixed this by putting my preferred resolution first in the list under the display section of xorg.conf.

However now the gdm screen runs in a virtual screen where I have to scroll off the screen to see the login box and seesion manager bit at the bottom left.  This is confusing other users when they try and logon because the screen looks blank.

How do I set the virtual resolution to be the same as the actual resolution, but keep the higher resolutions available for gaming etc?

Have found some mention of "Virtual" entries for xorg.conf when googlin but no idea where in xorg.conf to put this and whether it will solve my problem.

Cheers

Jon

---

### Post by nolanjurgens on 2007-03-14
I realize this is reply is several months late, but this came up as the top link on Google when I was trying to figure this out myself, so I figured I'd reply here for the sake of others who happen across this thread.

In xorg.conf there is a section "Screen" and most likely a subsection "Display". In that subsection is where you put the "Virtual" settting. For example, here is mine with a virtual resolution set at 1280x1024.


```
Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NVIDIA Default Card"
    Monitor        "E90-4"
    DefaultDepth    24
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024@75" "1280x960@60" "1280x854" "1280x960@85" "1152x768@54" "1280x1024@60" "1152x864@75" "1280x960@75" "1024x768@43" "1400x1050@60" "1024x768@60" "1400x1050@75" "1024x768@70" "1600x1200@65" "1024x768@75" "1600x1200@60" "1024x768@85" "1792x1344@60" "832x624@75" "1856x1392@60" "800x600@60" "800x600@85" "800x600@75" "800x600@72" "800x600@56" "640x480@85" "640x480@75" "640x480@72" "640x480@60"
        Virtual     1280 1024
    EndSubSection
EndSection
```

Hope it helps.

---

### Post by Bluedog260 on 2007-03-27
This works a treat, thanks!

---

