---
title: "how to test if 3d is running on ati x850xt?"
date: 2007-11-09
forum: Gaming &amp; Leisure
---

### Post by scaramoche on 2007-11-09
Ok,  make a long story short, im attempting to install wow, but i cant tell if it's the video driver, or wine?  so is there a way to test my 3d in linux?

hardware
ati x850xt
amd 64 3800

Ive read the ubuntu setup for both wow and driver install.

for 
fglrxinfo 
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON X850 XT
OpenGL version string: 2.0.6473 (8.37.6)

what else can i do?

---

### Post by Steve1961 on 2007-11-09
To check if you have 3d working type the following:
```

glxinfo | grep rendering
```

If the output is:

```
direct rendering: Yes
```

then all is well

---

### Post by Melhisedek on 2007-11-09
> **Steve1961 said:**
> 
If the output is:

```
direct rendering: Yes
```

then all is well

What can you do if the output is no? I have the ATi restricted driver enabled but output is still no :(

---

### Post by Steve1961 on 2007-11-09
I've never had an ATI card, but have you tried [envy]("http://albertomilone.com/nvidia_scripts1.html")?

---

### Post by cajunlibra on 2009-03-14
I did the following:

glxinfo | grep rendering
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
root@ROSSLAPTOP:~# LIBGL_DEBUG=verbose fglrxinfo
libGL: XF86DRIGetClientDriverName: 8.54.3 fglrx (screen 0)
libGL: OpenDriver: trying /usr/X11R6/lib/modules/dri/fglrx_dri.so
libGL error: dlopen /usr/X11R6/lib/modules/dri/fglrx_dri.so failed (/usr/X11R6/lib/modules/dri/fglrx_dri.so: cannot open shared object file: No such file or directory)
libGL error: unable to load driver: fglrx_dri.so
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI MOBILITY RADEON X300
OpenGL version string: 1.4 (2.1.8087 FireGL Release)

Segmentation fault


I used Envy to install the driver.  It worked just fine right before I attempted to use the proprietary driver. Since then it's jacked up. I had awn working wonderfully.I have uninstalled awn, compiz, and ati and then reinstalled it all again with no luck.

Running Intrepid, I installed Kubuntu Hardy but use Gnome most of the time.

How do I remove all ATI drivers currently on my system, including any proprietary drivers, so that the one that loads from the kubuntu live CD loads.

Managed to solve.

---

