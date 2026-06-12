---
title: "Grub Help Please"
date: 2008-12-02
forum: Desktop Environments
---

### Post by sromagazine on 2008-12-02
I tried to load Ubuntu on my dads computer and when it tried to re size his current partition it died.  So I rebooted and now it comes up with grub loader error problem.  How can I just use the boot CD and edit grub so it will boot off his xp partition.  I don't mind the grub menu coming up just as long as it defaults to xp.  I know I'm suppoed to use to xp recovery cd to fix it but when I use it the computer just reboots so that's not really an option.

---

### Post by caljohnsmith on 2008-12-02
You could just reinstall a Windows MBR (Master Boot Record) so you would boot directly into Windows on start up. To do that, boot your Live CD, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo apt-get install syslinux
sudo dd if=/usr/lib/syslinux/mbr.bin of=/dev/[COLOR="Blue"]sda[/COLOR]
```
That will install a Windows MBR to the internal sda drive. Next please post the output of:
```
sudo fdisk -l
```
And make sure the Windows partition (the NTFS/FAT partition) has an asterisk * next to it under the "boot" heading. If not, we can work from there, otherwise reboot and see if you go directly into Windows.

---

### Post by sromagazine on 2008-12-03
Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        3647    29294496    7  HPFS/NTFS

gonna reboot now.

---

