---
title: "server shell command question"
date: 2009-02-04
forum: General Help
---

### Post by badperson on 2009-02-04
Hi,
I have a lamp install on one of my machines...I'm wondering; how do see all the hard drives that are on that machine, and then navigate to them? 

I typed "df" and saw something like
/dev/sda5, 

but cd /dev/sda5 doesn't work, it says it's not a directory...
thanks!
bp

---

### Post by taurus on 2009-02-04
```
df -h
```
You access the hardrive/partition by navigating to the mount point.  Assuming /dev/sda5 is mounted to /media/share, you would do

```
cd /media/share
ls -la
```

---

### Post by mixmaster on 2009-02-04
It sounds as though you have a mainly windows background.

Windows has the concept of separate file systems on each drive.  There is a "root" and "current" directory for each.  Linux/unix uses the simpler system of a single directory tree, rooted at "/" which encompasses all block storage devices.  Thus /dev/sda1 will point to a partition on a hard drive (which may or may not span the whole drive), or on a raid array or whatever.  You can get to every available part of storage without needing any knowledge of the underlying physical geometry.  Even mountable devices such as external USB drives appear as part of this hierarchy.

If you are going to administer a server I suggest you read up a bit on the unix file system or you could get rather confused.

---

### Post by badperson on 2009-02-04
> **mixmaster said:**
> It sounds as though you have a mainly windows background.


guilty as charged. I installed ubuntu server on an old machine to get experience with it. will read up on the filesystem stuff..thanks for the help.
bp

---

### Post by badperson on 2009-09-02
revisiting this issue....
I have my server going again, and when I do: 
```
cd /
ls

```

I get: 
> bin  boot  cdrom  dev  etc  home  initrd  initrd.img  lib  lost+found  media  mnt  opt  proc  root  sbin  srv  sys  tmp  usr  var  vmlinuz


I have two hard drives on this macnine...which of the dirs listed is the root of the 2nd HD? It isn't media or cdrom...I checked those....

thanks, 
bp

---

### Post by BitJunkie on 2009-09-02
As already mentioned, ```
df -h
``` will show you your mount points (look for /dev/sd?). This is assuming the second drive is mounted.

---

### Post by badperson on 2009-09-03
Hi,
this is what I get from df -h (sorry I overlooked that before):

> Filesystem            Size  Used Avail Use% Mounted on
/dev/sda6             139G  1.9G  131G   2% /
varrun               1014M  184K 1014M   1% /var/run
varlock              1014M     0 1014M   0% /var/lock
udev                 1014M   60K 1014M   1% /dev
devshm               1014M     0 1014M   0% /dev/shm


In bios I see two HD's...but unless I'm wrong only one here...is that correct? Do I need to mount it? 
bp

---

### Post by i.r.id10t on 2009-09-03
Yes, you'll need to mount it... do you want to use it as storage, your /home directory/partition, or what?

---

### Post by badperson on 2009-09-03
Hi,
just use it as file storage...there are files there already from an earlier windows installaton

---

### Post by BitJunkie on 2009-09-03
Does anything other than /dev/sda show up when you type```
 cat /proc/partitions
``` or```
 sudo fdisk -l
```

---

### Post by snakepit # on 2009-09-03
> **badperson said:**
> Hi,
I have a lamp install on one of my machines...I'm wondering; how do see all the hard drives that are on that machine, and then navigate to them? 

I typed "df" and saw something like
/dev/sda5, 

but cd /dev/sda5 doesn't work, it says it's not a directory...
thanks!
bp

Thats because it is a /devICE

Everything is a file, even hardware.

To mount that drive:

# mkdir /mnt/sda5; mount /dev/sda5 /mnt/sda5

---

### Post by badperson on 2009-09-18
> **BitJunkie said:**
> Does anything other than /dev/sda show up when you type```
 cat /proc/partitions
``` or```
 sudo fdisk -l
```


cat /proc/partitions: 
> 
major minor  #blocks  name

   8     0  312571224 sda
   8     1  153517108 sda1
   8     2          1 sda2
   8     5    6080571 sda5
   8     6  146890264 sda6
   8     7    6080571 sda7
   8    16  244198584 sdb
   8    17  244187968 sdb1


and 


sudo fdisk -l:
> 
ver: 

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0004ea24

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19112   153517108+  83  Linux
/dev/sda2           19113       38913   159051532+   5  Extended
/dev/sda5           38157       38913     6080571   82  Linux swap / Solaris
/dev/sda6           19113       37399   146890264+  83  Linux
/dev/sda7           37400       38156     6080571   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x81c581c5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30400   244187968+   7  HPFS/NTFS
jason-server@ubuntu-server:/$ 


are all of those /dev/sda entries partitions? Can I mount any of them? 
bp

---

