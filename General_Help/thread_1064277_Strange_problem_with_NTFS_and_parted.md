---
title: "Strange problem with NTFS and parted"
date: 2009-02-08
forum: General Help
---

### Post by Fixman on 2009-02-08
I have two hard drives, and one of them has a single NTFS partition:

```
martin@Ubuntu:~/Desktop/CC$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbfffe9fd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19458   156296375    7  HPFS/NTFS

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa110a110

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9400    75505468+  83  Linux
/dev/sdb2            9401        9729     2642692+   5  Extended
/dev/sdb5            9401        9729     2642661   82  Linux swap / Solaris
```

I can mount normally that windows partition, however, when I go to gParted it shows no partition is there:

[IMG]http://201.231.227.60/img/inger/13.png[/IMG]

Also, if I select that partition form Parted, it shows me this error:

```
martin@Ubuntu:~$ sudo parted
[sudo] password for martin: 
GNU Parted 1.7.1
Using /dev/sda
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) p                                                                
Error: Can't have a partition outside the disk!
```


Does anybody have a solution to this?

---

### Post by caljohnsmith on 2009-02-08
> **Fixman said:**
> 
```
martin@Ubuntu:~/Desktop/CC$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, [COLOR="Red"]19457[/COLOR] cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbfffe9fd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       [COLOR="Red"]19458[/COLOR]   156296375    7  HPFS/NTFS

```

As shown highlighted in red, the ending cylinder of your NTFS partition exceeds the total number of cylinders the HDD has, so basically the sda partition table is corrupt right now. That's why parted complains that you "Can't have a partition outside the disk". Anyway, how about first posting:
```
sudo fdisk -lu
```
Note the "-lu" option will give the units in sectors, which will help determine what the next best course of action might be. We can work from there if you want.

---

### Post by Fixman on 2009-02-08
> **caljohnsmith said:**
> 
```
sudo fdisk -lu
```
Note the "-lu" option will give the units in sectors, which will help determine what the next best course of action might be. We can work from there if you want.

Here yoy go:

```
 martin@Ubuntu:~$ sudo fdisk -lu
[sudo] password for martin: 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xbfffe9fd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          20   312592769   156296375    7  HPFS/NTFS

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xa110a110

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   151010999    75505468+  83  Linux
/dev/sdb2       151011000   156296384     2642692+   5  Extended
/dev/sdb5       151011063   156296384     2642661   82  Linux swap / Solaris 
```

---

### Post by caljohnsmith on 2009-02-08
> **Fixman said:**
> 
```
 martin@Ubuntu:~$ sudo fdisk -lu
[sudo] password for martin: 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total [COLOR="Red"]312581808[/COLOR] sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xbfffe9fd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          20   [COLOR="Red"]312592769[/COLOR]   156296375    7  HPFS/NTFS

```
OK, so your sda1 partition definitely extends beyond the limits of the HDD according to the current partition table. I would recommend using testdisk to find the correct start/stop sectors of the partition (or actually testdisk only needs to find the correct ending sector), so how about downloading the [testdisk-6.10.linux26.tar.bz2]("http://www.cgsecurity.org/testdisk-6.10.linux26.tar.bz2") package to your desktop, and then do:
```

cd ~/Desktop
tar xvf testdisk-6.10.linux26.tar.bz2
sudo testdisk-6.10/linux/testdisk_static
```
After starting testdisk with the above command, choose "No Log", select HDD and "Proceed", "Intel", "Analyze", "Quick search", "Y" to search for Vista partitions, hit enter to continue, select "Deeper Search" so it does a deeper search, which could take a while. Please post the output of the screen that has the deep search results. Also, if there is more than one partition listed in the deep search results, use your up/down arrow keys to select each partition, and press "p" to get a directory listing; when you find the partition that has your Windows root directory, use your left/right arrow keys to mark that partition as "*", and then mark any other partitions listed as "D". Press enter to get to the next screen, and select "write" to write the new partition table. After that, please post the output of:
```
sudo fdisk -lu
sudo mount /dev/sda1 /mnt && ls -l /mnt
```
So I can check that the procedure went OK.

---

### Post by Fixman on 2009-02-09
> **caljohnsmith said:**
> OK, so your sda1 partition definitely extends beyond the limits of the HDD according to the current partition table. I would recommend using testdisk to find the correct start/stop sectors of the partition (or actually testdisk only needs to find the correct ending sector), so how about downloading the [testdisk-6.10.linux26.tar.bz2]("http://www.cgsecurity.org/testdisk-6.10.linux26.tar.bz2") package to your desktop, and then do:
```

cd ~/Desktop
tar xvf testdisk-6.10.linux26.tar.bz2
sudo testdisk-6.10/linux/testdisk_static
```
After starting testdisk with the above command, choose "No Log", select HDD and "Proceed", "Intel", "Analyze", "Quick search", "Y" to search for Vista partitions, hit enter to continue, select "Deeper Search" so it does a deeper search, which could take a while. Please post the output of the screen that has the deep search results. Also, if there is more than one partition listed in the deep search results, use your up/down arrow keys to select each partition, and press "p" to get a directory listing; when you find the partition that has your Windows root directory, use your left/right arrow keys to mark that partition as "*", and then mark any other partitions listed as "D". Press enter to get to the next screen, and select "write" to write the new partition table. After that, please post the output of:
```
sudo fdisk -lu
sudo mount /dev/sda1 /mnt && ls -l /mnt
```
So I can check that the procedure went OK.

