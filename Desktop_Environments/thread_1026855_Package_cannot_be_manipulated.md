---
title: "Package cannot be manipulated"
date: 2008-12-31
forum: Desktop Environments
---

### Post by spinstartshere on 2008-12-31
I have a package installed, matchbox-window-manager.  If I try to uninstall it, I get this error:

```
Removing matchbox-window-manager ...
dpkg (subprocess): unable to execute pre-removal script: Exec format error
dpkg: error processing matchbox-window-manager (--remove):
 subprocess pre-removal script returned error exit status 2
Errors were encountered while processing:
 matchbox-window-manager
```A similar thing happens when I try to reinstall it.  Is there another way I can remove it?

---

### Post by spinstartshere on 2009-01-18
bump

---

### Post by spinstartshere on 2009-01-25
I resolved this issue by following the instructions in [this]("http://www.linuxquestions.org/questions/showthread.php?p=3040967#post3040967") forum post.

---

