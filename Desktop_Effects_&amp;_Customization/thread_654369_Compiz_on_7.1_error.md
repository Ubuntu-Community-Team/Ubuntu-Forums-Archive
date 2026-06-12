---
title: "Compiz on 7.1 error"
date: 2007-12-31
forum: Desktop Effects &amp; Customization
---

### Post by Ponomous on 2007-12-31
Hey I am having trouble with compiz, i am trying to get the cube running.

i installed compiz but when i try running ccsm i get

Traceback (most recent call last):
  File "/usr/bin/ccsm", line 45, in <module>
    idle = ccm.IdleSettingsParser(context)
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 229, in __init__
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 228, in <lambda>
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 225, in FilterPlugin
AttributeError: 'compizconfig.Plugin' object has no attribute 'Initialized'

any ideas on whats going on?

thanks

---

### Post by Ub1476 on 2007-12-31
I guess you just installed compizconfig-settings-manager (Advanced Desktop Effects), since Compiz-Fusion comes by default in Ubuntu 7.10. And are you able to turn on normal effects in System>Appearance>Visual Effects?

---

### Post by Forlong on 2007-12-31
Post the output of ```
dpkg -l | grep compiz
``` and use the forum's CODE tag please (# button)

---

### Post by Ponomous on 2007-12-31
Sry about the code tag, i forgot to use it before.

Yes i can enable the normal effects as well as the advanced and custom.  I had wobbly windows for a while, somthing happened and they dont wobble any more.  I am at work right now so i will post the code later today, HALF DAY FOR NEWYEARS!!

Thanks

---

### Post by Kossilar on 2008-01-23
How did you get it working? I'm getting exactly the same output from running ccsm as you are.

> Post the output of
Code:
```

dpkg -l | grep compiz
```

and use the forum's CODE tag please (# button)

This is what I get:

```
~$ dpkg -l | grep compiz
ii  compiz                                     1:0.6.0+git20071008-0ubuntu1.1    OpenGL window and compositing manager
ii  compiz-core                                1:0.6.0+git20071008-0ubuntu1.1    OpenGL window and compositing manager
ii  compiz-fusion-plugins-extra                0.5.2+git20070928-0ubuntu1        Collection of extra plugins from OpenComposi
ii  compiz-fusion-plugins-main                 0.5.2+git20070928-0ubuntu2        Collection of plugins from OpenCompositing f
ii  compiz-gnome                               1:0.6.0+git20071008-0ubuntu1.1    OpenGL window and compositing manager - GNOM
ii  compiz-plugins                             1:0.6.0+git20071008-0ubuntu1.1    OpenGL window and compositing manager - plug
ii  compiz-settings                            0.07-1~3v1ubuntu0                 Compiz Configuration tool
ii  compizconfig-settings-manager              0.6.99~git20071005+3v1ubuntu0     Plugin and configuration tool - Compiz Fusio
ii  libcompizconfig-backend-gconf              0.6.0~git20071003+3v1ubuntu0      GNOME Backend for the Compiz Configuration S
ii  libcompizconfig0                           0.5.2+git20070919-0ubuntu3        Settings library for plugins - OpenCompositi
ii  python-compizconfig                        0.5.2+git20070912-0ubuntu1        Compiz configuration system bindings
```

EDIT: I have advanced effects working, I just can't customize anything.

---

### Post by Ponomous on 2008-01-30
Still no fix here, anyone have anything?

---

