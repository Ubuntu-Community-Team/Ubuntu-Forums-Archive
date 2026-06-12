---
title: "New Toshiba Laptop using ATI X1200 with visual effects - &quot;Could not be enabled.&quot;"
date: 2007-11-22
forum: Desktop Effects &amp; Customization
---

### Post by Roasted on 2007-11-22
Just simply that. I went into preferences - appearance to enable the visual effects and both options, the basic effects and advanced effects said "Could not be enabled." Nothing else. Why??

---

### Post by patryk77 on 2007-11-22
make sure you installed the ATI restricted drivers (System/ Admin/ Restricted drivers manager)

make sure you have the compiz packages installed in the synaptic package manager

And make sure that your card is rendering 3d preoperly. In the terminal:

```
LIBGL_DEBUG=verbose glxinfo | grep render
```

---

### Post by Roasted on 2007-11-22
direct rendering - No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
OpenGL renderer string : Mesa GLX indirect



ehh???

---

### Post by patryk77 on 2007-11-22
[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)

I followed this guide to get everything working properly, and other than problems with OpenGL rendering in other applications (which is known not to work with compiz enabled) and video output (for which there is a workaround) it's beautiful....

First, make sure that you are not using XGL (if installed, uninstall the "xserver-xgl" package using synaptic package manager) as it disables AIGLX, which is what you want to use.

Reboot, check again. If you still see Mesa as the renderer, then follow that guide to install the latest driver (note that ATI just released a new driver yesterday, so you will have to change the filenames accordingly)

---

### Post by Feanor3 on 2008-01-05
I am having this same issue. I suspect it is because the x1200 isn't supported by the proprietary driver.  

glxinfo
```

:~$ glxinfo | grep render
direct rendering: Yes
OpenGL renderer string: ATI Radeon X1200 Series

```
fglrxinfo
```

:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon X1200 Series
OpenGL version string: 2.1.7170 Release

```

Get that same error when I try to enable desktop effects.

I had it working without AIGLX, but that solution is subpar.

---

### Post by mauddib on 2008-01-07
Sorry to hijack your thread but does any of you x1200 users have 100% cpu usage when running any opengl application? I guess with 2d only this is normal but with direct rendering it shouldn't use any cpu..?

---

