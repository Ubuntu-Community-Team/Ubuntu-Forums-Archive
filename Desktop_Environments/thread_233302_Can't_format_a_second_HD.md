---
title: "Can't format a second HD"
date: 2006-08-09
forum: Desktop Environments
---

### Post by Cris987 on 2006-08-09
I'm trying to format an originalll fat32 hd into a linux partition so that I move and restore data from there when I ever decide to re-install ubuntu. I deleted the partition and made a primary linux partition using cfdisk, but when i try to use mkfs, it says "/dev/hdd2 is apparently in use by the system; will not make a filesystem here!". Any clue as to how I can fix that?

---

### Post by simonn on 2006-08-09
umount it

```

$ sudo umount /dev/hdd2

```

---

