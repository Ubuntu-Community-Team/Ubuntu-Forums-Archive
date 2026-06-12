---
title: "Ext4 repair"
date: 2009-06-13
forum: General Help
---

### Post by rado3105 on 2009-06-13
Hi I have jaunty and I use ext4 fs on my disk. I want to ask how to repair it, because the computer is freezing, sometimes cant start and shows bad blocks. The hardisk is allright, just filesystem seems to be corrupted.

---

### Post by Soul-Sing on 2009-06-13
press ESC at the GRUB menu then choose recovery mode
: choose harddisk: on an IDE disk then it will be "/dev/hda.."


example!
: ```
fsck /dev/hda1
```
------------------------------------------------------

better though via a live(cd) session. The partition should be unmounted!

```
sudo fsck /dev/hda<.>
```( <.> = number partition)

---

### Post by whoop on 2009-06-13
You could also boot from a live cd, startup partition editor (gparted) and right click on the ext4 partition and choose check.

---

### Post by rado3105 on 2009-06-13
Thanks a lot I was thinking it is different command than fsck.

---

