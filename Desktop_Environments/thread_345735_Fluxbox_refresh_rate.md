---
title: "Fluxbox refresh rate"
date: 2007-01-24
forum: Desktop Environments
---

### Post by tigerpants on 2007-01-24
Hi

Everytime I log into fluxbox the refresh rate is at 75mhz - in gnome i have the default at 60hmz as its better for my monitor. Is there a file I can edit that can lock the refresh rate at 60mhz? I cant see any option in the xorg.conf file to do this.

Thanks

---

### Post by yabbadabbadont on 2007-01-24
From /etc/X11/xorg.conf:
```
Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       30-69
        VertRefresh     50-80
        DisplaySize     306 230
EndSection
```
Change (or add) your VertRefresh setting.  It is the refresh rate in Hz.

---

### Post by tigerpants on 2007-01-25
Cheers man.

---

