---
title: "encrypted zfs for .home on workstation ?"
date: 2021-12-09
forum: Desktop Environments
---

### Post by chpnp on 2021-12-09
Hi,

Is anyone using an encrypted ZFS fs for /home on a a workstation ? would this be a significant performance hit ?

I would be considering this for data integrity checking, and snapshot, and potentially for duplicates management (for some reason i know i have about 10% of files which are duplicated)

I would like to know if this would be a practical, efficient, reasonnably fast environment.

Currently i encrypt / and /home on Luks/ext4 fs.

Tx for any hint / feedback

---

### Post by chpnp on 2021-12-09
Also as an additional question.
I have a 1TB ssd (encrypted) and a large external disk for additional, non permanent storage eg backups, pictures, etc.
I require encryption for work data on my external disk (as it is client data), but do not care for pics, which are private and of no interest except for me.
Until recently i have used separated ext4 over luks and ext4 only partitions for that purpose, or, a single non encrypted partition, with large files mounted as ext4 over luks partitions for client data or backups.
This proves a bit more administration than I wish
Is there a high cost of having a full luks partition on hdd including for eg private files like pictures ?? would they be much longer to access ?
I am asking because I do not realize the cost of luks for backups as mostly they run in the background so I do not care for time overhead.

For other daily data like pictures or other, i would care for the access time. I think I read the cost would be about 10% more than non encrypted but could not find relevant tests. Any idea on this ??
To tie this to my earlier question, I would consider luks+ZFS on my external HDD if the performance hit would be minimal, if noticeable at all..
Thanks

---

