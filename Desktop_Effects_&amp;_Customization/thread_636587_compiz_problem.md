---
title: "compiz problem"
date: 2007-12-10
forum: Desktop Effects &amp; Customization
---

### Post by jofishr on 2007-12-10
[SIZE="2"]I just installed compiz but when I click the program nothing happens I then started it in a terminal window by typing CCSM and I got the following

joe@joe-desktop:~$ ccsm
Traceback (most recent call last):
  File "/usr/bin/ccsm", line 45, in <module>
    idle = ccm.IdleSettingsParser(context)
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 229, in __init__
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 228, in <lambda>
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 225, in FilterPlugin
AttributeError: 'compizconfig.Plugin' object has no attribute 'Initialized'
joe@joe-desktop:~$

---

### Post by Ub1476 on 2007-12-10
Hi what version of Ubuntu are you using?

```
lsb_release -a
```

And where did you install Compiz from (link please)?

And what's your graphic card/controller?

```
lspci | grep VGA
```

---

