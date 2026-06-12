---
title: "[SOLVED] Compiz Settings Manager Missing"
date: 2007-11-07
forum: Desktop Effects &amp; Customization
---

### Post by derekr44 on 2007-11-07
When trying to run CCSM:

```
derek@derek-desktop:~$ ccsm
Traceback (most recent call last):
  File "/usr/bin/ccsm", line 45, in <module>
    idle = ccm.IdleSettingsParser(context)
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 229, in __init__
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 228, in <lambda>
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 225, in FilterPlugin
AttributeError: 'compizconfig.Plugin' object has no attribute 'Initialized'
```

Then I followed other suggestions and ran:

```
sudo apt-get autoremove compizconfig-settings-manager
```

then

```
sudo apt-get install compizconfig-settings-manager
```

Error still remains.

```
ii  compiz-core                                1:0.6.0+git20071008-0ubuntu1.1            OpenGL window and compositing manager
rc  compiz-gnome                               1:0.6.0+git20071008-0ubuntu1.1            OpenGL window and compositing manager - GNOM
rc  compiz-gtk                                 1:0.3.6-1ubuntu13                         OpenGL window and compositing manager - Gtk 
ii  compiz-plugins                             1:0.6.0+git20071008-0ubuntu1.1            OpenGL window and compositing manager - plug
ii  compizconfig-settings-manager              0.6.99~git20071005+3v1ubuntu0             Plugin and configuration tool - Compiz Fusio
ii  emerald                                    0.3~git20070717-0ubuntu1                  Decorator for compiz-fusion
rc  gnome-compiz-manager                       0.10.3-0ubuntu2                           Compiz Gnome Manager
ii  libcompizconfig0                           0.5.2+git20070919-0ubuntu3                Settings library for plugins - OpenCompositi
ii  libemeraldengine0                          0.3~git20070717-0ubuntu1                  Decoration engines for compiz-fusion
rc  libgnome-compiz-manager0                   0.10.3-0ubuntu2                           Compiz Gnome Manager
ii  python-compizconfig                        0.5.2+git20070912-0ubuntu1                Compiz configuration system bindings

```

Compiz & Emerald work perfectly otherwise.  I just can't make any changes to Compiz settings... any ideas?

---

### Post by FuturePilot on 2007-11-07
Try ```
sudo apt-get remove --purge compizconfig-settings-manager
sudo apt-get install compizconfig-settings-manager
```

---

### Post by trak87 on 2007-11-07
autoremove? Maybe try just remove.

---

### Post by derekr44 on 2007-11-07
Still the same issue.  Purge, autoremove and remove were all used in separate instances, but the error still remains after installing.

Are we talkin a complete reinstall of Compiz?

---

### Post by dysonsphere23 on 2007-11-07
I just got the exact same problem.  I had it working fine minutes ago then a did a system restart and now am unable to start the ccsm.

---

### Post by derekr44 on 2007-11-07
Finally got it working.

Apparently, the install command was pulling the installer from the Feisty repo.  So uncheck the Feisty repos in your Third Party Sources in Synaptic.

---

### Post by dysonsphere23 on 2007-11-07
A bit more complicated for me.  I had the kiba-dock set up so if you have trevino eycandy make sure you change the distribution from feisty (as indicated on the kiba-dock wiki) to gutsy in the software sources.  once this is done install the compiz settings manager.

---

