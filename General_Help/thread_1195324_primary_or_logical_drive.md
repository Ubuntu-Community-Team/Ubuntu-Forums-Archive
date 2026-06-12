---
title: "primary or logical drive?"
date: 2009-06-23
forum: General Help
---

### Post by firsttimeuser on 2009-06-23
I am installing a ubuntu 9 server with two disk drives, for drive 2, i want format it all as /data, and now the screen asks what kind of partition i want for it, should I choose primary or logical?

thanks

---

### Post by cknight on 2009-06-23
If you intend to use the entire disk as a data partition, then it really doesn't matter.  Your drive is limited to 4 primary partitions or 3 primary and 1 extended partition (with an inifinite(?) number of logical paritions within it).  Thus, if at some point in the future you think you might have a need for lots of paritions then extended/logical is the way to go.  

For what its worth, my /data partition is an extended/logical partition, and the only partition on its drive.

---

