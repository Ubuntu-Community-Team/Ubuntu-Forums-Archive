---
title: "Re-Partitioning SATA drive"
date: 2006-09-04
forum: Desktop Environments
---

### Post by sc10n on 2006-09-04
Hey all, I have been running Dappper (64bit) exclusively on my HP xw9300 for about a month now. So far I am very pleased with the results and I am going to make this a permanent solution. Now the problem I am having is the 2 SATA slave drives in the machine are formated NTFS (legacy from the box being Win2k3 server). I have tried several times to re-partition the drives. Each time i used fdisk. I unmounted the disk then ran fdisk. 

```
sudo fdisk /dev/sdb
```

Deleted the existing partition. Created the new one. and Sync'd the disk and quit. The result was the following.

 ```
  Device Boot      Start         End      Blocks       Id  	System
    /dev/sdb1           1       12188    97900078+  	83  	Linux
```

Next I went into the Gnome Disk Manager to format the partition. But in the DM it still showed the NTFS partition. So thinking it needed to be rebooted I went ahead and rebooted. No errors on at boot time. Went into Fdisk again and showed the NTFS partition.

 ```
  Device Boot    Start    End      Blocks     Id  	System
    /dev/sdb1         1  12188    97900078+  	7	HPFS/NTFS
```

Now I am positive I used the 'w' switch to sync and quit. I have tried this several times all with the same results. Am I missing something? Any responses would be very appreciated. 

Thanks.

sc10n.

---

