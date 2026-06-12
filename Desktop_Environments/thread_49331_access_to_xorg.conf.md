---
title: "access to xorg.conf"
date: 2005-07-15
forum: Desktop Environments
---

### Post by wingdom on 2005-07-15
how can i edit the xorg.conf file? when i poen it in a text editor i cant type or anything

---

### Post by f20cap1 on 2005-07-15
It's most likely a permissions issue.

Try ```
sudo gedit /etc/X11/xorg.conf
``` 

You may want to make a backup prior to editing.

---

