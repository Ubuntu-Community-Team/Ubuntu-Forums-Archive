---
title: "rsync: if bu dir doesn't exist, no warning"
date: 2009-06-03
forum: General Help
---

### Post by PGScooter on 2009-06-03
Hi, I am using this command to backup my music:

```

sudo rsync -av --delete -b --backup-dir=/medkia/My\ Book/rsync\ backup/ /home/agassi/music/ /media/My\ Book/music/ >> musicbu.log

```

As you see I mispelled "media" for the backup-dir, so the backup-dir does not exist. But there is no warning and rsync goes ahead and deletes things without backing them up.

How can I make it so that rsync produces a warning and does not delete anything if the backup folder does not exist?

thanks

---

### Post by PGScooter on 2009-06-03
nevermind, rsync makes the directory if it does not exist. I wonder what it does if it doesn't have the permission to make it. Oh well, I guess it's not that much of a problem.

---

