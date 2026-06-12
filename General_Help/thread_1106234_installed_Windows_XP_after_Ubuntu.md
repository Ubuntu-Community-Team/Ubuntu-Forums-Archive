---
title: "installed Windows XP after Ubuntu"
date: 2009-03-25
forum: General Help
---

### Post by Unkraut on 2009-03-25
Hi!

Once upon a time I had a second hard drive with Windows XP installed on it. That hard drive died tragically. Now after several months of mourning have passed I decided it was time to go on and install a new Windows XP on my other hard drive after shrinking the Ubuntu partition.

After installing Windows I booted from Intrepid live CD to reinstall GRUB. In GRUB I did this:

```

grub> find /boot/grub/stage1
 blah blah - found stage 1 at (hd0,0)
grub> root (hd0,0)
 blah whatever
grub> setup (hd0)
 mkay
grub> quit

```

My new partition layout looks as follows:

```

trollkotze@schrotthaufen:~$ sudo fdisk -lu
[sudo] password for trollkotze:

Platte /dev/sda: 250.0 GByte, 250059350016 Byte
255 Köpfe, 63 Sektoren/Spuren, 30401 Zylinder, zusammen 488397168 Sektoren
Einheiten = Sektoren von 1 × 512 = 512 Bytes
Disk identifier: 0x000293c0

   Gerät  boot.     Anfang        Ende     Blöcke   Id  System
/dev/sda1              63   357301664   178650801   83  Linux
/dev/sda2   *   357301665   482094584    62396460    7  HPFS/NTFS
/dev/sda3       482094585   488392064     3148740   82  Linux Swap / Solaris
trollkotze@schrotthaufen:~$ 


```

So I added to the end of my /boot/grub/menu.list the following lines to make Windows available:

```

# This entry was manually added by the Master for a non-linux OS
# on /dev/sda2
title           Windows
root            (hd0,1)
savedefault
makeactive
chainloader     +1

```

But now when I boot and select Windows from the GRUB menu the screen just goes black and the computer restarts. What did I do wrong?


EDIT: After just trying again the screen didn't go black instantly but instead Windows told me it had noticed that the last boot was unsuccessful and gave me the options to start windows normally, or in recovery mode, or in recovery mode without graphics, or whatever. I tried all the options. There quickly appear a lot of error messages having to do something with my hard drive - something with ata.0somenumber blah blah. Screen goes black then, too fast to actually read the error messages and computer reboots. Maybe this is problem is too Windows related. But anyway - any ideas?

---

