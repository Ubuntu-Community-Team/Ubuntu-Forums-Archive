---
title: "Partition Problem..."
date: 2006-03-02
forum: Desktop Environments
---

### Post by Swiss on 2006-03-02
I created 2 partitions for storing files securely by for some reason they dont show up in the file browser and I cant access them!

---

### Post by prizrak on 2006-03-02
You will need to mount them. Take a look at your fstab file to make sure the settings are correct.

---

### Post by Swiss on 2006-03-02
This is what it looks like:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda5       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda6       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0



How do you mount a drive?

---

### Post by dpm on 2006-03-02
[quote=Swiss]How do you mount a drive?[/quote] 
if the partitions are correctly defined in /etc/fstab,

```
sudo mount -a
``` 

will mount all the partitions in /etc/fstab at the specified locations. Everything that's in there will get mounted on every startup of the OS.

Otherwise, you can mount individual partitions with the mount command. Have a look at its man page.

```
man mount
``` 

BTW, it seems that your newly created partitions are not defined in /etc/fstab. Therefore, issuing a 'sudo mount -a' will not mount them until they are correctly defined.

What kind of partitions are they (ext3, FAT32, NTFS)? Where do you want to mount them? 

If you give some more info, I'm sure you'll get some more help.

Cheers.

---

