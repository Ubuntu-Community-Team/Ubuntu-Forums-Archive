---
title: "I Am Totally Lost. Please help!"
date: 2005-12-08
forum: General Help
---

### Post by bslusser on 2005-12-08
So I installed windows on my first drive and everything goes okay, then i install ubuntu on the second drive and install grub on the MBR and now things arent good. I have a liveCD and can access either drive but grub is giving me "error 25" at stage1.5 when i launch off the first disk.

here is my fdisk -l
```
 ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/hde: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hde1   *           1        5602    44998033+   c  W95 FAT32 (LBA)
/dev/hde2            5603       12161    52685167+   f  W95 Ext'd (LBA)
/dev/hde5            5603       12161    52685136    b  W95 FAT32

Disk /dev/hdg: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdg1   *           1        4677    37567971   83  Linux
/dev/hdg2            4678        4865     1510110    5  Extended
/dev/hdg5            4678        4865     1510078+  82  Linux swap / Solaris
``` 
here is my menu.lst
```
ubuntu@ubuntu:~$ cat /mnt/ubuntu/boot/grub/menu.lst
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         20

title           Ubuntu, kernel 2.6.12-9-386
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.12-9-386 root=/dev/hdg1 ro quiet splash
initrd          /boot/initrd.img-2.6.12-9-386
savedefault
boot

title           Ubuntu, kernel 2.6.12-9-386 (recovery mode)
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.12-9-386 root=/dev/hdg1 ro single
initrd          /boot/initrd.img-2.6.12-9-386
boot

title           Ubuntu, memtest86+
root            (hd1,0)
kernel          /boot/memtest86+.bin
boot

title           Other operating systems:
root

title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1

```

---

### Post by Bachstelze on 2005-12-08
My guess is that since your drives are /dev/hde and /dev/hdg you have to change the "root" line to (hd5,0) for windows and (hd7,0) for Ubuntu.

---

### Post by bslusser on 2005-12-08
i still get error 25 after changing it to those values :confused:

---

### Post by bslusser on 2005-12-08
bump!

 please does anyone have any ideas? any at all??

---

### Post by drogoh on 2005-12-08
From the debian-boot mailing list (found via your friendly neighborhood Google):

> Error 25 is unrecognized command which means that grub-installer made a booboo generating menu.lst.

Edit:  What is the full error message?  That could prove more useful since that mailing list post is 1.5 years old.

---

### Post by bslusser on 2005-12-08
its says:
grub loading stage1.5

grub loading, please wait...
error 25

and the only thing i can do is reboot

---

### Post by bslusser on 2005-12-08
So i can get windows to boot with root (hd0,0) but ubuntu will not load with (hd1,0) when i do that i get a Error 25: disk read error.. is it possible my second drive is damaged or just mbr problems? with the liveCD i can go through the files on the ubuntu system


does anyone have A suggestion?

---

### Post by Bachstelze on 2005-12-08
Try with (hd2,0) for ubuntu.

---

### Post by bslusser on 2005-12-08
didnt work

I've tried lots of combos of (hdx,0) and (hdx,1) most were error25 disk read error or does not exist. does my menu.lst and fdisk look alright?

---

### Post by Bachstelze on 2005-12-08
(hdx,1) certainly won't work, since your Ubuntu root FS is on /dev/hdg1...

---

### Post by bslusser on 2005-12-08
sorry x was refering to any number. ive tried lots of values.

ill probably just give up. thanks tho

---

### Post by mherring on 2005-12-08
I've had the identical problem--I solved it only by installing grub to a floppy during the install.
Coincidentally, my drives also start at hde---in my case because they are on a Highpoint controller and not the main IDE bus.

When my menu (below) is called from grub on the floppy, all is well.  Thus, I suggest that we can set aside all the comments about changing (hdx,y)

If memory serves, I had the same issue with 5.04.

You'll find a thread on this which I started.  My final outcome will go there.

Here is a clip from my "menu.lst":

title           Ubuntu, kernel 2.6.12-10-386
root            (hd2,0)
kernel          /boot/vmlinuz-2.6.12-10-386 root=/dev/hdg1 ro quiet splash
initrd          /boot/initrd.img-2.6.12-10-386
savedefault
boot

title           Ubuntu, kernel 2.6.12-10-386 (recovery mode)
root            (hd2,0)
kernel          /boot/vmlinuz-2.6.12-10-386 root=/dev/hdg1 ro single
initrd          /boot/initrd.img-2.6.12-10-386
boot

title           Ubuntu, memtest86+
root            (hd2,0)
kernel          /boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
#title          Other operating systems:
#root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hde1
title           Windows
root            (hd0,0)
savedefault
chainloader     +1

---

### Post by bslusser on 2005-12-08
yes my harddrives are also on a controller and not the main IDE bus.

the only solution is using a floppy huh?

---

