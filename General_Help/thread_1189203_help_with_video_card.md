---
title: "help with video card"
date: 2009-06-16
forum: General Help
---

### Post by Techfizzle on 2009-06-16
Hi Everyone
I have a  [SiS] 65x/M650/740 videocard intergrated into my motherboard 

i have had no luck finding a driver for this

someone said i needed to edit the xorg.conf under driver

but this is my xorg file... kinda blank looking

help please

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

