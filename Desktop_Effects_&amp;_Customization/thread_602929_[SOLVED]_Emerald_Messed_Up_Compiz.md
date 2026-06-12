---
title: "[SOLVED] Emerald Messed Up Compiz"
date: 2007-11-04
forum: Desktop Effects &amp; Customization
---

### Post by alsamman on 2007-11-04
I did a fresh new installation of Gutsy and I had Compiz woriking. Everything was working fine until I wanted to install emerald, I went into synaptic and searched emerald and it said that it needed to be upgraded. I tried to but I got an error so I decided to remove emerald and reinstall it. When I tried to install it I got an error
```

emerald:
 Depends: libemeraldengine0 but it is not going to be installed
 Depends: libwnck18 (>=2.15.90) but it is not installable

```
I tried installing though terminal the other emerald packages and it still got errors. Then I realized not much longer that compiz wouldnt work anymore and the manager also wouldnt open anymore. I tried compiz --replace but that didnt do anything.
when I try running compiz --replace in terminal rather than alt f2 I get this
```

compiz --replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0400 (rev a1) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1360x768) to maximum 3D texture size (8192): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format

```

So how can I fix all of this? (Get compiz working again and working installation of emerald)

---

### Post by Forlong on 2007-11-04
Please post the output of ```
dpkg -l | grep compiz
```

---

### Post by alsamman on 2007-11-04
```

manar@manar-desktop:~$ dpkg -l | grep compiz
ii  compiz                                     1:0.6.0+git20071008-0ubuntu1.1 OpenGL window and compositing manager
ii  compiz-core                                1:0.6.0+git20071008-0ubuntu1.1 OpenGL window and compositing manager
ii  compiz-fusion-plugins-extra                0.5.2+git20070928-0ubuntu1     Collection of extra plugins from OpenComposi
ii  compiz-fusion-plugins-main                 0.5.2+git20070928-0ubuntu2     Collection of plugins from OpenCompositing f
ii  compiz-gnome                               1:0.6.0+git20071008-0ubuntu1.1 OpenGL window and compositing manager - GNOM
ii  compiz-kde                                 1:0.6.0+git20071008-0ubuntu1.1 OpenGL window and compositing manager - KDE 
ii  compiz-plugins                             1:0.6.0+git20071008-0ubuntu1.1 OpenGL window and compositing manager - plug
ii  compiz-settings                            0.07-1~3v1ubuntu0              Compiz Configuration tool
ii  compizconfig-settings-manager              0.6.99~git20071005+3v1ubuntu0  Plugin and configuration tool - Compiz Fusio
rc  emerald                                    0.3~git20070717-0ubuntu1       Decorator for compiz-fusion
rc  gnome-compiz-manager                       0.10.3-0ubuntu2                Compiz Gnome Manager
ii  libcompizconfig-backend-gconf              0.6.0~git20071003+3v1ubuntu0   GNOME Backend for the Compiz Configuration S
ii  libcompizconfig-backend-kconfig            0.5.2~git20070920+3v1ubuntu0   KDE Backend for the Compiz Configuration Sys
ii  libcompizconfig0                           0.5.2+git20070919-0ubuntu3     Settings library for plugins - OpenCompositi
rc  libemeraldengine0                          0.3~git20070717-0ubuntu1       Decoration engines for compiz-fusion
ii  libgnome-compiz-manager0                   0.10.3-0ubuntu2                Compiz Gnome Manager
ii  python-compizconfig                        0.5.2+git20070912-0ubuntu1     Compiz configuration system bindings

```

---

### Post by Forlong on 2007-11-04
```
ii  compiz-settings                            0.07-1~3v1ubuntu0 
ii  compizconfig-settings-manager              0.6.99~git20071005+3v1ubuntu0
ii  libcompizconfig-backend-gconf              0.6.0~git20071003+3v1ubuntu0
ii  libcompizconfig-backend-kconfig            0.5.2~git20070920+3v1ubuntu0  
```
Remove those and then see here: [http://ubuntuforums.org/showthread.php?t=580063](http://ubuntuforums.org/showthread.php?t=580063)

---

### Post by alsamman on 2007-11-04
thank you so much for the help, I got compiz to work again

However...emerald still isnt installed and im afraid of trying to install it cause it might screw up everything again, so what should i do?

---

### Post by Forlong on 2007-11-04
> **alsamman said:**
> However...emerald still isnt installed and im afraid of trying to install it cause it might screw up everything again, so what should i do?
There's no reason to be afraid as long as you don't have any third-party reposities (regarding Compiz) enabled.

---

