---
title: "livd cd won't boot"
date: 2008-01-05
forum: Desktop Environments
---

### Post by stevek28 on 2008-01-05
i burned the live cd image and changed the boot order.   When I reboot my machine looks at the cd in which the xbuntu is located but goes right to windows xp.  What might be wrong?
BTW when I click the cd icon it brings up the Ubuntu browser.

---

### Post by Sef on 2008-01-05
1) Did you [md5sum]("https://help.ubuntu.com/community/HowToMD5SUM") the iso? (Checks to make sure the download was good.)

2) Did you burn the iso as an iso?

3) Did you burn the iso at 4x or less? (Faster can corrupt the download.)

4) Recheck that the cd-rom/r/rw is set before the hard drive.

---

### Post by stevek28 on 2008-01-05
> **Sef said:**
> 1) Did you [md5sum]("https://help.ubuntu.com/community/HowToMD5SUM") the iso? (Checks to make sure the download was good.)

2) Did you burn the iso as an iso?

3) Did you burn the iso at 4x or less? (Faster can corrupt the download.)

4) Recheck that the cd-rom/r/rw is set before the hard drive.

I did all you said, but it still does not boot.  However the picture of the cd shows 9 files but my CD only has 8.  In fact all the CDs I burned (3) only had 8 files (the correct number of directories, however).  The checksum was correct so I am at a lose to understand this

---

### Post by bharadwaj on 2008-01-06
When everything is fine and even md5sum is correct then probably the problem could only be with two of them either the ISO is not properly burnt or your boot records in the boot order, I mean did you make CD device as primary master or secondry master and tried booting?

---

### Post by stevek28 on 2008-01-06
> **bharadwaj said:**
> When everything is fine and even md5sum is correct then probably the problem could only be with two of them either the ISO is not properly burnt or your boot records in the boot order, I mean did you make CD device as primary master or secondry master and tried booting?
i had misidentified my two drives. I put the CD into the other drive and it booted up
thanks for your help
If I click on "install"icon (to speed up boot time) does this modify my windows system and interferes with normal windows operation?  Also,my networked drive is mounted but local drives are not.  Is that normal

---

