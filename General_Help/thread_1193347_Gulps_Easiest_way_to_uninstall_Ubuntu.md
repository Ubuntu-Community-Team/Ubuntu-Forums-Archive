---
title: "*Gulps* Easiest way to uninstall Ubuntu?"
date: 2009-06-21
forum: General Help
---

### Post by Oizu on 2009-06-21
Or failing that, is there anyway for me to be able to use the space to store some files off of windows, without uninstalling, but failing that, how can i uninstall?

Thanks

---

### Post by gettinoriginal on 2009-06-21
Never tried it, but I found this link for you:
[http://bobmorris.wordpress.com/2008/02/09/how-to-uninstall-ubuntu-on-dual-boot-windows-xp-using-windows-only/](http://bobmorris.wordpress.com/2008/02/09/how-to-uninstall-ubuntu-on-dual-boot-windows-xp-using-windows-only/)

---

### Post by SuperSonic4 on 2009-06-21
You can use gparted from a live cd to reduce the size of the ubuntu partition and create an ntfs partition for windows data.

Remember to hit apply at the end

---

### Post by oldos2er on 2009-06-21
> **Oizu said:**
> Or failing that, is there anyway for me to be able to use the space to store some files off of windows, without uninstalling, but failing that, how can i uninstall?

Thanks

 Are you using a Wubi install, or did you install Ubuntu to its own partition? 

 First thing you want to do is reinstall Windows boot loader. After that's done and you're booted to Windows, you can safely delete Ubuntu's partition(s).

---

### Post by egalvan on 2009-06-21
To uninstall, the prevoius post gave some good info.

----Make sure you have a backup of any data you don't want to lose...
mucking around with partitions, though generally safe,
is still open to problems.----

If you do not have a Windows Boot CD, though...

This should be done in two stages....

Stage one... restore Microsoft MBR
(this removes GRUB, and leaves you with a working, MS-OS machine.)


Stage two... recover Linux partitions for MS use.

The SuperGrub CD can do the first easily.

download at 

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

Second...
An Ubuntu LiveCD will work,
also, PartedMagic LiveCD will allow you to easily recover Linux partitions.

download at

[http://partedmagic.com/](http://partedmagic.com/)

Boot up, run gparted, and delete any linux partitions.


If you want specific help with parititions, then run gparted, take a screen-shot, and upload it here.

---

