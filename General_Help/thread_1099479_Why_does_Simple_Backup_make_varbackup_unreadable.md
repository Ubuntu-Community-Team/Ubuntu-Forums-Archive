---
title: "Why does Simple Backup make /var/backup unreadable?"
date: 2009-03-18
forum: General Help
---

### Post by bledsoe on 2009-03-18
I recently installed Simple Backup and tried creating my first backup, which was (presumably) written to the default location /var/backup, but when I went to find the backup file(s) and move it/them to an external drive, I discovered that /var/backup is "unreadable" and furthermore that "You are not the owner, so you cannot change these permissions."

So my questions are:

1. How do I get to my newly created backup file to copy it to an external drive?
2. Why does Simple Backup make this directory inaccessible?

Many thanks for any help,

---

### Post by kpatz on 2009-03-18
use the command **gksudo nautilus** to open nautilus as root (enter your password when prompted).  A root nautilus should be able to view/copy the files in /var/backup.

---

### Post by bledsoe on 2009-03-18
Thanks, I used gksudo nautilus to view the files, and was able to change the permissions so I could copy them to my external hard drive.

Still, it's kind of a pain.  Why does Simple Backup do this?  Wouldn't it be easy enough to make the backup files accessible (at least read-only) so they can be easily copied to an external drive?

---

### Post by geirha on 2009-03-18
If Simple Backup gave everyone read access to the backup files, then all users would have access to read all files in the other users' home directories. Would you want other users to read the personal e-mails you got stored in your home directory? There's no good way for Simple Backup to know how many users are using the system, and who should be allowed read access to the backup, so it makes it readable only to root, and leave it to the system administrator to decide.

---

### Post by bledsoe on 2009-03-18
Ah.  Makes sense.

Many thanks for the quick responses!

---

