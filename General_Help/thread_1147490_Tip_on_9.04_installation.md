---
title: "Tip on 9.04 installation"
date: 2009-05-03
forum: General Help
---

### Post by lelmo85 on 2009-05-03
The following problem has occurred over several Ubuntu revisions. I download, reboot and get thrown to an ash shell. In my case it said there was no such disk-sdc1. To correct, I typed "e" (no "") when the splash screen appeared and revised the command line to show the correct disk (sdb1 for me) If you want to follow the action on startup you can erase "quiet". Also, someone way back said add the phrase "all_generic_ide" at the end of the command line. Whatever - it works. I have two four-year old nVidia graphics cards which may be jamming up the auto install. I had to change the command line in /boot/grub/menu.lst. I use vim text editor. I never have been able to get the nVidia restricted graphics to work. Had to reinstall every time.

---

