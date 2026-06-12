---
title: "[SOLVED] compiz-manager being difficult..."
date: 2007-12-23
forum: Desktop Environments
---

### Post by Animal Mother on 2007-12-23
Hey there, I just recently upgraded from 7.04 to 7.10. (gnome)
Prior to the upgrade, I could access compiz manager no problem from the System menu and it would load up, I could muck with it no problem. Since the upgrade I get no love. If I click on the manager nothing happens. But all my effects still work just fine. This is what happens if I enter compiz-manager & in a terminal:

```

~$ compiz-manager &
[1] 12037
~$ bash: compiz-manager: command not found
<ctrl c>
[1]+  Exit 127                compiz-manager
 
```
I'm using the proprietary Nvidia driver. 
Any love? Thanks!

---

### Post by zarqoon on 2007-12-24
i dont know about 7.04 but with 7.10 i had to install a compiz manager seperately with
```
sudo apt-get install compizconfig-setting-manager
```
it will then show at system->preferences->advanced desktop effect setting
or start ist using ```
 ccsm & 
```

---

### Post by Animal Mother on 2007-12-28
Said package was already installed.

```

$ ccsm &
[1] 11539
$ Traceback (most recent call last):
  File "/usr/bin/ccsm", line 45, in <module>
    idle = ccm.IdleSettingsParser(context)
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 229, in __init__
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 228, in <lambda>
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 225, in FilterPlugin
AttributeError: 'compizconfig.Plugin' object has no attribute 'Initialized'

[1]+  Exit 1                  ccsm



```

---

### Post by Forlong on 2007-12-28
Post the output of ```
dpkg -l | grep compiz
```

---

### Post by Animal Mother on 2007-12-28
```
 ii  compiz                                     1:0.6.2+git20071119-0ubuntu1~gutsy1       OpenGL window and compositing manager
ii  compiz-bcop                                0.5.2-0ubuntu1                            Compiz option code generator
ii  compiz-core                                1:0.6.2+git20071119-0ubuntu1~gutsy1       OpenGL window and compositing manager
ii  compiz-fusion-plugins-extra                0.6.0+git20071121-0ubuntu1~gutsy1         Collection of extra plugins from OpenComposi
ii  compiz-fusion-plugins-main                 0.5.2+git20070928-0ubuntu2                Collection of plugins from OpenCompositing f
ii  compiz-gnome                               1:0.6.2+git20071119-0ubuntu1~gutsy1       OpenGL window and compositing manager - GNOM
rc  compiz-gtk                                 1:0.3.6-1ubuntu13                         OpenGL window and compositing manager - Gtk 
ii  compiz-plugins                             1:0.6.2+git20071119-0ubuntu1~gutsy1       OpenGL window and compositing manager - plug
ii  compizconfig-settings-manager              0.6.99~git20071005+3v1ubuntu0             Plugin and configuration tool - Compiz Fusio
ii  gnome-compiz-manager                       0.10.3-0ubuntu2                           Compiz Gnome Manager
ii  libcompizconfig-backend-gconf              0.6.0~git20071003+3v1ubuntu0              GNOME Backend for the Compiz Configuration S
ii  libcompizconfig0                           0.5.2+git20070919-0ubuntu3                Settings library for plugins - OpenCompositi
ii  libgnome-compiz-manager0                   0.10.3-0ubuntu2                           Compiz Gnome Manager
ii  libgnome-compiz-manager0-dev               0.10.3-0ubuntu2                           Compiz Gnome Manager
ii  python-compizconfig                        0.5.2+git20070912-0ubuntu1                Compiz configuration system bindings

```

---

### Post by Forlong on 2007-12-28
You have mixed up packages, remove those:
```
sudo apt-get remove --purge compizconfig-settings-manager libcompizconfig-backend-gconf gnome-compiz-manager libgnome-compiz-manager0 libgnome-compiz-manager0-dev && sudo apt-get autoremove
```

Then go to *System &#8594; Administration &#8594; Software Sources &#8594; Third Party Software* and remove anything related to feisty (as well as the ones you're not sure about).

Finally install again:
```
sudo apt-get install compiz compizconfig-settings-manager
```

---

### Post by Animal Mother on 2007-12-30
Thanks, fella, got it sorted!

---

