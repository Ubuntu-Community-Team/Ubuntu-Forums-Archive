---
title: "Compizconfig Settings Manager does nothing"
date: 2007-10-08
forum: Desktop Effects &amp; Customization
---

### Post by particleMan86 on 2007-10-08
I managed to install and run Compiz Fusion finally, under XGL with fglrx version 8.41, and the default effects work, but the ccsm doesn't appear to be working. I can make changes with the gui, but they are not applied *for real* For instance, I can't change from desktop wall to desktop cube, although the correct plugins are checked in ccsm.

When I run ccsm from a terminal I get this output:

```
Info: No sexy-python package found, don't worry it's optional.
Traceback (most recent call last):
  File "/usr/lib/python2.5/site-packages/ccm/Utils.py", line 138, in Update
    changedSettings = self.Context.ChangedSettings
AttributeError: 'compizconfig.Context' object has no attribute 'ChangedSettings'
Traceback (most recent call last):
  File "/usr/lib/python2.5/site-packages/ccm/Utils.py", line 138, in Update
    changedSettings = self.Context.ChangedSettings
AttributeError: 'compizconfig.Context' object has no attribute 'ChangedSettings'

```

I'm using compiz/ccsm from Amaranth's repo. If anyone has any idea how to fix this I'd appreciate it. Thanks!

---

### Post by Sturmeh on 2007-10-08
I have no idea why he discourages use of Treviño's Ubuntu feisty EyeCandy Repository...

But the compiz-fusion found there seems to work alot better for me, give it a try.

---

### Post by particleMan86 on 2007-10-08
Actually I did try trevino's first; it didn't work at all (Compiz wouldn't start). So I am a lot farther along with Amaranth, just need to get the settings manager to work...

---

### Post by particleMan86 on 2007-10-08
Well for now a simple apt-get remove compizconfig-settings-manager followed by a reinstall seems to have worked. But I've been messing with this too long to be really confident ;)

---

