---
title: "Adding a New Drive in FSTAB"
date: 2009-01-14
forum: General Help
---

### Post by CarlosinFL on 2009-01-14
I am using 8.10 and have a internal S-ATA drive listed below as /dev/sdb1. I would like to add this device to my system to manually mount. I looked in /etc/fstab and can't make out the correct way to add this to my system.

Can someone please tell me how to properly add this entry in my /etc/fstab if the device is /dev/sdb1 and the mount point is /data? The disk is formated with important data I can't lose as Ext3.

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000ebd04

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       38913   312568641   83  Linux

---

### Post by sisco311 on 2009-01-14
> UUID=xxxxxxxx-xxxx-xxxx-xxxxxxxxxxxxx /data ext3 defaults 0 2

where xxxxxxxx-xxxx-xxxx-xxxxxxxxxxxxx is the uuid of the partition:
```
sudo vol_id -u /dev/sdb1
```

---

### Post by CarlosinFL on 2009-01-14
Can't I simply add device path rather than UUID?

Ex...

/dev/sdb1   /data   ext3   0 0

---

### Post by taurus on 2009-01-14
```
/dev/sdb1 /data ext3 **defaults** 0 0
```

---

### Post by sisco311 on 2009-01-14
> **Carlwill said:**
> Can't I simply add device path rather than UUID?

Ex...

/dev/sdb1   /data   ext3  **defaults** 0 0

yes, you can but /dev/sd* is no longer preferred since these device assignments can change between system boots.

---

### Post by CarlosinFL on 2009-01-14
I have the following and it appears to work....

```
# /dev/sdb1
UUID=a2c0c76b-aaf3-4ed2-b16e-4fe2861be2ea /data           ext3    defaults        0       0

```

---

