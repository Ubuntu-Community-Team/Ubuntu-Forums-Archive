---
title: "[SOLVED] grub boot problem"
date: 2008-12-11
forum: General Help
---

### Post by Stolea on 2008-12-11
Hi,
I have 4 physical hard disks on my computer. I use grub to dual boot because I still have to use Windoze for some work like accounts. For some reason grub can't boot Windoze anymore. It will boot Ubuntu (hd 0/0) but it seems to have lost track of my Windoze disk. I have tried changing (hd 2/0) to (HD 1/0), but it doesn't do anything. The drive is fine, I can boot it if I change the startup order in bios.
How can I find what setting I need, or am I doomed to change things on a bios level if I want to change operating systems?

---

### Post by neu2buntu on 2008-12-11
paste the output of :  sudo fdisk -l ... this will show the disk partitions,if you have not already tried this

---

### Post by Stolea on 2008-12-11
Here is the output.

> Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0cd90cd8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               2       24321   195350400    f  W95 Ext'd (LBA)
/dev/sda5               2       24321   195350368+   7  HPFS/NTFS

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2fd5be2d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1          61      489951   83  Linux
/dev/sdb2              62       38913   312078690    f  W95 Ext'd (LBA)
/dev/sdb5              62         669     4883728+  82  Linux swap / Solaris
/dev/sdb6             670       12827    97659103+  83  Linux
/dev/sdb7           12828       22553    78124063+  83  Linux
/dev/sdb8           22554       38913   131411668+  83  Linux

Disk /dev/sdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd4e5d4e5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/sdc2            2551       38913   292085797+   f  W95 Ext'd (LBA)
/dev/sdc5            2551       38913   292085766    7  HPFS/NTFS

Disk /dev/sdd: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3c913c90

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               2       24321   195350400    f  W95 Ext'd (LBA)
/dev/sdd5               2       23046   185108931    7  HPFS/NTFS
/dev/sdd6           23047       24321    10241406   17  Hidden HPFS/NTFS


The Windoze Boot partition is on sdc1

---

### Post by neu2buntu on 2008-12-11
god this is a complicated setup you have, it seems that because you have 2 boot flags here and grub should have the only boot flag it cant load windoze... do you have gparted installed on you linux partition?  you will also have to edit your menu.lst file..  paste the output of :  gedit /boot/grub/menu.lst
  to see what is going on here... thanks

---

### Post by Stolea on 2008-12-11
> title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/vmlinuz-2.6.24-19-generic root=UUID=c7207fdb-9512-4603-adc1-de8ad596a1a5 ro quiet splash
initrd		/initrd.img-2.6.24-19-generic
quiet


title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,0)
kernel		/vmlinuz-2.6.24-19-generic root=UUID=c7207fdb-9512-4603-adc1-de8ad596a1a5 ro single
initrd		/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,0)
kernel		/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
title		Microsoft Windows XP Professional
root		(hd2,0)
savedefault
map		(hd0) (hd2)
map		(hd2) (hd0)
chainloader	+1
default 0

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdd6
# title		Microsoft Windows XP Professional
# root		(hd3,5)
# savedefault
# map		(hd0) (hd3)
# map		(hd3) (hd0)
# chainloader	+1

the second windoze is a ghost boot, in case the other one fails.

---

### Post by neu2buntu on 2008-12-11
according to your fdisk readout your master boot record is on (hd2,0).... your menu.lst file doesnt point to your kernel properly either..  have you reinstalled anything lately?   windows cant have a boot flag (master boot record either, your grub has to control all this!  the only easy way i can see around this is to reinstall ubuntu to drive sdc (with all drives plugged in,if any are external) and in the last step of install click advanced and make sure you put mbr on sdc (hd2,0) and this will give you a new grub bootloader . windows will only be able to boot through grub after this too....hope this is of some help..................................................OOOPS read the ubuntu install wrong it should be reinstall to drive sdb or (hd1,0) and not sdc as this is your win partition sorry

---

### Post by meierfra. on 2008-12-11
I don't see any  reason to reinstall Ubuntu. Try these:

title Microsoft Windows XP Professional  (hd1)
root (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1

title Microsoft Windows XP Professional  (hd2)
root (hd2,0)
map (hd0) (hd2)
map (hd2) (hd0)
chainloader +1

and 

title Microsoft Windows XP Professional  (hd3)
root (hd3,0)
map (hd0) (hd3)
map (hd3) (hd0)
chainloader +1

Do NOT use "default 0" in the Windows items.
If none of these work, we will have to  have a closer look at your setup.

---

### Post by Stolea on 2008-12-11
Thanks guys it worked. I had guessed the (hd1/0) correct, but didn't have the map settings right.
Cheers

---

