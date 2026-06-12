---
title: "Compizcomfig settings manager won't start."
date: 2007-09-26
forum: Desktop Effects &amp; Customization
---

### Post by BadEinar on 2007-09-26
Hi. 
I'm having problems starting up the CompizConfig settings manager. When I try to start from System > Preferences > CompizConfig settings manager, nothing happens! And when I try to start it from the terminal, I get this message:

Traceback (most recent call last):
  File "/usr/bin/ccsm", line 43, in <module>
    mainWin = ccm.MainWin(context)
  File "/usr/lib/python2.5/site-packages/ccm/Window.py", line 77, in __init__
    for category in sorted(self.Context.Categories, self.CatSortCompare):
  File "/usr/lib/python2.5/site-packages/ccm/Window.py", line 361, in CatSortCompare
    if self.Context.Plugins['core'].Category == v1:
KeyError: 'core'

Compiz is working and all that, but I can't adjust the settings..

I'm pretty new to ubuntu, and i really don't know what to do. I would be glad if someone could help me out on this one.

---

### Post by Forlong on 2007-09-26
This thread should help you out: [http://ubuntuforums.org/showthread.php?t=534341&page=2](http://ubuntuforums.org/showthread.php?t=534341&page=2)

---

### Post by HokeyFry on 2007-09-26
see if there are any python upgrades in the repositories, and make sure the latest version of python is installed

---

