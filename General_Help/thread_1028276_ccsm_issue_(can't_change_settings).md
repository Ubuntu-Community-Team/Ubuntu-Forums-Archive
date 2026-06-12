---
title: "ccsm issue (can't change settings)"
date: 2009-01-02
forum: General Help
---

### Post by Megistos on 2009-01-02
Hi all,

Whenever I open ccsm, the main window opens fine but if I click on any of the plugins, nothing happens i.e. no window opens for that plugin allowing me to change the settings. If I run ccsm from console and try, I get the following:

```
Traceback (most recent call last):
  File "/usr/local/lib/python2.5/site-packages/ccm/Pages.py", line 1303, in ShowPlugin
    pluginPage = PluginPage(plugin)
  File "/usr/local/lib/python2.5/site-packages/ccm/Pages.py", line 126, in __init__
    sortedGroups = sorted(plugin.Groups.items(), key=GroupIndexKeyFunc)
  File "/usr/local/lib/python2.5/site-packages/ccm/Utils.py", line 375, in GroupIndexKeyFunc
    return item[1][0]
KeyError: 0
```

Anyone have any idea how to solve this?

Thanks in advance

---

