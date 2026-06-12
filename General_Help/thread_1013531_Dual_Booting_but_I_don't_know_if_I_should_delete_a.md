---
title: "Dual Booting but I don't know if I should delete a partition"
date: 2008-12-16
forum: General Help
---

### Post by mgralley on 2008-12-16
I want to choose between booting Windows XP and Ubuntu. The problem is that I don't know if I should delete sda5 logical partition for the Windows install. Will this mess up any data stored on the sda1 partition, or crash the entire HDD? Or will everything be OK if I delete sda5 and install a Windows OS under Ubuntu?

---

### Post by dcstar on 2008-12-17
> **mgralley said:**
> I want to choose between booting Windows XP and Ubuntu. The problem is that I don't know if I should delete sda5 logical partition for the Windows install. Will this mess up any data stored on the sda1 partition, or crash the entire HDD? Or will everything be OK if I delete sda5 and install a Windows OS under Ubuntu?

You should not need to delete anything, the Ubuntu install will resize any Windows partition to make space for itself.

You cannot "install a Windows OS under Ubuntu" unless it is in a Virtual Machine.

---

### Post by unf4b1x on 2008-12-17
If you want to install Ubuntu after WinXP or vice versa, try reading this: [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by TeXtonyx on 2008-12-17
If there is nothing valuable on sda5 or its backed up, go ahead
and delete and leave the space unallocated. Then when you install
Windows you can install it to the unallocated space (pay attention
to how large the deleted partition is) and there is no worry
about overwriting Ubuntu. Resizing the drive 'on the fly' doesn't
work perfectly, this way is safer.

---

### Post by mgralley on 2008-12-17
I'll try it as VM first and if it doesn't work, then I'll try deleting sda5. If your wondering sda5 contains Linux swap/Solaris. So would it still be OK to delete if the VM doesn't work?

---

### Post by TeXtonyx on 2008-12-17
No, the logical swap partition won't work. Mostly they are 1GB or
less in size, but sometimes 2GB. Unless you changed this to about
10GB it is going to be way too small for XP. Ubuntu is sometimes
installed within Windows, a method called Wubi. Otherwise they
are all on separate partitions, Windows is not under Ubuntu and
Ubuntu is not under Windows(unless Wubi) there is no under to it.

If you meant the difference between a Windows bootloader and
a Linux bootloader, either one can be installed to the MBR.
Windows uses boot.ini for its menu options, and Linux uses
usually grub and a menu.lst for its boot options. "Under" all
by itself, doesn't include being under other boot menu options.

---

### Post by mgralley on 2008-12-17
OK so I can't delete the sda5. I guess I'm pretty much stuck with using VmWare. I have it installed with WINE, but it won't load. The options to start it are there, but the window won't open.

---

