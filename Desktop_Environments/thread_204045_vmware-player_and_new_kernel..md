---
title: "vmware-player and new kernel."
date: 2006-06-26
forum: Desktop Environments
---

### Post by denisesballs on 2006-06-26
I've upgraded to 2.6.15-25-686, and I can't get vmware-player to reconfigure. I've installed the restriced modules, but everytime I go to reinstall vmware I get:

```
Starting VMware services:
   Virtual machine monitor                                            failed
   Virtual ethernet                                                   failed
Module vmnet is not loaded.  Please verify that it is loaded before
running this script.

invoke-rc.d: initscript vmware-player, action "start" failed.
dpkg: error processing vmware-player (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 vmware-player
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

I haven't seen anyone else with that specific problem. Anyone?

---

