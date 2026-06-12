---
title: "partitions check, xp installed check, installing ubuntu??"
date: 2009-05-12
forum: General Help
---

### Post by intransit on 2009-05-12
Hi guys,

So i'm wondering what is going to have to my bootup?

the set up is as follows

/dev/sda1    ntfs         XP
/dev/sda2    linux-swap   Swap
/dev/sda3    ext3         Ubuntu 9.04

XP installed first. Ready to install ubuntu onto sda3 but i'm wondering what will happen after doing so to the boot process. Will grub look after the boot process and then its a matter of simply editing the grub file?

Cheers

---

### Post by hw-tph on 2009-05-12
If you leave everything to the defaults, grub will be installed on the master boot record of /dev/sda and the installation should pick up your Windows installation as well so you can select either OS when booting.

---

