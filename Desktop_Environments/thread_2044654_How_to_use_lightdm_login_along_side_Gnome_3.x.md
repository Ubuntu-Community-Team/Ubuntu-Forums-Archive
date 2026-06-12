---
title: "How to use lightdm login along side Gnome 3.x?"
date: 2012-08-19
forum: Desktop Environments
---

### Post by callmesuspect on 2012-08-19
Hello, I recently installed ubuntu 12.04, I didn't really care for the unity setup, so I installed gnome.

This, however, changed my login screen to the gnome login screen, and I have been struggling with how to switch back to the old, pretty, default login screen.

I've tried reinstalling lightdm, replacing unity, everything short of uninstalling gnome, can someone help me?

I just want to change the login screen to lightdm (Or unity, whatever the default for ubuntu 12.04 is) but still use gnome when logged in.

thanks.

---

### Post by zombifier25 on 2012-08-20
Run this command:
```
sudo dpkg-reconfigure lightdm
```
and choose lightdm at the choices. Then restart your computer.

---

### Post by callmesuspect on 2012-08-22
Thanks! This worked.

---

