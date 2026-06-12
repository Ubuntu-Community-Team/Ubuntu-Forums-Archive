---
title: "How to remove invalid icons for inexistent drives in gnome's &quot;places&quot;? dmraid"
date: 2008-10-25
forum: Desktop Environments
---

### Post by lores on 2008-10-25
Hello!

I should start with the most humping information... I am using dmraid for a software raid configuration of two 250 GB disks from which I am booting Ubuntu.

Why humping? Because my P5B's soft-raid is a very bad and not reliable idea that gets even worse when added Linux with dmraid, which messes things up entirely (You know, one disk referred to as three different devices, multiple names for one partition, incompatibility issues etc.)...

I have recently experimented a little with my partitions and I ended up repartitioning the entire hard disk subsystem and restoring my Ubuntu from a backup archive using Acronis TI. Since then, I have been having an icon with my root filesystem's label "Ubuntu" appearing in the Gnome's "Places" menu.

The point is - it is invalid, because it refers to a partition called "/dev/sda1", whereas my parttable consists of 4 partitions on the raid called isw_bgiaiaihdc_R1, isw_bgiaiaihdc_R2, isw_bgiaiaihdc_R3 and isw_bgiaiaihdc_R4 on a device called isw_bgiaiaihdc_R (all located in /dev/mapper/).

However, there are also entries sda, sda1, sda2, sda3, sda4 and sdb in my /dev/ folder, which are unfortunately invalid, as those partitions are physically located on sdb as well (btw., therefore, I get plenty of "Buffer I/O error on device sdaX" and "Partition xxx is located outside the disk" messages during boot).

For those reasons, when to be mounted, the "Ubuntu" device gives me this error: "mount: /dev/sda1 already mounted or /media/Ubuntu busy". /media/Ubuntu does not matter if existent or not (it is certainly not busy).

Remarkable is that in /dev/disk/by-id/ I have:

```

ata-SAMSUNG_HD250HJ_S0URJ9DQ209101
ata-SAMSUNG_SP2504C_S09QJ1UA106174
ata-SAMSUNG_SP2504C_S09QJ1UA106174-part1
ata-SAMSUNG_SP2504C_S09QJ1UA106174-part2
ata-SAMSUNG_SP2504C_S09QJ1UA106174-part3
ata-SAMSUNG_SP2504C_S09QJ1UA106174-part4
scsi-1ATA_SAMSUNG_HD250HJ_S0URJ9DQ209101
scsi-1ATA_SAMSUNG_SP2504C_S09QJ1UA106174
scsi-1ATA_SAMSUNG_SP2504C_S09QJ1UA106174-part1
scsi-1ATA_SAMSUNG_SP2504C_S09QJ1UA106174-part2
scsi-1ATA_SAMSUNG_SP2504C_S09QJ1UA106174-part3
scsi-1ATA_SAMSUNG_SP2504C_S09QJ1UA106174-part4

```

In /dev/disk/by-path/

```
pci-0000:00:1f.2-scsi-0:0:0:0	     pci-0000:00:1f.2-scsi-0:0:0:0-part4
pci-0000:00:1f.2-scsi-0:0:0:0-part1  pci-0000:00:1f.2-scsi-1:0:0:0
pci-0000:00:1f.2-scsi-0:0:0:0-part2  pci-0000:03:00.1-scsi-0:0:0:0
pci-0000:00:1f.2-scsi-0:0:0:0-part3

```

But in /dev/disk/by-label/ just
```
Ubuntu
```

And in /dev/disk/by-uuid/ also just
```
a89965db-f8e6-4c94-bfca-942c9bb92c59
```which corresponds to the root filesystem (called Ubuntu).

The two other partitions are labelled "Data" (R4) and "WinXP" (R3), whereas the fourth one is swap (R2).

I did not dare to remove the one named "Ubuntu" and its uuid entries from /dev/disk/by-label and by-uuid/, though despite the fact of the other partitions' entries' inexistence, they are fully accessible... I tried to exchange the uuid from fstab's root filesystem for the full path ("/dev/mapper/isw_bgiaiaihdc_R1"), but it had no effect.



All I am opting for is the removal of the single icon from the "Places" menu. I am aware it is actually quite a common problem (some dmraid configurations are worse, as they generate much more such invalid places' entries), since I found lots of similar problems - none of them solved. It'd be truly great if this weren't the case here... :)


Thanks!



/etc/fstab:

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc            /proc           proc    defaults        0       0
a89965db-f8e6-4c94-bfca-942c9bb92c59 /               ext3    noatime,nodiratime,errors=remount-ro 0       1
/dev/mapper/isw_bgiaiaihdc_R2 none swap sw 0 0

/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

/dev/mapper/isw_bgiaiaihdc_R3	/media/WinXP	ntfs  defaults,noatime,nodiratime  0 0
/dev/mapper/isw_bgiaiaihdc_R4	/media/Data	ext3  noatime,nodiratime  0 1

```


Hardware:
Asus P5B Deluxe with built-in Intel Matrix (soft RAID controller); Samsung 250 GB SP2504 + Samsung 250 GB HD250HJ.

---

### Post by lores on 2008-10-26
Anyone?

---

### Post by lores on 2008-10-27
Come on...

---

### Post by lores on 2008-10-29
Oh...

---

### Post by DMoRiaM on 2009-05-31
You shall mount your volumes in /mnt instead.
Monted on /media they will show on Places and Desktop (when mounted).

I know, old topic, but I find it a pain when see one not responded yet.

[]s

---

### Post by lores on 2009-06-01
Well, thx for your reply.

In the newer versions of Ubuntu, that particular dmraid problem has disappeared.

However, it's still an issue if one wants to remove an icon from "Places", but only in case of - e.g. - FUSE, which falsely detects a volume and automatically mounts them in /media.

Normally, you could sure use /mnt instead, but sometimes something else is done for you...

---

### Post by DMoRiaM on 2009-06-01
Well, I'll do some research about it, 'cause I need to know the answer. 
It is very annoying when something just don't work as needed.
I'll tell if I find anything!

[]'s

PS.: By the way, what's up with the 'Apostile' guy?

---

### Post by pedrobl on 2009-07-02
I also have problems with the places menu that can't seem to solve. I created new partitions in a new disk, and I wanted some partitions to mount with a specific owner, group and permissions. I found the application "Storage Device Manager" (pysdm) which allows you to configure this kind of things, but it's a little buggy I guess.

In my fstab I have the partitions listed correctly, and mounted under /media with specific names. Unfortunately, the names of those partitions in the Places menu are wrong, and I don't know where to modify them... any news on this?

TIA!

---

### Post by lores on 2009-07-06
I think you can modify the volume names under *Places* by changing labels of the given drives. Use e. g. gparted for that.

EDIT: It also depends on the mountpoint's dir name.

---

### Post by pedrobl on 2009-07-07
> **lores said:**
> I think you can modify the volume names under *Places* by changing labels of the given drives. Use e. g. gparted for that.

I tried that but it doesn't work... and IMHO it should be easier to edit the Places menu to the user liking.

Thanks!

---

### Post by lores on 2009-07-07
Sure it should be possible... Perhaps there is even a wish for that posted already in a wishlist - I would gladly support it.

---

