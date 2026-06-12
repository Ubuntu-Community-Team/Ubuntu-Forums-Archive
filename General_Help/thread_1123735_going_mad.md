---
title: "going mad"
date: 2009-04-12
forum: General Help
---

### Post by looplu on 2009-04-12
new to Linux

trying to get my CRT screen resolution right , but when i change the aspect in S/R wrong -preferences , the "active apply" plane disappears ???  

its gone below the tool bar and wont resize, gahrrr !! what should i do?

surely not a full reinstall ?

---

### Post by taurus on 2009-04-12
Press <Ctrl><Alt>F2 and login again.  Then run

```
sudo dpkg-reconfigure -phigh xserver-xorg
```
Once it's done, press <Ctrl><Alt>Backspace to restart the X server. 

Otherwise, boot into recovery mode from GRUB menu and pick the xfix option to fix your X.

---

### Post by looplu on 2009-04-12
> **Taurus said:**
> Press <Ctrl><Alt>F2 and login again.  Then run

```
sudo dpkg-reconfigure -phigh xserver-xorg
```
Once it's done, press <Ctrl><Alt>Backspace to restart the X server. 

Otherwise, boot into recovery mode from GRUB menu and pick the xfix option to fix your X.

thanks for that Taurus 

the second fix , boot in grub - xfiix got me back to square one ..

sanity saved for now

---

