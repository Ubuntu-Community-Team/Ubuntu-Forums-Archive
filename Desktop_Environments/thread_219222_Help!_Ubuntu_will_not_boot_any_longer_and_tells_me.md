---
title: "Help! Ubuntu will not boot any longer and tells me there is a filesystem error"
date: 2006-07-19
forum: Desktop Environments
---

### Post by mkaareng on 2006-07-19
When booting, I get to the root file system check, and that fails.

Here is what it says:

/dev/sda contains a file system with errors, check forced

A manual fsck must be performed, then the system rebooted.

Problem is, I have no idea how to run a manual fsck. What command would that be?

Thank you.

---

### Post by OffHand on 2006-07-19
If it is an error on your boot partition you will probably need a live cd and boot it. Then, using the live cd, type ```
 sudo fsck /path/of/harddisk
```

---

