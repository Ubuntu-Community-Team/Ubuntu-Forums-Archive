---
title: "mount: no medium found"
date: 2009-03-22
forum: General Help
---

### Post by aguaba on 2009-03-22
Hey all,

During boot I get the following message:
"Mounting local filesystems
 mount: no medium found             [fail]"

The fstab is this:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc /proc proc defaults 0 0
# /dev/sda6
UUID=415e1c34-2bdf-4512-af2e-90ba1582ceec / ext3 nouser,relatime,errors=remount-ro,atime,auto,rw,dev,exec,suid 0 1
# /dev/sda5
UUID=4b7c92f2-9c61-4c3d-b195-3c73dfc9b85f none swap sw 0 0
/dev/hda /media/cdrom0 auto user,utf8,atime,auto,rw,dev,exec,suid 0 0
/dev/sda3 /media/DATA vfat defaults,uid=1000,gid=1000,auto,rw,nouser 0 1

Is something wrong?
thanx

---

### Post by Seiji338 on 2009-03-22
Probably the cdrom line. Mine looks like this by default in 8.10:

```
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

---

### Post by aguaba on 2009-03-22
Should I change this? I don't know.. I'm afraid I might cause a severe damage to the system.

---

### Post by Seiji338 on 2009-03-23
Make a backup of the fstab file so if anything unexpected happens you can restore from the backup.

To make a backup:

```
sudo cp /etc/fstab /etc/fstab.old
```

To restore from backup:

```
sudo cp /etc/fstab.old /etc/fstab
```

The part I was interested in is in bold. The second auto means it would be automatically mounted at boot. If you don't have media in the drive it would throw an error. Change this to **noauto**.

```
/dev/hda    /media/cdrom0    auto    user,utf8,atime,**auto**,rw,dev,exec,suid    0    0
```

If you're still getting the error, post the output of:

```
sudo fdisk -l
```

---

### Post by aguaba on 2009-03-26
Thanx Seiji338! SOLVED

---

