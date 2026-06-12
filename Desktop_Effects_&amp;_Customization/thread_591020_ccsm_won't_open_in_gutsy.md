---
title: "ccsm won't open in gutsy"
date: 2007-10-25
forum: Desktop Effects &amp; Customization
---

### Post by haran_elessar on 2007-10-25
Hi,

I had compiz-fusion working in feisty. I upgraded to gutsy and I can't access the compiz configuration settings manager. I clicked on preferences in the custom effects settings under appearance and nothing happened. After that I clicked on the ccsm icon in the system>preferences menu and nothing happened either. I tried downloading it from the terminal as someone suggested in another thread and it says that I already have the newest version.

What should I do? Someone had a similar problem and he was told to completely remove compiz and then install it again but he didn't respond to say if that worked or if it didn't. Can someone help me out?:confused:

---

### Post by Forlong on 2007-10-25
Please post the output of ```
ccsm
``` as well as ```
dpkg -l | grep compiz
``` in a terminal and use the forum's CODE tag please (# button)

---

### Post by ronmarley1 on 2007-10-25
Uninstall and reinstall.
Then it will be called "Advanced Desktop Effects Settings" in the System Preferences menu, but it's the same app.

---

### Post by haran_elessar on 2007-10-25
This is the output I get when typing ccsm

 ```
Traceback (most recent call last):
  File "/usr/bin/ccsm", line 45, in <module>
    idle = ccm.IdleSettingsParser(context)
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 229, in __init__
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 228, in <lambda>
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 225, in FilterPlugin
AttributeError: 'compizconfig.Plugin' object has no attribute 'Initialized'

```

and after typing  dpkg -l | grep compiz

```
david@david-laptop:~$ dpkg -l | grep compiz
ii  compiz                                     1:0.6.0+git20071008-0ubuntu1         OpenGL window and compositing manager
ii  compiz-core                                1:0.6.0+git20071008-0ubuntu1         OpenGL window and compositing manager
ii  compiz-fusion-plugins-extra                0.5.2+git20070928-0ubuntu1           Collection of extra plugins from OpenComposi
ii  compiz-fusion-plugins-main                 0.5.2+git20070928-0ubuntu2           Collection of plugins from OpenCompositing f
ii  compiz-gnome                               1:0.6.0+git20071008-0ubuntu1         OpenGL window and compositing manager - GNOM
rc  compiz-gtk                                 1:0.3.6-1ubuntu13                    OpenGL window and compositing manager - Gtk 
ii  compiz-plugins                             1:0.6.0+git20071008-0ubuntu1         OpenGL window and compositing manager - plug
ii  compizconfig-settings-manager              0.6.99~git20071005+3v1ubuntu0        Plugin and configuration tool - Compiz Fusio
ii  emerald                                    0.3~git20070717-0ubuntu1             Decorator for compiz-fusion
ii  libcompizconfig-backend-gconf              0.6.0~git20071003+3v1ubuntu0         GNOME Backend for the Compiz Configuration S
ii  libcompizconfig0                           0.5.2+git20070919-0ubuntu3           Settings library for plugins - OpenCompositi
ii  libemeraldengine0                          0.3~git20070717-0ubuntu1             Decoration engines for compiz-fusion
ii  python-compizconfig                        0.5.2+git20070912-0ubuntu1           Compiz configuration system bindings

```

also what exactly does the second command does? I want to learn since I'm fairly new to this :)

---

### Post by Forlong on 2007-10-25
That lists all installed packages related to Compiz.


You have mixed up packages installed.
First remove those:
```
sudo apt-get remove --purge compizconfig-settings-manager libcompizconfig-backend-gconf
```

Then go to **System &#8594; Administration &#8594; Software Sources &#8594; Third Party Software** and remove the 3v1 repository(s) from there.

Finally, install again.

---

### Post by haran_elessar on 2007-10-25
I'm getting this messager after inputing that command

```
E: Command line option --purgecompizconfig-settings-manager is not understood
```

---

### Post by Forlong on 2007-10-25
There should be a space between *--purge* and *compizconfig-settings-manager*
See above.

---

### Post by haran_elessar on 2007-10-25
Yes! Thanks for the help it worked like a charm :)

---

