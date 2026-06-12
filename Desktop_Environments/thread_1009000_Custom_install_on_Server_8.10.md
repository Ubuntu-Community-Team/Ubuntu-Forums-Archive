---
title: "Custom install on Server 8.10"
date: 2008-12-12
forum: Desktop Environments
---

### Post by atiflz on 2008-12-12
I installed Server 8.10 x64 version and then manually(apt-get) installed xdm and xfce.

The problem is, the screen updates very slowly. The lag is disturbing whenever I move a window or scroll in firefox. I'm missing something but i can't find out what. Any ideas?

 Here's my xorg.conf

Section "Device"
        Identifier      "Configured Video Device"
        Driver          "fglrx"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        DefaultDepth    24
EndSection

Section "Module"
        Load "glx"
EndSection

---

### Post by renzokuken on 2008-12-12
do you have an ATI chipset in your server then? post the output of 

```
lspci -v
```

you could try using the "vesa" driver instead of "fglrx"

---

### Post by atiflz on 2008-12-15
I already made sure I have an ATI chip:
~$ lspci -v
...
 VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 3470
...

---

