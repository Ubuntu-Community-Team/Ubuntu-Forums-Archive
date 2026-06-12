---
title: "Error 17 SATA disk"
date: 2007-09-05
forum: Dell  Ubuntu Support
---

### Post by Mariachi on 2007-09-05
I'm a newbie in Linux, I have a P4 Dell Optiplex 170L with one port for SATA disk

The Master HD has XP, I installed a second one and installed Ubuntu. However, I have a third Sata disk where I store all my music, pics, etc and I realize that because of this disk I was getting the "Grub Error 17".

When I boot from Live Cd, it recognizes all three disks, I can even navigate through them. The thing is that when I boot normally it gives me "Grub Error 17". If I unplug the Sata disk it won't give me any errors, it displays the options to boot either from my first HD (WinXP) or my second HD (Ubuntu) but the Sata disk has to be unplugged in order for the Grub to boot correctly, and obviously the disk won't be available on any of the OS.

How can I make the Grub recognize my Sata disk and boot normally, or at least to give me the option to use it in WinXP.


Thanks for all your help!!

---

### Post by Mariachi on 2007-09-07
Nothing close, at least ... :(

---

### Post by neptho on 2007-09-07
Adding this disk has changed your SATA layout, it seems.

So if the first was /dev/sda, and the second was /dev/sdb, when you added it, it seems that the third may have become /dev/sdb, and the second is now /dev/sdc.  You'll have to reinstall grub to the primary partition, or edit your /boot/grub/menu.lst to point to the new disk.

---

### Post by Mariachi on 2007-09-14
And how do I edit the Grub ... ??

---

### Post by meierfra on 2007-09-15
post the output of

```
sudo fdisk -l
```

and

```
 cat /boot/grub/menu.lst
```
(l is a lower case L)

---

