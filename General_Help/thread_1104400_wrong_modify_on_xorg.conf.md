---
title: "wrong modify on xorg.conf"
date: 2009-03-23
forum: General Help
---

### Post by hero3 on 2009-03-23
I edited wrong the file xorg.conf and now when kubuntu not work fine... when i start the system i see black page with login information request.
i insert it and then happens nothing!
how can i resolve this?

sorry for my english

---

### Post by sisco311 on 2009-03-23
Switch to a virtual terminal (Ctrl+Alt+F2), log in and try to generate a new xorg.conf file:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Or boot in Recovery Mode and select the *xfix - Try to fix X server* option from the Recovery Menu.

---

