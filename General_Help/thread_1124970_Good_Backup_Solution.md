---
title: "Good Backup Solution"
date: 2009-04-13
forum: General Help
---

### Post by HOLOGRAPHICpizza on 2009-04-13
I'm looking for a backup program / script that I could schedule to run once a week, the first time a full backup, then incremental after that.

One feature that I really need is the ability for the program / script to detect if a file was *deleted* since the last incremental backup. That way the backup dosen't become massive and bloated with every file that I ever had at any time in my life.

I have 2 identical 500 gb harddrives with 1 big ext3 partition on each. One is full of files, and the other one is empty, and I plan to use it to back up to.

Any suggestions would be appricated!

---

### Post by lovinglinux on 2009-04-13
rsync

---

### Post by aaronp on 2009-04-14
I like rsync too, and will be looking at this as my next solution after recently discovering it.

I used to use simple backup which is also excellent. Schedule full backups and incremental backups and a gui tool to restore files.

---

### Post by HOLOGRAPHICpizza on 2009-04-14
> **lovinglinux said:**
> rsync

Awesome! :D
I *never* thought of that! Thanks!

---

