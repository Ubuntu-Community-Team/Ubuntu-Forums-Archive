---
title: "need help recovering ext3 partition after initializing with windows"
date: 2009-06-16
forum: General Help
---

### Post by horde on 2009-06-16
I was trying to get extifs on Windows to read a disk formatted ext3.  Windows wasn't even mounting the disk, so I went into Control Panel>Administrative Tools>(some sort of management) and initialized the disk.  It wasn't a format, and the operation was instantaneous.  Windows still didn't recognize the drive, even with extifs.

I rebooted into Ubuntu and it didn't recognize the drive either...the fsck check hung while booting.  In GParted it says that the disk is now unallocated...but the data has to still be there...initializing didn't take long enough to overwrite it.

I was hoping someone could tell me how to recover my data/rebuild the partition.

Many thanks in advance.

---

### Post by [z]er0 HP on 2009-06-16
I'm having a similar problem amazingly enough using that same bloody program in windows. My situation the program actually worked and was transferring data, windows BSOD, corrupt HDD.

Any help to rebuild partition would be greatly appreciated. (i have to much custom configuration done to reinstall ubuntu)

---

### Post by ad_267 on 2009-06-16
You could try some of the tools mentioned here:
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

I know testdisk can recover a deleted partition, I'm not sure if it will restore a partition that has been "initialized".

You can boot from a LiveCD and run "sudo fdisk -l" to list all your partitions. You can run "sudo testdisk" to recover a deleted partition.

---

