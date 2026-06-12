---
title: "How do I get grub to recognize an install on a disk I moved to a different computer?"
date: 2008-12-11
forum: General Help
---

### Post by bpont on 2008-12-11
My old Pentium III finally gave up the ghost.  I replaced it with a used Dell box and added my Ubuntu hard drive as a slave.  The master is XP.

My question is: can I run grub to recognize my perfectly good Ubuntu installation and have it simply create a proper dual boot menu and overwrite the MBR?

Also, how do I rewrite the MBR just in case things go terribly wrong and I am locked out of my XP installation?

Unfortunately, I still need XP for some stuff.

Thanks.

---

### Post by FoxIII on 2008-12-11
I'm not sure, but shouldn't you be able to change the priority of the disks so that the ubuntu disk is the master and xp is the slave and then use your ubuntu live cd to re-install grub (or update it) to set this up for you?

I may have this totally wrong, but that's the way I would initially try myself.

---

### Post by phidia on 2008-12-11
You don't say how the drive is installed and/or it's position in bios boot order-that will mean a lot to how you do this.
But if the drive is now the 2nd drive (is this a sata or pata drive?) then the fstab on the install partition and the /boot/grub/menu.lst will have to be edited to reflect the change. You can use a live cd to do that or get [super grub disk]("http://www.supergrubdisk.org/").

---

