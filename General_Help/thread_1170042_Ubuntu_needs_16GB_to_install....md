---
title: "Ubuntu needs 16GB to install...?"
date: 2009-05-25
forum: General Help
---

### Post by unsavory on 2009-05-25
Perhaps someone can help me with this.  I just installed Ubuntu 9.04 alogside Vista.  I partitioned 20GB out for Ubuntu.  17GB for the ext4 fs and 3 GB for swap.

But when I tried to create some folders I found that the ENTIRE drive was full!

Anyone have an idea what I'm doing wrong and why Ubuntu is taking up all 17GB of disk space on a brand new fresh install?

Output from DF -Th:
Filesystem    Type    Size  Used Avail Use% Mounted on
/dev/sda5     ext4     17G   16G     0 100% /
tmpfs        tmpfs    1.9G     0  1.9G   0% /lib/init/rw
varrun       tmpfs    1.9G  108K  1.9G   1% /var/run
varlock      tmpfs    1.9G     0  1.9G   0% /var/lock
udev         tmpfs    1.9G  180K  1.9G   1% /dev
tmpfs        tmpfs    1.9G   76K  1.9G   1% /dev/shm
lrm          tmpfs    1.9G  2.7M  1.9G   1% /lib/modules/2.6.28-11-generic/volatile

Thanks!

---

### Post by Steelmourne on 2009-05-25
You gave ubuntu a 17gb main partition with the rest for swap. Delete the partition and for the next install give 5gb for the main partition and 1-2gb for the swap, depending on how much memory you have.

---

