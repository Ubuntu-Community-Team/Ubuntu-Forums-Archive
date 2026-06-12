---
title: "[SOLVED] xubuntu screen resolution HELP"
date: 2006-06-12
forum: Desktop Environments
---

### Post by pappo on 2006-06-12
I can't get my Xubuntu display settings to go higher than 800x600.
I have loaded the latest Nvidia drivers with Automatix and everything appears to be working properly.
I did not have this problem when I was running ubuntu (gnome desktop) on this same PC.  In fact I ran Xfce under Ubuntu and had no problems.  This has only showed up since I installed Xubuntu.

Any ideas would be appreciated.

Regards,
Pappo

---

### Post by jvictor on 2006-06-12
add ur monitors h/v freq rates to /etc/X11/xorg.conf

```
Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       30-70
        VertRefresh     50-120
EndSection

```

replace it with ur actual values.. If not it can FRY ur monitor

IN addition to that add the resolution that ur monitor acn support in the depth section 

```
SubSection "Display"
                Depth           24
                Modes           "1152x864" "1024x768"
EndSubSection


```

Edit 
Can not acn :)

---

