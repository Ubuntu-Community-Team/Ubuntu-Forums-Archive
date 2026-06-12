---
title: "Errors... What do these mean? How Can I fix it!?"
date: 2009-09-28
forum: Desktop Environments
---

### Post by iamjfarrell on 2009-09-28
**Fusion-Icon**

```
justin@justin-laptop:~$ fusion-icon
Traceback (most recent call last):
  File "/usr/bin/fusion-icon", line 57, in <module>
    from FusionIcon.interface import choose_interface
  File "/usr/lib/python2.6/dist-packages/FusionIcon/interface.py", line 21, in <module>
    from util import env
  File "/usr/lib/python2.6/dist-packages/FusionIcon/util.py", line 21, in <module>
    import os, compizconfig, ConfigParser, time
ImportError: /usr/lib/python2.6/dist-packages/compizconfig.so: undefined symbol: ccsGetPluginStrExtensions

```

**CCSM**

```
Traceback (most recent call last):
  File "/usr/local/bin/ccsm", line 38, in <module>
    import compizconfig
ImportError: /usr/lib/python2.6/dist-packages/compizconfig.so: undefined symbol: ccsGetPluginStrExtensions
```

Compiz does not currently work and I am trying to get it work. What do I need to do get it working?

---

