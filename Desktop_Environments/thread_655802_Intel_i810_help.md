---
title: "Intel i810 help"
date: 2008-01-01
forum: Desktop Environments
---

### Post by kaymac12 on 2008-01-01
Hey everybody
I just installed ubuntu on my new laptop (Lenovo T61) and it's been working *almost* perfect - the one thing that is giving me trouble (I've been working at it all afternoon) is the graphics card. Ubuntu just wants t default to VESA framebuffer, and often times at startup I get a notice saying something along the lines of "Your computer is operating in low graphics mode" and an option to reconfigure. The problem is, No matter how many different ways I try to change xorg.conf (dpkg-reconfigure xserver-xorg, deconf, the GUI under System>Administration>Screens and Graphics) Ubuntu just falls back on vesa.

Interestingly enough, the graphics card worked fine upon a fresh install of ubuntu... right up until the automatic update.

a chunk of lspci:
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)

attached is the xorg.conf I wrote myself

Thanks in advance, and I apologize if this is already a documented bug

---

### Post by foolsh on 2008-01-02
try disabling 
    ```
#VideoRam	128000
#Option		"UseFBDev"		"true"
```
or try the intel driver
```
Driver		"intel"
```

hope this helps

---

