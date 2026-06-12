---
title: "ntfs-3g and hidden files"
date: 2006-08-30
forum: Desktop Environments
---

### Post by misosofos on 2006-08-30
Hi all:

I have recently installed ntfs-3g package, added 3 ntfs partitions to my fstab and got loaded the fuse module.

It worked properly, but now I can't see hidden files stored on these partitions.

After I installed ntfs-3g, partitions where mounted using ntfsprogs and I was able to see hidden files.

It can be due to umask? Some ntfs-3g limitation?

Here is my fstab file:

```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda4       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda3       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/sda1 /media/sda1 ntfs-3g silent,umask=007,gid=46,locale=es_ES.utf8,no_def_opts,allow_other 0 0
/dev/sda5 /media/sda5 ntfs-3g silent,umask=007,gid=46,locale=es_ES.utf8,no_def_opts,allow_other 0 0
/dev/sda6 /media/sda6 ntfs-3g silent,umask=007,gid=46,locale=es_ES.utf8,no_def_opts,allow_other 0 0
```

---

### Post by ciscosurfer on 2006-08-30
I can see hidden files just fine using ntfs-3g

Here's the line in my /etc/fstab```
/dev/dev_name /media/mount_point ntfs-3g silent,umask=0,locale=en_US.utf8,no_def_opts,allow_other    0    0
```

---

### Post by misosofos on 2006-08-30
Thanks ciscosurfer!

You are great!

---

### Post by ciscosurfer on 2006-08-30
> **misosofos said:**
> Thanks ciscosurfer!

You are great!

Anytime!  Glad it worked! :KS

---

### Post by misosofos on 2006-08-30
Well...

It was just for a while :confused: 
Now it doesn't show hidden files again!

---

