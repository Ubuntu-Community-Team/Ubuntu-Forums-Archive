---
title: "Dapper not booting off RAID array"
date: 2006-09-02
forum: Desktop Environments
---

### Post by timothyM on 2006-09-02
Hello,

I've got my computer set up with a 90Mb /boot on an IDE drive which then loads a software raid-0 / partition off two sata drives. This has been working fine for over a year, but when I recently tried to turn my machine on it won't boot. I get:

    "VFS: Cannot open root device "md0" or unknown-block(0,0)"

with the resulting kernel panic:

    "Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0.0)"

This computer hasn't been connected to the internet since late June, (new house), so it has had no updates, and very light use. I certainly haven't touched the arrays in a long time. I thought this might be indicative of a drive failure, but when I use the Dapper install CD, I can mount the raid array fine, and it seems that the contents are unchanged. I ran e2fsck on it, but this had no results.

I had had a similar problem recently with my raid-1 /home where the system was failing to build the array when booting, and couldn't be convinced to do so but for no apparent reason. As I was short of time I just used one of the partions that made up the array as my /home. When I boot the Ubuntu CD, it reports that it cannot mount the raid-1 array. Interestingly I can individually mount the partiton that I hadn't been using, but the one I had substituted as /home will no longer mount, telling me it's already mounted.

I'm currently not sure what to do, and any help/ideas really appreciated, (I really don't want to have to do a reinstall)!

---

