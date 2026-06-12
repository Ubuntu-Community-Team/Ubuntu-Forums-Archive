---
title: "read-only file system?"
date: 2006-10-25
forum: Desktop Environments
---

### Post by hraposo on 2006-10-25
When I start the ubuntu the system don´t start several services like samba, etc, because it said that it's a read-only file system.
When I do fdisk - /dev/hda1 appears that I have not a correct partition table. What can I do?

---

### Post by bswilson on 2006-10-25
My guess would be that we can edit your **/etc/fstab** file, which is the filesystem table, so that when mounted your disk is read-write.  Can you share the contents of **/etc/fstab** here, so that we can try to help you?

---

### Post by hraposo on 2006-10-25
My fstab > # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro  0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0


---

### Post by bswilson on 2006-10-25
The line that says:

```
/dev/hda1 / ext3 defaults,errors=remount-ro 0 1
```

...means that if the disk has errors while booting up, it should be loaded as a read-only filesystem.  I'm curious, have you rebooted more than once since this problem occurred?  Because this _is_ the proper setting...

If you have rebooted more than once and you have this problem, try these 2 commands to check and repair any errors:

```
sudo fsck /dev/hda1
sudo e2fsck -c /dev/hda1
```

This *could* take a long time, depending on the size and speed of your disk.

---

