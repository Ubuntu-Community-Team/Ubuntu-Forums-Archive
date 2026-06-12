---
title: "How to uninstall Ubuntu &amp; Grub from multiple boot system?"
date: 2006-05-13
forum: Desktop Environments
---

### Post by till on 2006-05-13
Dear all,

Currently, my desktop PC is running Edubuntu 5.10 and Windows XP Home as a multiple boot system with Grub as boot manager. Edubuntu and Windows run on different partitions of the same hard disk. How do I uninstall Edubuntu and Grub boot manager, so that Windows still would be booting after uninstalling them?

Thank you very much for your help!

---

### Post by louis_nichols on 2006-05-13
Well, I'd start by removing Grub. This is done very easily using the Win XP install cd. Put it in your CD drive, start your computer so that it boots from it. At the option sscreen, press "R" to enter rescue mode and, after getting to the command line, issue the commands

```
fixmbr
``` then ```
fixboot
```
so this deletes grub and makes Win boot by default. After booting win xp, right click on My Computer, choose manage, then go to Disk Management and simply format the partition on which edubuntu is currently installed.

---

### Post by till on 2006-05-14
Thank you very much!

---

