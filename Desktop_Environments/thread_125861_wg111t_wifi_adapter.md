---
title: "wg111t wifi adapter"
date: 2006-02-05
forum: Desktop Environments
---

### Post by thejoeandchip on 2006-02-05
i have used ndiswrapper to install the driver for the wg111t but when i hit -l for a list of the drivers all it says is

Installed ndis drivers:
netwg11t        driver present

when it should say hardware present also, because the adapter is pluged in. help would be appreciated.:)

---

### Post by jasmuz on 2006-02-05
Did you insert the kernel module for Ndiswrapper like this?

$ sudo ndiswrapper -m

then check it out like this 
$ lsmod | grep ndiswrapper   

It should be already loaded

---

