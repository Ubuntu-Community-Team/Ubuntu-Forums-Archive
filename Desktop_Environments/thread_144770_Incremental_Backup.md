---
title: "Incremental Backup"
date: 2006-03-15
forum: Desktop Environments
---

### Post by Mau on 2006-03-15
Hi guys,
I'm looking for an incremental backup utility (one that only copies changed or new files).  I have played with Konserve and KDar, but they do not work as advertised.

While compression is good, it is not important.  On Windows, I used one called RapidBackup, which just replicated my entire "home" partition.  I'm looking for a replacement here--be it a shell script of full app.

Any ideas?

---

### Post by Koybe on 2006-03-15
Look at backuppc it's fine, or you can simply use rsync with a batch script+crontab.

---

### Post by Zelut on 2006-03-15
As far as terminal based apps go I'd suggest **rsync**.  man rsync should give you some more info..

---

### Post by pgmario on 2006-03-23
Have a look at [unison](http://www.cis.upenn.edu/~bcpierce/unison/). It has both a command line and GTK-based interface. It's in the official repositories.

---

