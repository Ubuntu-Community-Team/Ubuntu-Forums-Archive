---
title: "compizfusion dies after update"
date: 2008-01-02
forum: Desktop Environments
---

### Post by querulousennui on 2008-01-02
I just updated compiz-fusion, but now it doesn't work.

I get this message:
```

kristin@qennui:~$ ccsm
Traceback (most recent call last):
File "/usr/bin/ccsm", line 45, in <module>
idle = ccm.IdleSettingsParser(context)
File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 229, in __init__
File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 228, in <lambda>
File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 225, in FilterPlugin
AttributeError: 'compizconfig.Plugin' object has no attribute 'Initialized'

```

I tried to uninstall/reinstall, that didn't work.
```

sudo aptitude purge compizconfig-settings-manager

```

then with 
```

sudo apt-get install compizconfig-settings-manager

```

Any ideas how to fix this?
Thanks!

edit: I also tried to uninstall the update in synaptic, but I'm not sure which to uninstall, and without dates next to when things were installed, how would i find that out?

---

