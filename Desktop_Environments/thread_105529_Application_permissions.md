---
title: "Application permissions"
date: 2005-12-18
forum: Desktop Environments
---

### Post by Rhino1 on 2005-12-18
I installed Dillo to use as a web browser, due to slow modem connections (14.4kbps).  The application works fine, but only if I open it through a terminal with sudo.   I originally installed it through apt-get, then reinstalled it through the Synaptic Package manager, both times got the same result.  I can read all of the files but have no permission to change or edit.  I checked the file and it has root ownership only!  How do I change ownership permissions easily, so I can select this off of the menu?  When I select file -->properties...all of the rename and edit functions are greyed out and under permissions it just states I'm not the owner.  thanks in advance.

---

### Post by endersshadow on 2005-12-18
```
chmod 755 filename
```

That command will work for it.  Just replace filename with the dillo executable :-D

---

