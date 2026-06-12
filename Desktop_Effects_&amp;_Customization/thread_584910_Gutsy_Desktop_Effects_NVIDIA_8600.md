---
title: "Gutsy Desktop Effects NVIDIA 8600"
date: 2007-10-21
forum: Desktop Effects &amp; Customization
---

### Post by MourningWood on 2007-10-21
I've been try to get compiz or even beryl (until I uninstalled it) running without any luck.  I upgraded from feisty without any problems and got my NVIDIA card working without too much difficulty.  When ever I load compiz it tells me I need Glx and when I install it compiz will run but everything will go in slow motion and my terminal turns white.  I uninstall Glx and everything runs fine again but no compiz.  Also, when I had beryl install still it would run but would also go in slow motion with or without Glx.

If anyone could help me troubleshoot this I would appreciate it. 

compiz ran from terminal
```
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0402 (rev a1) (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
aborting and using fallback: /usr/bin/metacity 
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"

```
thats as far as it gets until I stop it with ctrl+c

dpkg -l | grep compiz
```
ii  compiz                                     1:0.6.0+git20071008-0ubuntu1         OpenGL window and compositing manager
ii  compiz-core                                1:0.6.0+git20071008-0ubuntu1         OpenGL window and compositing manager
ii  compiz-fusion-plugins-extra                0.5.2+git20070928-0ubuntu1           Collection of extra plugins from OpenCompositing for
ii  compiz-fusion-plugins-main                 0.5.2+git20070928-0ubuntu2           Collection of plugins from OpenCompositing for Compi
ii  compiz-gnome                               1:0.6.0+git20071008-0ubuntu1         OpenGL window and compositing manager - GNOME window
rc  compiz-gtk                                 1:0.3.6-1ubuntu13                    OpenGL window and compositing manager - Gtk window d
ii  compiz-plugins                             1:0.6.0+git20071008-0ubuntu1         OpenGL window and compositing manager - plugins
ii  compizconfig-settings-manager              0.5.2+git20070912-0ubuntu1           Compiz configuration settings manager
ii  emerald                                    0.3~git20070717-0ubuntu1             Decorator for compiz-fusion
ii  gnome-compiz-manager                       0.10.3-0ubuntu2                      Compiz Gnome Manager
ii  libcompizconfig-backend-gconf              0.5.2+git20071010-0ubuntu1           Settings library for plugins - OpenCompositing Proje
ii  libcompizconfig0                           0.5.2+git20070919-0ubuntu3           Settings library for plugins - OpenCompositing Proje
ii  libemeraldengine0                          0.3~git20070717-0ubuntu1             Decoration engines for compiz-fusion
ii  libgnome-compiz-manager0                   0.10.3-0ubuntu2                      Compiz Gnome Manager
ii  python-compizconfig                        0.5.2+git20070912-0ubuntu1           Compiz configuration system bindings

```

---

### Post by MourningWood on 2007-10-21
Let me know if I need to post anything else.  I would love any help that I can get.

---

### Post by MourningWood on 2007-10-22
bump

---

### Post by elmz350 on 2007-12-29
Hello:

I'm having a similar issue.  I cannot enable desktop effects on a clean install of Gutsy.  I've been researching a solution on how to install NVIDIA 8600 GT drivers...

Thanks in advance.

---

### Post by mailbinoy on 2008-01-01
have you guys tried envy. i don't have a 8600 but I believe it works 
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

