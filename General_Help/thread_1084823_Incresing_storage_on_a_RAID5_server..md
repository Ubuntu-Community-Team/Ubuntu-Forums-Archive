---
title: "Incresing storage on a RAID5 server."
date: 2009-03-02
forum: General Help
---

### Post by jmail524 on 2009-03-02
Hi everyone,

I have a system running Ubuntu 8.04 AMD64 as a small home server.  The storage sub system consists of 3 1TB hard drives in RAID5 configuration giving a total available capacity of 2TB.

I recently ran low on space so I added another 1TB hard drive to the RAID set.  However, Ubuntu (GParted/fdisk) did not see the increase until I rebooted the system. The RAID controller supports online migration/upgrade, but how do I force Ubuntu to see the changes when the controller is done adding the capacity to my RAID set.  I would like to be able to add capacity in the future without rebooting the system.

Thanks.
Brian

---

