---
title: "File system corruption"
date: 2008-12-22
forum: General Help
---

### Post by xadloki on 2008-12-22
Due to a sudden power outage my ubuntu was shutdown badly and I'm having problems with mounting a drive that was corrupted.

I've tried different superblocks to see if it mounts but have had no luck, I'm able to mount the partition sometimes after restarting so I've been able to recover most of my data and the rest is backed up. However since there are plenty of power outages where I live this could be a big problem. What filesystem can handle best bad shutdowns without data corruption? And are there any major differences in distributions and how reliable they are?

---

### Post by beno1990 on 2008-12-22
> **xadloki said:**
> Due to a sudden power outage my ubuntu was shutdown badly and I'm having problems with mounting a drive that was corrupted.

I've tried different superblocks to see if it mounts but have had no luck, I'm able to mount the partition sometimes after restarting so I've been able to recover most of my data and the rest is backed up. However since there are plenty of power outages where I live this could be a big problem. What filesystem can handle best bad shutdowns without data corruption? And are there any major differences in distributions and how reliable they are?

JFS and XFS are probably the best filesystems for error protection IMO, but XFS will only work under FUSE on Linux and not in the kernel (due to licensing issues), so you can't use XFS for your root or boot partitions, and because it's FUSE, it might suffer a bit of a performance overhead.

---

### Post by HermanAB on 2008-12-22
Ext3 is best.  Ext2 is worst and should not be used at all.

JFS and XFS are good too.

---

