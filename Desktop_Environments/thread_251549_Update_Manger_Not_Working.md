---
title: "Update Manger Not Working"
date: 2006-09-05
forum: Desktop Environments
---

### Post by eyesonly on 2006-09-05
I have looked at related posts but could not get this going again. Unfortunately I am getting nowhere with updates and python problems here is what I see My gnome terminal also stopped working.  Don't know if it is related.

Here is my output.



jbs@jbs-ubuntu:~$ gksudo update-manager
/usr/lib/python2.4/site-packages/apt/__init__.py:17: FutureWarning: apt API not stable yet
warnings.warn("apt API not stable yet", FutureWarning)
Traceback (most recent call last):
File "/usr/bin/update-manager", line 71, in ?
app.main(options)
File "/usr/lib/python2.4/site-packages/UpdateManager/UpdateManager.py", line 749, in main
self.fillstore()
File "/usr/lib/python2.4/site-packages/UpdateManager/UpdateManager.py", line 599, in fillstore
self.initCache()
File "/usr/lib/python2.4/site-packages/UpdateManager/UpdateManager.py", line 716, in initCache
self.cache._depcache.Init()
SystemError: E:The package mfc8420lpr needs to be reinstalled, but I can't find an archive for it.
jbs@jbs-ubuntu:~$ 

I could use some help.........

Thanks

---

