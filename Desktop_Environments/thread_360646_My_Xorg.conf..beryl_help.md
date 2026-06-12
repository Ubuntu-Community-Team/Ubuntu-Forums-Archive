---
title: "My Xorg.conf..beryl help"
date: 2007-02-13
forum: Desktop Environments
---

### Post by GQed76 on 2007-02-13
Im trying to get Berly to work right with my nvidia card. I get no window borders or maximize/minimize buttons. I have a Geforce 7600.

This is what my xorg says.

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       28.0 - 84.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "nVIdia Geforce 6600"
    Driver         "nvidia"
EndSection


It has the wrong card and not very much info.  Ive installed the driver myself...now i can run WoW in wine and Cedega so it works, but im not sure its running correctly after seeing this,,,,any ideas?

---

### Post by Sqwishy on 2007-02-13
Look in your notification area, find the beryl icon. Right click and make sure emerald is selected for your window decorator and then if it is click restart windows decorator.

---

### Post by lawsondba on 2007-04-29
I have the same problems, at least with the borders, also I can not move the windows.
How did you install the driver manually?

My Device section is as follows:
Section "Device"
    Identifier     "NVIDIA Corporation NVIDIA Default Card"
    Driver         "nvidia"
EndSection


> **GQed76 said:**
> Im trying to get Berly to work right with my nvidia card. I get no window borders or maximize/minimize buttons. I have a Geforce 7600.

This is what my xorg says.

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       28.0 - 84.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "nVIdia Geforce 6600"
    Driver         "nvidia"
EndSection


It has the wrong card and not very much info.  Ive installed the driver myself...now i can run WoW in wine and Cedega so it works, but im not sure its running correctly after seeing this,,,,any ideas?

---

