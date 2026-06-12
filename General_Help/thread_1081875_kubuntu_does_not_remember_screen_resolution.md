---
title: "kubuntu does not remember screen resolution"
date: 2009-02-27
forum: General Help
---

### Post by nightgale on 2009-02-27
Hi,

I've a problem on my kubuntu 8.10, that it does not remember my 2nd monitor's resolution.
I'm using a laptop with a LCD connected. The LCD maximum resolution is 1280*1024 while the laptop is 1024*768. In System settings > Display Kubuntu could recognize both monitor correctly. As soon as I clicked Display the resolution of LCD is refreshed to 1280*1024. But as soon as KDE restarts in the logon window the resolution of LCD is changed to 1024*768.

This problem does not happen with ubuntu desktop(gnome). Seems it "remembers" the resolution easily.

I checked xorg.conf it is like this:

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


Can anyone help me with this issue?

Thanks a lot in advance.

---