I did the procedure and it looked okay (the partition was shown correctly), then I chose to write, rebooted, but it has anyway the same problem (parted and fdisk -lu give me the same output, and I can mount normally). Do you have any other solution?

---

### Post by caljohnsmith on 2009-02-09
How about posting the output again of:
```
sudo fdisk -lu
```
So I can see if the ending sector is exactly the same.

---

### Post by Fixman on 2009-02-09
> **caljohnsmith said:**
> How about posting the output again of:
```
sudo fdisk -lu
```
So I can see if the ending sector is exactly the same.

```

martin@Ubuntu:~$ sudo fdisk -lu
[sudo] password for martin: 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xbfffe9fd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          20   312592769   156296375    7  HPFS/NTFS

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xa110a110

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   151010999    75505468+  83  Linux
/dev/sdb2       151011000   156296384     2642692+   5  Extended
/dev/sdb5       151011063   156296384     2642661   82  Linux swap / Solaris

```

---

### Post by caljohnsmith on 2009-02-09
OK, how about posting:
```
sudo umount /dev/sda1
sudo ntfsresize -i /dev/sda1
```
And we can work from there.

---

### Post by Fixman on 2009-02-10
> **caljohnsmith said:**
> OK, how about posting:
```
sudo umount /dev/sda1
sudo ntfsresize -i /dev/sda1
```
And we can work from there.

For some reason I can't use the -i reason, however it works if I force it, and gives me this output:

```

martin@Ubuntu:~$ sudo ntfsresize -if /dev/sda1
ntfsresize v2.0.0 (libntfs 10:0:0)
Device name        : /dev/sda1
NTFS volume version: 3.1
Cluster size       : 4096 bytes
Current volume size: 160041603584 bytes (160042 MB)
Current device size: 160047488000 bytes (160048 MB)
Checking filesystem consistency ...
Cluster 15867902 is referenced multiple times!
Cluster 15867903 is referenced multiple times!
Cluster 15867904 is referenced multiple times!
Cluster 15867905 is referenced multiple times!
Cluster 15867906 is referenced multiple times!
Cluster 15867907 is referenced multiple times!
Cluster 15867908 is referenced multiple times!
Cluster 15867909 is referenced multiple times!
Cluster 15867910 is referenced multiple times!
Cluster 15867911 is referenced multiple times!
100.00 percent completed
ERROR: Filesystem check failed!
ERROR: 401 clusters are referenced multiply times.
NTFS is inconsistent. Run chkdsk /f on Windows then reboot it TWICE!
The usage of the /f parameter is very IMPORTANT! No modification was
and will be made to NTFS by this software until it gets repaired.

```

---

### Post by Yashiro on 2009-02-10
Before doing any of this you should have ran chkdsk /R on the NTFS partition from within Windows.

---

### Post by caljohnsmith on 2009-02-10
> **Fixman said:**
> 
```

martin@Ubuntu:~$ sudo ntfsresize -if /dev/sda1
ntfsresize v2.0.0 (libntfs 10:0:0)
Device name        : /dev/sda1
NTFS volume version: 3.1
Cluster size       : 4096 bytes
Current volume size: [COLOR="Blue"]160041603584[/COLOR] bytes (160042 MB)
Current device size: 160047488000 bytes (160048 MB)
Checking filesystem consistency ...
Cluster 15867902 is referenced multiple times!
Cluster 15867903 is referenced multiple times!
Cluster 15867904 is referenced multiple times!
Cluster 15867905 is referenced multiple times!
Cluster 15867906 is referenced multiple times!
Cluster 15867907 is referenced multiple times!
Cluster 15867908 is referenced multiple times!
Cluster 15867909 is referenced multiple times!
Cluster 15867910 is referenced multiple times!
Cluster 15867911 is referenced multiple times!
100.00 percent completed
ERROR: Filesystem check failed!
ERROR: 401 clusters are referenced multiply times.
NTFS is inconsistent. Run chkdsk /f on Windows then reboot it TWICE!
The usage of the /f parameter is very IMPORTANT! No modification was
and will be made to NTFS by this software until it gets repaired.

```
Well the good news is your NTFS file system is 160041603584 bytes, which means it is 160041603584/512 = 312581257 sectors, which does not exceed the total number of sectors of your HDD (unlike the partition's current ending sector). Therefore, if you can fix the your NTFS partition with "chkdsk /r", then once ntfsresize reports that partition as clean, we can easily change the ending sector of the partition to correctly match the file system size. Then you shouldn't have any problem using gparted on that drive. So how about booting your Windows Install CD, go to the "recovery console", and then do:
```
chkdsk /r
```
And run it as many times as it takes until it reports no errors. Then boot back into Ubuntu and run the ntfsresize -i command on it again, and see if it comes up clean. We can work from there.

---

