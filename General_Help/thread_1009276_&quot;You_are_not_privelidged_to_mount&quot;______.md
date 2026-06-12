---
title: "&quot;You are not privelidged to mount&quot; _______"
date: 2008-12-12
forum: General Help
---

### Post by MrBucket101 on 2008-12-12
whenever i plug in any sort of external storage device, this shows up

[IMG]http://i392.photobucket.com/albums/pp9/MrBucket010/Screenshot-4.png[/IMG]

I know I can work around this by going to the terminal but in this case I think the GUI might be faster, and I would like it to work the way it was intended


Heres the output of my sudo fdisk -l
I bolded the drive
```
Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x95aa95aa

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4220    33897118+   7  HPFS/NTFS
/dev/sda2            4221        5987    14193427+  83  Linux
/dev/sda3           11901       12161     2096482+  82  Linux swap / Solaris
/dev/sda4            5988       11900    47496172+  83  Linux

Partition table entries are not in disk order

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000754a8

   Device Boot      Start         End      Blocks   Id  System
**/dev/sdc1               1      121601   976760001    7  HPFS/NTFS**

```


here is my fstab
I bolded the two lines I added

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=dd705895-5538-4587-8d5f-5e8719b91343 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda4
UUID=fa77315e-fbac-477d-8216-388ba260304c /home           ext3    relatime        0       2
# /dev/sda1
UUID=D416953316951796 /windows        ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda3
UUID=782993da-4fbe-470a-b819-11ca2136f47b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

[B]#Backup 
UUID=2DBF7EB547E774CF /media/Backup ntfs
#X-ternal
UUID=5F9FAD694DE4D730 /media/X-ternal ntf[/B]s
```

---

### Post by Graf555 on 2008-12-12
Try this, it should be help you with the privilegies ...and access too)

> 
#Backup 
UUID=2DBF7EB547E774CF /media/Backup ntfs user,rw 0 0
#X-ternal
UUID=5F9FAD694DE4D730 /media/X-ternal ntfs user,rw 0 0


---

### Post by MrBucket101 on 2008-12-12
I'm assuming those additions basically mount the devices as user?

anyways I added the changes proposed and now this is what happens when i try to unmount in nautilus by clicking the eject button

Does anybody know what the second error means? The drive seems to be acting up lately, and I'm also hearing some noises coming from it...

[IMG]http://i392.photobucket.com/albums/pp9/MrBucket010/Screenshot-1-2.png[/IMG]

---

### Post by Graf555 on 2008-12-12
> **MrBucket101 said:**
> I'm assuming those additions basically mount the devices as user?

Option "user" get you rights to mount volumes. besides, only user, who has mount the disk, can unmount it. What about user politics on your computer?

---

### Post by MrBucket101 on 2008-12-12
> **Graf555 said:**
> Option "user" get you rights to mount volumes. besides, only user, who has mount the disk, can unmount it. What about user politics on your computer?
oooooh, I simply copied and pasted your changes

should i change user to my username or leave it as user

either way, I'm getting the same error as before

---

### Post by Graf555 on 2008-12-12
hmm... 
```
UUID=2DBF7EB547E774CF /media/Backup ntfs defaults 0 0 
```
if errors will shown again, learn
```
man mount
```

---

### Post by RuleMaker on 2008-12-12
This is how it should look like:
```
#X-ternal
UUID=5F9FAD694DE4D730 /media/X-ternal ntfs-3g auto,users,uid=1000
```
Just replace your uid with your ID, if you are the first user created on istallation then your ID is 1000.

---

