---
title: "Mounting NTFS error I'm having."
date: 2009-04-30
forum: General Help
---

### Post by badgaz1 on 2009-04-30
Hello. When I try to click on my NTFS harddrive to mount it I get the following error message.

[IMG]http://img208.imageshack.us/img208/2852/errorhkv.png[/IMG]

It used to work before and I can't think of anything I could have done to break it.

Also Gparted seems to have some issues detecting the NTFS partitions despite the NTFS packages all being installed.

[[IMG]http://img156.imageshack.us/img156/263/gparted.png[/IMG]]("http://img208.imageshack.us/img208/263/gparted.png")

Anybody lend a hand? Thank you.

---

### Post by caljohnsmith on 2009-04-30
So is the partition in question on your 1 TB sdb drive? If so, it looks like the issue is that drive may have a corrupt partition table, or maybe the partition table somehow got deleted, because gparted shows the drive as entirely unallocated. How about opening a terminal and please post the output of the following commands:
```
sudo fdisk -lu
sudo parted /dev/sdb print
```
Also, what are your partitions on the sdb HDD supposed to be, and what are their file systems (are they all NTFS)? 

John

---

### Post by badgaz1 on 2009-05-01
Hello. My I have three harddrives in my computer.

One of them is the Ubuntu 9.04 one (ext3). One of them is my Vista one (NTFS) and the other just has all my documents etc on it (NTFS) which is the 1tb one (just one partiton). Ubuntu detects both the Vista and Documents drives as Unallocated but obviously Vista detects them fine.

This is the output for 'sudo fdisk -lu'

```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf8a892f6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   488408129   244203041    7  HPFS/NTFS

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf996005f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048  1953536129   976767041    7  HPFS/NTFS

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd5748c8d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              63   468519659   234259798+  83  Linux
/dev/sdc2       468519660   488392064     9936202+   5  Extended
/dev/sdc5       468519723   488392064     9936171   82  Linux swap / Solaris

```

'sudo parted /dev/sdb' print just brings up:

```
Error: Cannot have a partition outside the disk!
```


Thank you for your help so far.

UPDATE: Doing "sudo mount /dev/sdb1 /mnt/stuff" has mounted the drive fine although now it no longer appears as a disk drive in the Computer folder, I suppose that's good enough for now although abit sloppy!

---

### Post by caljohnsmith on 2009-05-01
> **badgaz1 said:**
> 
This is the output for 'sudo fdisk -lu'

```

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total [COLOR="Red"]488397168[/COLOR] sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf8a892f6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   [COLOR="Red"]488408129[/COLOR]   244203041    7  HPFS/NTFS

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total [COLOR="Red"]1953525168[/COLOR] sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf996005f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048  [COLOR="Red"]1953536129[/COLOR]   976767041    7  HPFS/NTFS

```

'sudo parted /dev/sdb' print just brings up:

```
[COLOR="Red"]Error: Cannot have a partition outside the disk![/COLOR]
```

The "sudo parted /dev/sdb print" command confirms my suspicions that your sdb partition table is corrupt; as shown highlighted in red in the fdisk output, the ending sector of your sdb1 partition, 1953536129, exceeds the total number of sectors available on your HDD, or 1953525168. The same is true for your sda1 partition on the sda HDD--it's ending sector is outside of the HDD. But because the starting sector of those partitions are correct, that's why you can mount the partitions OK. Since we don't know the correct ending sector for either partition, I would recommend using "testdisk" (a really good partition recovery utility) to figure it out for us. How about downloading the [testdisk-6.11.1.linux26.tar.bz2]("http://www.cgsecurity.org/testdisk-6.11.1.linux26.tar.bz2") package to your Ubuntu desktop, and then do:
```

cd ~/Desktop
tar xvf testdisk-6.11.1.linux26.tar.bz2
sudo testdisk-6.11/linux/testdisk_static
```
After starting testdisk with the above command, choose "No Log", select the sda HDD and then "Proceed", "Intel", "Analyze", "Quick search", "N" to search for Vista partitions, hit enter to continue, select "Deeper Search" so it does a deeper search, which could take a while. Please post the output of the screen that has the deep search results. Also, use your up/down arrow keys to select each partition listed in the deep search results, and press "p" to get a directory listing; please let me know exactly which partitions give you a directory listing (hopefully just one partition will give a directory listing), and also which of those partitions seems to be your existing sda1 partition. Then repeat the whole process with testdisk for your sdb drive. We can work from there if you want.

Cheers,
John

---

