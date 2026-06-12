---
title: "AWN problem"
date: 2008-01-05
forum: Desktop Environments
---

### Post by swoll1980 on 2008-01-05
/usr/share/avant-window-navigator/awn-manager/awnPreferences.py:242: DeprecationWarning: raising a string exception is deprecated
  raise "\nKey: "+key+" isn't set.\nRestarting AWN usually solves this issue\n"
Traceback (most recent call last):
  File "/usr/bin/awn-manager", line 200, in <module>
    awnmanager = AwnManager()
  File "/usr/bin/awn-manager", line 101, in __init__
    self.prefManager = awnPreferences(self.wTree)
  File "/usr/share/avant-window-navigator/awn-manager/awnPreferences.py", line 150, in __init__
    self.setup_chooser(APP_ACTIVE_PNG, self.wTree.get_widget("activefilechooser"))
  File "/usr/share/avant-window-navigator/awn-manager/awnPreferences.py", line 242, in setup_chooser
    raise "\nKey: "+key+" isn't set.\nRestarting AWN usually solves this issue\n"

Key: /apps/avant-window-navigator/app/active_png isn't set.
Restarting AWN usually solves this issue

Don't know what it means but it's not good. Any Ideas?

---

### Post by pavpan on 2008-01-05
Run awn at least once before running AWN-Manager.

Please post to the awn forums (awn.planetblur.org) next time for awn problems

---

### Post by swoll1980 on 2008-01-05
> **pavpan said:**
> Run awn at least once before running AWN-Manager.

Please post to the awn forums (awn.planetblur.org) next time for awn problems

How do I run it I tried awn that doesn't work

---

