---
title: "compiz-fusion extra plugins 0.6.2 or 0.6.3, how!?"
date: 2007-12-03
forum: Desktop Effects &amp; Customization
---

### Post by Hawk__0 on 2007-12-03
REALLY confused...
first off, this is what output i get from:
compiz --version
```
steve@steve:~/Desktop$ compiz --version
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0391 (rev a1) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1440x900) to maximum 3D texture size (4096): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting emerald
[B]compiz 0.6.3
[/B]
```
And this is the info i get from dpkg -l | grep compiz
```

ii  compiz-bcop                                0.6.100~git20070906+3v1ubuntu0       Compiz option code generator
ii  compiz-core                                1:**0.6.2**+git20071119-0ubuntu1~gutsy1  OpenGL window and compositing manager
ii  compiz-dev                                 1:0.6.2+git20071119-0ubuntu1~gutsy1  OpenGL window and compositing manager - deve
ii  compiz-fusion-plugins-extra                0.6.0+git20071121-0ubuntu1~gutsy1    Collection of extra plugins from OpenComposi
ii  compiz-fusion-plugins-main                 0.5.2+git20070928-0ubuntu2           Collection of plugins from OpenCompositing f
ii  compiz-gnome                               1:0.6.2+git20071119-0ubuntu1~gutsy1  OpenGL window and compositing manager - GNOM
ii  compiz-plugins                             1:0.6.2+git20071119-0ubuntu1~gutsy1  OpenGL window and compositing manager - plug
ii  compizconfig-settings-manager              0.5.2+git20070912-0ubuntu1           Compiz configuration settings manager
ii  emerald                                    0.3~git20070717-0ubuntu1             Decorator for compiz-fusion
ii  libcompizconfig-backend-gconf              0.6.0~git20071003+3v1ubuntu0         GNOME Backend for the Compiz Configuration S
ii  libcompizconfig0                           0.5.2+git20070919-0ubuntu3           Settings library for plugins - OpenCompositi
ii  libemeraldengine0                          0.3~git20070717-0ubuntu1             Decoration engines for compiz-fusion
ii  python-compizconfig                        0.5.2+git20070912-0ubuntu1           Compiz configuration system bindings


```
So A: I really have no idea which version i am using, and B: I have no idea how to get the extra plugins like snow running.  I tried MANY guides, but they all seem to be for 0.6.1...
and obviously, I do not have that.

is there any way i can install the extra plugins? someone please help!

---

