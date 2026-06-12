---
title: "[SOLVED] Error Loading CCSM (compizconfig-settings-manager)"
date: 2007-11-08
forum: Desktop Effects &amp; Customization
---

### Post by aimnano on 2007-11-08
# This post has been resolved.  Resolution:  [http://forum.compiz-fusion.org/showpost.php?p=32268&postcount=7](http://forum.compiz-fusion.org/showpost.php?p=32268&postcount=7)

~$ ccsm
Traceback (most recent call last):
  File "/usr/bin/ccsm", line 45, in <module>
    idle = ccm.IdleSettingsParser(context)
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 229, in __init__
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 228, in <lambda>
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 225, in FilterPlugin
AttributeError: 'compizconfig.Plugin' object has no attribute 'Initialized'

I have been unable to get CCSM to load.  I've read several forums posts saying to uninstall and reinstall...but to no avail.  Anyone dare to guide me through the debugging process?  Let me know any information that would be helpful in solving this problem.

---

