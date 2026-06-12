---
title: "screen resolution"
date: 2009-06-23
forum: General Help
---

### Post by andrew_g on 2009-06-23
Hi, just installed ubuntu 9.04, works, but screen res is limited to 800x480 max.

Heres my xorg.conf file.

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

Appreciate any help - Thanks

---

