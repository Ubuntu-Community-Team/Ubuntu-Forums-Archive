---
title: "Partitioning multiple drives"
date: 2009-01-15
forum: General Help
---

### Post by kvk on 2009-01-15
I have a two-disk system. Loading 8.10 formatted the master drive, but I haven't partitioned the slave drive. How is this accomplished so that both drives are accessible and the second drive serves simply as data storage space?

---

### Post by iaculallad on 2009-01-15
Ubuntu will automatically detect those drives for you. You can configure those drives to [automount]("http://ubuntuforums.org/showthread.php?t=1039892") at startup (Sample on the link automount a NTFS partition).

---

### Post by Bucky Ball on 2009-01-15
Go to Applications->Admin->Partition Editor and format using that. Partition away. If you want more than 4 partitions on the drive, create an extended partition the size of the drive and logical partitions inside that. If you want one big partition, no extended required. If you can't find Partition Editor, in a terminal paste:

```
sudo apt-get install gparted
```

---

### Post by kvk on 2009-01-15
Thanks so much! :-)

Can I simply replace 'NTFS' with 'ext3_Drive'?

---

### Post by iaculallad on 2009-01-15
> **kvk said:**
> Thanks so much! :-)

Can I simply replace 'NTFS' with 'ext3_Drive'?

Sure do, you're choice of naming.

---

