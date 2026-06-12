---
title: "Compiz Configuration Settings Manager problem"
date: 2011-05-03
forum: Desktop Environments
---

### Post by Jerriy on 2011-05-03
I'm unable to load the settings of compiz. 

Typing ccsm in terminal results in this:```
(process:3248): Gtk-WARNING **: Locale not supported by C library.
    Using the fallback 'C' locale.
Traceback (most recent call last):
  File "/usr/bin/ccsm", line 100, in <module>
    import ccm
  File "/usr/lib/python2.6/dist-packages/ccm/__init__.py", line 1, in <module>
    from ccm.Conflicts import *
  File "/usr/lib/python2.6/dist-packages/ccm/Conflicts.py", line 27, in <module>
    from ccm.Constants import *
  File "/usr/lib/python2.6/dist-packages/ccm/Constants.py", line 88, in <module>
    locale.setlocale(locale.LC_ALL, "")
  File "/usr/lib/python2.6/locale.py", line 513, in setlocale
    return _setlocale(category, locale)
locale.Error: unsupported locale setting

```I do have it installed (can see the compiz settings option in the GUI panel's main menu and also a button at "control center" (but clicking on them doesn't doesn't help).

---

