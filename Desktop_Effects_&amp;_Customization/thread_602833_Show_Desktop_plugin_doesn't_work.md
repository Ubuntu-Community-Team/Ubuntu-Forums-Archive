---
title: "Show Desktop plugin doesn't work"
date: 2007-11-04
forum: Desktop Effects &amp; Customization
---

### Post by fergarciaga on 2007-11-04
Hello everybody!
I've got a brand new laptop with Feisty installed, nVidia Quadro FX 360M and the latest version of Compiz and its plugins, see:
```
~$ dpkg -l | grep -i compiz
ii  compiz                                     1:0.6.0+git20071008-0ubuntu1.1 OpenGL window and compositing manager
ii  compiz-bcop                                0.5.2-0ubuntu1                 Compiz option code generator
ii  compiz-core                                1:0.6.0+git20071008-0ubuntu1.1 OpenGL window and compositing manager
ii  compiz-dev                                 1:0.6.0+git20071008-0ubuntu1.1 OpenGL window and compositing manager - deve
ii  compiz-fusion-plugins-extra                0.5.2+git20070928-0ubuntu1     Collection of extra plugins from OpenComposi
ii  compiz-fusion-plugins-main                 0.5.2+git20070928-0ubuntu2     Collection of plugins from OpenCompositing f
ii  compiz-gnome                               1:0.6.0+git20071008-0ubuntu1.1 OpenGL window and compositing manager - GNOM
ii  compiz-plugins                             1:0.6.0+git20071008-0ubuntu1.1 OpenGL window and compositing manager - plug
ii  compizconfig-settings-manager              0.5.2+git20070912-0ubuntu1     Compiz configuration settings manager
ii  gnome-compiz-manager                       0.10.3-0ubuntu2                Compiz Gnome Manager
ii  libcompizconfig-backend-gconf              0.5.2+git20071010-0ubuntu1     Settings library for plugins - OpenCompositi
ii  libcompizconfig0                           0.5.2+git20070919-0ubuntu3     Settings library for plugins - OpenCompositi
ii  libcompizconfig0-dev                       0.5.2+git20070919-0ubuntu3     Development file for plugin settings - OpenC
ii  libdecoration0                             1:0.6.0+git20071008-0ubuntu1.1 Compiz window decoration library
ii  libdecoration0-dev                         1:0.6.0+git20071008-0ubuntu1.1 Compiz window decoration library - developme
ii  libgnome-compiz-manager0                   0.10.3-0ubuntu2                Compiz Gnome Manager
ii  libgnome-compiz-manager0-dev               0.10.3-0ubuntu2                Compiz Gnome Manager
ii  python-compizconfig                        0.5.2+git20070912-0ubuntu1     Compiz configuration system bindings
```

Most of the plugins and effects are working properly and very fancy... However, the "Show Desktop" plugin only runs sometimes, after manually de-activating and re-activating it in CCSM, and not even all the times that I do so.
It seems to be well configured in the Gnome Compiz Preferences GUI, but won't work on start-up when moving the mouse pointer to the upper-left corner. I also tried activating the plugin by editing with gconf-edit (both as a common user and as root) this field
```
/apps/compiz/general/allscreens/options/active_plugins
```
and loading it at start-up
```
compiz --replace gconf
```
but no results... any idea?
Thank you very much in advance
Fernando

---

### Post by fergarciaga on 2007-11-04
Sorry, I was totally confused with the amount of all the Compiz plugins, "Show Desktop" was NOT the effect I was looking for!!!... but "Expo". Shame on me!!! ](*,) ](*,) ](*,)
By the way, it's solved by gconf-editor ```
/apps/compiz/plugins/expo/allscreens/options/expo_edge/[TopLeft]
```
or in csm, enabling ```
expo/actions/bindings/screen edge/TopLeft
```
and finally, to load changes on start-up
```
compiz --replace gconf
```

SOLVED, thanks
Fernando

---

