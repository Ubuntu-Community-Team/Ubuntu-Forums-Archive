---
title: "compizconfig-settings-manager won't work - lost all configuration"
date: 2008-01-27
forum: Desktop Effects &amp; Customization
---

### Post by tom66 on 2008-01-27
I've lost all my configuration for Compiz. Not only that, I can't seem to access CCSM. Any tips on getting this working again are appreciated!

The error message in the console:

```

thomas@orpheus:~$ ccsm
Traceback (most recent call last):
  File "/usr/bin/ccsm", line 45, in <module>
    idle = ccm.IdleSettingsParser(context)
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 229, in __init__
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 228, in <lambda>
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 225, in FilterPlugin
AttributeError: 'compizconfig.Plugin' object has no attribute 'Initialized'

```

Thanks,
Tom

---

### Post by overfloat on 2008-01-27
I've got the exact same problem - it happened after i installed kiba dock (i think?)

the answer is here
[http://ubuntuforums.org/showthread.php?t=534341&highlight=ccsm&page=3](http://ubuntuforums.org/showthread.php?t=534341&highlight=ccsm&page=3)

downgrade your compiz

---

### Post by tom66 on 2008-01-28
I didn't touch anything. I just restarted.

Anyway, I seem to have some basic animations, such as the sliding between desktops, and the scale animation, so Compiz isn't fubar'd but I really miss wobbly windows! Is there anyway - lest reinstalling Compiz, I can get this back?

---

