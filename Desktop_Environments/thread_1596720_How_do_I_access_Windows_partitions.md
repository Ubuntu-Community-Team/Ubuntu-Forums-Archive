---
title: "How do I access Windows partitions?"
date: 2010-10-14
forum: Desktop Environments
---

### Post by user2037 on 2010-10-14
Ubuntu Netbook's new UI does not make it clear how one would mount NTFS partitions. Adding an entry to Fstab appears to require root/sudo or "rebuild NTFS-3G with integrated FUSE support and make it setuid root".

So is there a easier or better way to grant non-root mount and unmount capabilities for NTFS partitions?

---

### Post by rMatey on 2010-10-14
Hi!

 Have you tried the NTFS Configuration tool under the Ubuntu Software Center???  You can find that button under your Applications menu.  It allows read/write support.

---

### Post by user2037 on 2010-10-14
Ntfs-config fails with an error about a missing "hal" file. Perhaps HAL has been removed from UN 10.10.

---

