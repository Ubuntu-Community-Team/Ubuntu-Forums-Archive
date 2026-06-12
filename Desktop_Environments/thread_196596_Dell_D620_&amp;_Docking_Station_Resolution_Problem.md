---
title: "Dell D620 &amp; Docking Station: Resolution Problems"
date: 2006-06-14
forum: Desktop Environments
---

### Post by MystaMax on 2006-06-14
I have a Dell D620 laptop, which I use occasionally w/ a docking station @ work. The issue I am having is that @ the login screen, the resolution doesn't seem to fit correctly. The laptop has a default resolution of 1400x900, and the monitor connected to my docking station is a 19 inch w/ a native resolution of 1280x1024. At the login screen, if I move my mouse from the top of the screen to the bottom, I can see the screen slide to show the rest of the screen. As if the resolution was too large for the screen.

I adjusted my xorg.conf file by adding the 1280x1024 to the subsection w/ 24bit Depth. like so:

```
SubSection     "Display"
        Depth       24
        Modes      "1440x900" "1280x1024"
    EndSubSection
```

My first question, is how do i fix it the login screen size so it fits properly while docked in the docking station w/ the 19 inch?  Secondly, Is it possible to have the computer autoconfigure so that when I'm using the laptop by itself, it'll default to 1440x900, and when I'm using my docking station (w/ the 19 inch) it'll default to 1280x1024. Thanks.

---

### Post by MystaMax on 2006-06-17
Ok, it looks like the computer is defaulting to the correct resolution now. But, my login screen still does not fit on my screen. I have to scroll down to see the Options. Any ideas?

---

### Post by fast1 on 2006-06-19
Try to add the size of your external display in the monitor section. Mine is

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        DisplaySize     433    270
        HorizSync       30-93
        VertRefresh     56-85
        ModeLine       "1680x1050" 147.1 1680 1784 1968 2256 1050 1051 1054 1087 -hsync +vsync
EndSection

---

