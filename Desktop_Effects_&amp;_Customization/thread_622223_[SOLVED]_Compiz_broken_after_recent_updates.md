---
title: "[SOLVED] Compiz broken after recent updates"
date: 2007-11-24
forum: Desktop Effects &amp; Customization
---

### Post by Junk_head on 2007-11-24
Hello all,
I recently updated the compiz set, now my whole setup is borderless and no emerald goodness. I tried to bring up the compiz config setting manager but it never comes up when called. I tried compiz--replace and got :```

Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:02.0 0300: 8086:27a2 (rev 03) (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x800) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting emerald
/home/alex/.themes/gommapiumalooks/gtk-2.0/gtkrc:234: error: invalid string constant "clearlooks-panelbg", expected valid string constant
```
Anyone can lend a hand? Im using ubuntu gutsy.

---

### Post by Forlong on 2007-11-24
Post the output of ```
dpkg -l | grep compiz
```

---

### Post by Junk_head on 2007-11-24
There you go:

```
dpkg -l | grep compiz
ii  compiz                                     1:0.6.2+git20071119-0ubuntu1~gutsy1  OpenGL window and compositing manager
ii  compiz-bcop                                0.6.0+git20071111                    Compiz option code generator
ii  compiz-core                                1:0.6.2+git20071119-0ubuntu1~gutsy1  OpenGL window and compositing manager
ii  compiz-fusion-plugins-extra                0.6.0+git20071121-0ubuntu1~gutsy1    Collection of extra plugins from OpenComposi
ii  compiz-fusion-plugins-main                 0.5.2+git20070928-0ubuntu2           Collection of plugins from OpenCompositing f
ii  compiz-gnome                               1:0.6.2+git20071119-0ubuntu1~gutsy1  OpenGL window and compositing manager - GNOM
ii  compiz-plugins                             1:0.6.2+git20071119-0ubuntu1~gutsy1  OpenGL window and compositing manager - plug
ii  compizconfig-settings-manager              0.5.2+git20070912-0ubuntu1           Compiz configuration settings manager
ii  emerald                                    0.3~git20070717-0ubuntu1             Decorator for compiz-fusion
ii  gnome-compiz-manager                       0.10.3-0ubuntu2                      Compiz Gnome Manager
ii  libcompizconfig                            0.6.0+git20071111                    Settings library for plugins - OpenCompositi
ii  libcompizconfig-backend-gconf              0.5.2+git20071010-0ubuntu1           Settings library for plugins - OpenCompositi
ii  libcompizconfig0                           0.5.2+git20070919-0ubuntu3           Settings library for plugins - OpenCompositi
ii  libemeraldengine0                          0.3~git20070717-0ubuntu1             Decoration engines for compiz-fusion
ii  libgnome-compiz-manager0                   0.10.3-0ubuntu2                      Compiz Gnome Manager
ii  python-compizconfig                        0.5.2+git20070912-0ubuntu1           Compiz configuration system bindings
```

---

### Post by Forlong on 2007-11-24
Do you have the gutsy-backports repository enabled?
Or any other third-party repo?

---

### Post by Junk_head on 2007-11-24
I do have gutsy backports enabled aswell as modblock hendrik and two jldugger launchpad repos.

---

### Post by Forlong on 2007-11-24
That appears to be the problem. Most of the poackages are not the one's from the official Gutsy repos.
Try this:
```
sudo apt-get remove --purge compiz* emerald* && sudo apt-get autoremove
```
And afterwards:
```
sudo apt-get install compiz compizconfig-settings-manager emerald
```

---

### Post by Junk_head on 2007-11-24
Ahh thank you so much Forlong :), it's great to have my desk back. I'll remove my 3rd part repos asap just aint worth the risk for some small apps.

---

