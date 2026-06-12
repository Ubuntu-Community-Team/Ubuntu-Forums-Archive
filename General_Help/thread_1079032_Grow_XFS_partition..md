---
title: "Grow XFS partition."
date: 2009-02-23
forum: General Help
---

### Post by jmail524 on 2009-02-23
Hi everyone,

I have a server running Ubuntu 8.04LTS 64-bit and hardware RAID5.  I recently upgraded my RAID5 from 3x 1TB drives to 4x 1TB drives.  I am using XFS for my filesystem.  GParted sees the increase in hard drive space.  Previously it showed 2TB of hard drive space with all 2TB used by a partition.  Now it shows 3TB of hard drive space with 2TB used and 1TB unpartitioned.

Now for the problem.  I tried using GParted to expand the partition but I get an error stating 'A partition cannot have a length of -438301395 sectors.'  Since that didn't seem to work, I then attemped to use the 'xfs_growfs' command.  It looks liks it completes successfully, but the size of the partition doesn't seem to change.

What am I doing wrong or what step am I missing.

Thanks.
Brian

---

