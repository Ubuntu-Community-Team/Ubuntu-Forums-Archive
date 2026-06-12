---
title: "Mount an inconsistent NTFS partition?"
date: 2009-02-24
forum: General Help
---

### Post by valros on 2009-02-24
After WUBI set up a host for Ubuntu it somehow corrupted the partition, it is now labeled as an inconsistent NTFS partition. I dont believe that the partition tables on the disk are damaged, but the index or configurations of this one NTFS partition might be. Here are the results from blkid:

/dev/sdb1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="07D6-0C0F" TYPE="vfat"
/dev/sdb2: UUID="B42CC3662CC3226A" TYPE="ntfs"
/dev/sdb3: LABEL="DellRestore" UUID="0000-0000" TYPE="vfat"

I am trying to access sdb2, no luck mounting it and no idea how to recover files any other way. The only thing I got ddrescue to do was make an img of it, and fsck(from what I know) cannot check the consistency of NTFS, and I dont have access to chkdisk. Any way to recover the files?

---

### Post by caljohnsmith on 2009-02-25
How about first posting the output of:
```
sudo mount -t ntfs-3g /dev/sdb2 /mnt -o force && ls -l /mnt
```
And we can work from there if you want.

---

### Post by valros on 2009-02-25
Ok, executed the above and recieved the following.

Failed to mount '/dev/sdb2': Input/output error
NTFS is either inconsistent, or you have hardware faults, or you have a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows TWICE. The usage of the /f parameter is very
important! If you have SoftRAID/FakeRAID then first you must activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for the details.

---

### Post by caljohnsmith on 2009-02-25
OK, how about posting:
```
sudo fdisk -lu
sudo vol_id --probe-all /dev/sdb2
```
Since you mentioned you don't have access to chkdsk, how about downloading a Windows Recovery CD from [here]("http://www.webtree.ca/windowsxp/tools/bootdiscs/xp_rec_con.zip"), boot that, go to the "recovery console" and do:
```
map
```
That will show the drive letters for all the partitions, find the drive letter for the sdb2 NTFS partition and do:
```
chkdsk /r X:
```
But replace "X" with the sdb2 partition drive letter, and run the chkdsk command as many times as it takes until it reports no errors. Then try mounting the partition again in Ubuntu via the command from my previous post. Let me know how that goes.

---

### Post by valros on 2009-02-25
sudo fdisk -lu gives

Disk /dev/sdb: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders, total 488281250 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe686f016

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb2   *      112455   478528154   239207850    7  HPFS/NTFS

Ill have to work with Windows Recovery later, no time now.

---

### Post by caljohnsmith on 2009-02-25
What happened to sdb1 and sdb3 that you showed in your first post?

---

### Post by valros on 2009-02-25
I just erased them with gparted. Nothing on them, a 5 gb restore and something else around 80 mgbs.

---

### Post by valros on 2009-02-25
Ok, so I did get the drive mountable, ran checkdisk in the Windows Recovery and after a while it froze at 50%, dam, I thought. After a forced shutdown I opened it back up under Ubuntu, all it needed then was a forced mount and there were all the files, sweet.

---

