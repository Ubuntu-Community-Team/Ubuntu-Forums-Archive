---
title: "Compiz Fusion Settings manager wont open"
date: 2007-08-08
forum: Desktop Effects &amp; Customization
---

### Post by Opeth115 on 2007-08-08
When i try to access the Compiz fusion settings manager it will refuse to open.  I tried typing ccsm into alt+f2 but still nothing so i did it in a terminal and got this error message at the end.

```
Traceback (most recent call last):
  File "/usr/local/bin/ccsm", line 43, in <module>
    mainWin = ccm.MainWin(context)
  File "/usr/local/lib/python2.5/site-packages/ccm/Window.py", line 84, in __init__
    self.ResetMainWidgets()
  File "/usr/local/lib/python2.5/site-packages/ccm/Window.py", line 178, in ResetMainWidgets
    self.BuildTable(pluginsVPort)
  File "/usr/local/lib/python2.5/site-packages/ccm/Window.py", line 230, in BuildTable
    pluginEnable.set_sensitive(self.Context.AutoSort)
AttributeError: 'compizconfig.Context' object has no attribute 'AutoSort'
```

any help to get this tow ork is appreciated.

---

### Post by Opeth115 on 2007-08-08
anyone know of any solutions?

---

### Post by Opeth115 on 2007-08-08
anybody? i tried reinstalling adn it still will not open...

---

### Post by goemon_h on 2007-08-09
I am having this same issue, does anyone know a workaround?

---

### Post by realvz on 2007-08-16
same issue....different thread,,,no solution....hv u guys tried reinstalling?

[http://ubuntuforums.org/showthread.php?p=3172853](http://ubuntuforums.org/showthread.php?p=3172853)

---

### Post by Azzco on 2007-08-16
I have the exact same problem... I had it working once on this installation so it must have been some thing I did... I'm running Kubuntu BTW I don't think that's the problem but are you guys running KDE or gnome (or even xfce)?

---

### Post by Azzco on 2007-08-16
I got it to work again, I purged all the compiz related packages and then reinstalled, worked like a charm :D

Did you guys have compiz-bcode installed too?

---

