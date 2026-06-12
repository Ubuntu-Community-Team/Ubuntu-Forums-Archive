---
title: "Is there a good Backup Manager?"
date: 2006-09-09
forum: Desktop Environments
---

### Post by beerloko on 2006-09-09
Hello for all, 


Anyone knows if have a good software for manager backups of my personal files?

Thank's

Bruno

---

### Post by ruibernardo on 2006-09-09
if you're talking about a graphical way of doing backups, you can use Simple Backup (apt-get install sbackup).

if you want a pratical way of doing backups, tar is your friend :)

---

### Post by aysiu on 2006-09-09
I would highly recommend *rsync*. If you don't like the terminal, there's a graphical frontend for it called *grsync*.

```
rsync -av /home/beerloko /media/backupdevice
``` should do the trick. Every time you run the command, it will copy over only the files that have been changed or added since the last *rsync*.

---

