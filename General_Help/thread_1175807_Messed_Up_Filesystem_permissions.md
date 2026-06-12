---
title: "Messed Up Filesystem permissions"
date: 2009-06-01
forum: General Help
---

### Post by jimi_hendrix on 2009-06-01
i was svn'ing e17, when all of a sudden my /home partition went read only

here is my fstab

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda7
UUID=0ce8baf2-d679-4ec3-861c-3b525066c5dc /               jfs     relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=38ee9b17-4b83-4fb4-81d3-53d12d1457ca /home           reiserfs relatime        0       2
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

my root is JFS and my /home is reiserfs

---

### Post by Wiebelhaus on 2009-06-01
Run this:

```
ls -la /home
```

And post output please.

---

### Post by Wiebelhaus on 2009-06-01
You need to do this from recovery mode:

.drmc file permissions, in a terminal: 

> sudo chmod 644 .dmrc
sudo chown user_name .dmrc
sudo chmod 755 /home/user_name
sudo chown -R user_name /home/user_name

if that fails:

> sudo chown -R user_name /home/user_name
sudo chmod 755 /home/user_name
sudo rm -rf /home/user_name/.dmrc

If none of this works your looking at a reinstall , But you may want to inspect /var/logs to try and determine what happened.

---

