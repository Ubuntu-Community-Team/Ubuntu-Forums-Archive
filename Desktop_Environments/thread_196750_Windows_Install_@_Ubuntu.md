---
title: "Windows Install @ Ubuntu"
date: 2006-06-14
forum: Desktop Environments
---

### Post by ohman11 on 2006-06-14
I have a dual boot system now with XP and Dapper. Here is the deal, I got a newer ver. of win (Vista) and wanted to install it just to check it out but I dont want to have to install Dapper again. I think I remember reading that the windows install will mess up the mbr. How do I fix it after the win install? I have 1 drive with 2 partitions and windows is on the first and ubuntu on the second.

---

### Post by Amon_Re on 2006-06-14
Basicly, you install windows onto the ntfs partition, then boot from the live cd and chroot into your linux system.

From there it's just a matter of grub-install & it's done.

---

### Post by ohman11 on 2006-06-14
[QUOTE=Amon_Re]Basicly, you install windows onto the ntfs partition, then boot from the live cd and chroot into your linux system.

From there it's just a matter of grub-install & it's done.[/QUOTE]

  Well I dont have the live cd, is there another way to do this?

---

### Post by ????? on 2006-06-14
You need a dapper CD to fix grub after you install Vista. If you want, you can also try Vista by installing it virtually via VMWare Server

---

### Post by Amon_Re on 2006-06-14
Maybe, if TestDisk ([http://www.cgsecurity.org/wiki/TestDisk]("http://www.cgsecurity.org/wiki/TestDisk")) allows you to backup the mbr, then you could use TeskDisk (from within windows) to restore it.

Another possibility is to install grub into the boot sector of your linux partition, and set the ntfs partition as "active" before you install windows vista.

Once vista is installed, setting the linux partition as "active" again should suffice

---

### Post by frying_fish on 2006-06-14
with any form of live cd, such as knoppix, you need to boot a cd to rescue grub.  if you don't have the live cd, or knoppix et al, then download a copy. and the guide for recovering grub is at: [https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RecoveringGrub](https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RecoveringGrub)

---

### Post by Amon_Re on 2006-06-14
[QUOTE=?????]You need a dapper CD to fix grub after you install Vista. If you want, you can also try Vista by installing it virtually via VMWare Server[/QUOTE]

It need not be a dapper cd, any recent enough bootable cd with "chroot" will do

---

### Post by ohman11 on 2006-06-14
[QUOTE=Amon_Re]It need not be a dapper cd, any recent enough bootable cd with "chroot" will do[/QUOTE]

  I have the Dapper install cd, just not the live one.

---

### Post by Amon_Re on 2006-06-14
[QUOTE=ohman11]I have the Dapper install cd, just not the live one.[/QUOTE]

I don't have that cd, so i can't test/verify if it would work with that. Sorry

---

### Post by frying_fish on 2006-06-14
is there a way to boot a recovery mode from the install cd.

As if there is, or if you can break out of the installation once its loaded isolinux, see if there is chroot on it, and if so then you can just go ahead and fix grub.

Or, just download a small live cd that can do it.

---

### Post by Stereotypical Rage on 2006-06-14
[QUOTE=ohman11]I have the Dapper install cd, just not the live one.[/QUOTE]
Dapper Drake CDs are both Live and Install on one disc.

---

### Post by ohman11 on 2006-06-14
Well I used the install cd and used rescue mode and it has a place to reinstall grub....I am typing from Ubuntu as we speak. As far as Vista goes, it is pretty cool as far as eye candy but very slow and a mem hog. I hate windows but I do a lot of video editing and there are times I need windows......Thanks for all of the help!

---

