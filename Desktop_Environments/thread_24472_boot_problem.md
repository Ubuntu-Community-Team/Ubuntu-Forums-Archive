---
title: "boot problem"
date: 2005-04-07
forum: Desktop Environments
---

### Post by t3rm1n8r1x on 2005-04-07
i jst installed captive-ntfs and changed the fstab entry for my winxp partition to be of type captive-ntfs, but now when i boot it says captive-sandbox-server couldn't be accessed and to run it by hand, then just stops. I thought there was a way to control exactly what started at boot, but i can't find it in the wiki or the forums. If there's a way to edit fstab through windows(i can access the linux part using ext2fsd, but its readonly), i could do that, but i don't know how. can anybody help me?

---

### Post by nad on 2005-04-08
First, to access your ext3 partition, have you tried stating ubuntu in recovery (single user) mode? If you can't do this, do you have a live CD distribution of Linux?

The change you want to make is to the fstab options section of this mount. Auto to noauto.
This will have your ntfs partition not mount at start.

Dan M

---

### Post by t3rm1n8r1x on 2005-04-11
i tried the recovery option, and it still tried to load the partition, which failed. I don't have a live cd. I could also change the file type back to just 'ntfs'

---

