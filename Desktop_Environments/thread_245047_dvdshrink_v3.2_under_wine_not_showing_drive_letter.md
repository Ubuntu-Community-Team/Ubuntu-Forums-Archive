---
title: "dvdshrink v3.2 under wine not showing drive letters..."
date: 2006-08-27
forum: Desktop Environments
---

### Post by mmcmonster on 2006-08-27
Hi.
  I installed dvdshrink under wine as per the directions on [this page]("https://help.ubuntu.com/community/DVDShrink").

The program starts up fine, and if I select the "Open Files" icon, I can see all my physical CD/DVD drives.

The problem is that if I select "Open Disc", I have no drive that I can select from to read the disc.

```

$ ls -l .wine/dosdevices/
total 0
lrwxrwxrwx 1 mmc mmc 10 2006-08-26 22:24 c: -> ../drive_c
lrwxrwxrwx 1 mmc mmc 5 2006-08-26 22:24 d: -> /home
lrwxrwxrwx 1 mmc mmc 11 2006-08-26 22:24 e: -> /media/sda1
lrwxrwxrwx 1 mmc mmc 11 2006-08-26 22:24 f: -> /media/sda2
lrwxrwxrwx 1 mmc mmc 13 2006-08-26 22:24 g: -> /media/cdrom0
lrwxrwxrwx 1 mmc mmc 10 2006-08-26 22:24 h: -> /mnt/media
lrwxrwxrwx 1 mmc mmc 13 2006-08-26 22:24 i: -> /home/karthik
lrwxrwxrwx 1 mmc mmc 1 2006-08-26 22:24 z: -> /
$

```

As you can see, I should be able to see the drives.  How can I get them to be detected in the dialog.  As I mentioned above, the drives show up fine from the "Open Files" dialog.

---

### Post by mmcmonster on 2006-08-28
bump

---

