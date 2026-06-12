---
title: "CompizConfig settings manager problems"
date: 2007-11-29
forum: Desktop Effects &amp; Customization
---

### Post by 01100001 on 2007-11-29
I have ubuntu 7.10 and it was working GREAT till today. I wanted to enable some effects and went to open CCSM.. it didn`t want to open, and after a restart, MOST of the enabled effects were gone, only the default ones were active and sill ccsm didn`t want to start.

I did this in terminal in order to see whats the problem:

```
aleks@aleks-desktop:~$ ccsm 
Traceback (most recent call last):
  File "/usr/bin/ccsm", line 45, in <module>
    idle = ccm.IdleSettingsParser(context)
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 229, in __init__
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 228, in <lambda>
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 225, in FilterPlugin
AttributeError: 'compizconfig.Plugin' object has no attribute 'Initialized'
aleks@aleks-desktop:~$ 
```

PLS Help.. cos, I`ve done a format several times on my ubuntu PC just for this problem

---

### Post by 01100001 on 2007-11-29
Fixed, I`ve reinstalled the old version of the manager :)

---

