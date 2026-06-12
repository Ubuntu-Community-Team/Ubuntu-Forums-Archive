---
title: "Xorg.conf Borked Up-Need to Restore"
date: 2006-08-28
forum: Desktop Environments
---

### Post by ronmarley1 on 2006-08-28
Hi All,
I was playing around and changed the Xorg.conf file and now I can't boot to a GUI.  I can boot the Live CD.  I thought I'd copy the Xorg.conf file created by the Live CD, but it won't let me mount my linux partition.  How can I mount the linux partition so that I can copy the new file over top of the old (corrupt) one?
Thanks in advance for the help.

---

### Post by lkh on 2006-08-28
Hi,

you have tried "sudo dpkg-reconfigure xserver-xorg" after a non-graphical login?

---

### Post by ronmarley1 on 2006-08-28
Hi,
Thanks for the quick reply.  I did as you suggested, and everything was OK until I rebooted.  It looks like it did not save the changes, though.  Any ideas?

---

### Post by Rog131 on 2006-08-28
Copying xorg.conf:

Where penquin is ?
> ubuntu@ubuntu:~$ sudo fdisk -l /dev/hdb

Disk /dev/hdb: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        7228    58058878+  83  Linux
/dev/hdb2            7229        9963    21968887+   f  W95 Ext'd (LBA)
/dev/hdb5            7417        9963    20458746    b  W95 FAT32
/dev/hdb6            7229        7416     1510047   82  Linux swap / Solaris

Partition table entries are not in disk order


Mounting:

> sudo mount dev/hdb1 /media


Copying:

> ubuntu@ubuntu:/$ sudo cp /etc/X11/xorg.conf /media/etc/X11/xorg.conf

---

### Post by ronmarley1 on 2006-08-28
Hi Rog131,
Thanks for the reply.  All is well now.

---

