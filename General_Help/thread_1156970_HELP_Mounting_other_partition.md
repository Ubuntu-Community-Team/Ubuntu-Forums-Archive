---
title: "HELP: Mounting other partition"
date: 2009-05-12
forum: General Help
---

### Post by infernus_crusher on 2009-05-12
I just upgraded to Jaunty Jackalope and the partition containing Windows XP didn't show up like it used to do on Intrepid Ibex. Can anybody teach me how to mount it manually? I remember that it has something to do with the directory /etc/fstab in File Systems.

---

### Post by Greenwidth on 2009-05-12
To mount it manually there should be an entry on the 'Places' menu no?

---

### Post by infernus_crusher on 2009-05-20
No it is nowhere in Places. I've restarted XP several times thinking there might be a bug that prevents it to be accessed by Ubuntu but it doesn't seem to work. It probably hasn't been mounted.

---

### Post by infernus_crusher on 2009-05-31
Can anybody help?

---

### Post by merlinus on 2009-05-31
You might post the results of

```

sudo fdisk -l

```

---

### Post by infernus_crusher on 2009-06-01
My Windows partition is sda1.

```
Disk /dev/sda: 59.8 GB, 59814236160 bytes
255 heads, 63 sectors/track, 7272 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb170b170

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2432    19535008+   7  HPFS/NTFS
/dev/sda2            2433        7272    38877300    5  Extended
/dev/sda5            2433        2681     2000061   82  Linux swap / Solaris
/dev/sda6            2682        7272    36877176   83  Linux

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa4b57300

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38913   312568641    7  HPFS/NTFS
```

---

### Post by merlinus on 2009-06-01
Please post results of:

```

cat /etc/fstab
blkid

```

---

### Post by infernus_crusher on 2009-06-02
```
cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda6 during installation
UUID=5d05805b-bd36-40fd-a157-0817b8eecc65 /               ext3    relatime,errors=remount-ro 0       1
# /windows was on /dev/sda1 during installation
UUID=FC14AFB214AF6DF8 /windows        ntfs    defaults,nls=utf8,umask=007,gid=46,errors=remount-ro	0       1
# swap was on /dev/sda5 during installation
UUID=7d8901be-06e0-4fb7-9a70-08d6208b56a2 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

```
blkid
/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="FC14AFB214AF6DF8" LABEL="XP" TYPE="ntfs" 
/dev/sda5: UUID="7d8901be-06e0-4fb7-9a70-08d6208b56a2" TYPE="swap" 
/dev/sda6: UUID="5d05805b-bd36-40fd-a157-0817b8eecc65" TYPE="ext3" 
/dev/sdb1: UUID="2E18186F181837F3" LABEL="Seagate" TYPE="ntfs" 

```

---

### Post by Legace on 2009-06-02
1) Type in the following in Terminal
```
sudo mkdir /media/windows
```

2) Make sure the windows entry in /etc/fstab looks like the one below:
```
# /media/Windows was on /dev/sda1 during installation
UUID=FC14AFB214AF6DF8 /media/windows  ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
```

3) Reboot, and you should be fine.

---

### Post by infernus_crusher on 2009-06-07
Wonderful. Thanks a lot.

---

