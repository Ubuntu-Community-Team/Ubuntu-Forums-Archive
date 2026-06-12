---
title: "Mount 3th hard drive"
date: 2005-12-19
forum: Desktop Environments
---

### Post by doc_holiday on 2005-12-19
I've just bought a new hd because the old one was breaking down. I've started the computer without the almost broken one. So I have 2 hd's and a cd-rom at first install. I've replaced the cd rom with the old hd, but I can't mount it.

My fstab looks like this:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda6       /home           ext3    defaults        0       2
/dev/hdb        /media/hdb      ext3    defaults        0       2
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

In my /dev there is no other hd then hda and hdb.
How can I mount the hd?

---

### Post by wounded on 2005-12-19
"sudo fdisk -l" should list every detected physical drive as well as its partitions. From there you can just look at the thingy ( :P ) /dev/hdb1 or whatever and mount it either from the command line or put it in fstab (and then "sudo mount -a" i believe). That help?

---

### Post by dcstar on 2005-12-19
[QUOTE=doc_holiday]I've just bought a new hd because the old one was breaking down. I've started the computer without the almost broken one. So I have 2 hd's and a cd-rom at first install. I've replaced the cd rom with the old hd, but I can't mount it.

My fstab looks like this:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda6       /home           ext3    defaults        0       2
/dev/hdb        /media/hdb      ext3    defaults        0       2
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

In my /dev there is no other hd then hda and hdb.
How can I mount the hd?[/QUOTE]
hda**1** means partition 1 on your first IDE device (hda), hda**2** means the second partition etc.

hda is the Master IDE device on the first channel, hdb is the slave, hdc is the Master on your second IDE channel, hdd is the slave IDE device - if you move devices (or replace them), make the necessary changes to your fstab file - or:

Go to: System-Administration-Disks and you should see all your drives listed, you should be able to partition/mount it from that tool.

---

### Post by doc_holiday on 2005-12-21
Thank you Guys, it worked for me.

---

