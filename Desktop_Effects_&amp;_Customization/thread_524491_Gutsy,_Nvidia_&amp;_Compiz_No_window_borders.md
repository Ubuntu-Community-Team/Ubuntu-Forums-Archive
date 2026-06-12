---
title: "Gutsy, Nvidia &amp; Compiz: No window borders"
date: 2007-08-13
forum: Desktop Effects &amp; Customization
---

### Post by el3ktro on 2007-08-13
I have installed Gutsy on two of my machines, one with an Intel GMA 950 and one with an Nvidia GeForce 6200. On the Nvidia machine, I have installed nvidia-glx-new and when I try to run Compiz (compiz --replace) it would start and the effects would work, but there are no windows borders. This is the output from compiz --replace:

```

Checking for Xgl: not present. 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking for nVidia: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (wall) - Error: Couldn't create cairo context for switcher
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (wall) - Error: Couldn't create cairo context for switcher
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (wall) - Error: Couldn't create cairo context for switcher
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (wall) - Error: Couldn't create cairo context for switcher
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (resizeinfo) - Warn: Bind Pixmap to Texture failure
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (resizeinfo) - Warn: Bind Pixmap to Texture failure
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32

```

On the Intel GMA 950 Compiz worked right from the start. Is this a known problem with Compiz & Nvidia?

---

### Post by InfinityCircuit on 2007-08-13
On all of my Gutsy machines I have had to install an xgl server to get Compiz Fusion to work with window borders and without crashing, which you don't appear to have.  You could try to follow this document: [https://help.ubuntu.com/community/CompositeManager/Xgl](https://help.ubuntu.com/community/CompositeManager/Xgl)

What happened if you tried compiz --replace --indirect-rendering?

---

### Post by mmcev106 on 2008-01-25
I had this problem once, I tried all the suggested configuration changes to no avail.  I ended up simply reloading the nvidia kernel module, and everything worked perfectly with the default xorg.conf spit out by the nvidia-xconfig command.  So that's worth a try.  If you don't know how to reload that module manually, a reboot will do it.  Good luck.

---

