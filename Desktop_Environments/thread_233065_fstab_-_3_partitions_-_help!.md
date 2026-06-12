---
title: "fstab - 3 partitions - help!"
date: 2006-08-09
forum: Desktop Environments
---

### Post by GoLoGo on 2006-08-09
Alright I have 1 20GB Hardrive and 1 200GB Hardrive. The 20GB has Ubuntu installed on it, partitioned respectively. The 200GB is partitioned into 4 partitions. Each 50GB, 1 is NFTS - the other 3 are ext3 filesystems. The problem is, I had all 3 Ext3 partitions displaying and working correctly, even had them mounted, and they would always stay mounted. Then all of a sudden when I turned on the computer they where all unmounted (the ext3 filesystems) and one of the partitions was not getting displayed. When I try to make an entry is fstab exactly how the documents in the website say, the partition I add, is gone from the file browser. I dont know whats going on, im still new with linux. If somebody can help me out, I would really appreciate it. **_I want all 3  ext3 filesystems partitions mounted, viewable, writable, readable, and permanently mounted._** I open them with Gparted and it doesnt report any problems. Thanks.

---

### Post by meng on 2006-08-09
It would help to see the contents of your /etc/fstab, and also to know where in your file browser you are expecting to see these partitions.

---

### Post by GoLoGo on 2006-08-09
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
#Added by diskmounter utility
/dev/hdb1 /media/hdb1 ntfs ro,user,fmask=0111,dmask=0000 0 0
```

the devices that I want permanently mounted, writable, readable, and viewable are:

/dev/hdb5
/dev/hdb6
/dev/hdb7

all ext3 filesystems. One of those does not get displayed in the filebrowser, and if i make an entry in the fstab, it dissapears. Like if I add /dev/hdb7 /home/owen/Shared ext3 defaults 0 0 , it stops displaying it.

---

### Post by meng on 2006-08-09
So, at the time it disappears, is your file browser pointing to /home/owen/Shared?

Otherwise you could drop to command line and type
sudo mount /dev/hdb7 /home/owen/Shared
just to make sure that mounting works manually.

---

### Post by GoLoGo on 2006-08-09
Yes, mounting seems to work manually, although if I mount all 3 manually, it only still displays 2 of the partitions in the file browser.

---

### Post by rekahsoft on 2006-08-09
You fstab should look like this:
```
# /etc/fstab: static file system information.
# 
# <file system> <mount point>   <type>  <options>               <dump>  <pass>
proc            /proc           proc    defaults                   0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw                         0       0
/dev/hdb5       /mnt/one        ext3    defaults                   0       1
/dev/hdb6       /mnt/two        ext3    defaults                   0       1
/dev/hdb7       /mnt/three      ext3    defaults                   0       1
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto            0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto            0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto             0       0
#Added by diskmounter utility
/dev/hdb1 /media/hdb1 ntfs ro,user,fmask=0111,dmask=0000           0       0
```
btw...on the 200gb drive why are the last three partitions on the drive hdb5, hdb6 and hdb7? The NTFS partition is hdb1 but the next partion is hdb6???? Report back with the output from this command:```
sudo fdisk -l /dev/hdb
``` Also note that you have to create the folders to which you are going to mount the partions...i have the set to mount at [/mnt/][one, two, three] so you would make the folders like this:```
sudo mkdir /mnt/one
sudo mkdir /mnt/two
sudo mkdir /mnt/three
```

---

### Post by GoLoGo on 2006-08-09
This is what i got from fdisk:
```

Disk /dev/hdb: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        6079    48829536    7  HPFS/NTFS
/dev/hdb2            6080       24792   150312172+   f  W95 Ext'd (LBA)
/dev/hdb5            6080       12158    48829536   83  Linux
/dev/hdb6           12159       18237    48829536   83  Linux
/dev/hdb7           18238       24792    52653006   83  Linux

```

Im about to restart, to see what happens.

---

### Post by GoLoGo on 2006-08-09
[[img]http://www.uploadfile.info/uploads/c1d617fc3f.png[/img]](http://www.uploadfile.info)

It does not display any of them, they are all gone. For some reason it also made a copy of my Digital Cameras scan card. I dont know whats going on :(...

---

### Post by rekahsoft on 2006-08-09
So you didn't get any output from ```
sudo fdisk -l /dev/hdb
```???

---

### Post by GoLoGo on 2006-08-09
read the post that was made **23 minutes ago. Post #7**

---

### Post by rekahsoft on 2006-08-09
srry i missed that...did you make the directories? [/mnt/][one, two, three]? Can u mount them manualy? ```
sudo mount /dev/hdb5
sudo mount /dev/hdb6
sudo mount /dev/hdb7
```
Try mounting them manualy...report back

---

### Post by GoLoGo on 2006-08-09
Yes I can mount them manually, but they arent writable, and they dont appear in "Computer - File Browser", my fstab entries are as follows:

```
/dev/hdb5       /shared/disk2_shared       ext3    defaults         0       1
/dev/hdb6       /shared/disk3_shared       ext3    defaults         0       1
/dev/hdb7       /home/owen/Shared          ext3    defaults         0       1
```

---

### Post by rekahsoft on 2006-08-09
hmmm...wierd...can you write to them using sudo?

---

### Post by meng on 2006-08-09
After they're mounted, what do you get if you
ls /home/owen/Shared
In other words, do the contents of the drive appear there or not?

---

### Post by rekahsoft on 2006-08-09
yes...and can you write to the partition (can you write to the partition using sudo)?

---

### Post by GoLoGo on 2006-08-09
Yes I can see the contents "lost+found and Recycled" to all 3 folders. /home/owen/Shared has a lock on it, and all 3 partitions dont display in the Computer, meaning the window that opens up when you go to Places> Computer. Yes I can write to /home/owen/Shared using the sudo command - sudo mkdir /home/owen/Shared - how do i make it writable and readable by all? to all 3 mount points and partitions. Also I really want it to display in the Computer window.

---

### Post by rekahsoft on 2006-08-09
I don't know how to add it to the My Computer window but i do know how to make it writable. I will figure out how to get them to display in the My Computer Window tonight and report back APAP...it probably involves editing some configuration files...as for making the partitions writable make it either owned by you or change the permissions on the folder using chmod. ```
sudo chown -R username folder-name
``` OR ```
sudo chmod 777 test
``` I recomend changing the ownership (the first method).

---

### Post by GoLoGo on 2006-08-09
Alright thank you, I have made them writable, they are working pretty good - although there is a red X on the lost+found folders I dont know if thats normal. Please get back to me asap on how to display them in the computer window, thanks.

---

### Post by rekahsoft on 2006-08-09
No problem :) i hope we can get this working for you...it is just one of those things...

---

### Post by rekahsoft on 2006-08-12
ok...first thing is restart and see if it is detected...if not..then you can bookmark it and it will show up in places...i am still looking for a way to get it in "My Computer".

---

