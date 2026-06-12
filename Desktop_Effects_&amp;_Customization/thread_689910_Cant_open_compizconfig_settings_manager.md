---
title: "Cant open compizconfig settings manager"
date: 2008-02-06
forum: Desktop Effects &amp; Customization
---

### Post by LaxFreek on 2008-02-06
I go click on it in the system>pref place and it just won't open for me. Anybody know why?

---

### Post by FuturePilot on 2008-02-06
Try running 
```
ccsm
```
from the terminal and see if there are errors.

---

### Post by LaxFreek on 2008-02-06
Traceback (most recent call last):
  File "/usr/bin/ccsm", line 45, in <module>
    idle = ccm.IdleSettingsParser(context)
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 229, in __init__
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 228, in <lambda>
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 225, in FilterPlugin
AttributeError: 'compizconfig.Plugin' object has no attribute 'Initialized'

---

### Post by FuturePilot on 2008-02-06
Maybe try uninstalling it then reinstall it
```
sudo apt-get remove --purge compizconfig-settings-manager
sudo apt-get install compizconfig-settings-manager
```

---

### Post by Lderan on 2008-02-10
I get this error, even after removing then re-installing it

Traceback (most recent call last):
  File "/usr/bin/ccsm", line 43, in <module>
    mainWin = ccm.MainWin(context)
  File "/usr/lib/python2.5/site-packages/ccm/Window.py", line 77, in __init__
    for category in sorted(self.Context.Categories, self.CatSortCompare):
  File "/usr/lib/python2.5/site-packages/ccm/Window.py", line 361, in CatSortCompare
    if self.Context.Plugins['core'].Category == v1:
KeyError: 'core'

---

