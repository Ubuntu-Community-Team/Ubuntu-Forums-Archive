---
title: "Cant open compiz settings"
date: 2007-08-29
forum: Desktop Effects &amp; Customization
---

### Post by dsforsaken on 2007-08-29
i followed this guide and i still cant open compiz settings manager, any reason why or anyone else have this problem?

the errror in the terminal says:
```
Traceback (most recent call last):
  File "/usr/local/bin/ccsm", line 44, in <module>
    idle = ccm.IdleSettingsParser(context)
  File "/usr/local/lib/python2.5/site-packages/ccm/Utils.py", line 155, in __init__
    self.Context.Plugins.items ())
  File "/usr/local/lib/python2.5/site-packages/ccm/Utils.py", line 154, in <lambda>
    self.PluginList = filter (lambda p: FilterPlugin (p[1]),
  File "/usr/local/lib/python2.5/site-packages/ccm/Utils.py", line 151, in FilterPlugin
    return not p.Initialized and p.Enabled
AttributeError: 'compizconfig.Plugin' object has no attribute 'Initialized'

```

---

### Post by cudaman73 on 2007-08-29
What guide are you talking about?

If you're talking about the "best way to install compiz" guide, then you probably didn't uninstall desktop-effects and related compiz settings prior to following the guide. I had the same problem.

Uninstall all of your compiz related stuff, and then try again. Make sure that you apt-get remove desktop-effects as well.

---

