---
title: "Reinstalled grub gives me errors 17 and 13"
date: 2009-05-27
forum: General Help
---

### Post by darthlunchbox42 on 2009-05-27
I've got Ubuntu and Windows XP dual booted on two sperate hard drives on my computer.  A bit ago, I had to replace the XP hard drive and reinstall XP.  I've done this before, minus the new hard drive bit, so I knew that I'd have to reinstall grub.  I've been booting from the XP hard drive fine, but  to get into grub I have to boot from the Ubuntu hard drive, so all the following occurs when it boots that way.  If it boots from the XP drive, XP boots normally.

Through the live cd, I went into the terminal and input 'sudo fdisk -l'.  The output was this (edited down to the necessary bits):
> Disk /dev/sda: 320.0 GB
/dev/sda1     HPFS/NTFS

Disk /dev/sdb: 320.0 GB
/dev/sdb1     Linux
/dev/sdb2     Extended
/dev/sdb5     Linux swap / Solaris

I then opened grub in the terminal and did the following:
> > find /boot/grub/stage1
(hd1,0)
>root (hd1,0)
>setup (hd1)

After which I rebooted.  It opened grub fine, but when I tried to boot into Ubuntu I got 'Error 17: Cannot mount selected partition'.  When I tried to boot into XP, I got 'Error 13: Invalid or unsupported executable format'.  

Confused, I pressed 'c' to get at the command line from there.  I input 'find /boot/grub/stage1', but got a different output message:
> (hd0,0)
(hd2,0)
This, in my thoroughly unexperienced opinion, seemed to suggest that I had a mysterious third hard drive somewhere.  I don't have any flash drives hooked up, and nothing was in the cd drive.  I tried setting up grub on each of those partitions, but to no luck.

And just in case the information is needed, here's the Ubuntu and XP boot info from menu.lst:
> title		Ubuntu 8.04.2, kernel 2.6.24-23-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=d9828921-edee-468d-8315-b90b24fbac59 ro quiet splash
initrd		/boot/initrd.img-2.6.24-23-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-23-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=d9828921-edee-468d-8315-b90b24fbac59 ro single
initrd		/boot/initrd.img-2.6.24-23-generic


title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1

My thinking is that the problem lies in the fact that I have a new hard drive, and grub is looking for the old one, on which it was originally installed.  But I don't know where to go from here, any help would be appreciated.

---

### Post by VMC on 2009-05-27
If you want grub installed as the mbr: setup (hd0)

Also, since you didn't show the complete fdisk output, where is the '*' under the boot label?

---

### Post by darthlunchbox42 on 2009-05-27
Ach, my bad.  Here's the entire output of 'sudo fdisk -l':
```
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x18181817

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38912   312560608+   7  HPFS/NTFS

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000ab53a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       38536   309540388+  83  Linux
/dev/sdb2           38537       38913     3028252+   5  Extended
/dev/sdb5           38537       38913     3028221   82  Linux swap / Solaris
```

And as for setting up grub in hd0, where would I set root to?

---

### Post by VMC on 2009-05-27
Root is the root of where grub found stage1:
root (hd1,0)

---

### Post by presence1960 on 2009-05-27
you may want to delete the old hard disk entry in fstab if it is still there. Your new disk may have different UUID. Also try this for windows entry in menu.lst

> title		Microsoft Windows XP Home Edition
rootnoverify    (hd0,0)
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

When I had my setup like yours I had GRUB on the MBR of the Ubuntu disk and had the Ubuntu disk set to boot first in BIOS. Thus the map lines in the windows setup in menu.lst. Lets windows think it is on the first boot device.

---

