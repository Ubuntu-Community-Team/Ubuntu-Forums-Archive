---
title: "sdb ubuntu missing after fresh windows sda installation"
date: 2009-03-15
forum: General Help
---

### Post by sponsoredwalk on 2009-03-15
Hi i recently reinstalled my old windows XP onto my sda1 drive, i also have ubuntu 7.10 on my sdb drive. My problem is that i cannot access any of my sdb files from windows, i only get "local disk C" when i open "computer2 and if i try to install a new drive and select the other disk it says it is working properly... how do i access all my music on the ubuntu disk directly from windows.

Also my grub has dissappeared it logs directly into windows and if i disable the disk and log into sdb(ubuntu) i get grrub error 15, i think i can reinstall it if i use my 7.10 disk and recover the system but i lost the disk, is it just a case of downloading a new 7.10, burning it and the BIOS will be easy to reconfigure or are there alternative easy ways of setting it up?

---

### Post by LiamWilson on 2009-03-15
Well. You can't access EXT3 from windows. But you can download a new 7.10 cd, access sdb, and edit the grub menu. (/boot/grub/menu.lst) with Gedit. But you'll probably need to do it with Root access.

(gksudo gedit /boot/grub/menu.lst) 

In a terminal. However, I'm not sure what you'd need to do from there.

---

### Post by taurus on 2009-03-15
1.  Windows won't read ext2/ext3 filesystem so you can't access your Ubuntu partition from windows unless you install fs-driver first, [http://www.fs-driver.org/](http://www.fs-driver.org/).

2.  When you reinstalled windows, it wiped GRUB from MBR so you need to reinstall GRUB back to MBR if you want to boot both Ubuntu and windows.

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

