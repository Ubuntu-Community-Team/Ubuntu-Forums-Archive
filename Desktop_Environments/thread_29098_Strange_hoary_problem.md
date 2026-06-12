---
title: "Strange hoary problem"
date: 2005-04-22
forum: Desktop Environments
---

### Post by hayluc on 2005-04-22
I have installed Hoary on a toshiba 1005 s157 (celeron 1066, 500mb ram) laptop.  Warty was very stable on this machine.  The problem I am now having is that after running for a few hours the system seem to speed up.  To illustrate, the throbber on firefox starts spinning extremely fast, the menus on gnome drop down, but immedianty pop back up, games start running way to fast.  The problem has occured using i386, i686, as well as a custom kernel (the custom kernel was not compiled with cpu frequency scaling as it is not supported by the celeron)  I am using ndiswrapper to provide a driver for a DWL-G630.  I am not sure if it is related.  Any ideas?  P.S. a reboot fixes the problem for a few hours...

---

### Post by hayluc on 2005-04-24
Seemed to have solved problem.  Switched ndiswrapper driver to ASUS wa-138g WinXP driver from D-link DWL-G630 shipping WinXP driver.  System seems stable now...

---

