---
title: "Logical Names of Mounted Partitions"
date: 2009-04-21
forum: General Help
---

### Post by satish_j on 2009-04-21
I have mounted 4 windows partitions in Ubuntu.Everytime system boots,it auto-detects these partitions,but the names displayed for these partitions are very annoying.i.e it says 42GB HardDisk,13.5GB HardDisk..........likewise..
How can i set ubuntu to display the actual Drive letters for these partitions instead of their sizes??
Thanks in advance..

---

### Post by Elfy on 2009-04-21
If you mount them with fstab you can give them any name you want.

For windows ntfs - the simplest method is to install ntfs-config, once installed there is a tool in System Tools which you can use to deal with them.

Or you can manually add them to fstab - [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

### Post by satish_j on 2009-04-21
Thanks for the reply...But,when I installed Ubuntu,it automatically detected windows partitions and mounted them at boot-up.
Now,if i go for fstab,will I have to disable this auto-mount feature of ubuntu OR can i go ahead directly without any issue.

---

### Post by Elfy on 2009-04-21
Please run this and post the result

```
cat /etc/fstab
```

---

### Post by satish_j on 2009-04-21
> **forestpixie said:**
> Please run this and post the result

```
cat /etc/fstab
```

Here is the output:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=a0e89d83-6f9d-4d39-91b7-4db80eb01738 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda7
UUID=c074ae55-47de-41dd-b218-2343313f0e73 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

---

### Post by Elfy on 2009-04-21
Ok - they aren't mounted through fstab - do as I showed earlier with the ntfs tool - post #2

If you want to do it _manually_ and need help post back with the results of

```
ls -al /dev/disk/by-uuid/
```

Also what do you want the different drives to be called, this will list them

```
sudo fdisk -l
```

---

