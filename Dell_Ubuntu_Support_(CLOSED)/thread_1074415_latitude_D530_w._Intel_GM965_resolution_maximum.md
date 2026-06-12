---
title: "latitude D530 w. Intel GM965 resolution maximum"
date: 2009-02-19
forum: Dell Ubuntu Support (CLOSED)
---

### Post by ubu4all on 2009-02-19
Hi,

I have a DELL latitude D530 with the intel GM965 graphics chipset. My laptop monitor can do 1400x1050 without problems but I also have an external DELL 22" wide LCD and cannot raise the resolution. The best it can do is 1400x1050 as well. 
I know that this graphics chipset can do 1600x1024@60Hz, but I have no clue on how to configure it.

Here's the output from "lspci"

00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)


and my /etc/X11/xorg.conf is pretty much empty. Here's the putput as well:

Section "Device"
        Identifier      "Configured Video Device"
        Option          "UseFBDev"              "true"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection




Thanx!

---

