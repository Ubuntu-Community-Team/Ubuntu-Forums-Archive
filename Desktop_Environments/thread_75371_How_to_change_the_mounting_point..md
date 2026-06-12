---
title: "How to change the mounting point."
date: 2005-10-13
forum: Desktop Environments
---

### Post by Adam Lee on 2005-10-13
Hi there : ) I just finished installing 5.10 and having a lot of fun with it.
However, all the disks are automatically mounted to my Desktop
and I was wondering if there is a way to change the mounting point to some where else ex/ /mnt/windows/

Ideas would be greately appreciated!

---

### Post by taurus on 2005-10-13
Yes, you can change your mountpoints in /etc/fstab.  Make sure you create those directories in /mnt first if you want to mount them there...

---

### Post by Adam Lee on 2005-10-13
[QUOTE=taurus]Yes, you can change your mountpoints in /etc/fstab.  Make sure you create those directories in /mnt first if you want to mount them there...[/QUOTE]

Wow that worked out greatly. However, those mounted disks have disappeared from Disk Mounter app on the panel. 
Is there way to recover them and still keep them in /mnt ??

Also can I add 

charset=utf8 

under <options> column? 
I need to give that option to read certain file names. 

Thx!
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /mnt/hda1     vfat    defaults        0       0
/dev/hda2       /mnt/hda2     vfat    defaults        0       0
/dev/hdb1       /mnt/hdb1     vfat    defaults        0       0
/dev/hdb5       /mnt/hdb5     vfat    defaults        0       0
/dev/hdb6       /mnt/hdb6     vfat    defaults        0       0
/dev/hdb7       /mnt/hdb7     vfat    defaults        0       0
/dev/hdb8       /mnt/hdb8     vfat    defaults        0       0
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sda        /media/usb0     auto    rw,user,noauto  0       0

```

---

### Post by manicka on 2005-10-13
You could bookmark them and they will appear in the 'Places' menu

---

### Post by Adam Lee on 2005-10-13
Manicka, I don't know how to bookmark a disk +_+;
When I right click on one of the mounted disks, shouldn't I see something like "bookmark this" or "make shortcut" ??

---

### Post by taurus on 2005-10-13
You may want to create a shortcut on your desktop then!!!  :)

---

### Post by Adam Lee on 2005-10-13
haha I got it working : ) Thanks everyone ;)

---

