---
title: "How to restore unity login screen"
date: 2013-04-13
forum: Desktop Environments
---

### Post by emcompu on 2013-04-13
I installed the Gnome rollback with 12.10 and have since went back to the Unity desktop environment. I uninstalled the gnome packages and deleted the gnome.desktop file from the xsessions directory. What I would like to do is get the original unity login screen back that installs with ubuntu desktop. Thanks.

---

### Post by mreq on 2013-04-13
See if you have lightdm installed. If you don't install it.

Afterwards, run ```
sudo dpkg-reconfigure lightdm
```

---

