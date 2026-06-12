---
title: "Is there a scheduler?"
date: 2008-12-12
forum: General Help
---

### Post by Maheriano on 2008-12-12
I want to copy all files from a certain folder and back them up on a separate drive nightly. That way when a drive fails I won't lose any of my files.

---

### Post by marshall.robert on 2008-12-12
look for Gnome Schedule in Add/Remove...

---

### Post by m_l17 on 2008-12-12
You can also use cron:

[https://help.ubuntu.com/community/CronHowto]("https://help.ubuntu.com/community/CronHowto")

---

### Post by rbmorse on 2008-12-13
There is an application named sbackup that was written specifically to handle exactly this kind of thing. It's in repository, is easy to use and I've found it to be very reliable. I've used it to backup my /home for about 6 months and it works without problem.

---

### Post by 12barz on 2008-12-13
RBMorse - Have you checked to make sure your sbackup backups are truly restorable?  I tried to backup my Photos folder (a subfolder of Home) and got fewer than half of the original files back. The restore was done as a test from the .ful backup.  I had first copied my photos onto a separate external hard drive, then cleared the original folder, then tried to restore.  The original archive seems to contain all the missing files, just wouldn't restore them.  Very disappointed and looking for another application.  If it won't restore, the reliably appearing daily backups are meaningless.

---

