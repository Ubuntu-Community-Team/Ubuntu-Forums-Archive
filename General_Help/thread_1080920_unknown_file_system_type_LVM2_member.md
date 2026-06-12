---
title: "unknown file system type LVM2_member"
date: 2009-02-25
forum: General Help
---

### Post by MountainX on 2009-02-25
I have booted up the 8.10 Live CD.
Gparted shows /dev/sde1 ext2 with boot flag set. This partition has grub installed.

In the Live CD, I type
```
# mount /dev/sde1 /mnt/temp
```

The error is:
```
mount: unknown file system type 'LVM2_member'
```

sde has 2 partitions:
/boot is not LVM - it is plain old ext2
the _**other**_ partition is the physical volume for LVM.

any ideas?


SOLVED
```
# mount -t ext2 /dev/sde1 /mnt/temp
```

---

