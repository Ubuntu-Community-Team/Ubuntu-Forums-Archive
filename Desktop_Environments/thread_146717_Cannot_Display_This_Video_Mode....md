---
title: "Cannot Display This Video Mode..."
date: 2006-03-18
forum: Desktop Environments
---

### Post by chugru on 2006-03-18
Hi, All...

I need help if I am to get my display working properly...

Graphics Card = Radeon 9200 SE (RV280)

Monitor = DELL E173FP (LCD)

Snippit from my **/etc/X11/xorg.conf:**
```
Section "Monitor"
        Identifier   "Monitor"
        HorizSync    31.0 - 80.0
        VertRefresh  56.0 - 75.0
        Option          "DPMS"

EndSection
Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies, Inc. Radeon 9200 SE (RV280)"
        Monitor         "Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth     16
                Modes     "1280x1024@75Hz" "1280x1024" "1024x768"
        EndSubSection
EndSection

```Whenever I reboot, I end up with a very long delay as X window tries to load and the followind message shows:```
Cannot Display This Video Mode
```I have tried, without success, various display settings from within KDE as well as in **xorg.conf**

It's obvious I don't really know what to do to fix this problem.:( 

I could definitely use some expert help!

Thanks...

---

### Post by xmastree on 2006-03-19
Well, I've never seen Hz mentioned in the "screen" section of xorg.conf as it appears in yours:

Modes     [COLOR="Red"]**"1280x1024@75Hz"**[/COLOR] "1280x1024" "1024x768"

I would try removing that bit in red.

---

### Post by chugru on 2006-03-19
[QUOTE=xmastree]Well, I've never seen Hz mentioned in the "screen" section of xorg.conf as it appears in yours:

Modes     [COLOR="Red"]**"1280x1024@75Hz"**[/COLOR] "1280x1024" "1024x768"

I would try removing that bit in red.[/QUOTE]

Thanks for your suggestion. I tried what you proposed, but it made no difference. The monitor still hangs, as before, with the message: **Cannot Display...**.

Edit: After additional modification the problem went away: ```
DefaultDepth    16
```

Thanks!

---

