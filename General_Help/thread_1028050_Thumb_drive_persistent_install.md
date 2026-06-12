---
title: "Thumb drive persistent install"
date: 2009-01-02
forum: General Help
---

### Post by gehzumteufel on 2009-01-02
I did some searching but was unable to find an answer.

My laptop sucks and is killing HDs but I don't have the money to replace it. I am trying to run an effective install off of my 16gb flash drive, but I keep running out of room when I update the packages. The "/dev/sdb1" has the most amount of space, but "rootfs" seems to be where all this stuff ends up. Or at least that is the part that gets full and it fails when this happens.

Is there anything I can do to fix this?

---

### Post by dcstar on 2009-01-02
> **gehzumteufel said:**
> I did some searching but was unable to find an answer.

My laptop sucks and is killing HDs but I don't have the money to replace it. I am trying to run an effective install off of my 16gb flash drive, but I keep running out of room when I update the packages. The "/dev/sdb1" has the most amount of space, but "rootfs" seems to be where all this stuff ends up. Or at least that is the part that gets full and it fails when this happens.

Is there anything I can do to fix this?

The filesystem used for the stored data is called "casper-rw". If you make a reasonable sized EXT3 partition on your flash drive with this label then it will be used for the data storage.

AFAIK the standard install creates a folder called "casper-rw" on the main partition, this is why you end up running out of space.

---

### Post by gehzumteufel on 2009-01-02
The mount point of sdb1 is /cdrom though. Does that make a difference? Or is that unpartitioned space?

---

