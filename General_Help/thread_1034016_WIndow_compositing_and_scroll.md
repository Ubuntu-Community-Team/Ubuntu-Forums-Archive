---
title: "WIndow compositing and scroll"
date: 2009-01-07
forum: General Help
---

### Post by Ranjan_Hegde on 2009-01-07
I have ubuntu 8.10 on inspiron 9200 laptop. When I enable window compositing (compiz or gnome) scrolling is lags. (firefox, file browser etc). It is probably not  a compiz bug as I have almost the identical issue when I turn of gnome window compositing. Any suggestion on how to fix this is greatly appreciated.  COMPIZ otherwise works great. I am using open source radeon driver.

Here are the details. 

direct rendering: Yes

VGA compatible controller: ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]

xorg.conf

Section "Device"
        Identifier      "Configured Video Device"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection

---

### Post by Ranjan_Hegde on 2009-01-11
Following works like a charm..

        Option "AccelMethod" "EXA"
        Option "MigrationHeuristic" "greedy"

---

