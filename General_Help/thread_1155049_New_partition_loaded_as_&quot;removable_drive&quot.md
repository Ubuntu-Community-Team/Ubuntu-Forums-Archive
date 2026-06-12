---
title: "New partition loaded as &quot;removable drive&quot;"
date: 2009-05-10
forum: General Help
---

### Post by shafin on 2009-05-10
Hi,
When I installed ubuntu on my HDD, I left some unpartitioned space. Later I formatted the partition to NTFS. Then I edited fstab with its uuid to auto mount the partition. The problem is, the partition is automounting as a removable drive. Taat means it goes under the menu "removable drives" in places menu. So it needs three clicks to reach it instead of two. How can I get ubuntu to register the paririon as a normal HDD partition rathere than a removable drive?

Thanks in advance.

---

### Post by drs305 on 2009-05-10
Try mounting it in /mnt rather than in /media, if that is where it is. Make a new mount point in /mnt and then point fstab to the new mount point. Unmount the device and then run "sudo mount -a" to see if that makes a difference.

---

### Post by danwood76 on 2009-05-10
It will get grouped as a removable drive if you have several removable drives conencted.
This is the same for all partitions that are not system partitions I believe. (mounted in /media)

There is probably a way to modify the count before it makes that menu so all the removable drives are always listed.

---

### Post by shafin on 2009-05-10
Is there some way to get it done while still having it mounted under /media. I asked it because I run many virtual machines and share the /media folder with all of them, that way they get instant access to all my drives, If I try the mnt path, I'll have to include it in every single one of them. Also I'll have to change a lot of shortcuts.

---

