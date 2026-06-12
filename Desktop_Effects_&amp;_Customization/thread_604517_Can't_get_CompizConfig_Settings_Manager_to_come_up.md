---
title: "Can't get CompizConfig Settings Manager to come up"
date: 2007-11-06
forum: Desktop Effects &amp; Customization
---

### Post by Xeeon on 2007-11-06
OK I've properly installed Compiz, and I have properly installed CCSM, but when I click System >> Preferences >> CompizConfig Settings Manager, NOTHING happens... I've waited and waited and clicked and clicked... nothing.

I have no idea what's going on.

---

### Post by Forlong on 2007-11-06
Post the output of ```
dpkg -l | grep compiz
``` and use the forum's CODE tag please (# button)

---

### Post by Xeeon on 2007-11-06
```
ii  compiz                                     1:0.6.0+git20071008-0ubuntu1.1       OpenGL window and compositing manager
ii  compiz-core                                1:0.6.0+git20071008-0ubuntu1.1       OpenGL window and compositing manager
ii  compiz-fusion-plugins-extra                0.5.2+git20070928-0ubuntu1           Collection of extra plugins from OpenComposi
ii  compiz-fusion-plugins-main                 0.5.2+git20070928-0ubuntu2           Collection of plugins from OpenCompositing f
ii  compiz-gnome                               1:0.6.0+git20071008-0ubuntu1.1       OpenGL window and compositing manager - GNOM
rc  compiz-gtk                                 1:0.3.6-1ubuntu13                    OpenGL window and compositing manager - Gtk 
ii  compiz-plugins                             1:0.6.0+git20071008-0ubuntu1.1       OpenGL window and compositing manager - plug
ii  compizconfig-settings-manager              0.6.99~git20071005+3v1ubuntu0        Plugin and configuration tool - Compiz Fusio
ii  libcompizconfig-backend-gconf              0.6.0~git20071003+3v1ubuntu0         GNOME Backend for the Compiz Configuration S
ii  libcompizconfig0                           0.5.2+git20070919-0ubuntu3           Settings library for plugins - OpenCompositi
ii  python-compizconfig                        0.5.2+git20070912-0ubuntu1           Compiz configuration system bindings
```

---

### Post by Forlong on 2007-11-06
You have packages from a third-party repository that are not compatible to the rest. Remove them:
```
sudo apt-get remove compizconfig-settings-manager libcompizconfig-backend-gconf
```
Then go here: [http://ubuntuforums.org/showthread.php?t=580063](http://ubuntuforums.org/showthread.php?t=580063)

---

### Post by Xeeon on 2007-11-06
Thanks very much, it works flawlessly now.

---

