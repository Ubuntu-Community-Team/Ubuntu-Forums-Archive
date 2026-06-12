---
title: "Super-secret util for imaging HDs with NTFS and ext3"
date: 2009-06-17
forum: General Help
---

### Post by tixetsal on 2009-06-17
Does anyone know of a boot disc (or anything else) that can take and image of a drive that contains both NTFS and ext3 primary partitions?  I have tried Ghost and a couple of other open-source options, but I have not been successful.  I am trying to take a pristine image of a dual-boot windows (for blu-ray and oracle calendar synced iphone) / linux (everything else) setup.  The image seems to always fail to include the actual data from at least one of the partitions - usually affecting the ext3 the most.  

Your feedback is appreciated!

---

### Post by Ocxic on 2009-06-17
it's called "dd" comes installed by default in ubuntu. just "sudo dd if=/dev/sda of=/path/to/image" and that will make an exact copy of the HD.(including the free space)

(replace /dev/sda with the drive that you want to backup/image

---

### Post by tixetsal on 2009-06-17
Ocxic,

Thanks!  I will give this a shot tomorrow at work and post back.

> **Ocxic said:**
> it's called "dd" comes installed by default in ubuntu. just "sudo dd if=/dev/sda of=/path/to/image" and that will make an exact copy of the HD.(including the free space)

(replace /dev/sda with the drive that you want to backup/image

---

