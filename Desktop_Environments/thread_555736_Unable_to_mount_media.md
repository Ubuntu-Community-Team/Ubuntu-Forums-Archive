---
title: "Unable to mount media"
date: 2007-09-20
forum: Desktop Environments
---

### Post by GolfGeek on 2007-09-20
I have a Samsung CR\DRW drive that work perfectly on boot up (if I leave a live CD in the drive, it will boot) but once I am logged in, I cannot access the drive. The message is the same "Unable to mount media". I am trying to burn a new .iso and am getting very frustrated. In places, computer it shows the CDRW drive but no access. Any suggestions.
thanx

---

### Post by GolfGeek on 2007-09-20
Edit to the first message:
I went to a terminal session and checked the settings in fstab:

proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=2a4a330d-9eed-4fbd-8332-42796ee47ddc /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=04b749bd-0570-44de-a7a6-7d8ae69ad2d4 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

Does any of this make sense as to why I can't access the drive?

---

