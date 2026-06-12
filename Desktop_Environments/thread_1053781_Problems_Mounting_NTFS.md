---
title: "Problems Mounting NTFS"
date: 2009-01-29
forum: Desktop Environments
---

### Post by DeltaFee on 2009-01-29
Hi I am having a little bit of trouble with mounting my NTFS Partition: I am not sure what I am doing wrong 

Here is my FSTAB -l

>  
Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5140    41287018+   7  HPFS/NTFS
/dev/sda2            5141        9705    36668362+  83  Linux
/dev/sda3            9706        9729      192780   82  Linux swap / Solaris
 

here is my FSTAB
> 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=0b224239-ac94-4721-99f8-46a7e4bb2fcc /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda3
UUID=a68e5912-e381-404b-8651-d8cf48ef762a none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
# Windows File System
/dev/sda1 /mnt/XP ntfs-3g auto,users,uid=1000,gid=100,utf8,dmask=027,fmask=1 37 0 0


---

### Post by m_duck on 2009-01-29
I would have thought the problem is on the last line:
```

/dev/sda1 /mnt/XP ntfs-3g auto,users,uid=1000,gid=100,utf8,dmask=027,fmask=1 **[COLOR=Red]37[/COLOR] **0 0
```Though I don't know for sure, it looks like that is probably being read as the next field along. If removing the 37 doesn't do the trick, for the sake of simplicity, I tend to mount mine like:```
/dev/sda1 /mnt/XP ntfs-3g defaults 0 0
```Then run in terminal ```
sudo mount -a
```This will either give you an error or just return you to "user@host ~$" having mounted the partition.

---

### Post by XanTrax on 2009-01-29
I mount mine as such (from FSTAB)

```

UUID=10383C5E383C454E /media/WindowsXP ntfs-3g defaults 0 0

```

You can get the UUID by doing

```

ls -al /dev/disk/by-uuid

```

Will output something like

```

drwxr-xr-x 2 root 100 2009-01-29 05:05 ./
drwxr-xr-x 6 root 120 2009-01-29 05:05 ../
lrwxrwxrwx 1 root  10 2009-01-29 05:05 10383C5E383C454E -> ../../sda1
lrwxrwxrwx 1 root  10 2009-01-29 05:05 6c27bea9-f2c8-43e3-a9b4-f3a80956c1ea -> ../../sda5
lrwxrwxrwx 1 root  10 2009-01-29 05:05 98b1c716-53a2-4296-a595-1ae31b0cb292 -> ../../sda2

```

That is UUID with a symlink to the device.  As you can see, /dev/sda1 matches the UUID in how I mount it.

---

### Post by DeltaFee on 2009-01-29
When I do 
> 
ls -al /dev/disk/by-uuid


I get:
> 
drwxr-xr-x 2 root root  80 2009-01-29 11:30 .
drwxr-xr-x 5 root root 100 2009-01-29 11:30 ..
lrwxrwxrwx 1 root root  10 2009-01-29 11:30 0b224239-ac94-4721-99f8-46a7e4bb2fcc -> ../../sda2
lrwxrwxrwx 1 root root  10 2009-01-29 11:30 a68e5912-e381-404b-8651-d8cf48ef762a -> ../../sda3


Can't find my /dev/sda1, any ideas?

---

### Post by XanTrax on 2009-01-29
> **DeltaFee said:**
> When I do 


I get:


Can't find my /dev/sda1, any ideas?


Thats weird that it wont show up like that but shows up in fdisk.  Please type this

```
ls -al /dev | grep -i sda1
```

and post the output

---

### Post by DeltaFee on 2009-01-29
I get this, I am not sure why but I did make sure to keep my NTFS xp.

> 
brw-rw----   1 root   disk      8,   1 2009-01-29 12:10 sda1


---

### Post by Giannis68 on 2009-01-29
reinstall ntfs-3g...
i had the same problem on my laptop dual boot vista and linux..
vista needs shutdown before i boot to linux!!!
with restart or sleep ntfs partition not mounted on linux...

---

### Post by XanTrax on 2009-01-29
> **DeltaFee said:**
> I get this, I am not sure why but I did make sure to keep my NTFS xp.

Well, this is getting weird lol.  What happens when you do

```

sudo mkdir /media/xp
sudo mount.ntfs-3g /dev/sda1 /media/xp

```

Please post the output

---

### Post by DeltaFee on 2009-01-29
tried that here is the output:
> 
Failed to mount '/dev/sda1': Invalid argument
The device '/dev/sda1' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?


---

### Post by DeltaFee on 2009-02-05
Thxs. I got it working.

---

### Post by XanTrax on 2009-02-05
> **DeltaFee said:**
> Thxs. I got it working.

How so?

---

### Post by DeltaFee on 2009-02-07
It turned out the NTFS partition was corrupted. Apparently I f***d it up somehow. Though I did use partition magic in xp, when I tried to boot it I got corrupted partition table. Had to reinstall both ubuntu and xp.

---

### Post by XanTrax on 2009-02-07
> **DeltaFee said:**
> It turned out the NTFS partition was corrupted. Apparently I f***d it up somehow. Though I did use partition magic in xp, when I tried to boot it I got corrupted partition table. Had to reinstall both ubuntu and xp.

Nah, you didnt have to do that much.  You can use ntfsfix.  Comes included with ntfs-utils package (I believe) or by default.  Either way, it works out.  I had some crazy error on my jump drive that used to randomly unmount itself then become unmountable completely.  Using NTFSFix though, seemed to fix the problem.

---

