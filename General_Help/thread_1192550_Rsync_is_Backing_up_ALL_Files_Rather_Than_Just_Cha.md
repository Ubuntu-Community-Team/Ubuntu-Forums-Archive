---
title: "Rsync is Backing up ALL Files Rather Than Just Changed Files"
date: 2009-06-20
forum: General Help
---

### Post by Penguin Guy on 2009-06-20
I am trying to run an rsync from /home to my backup device mounted at /media/backup but it is copying all files rather than just those that have changed. Both are on an ext3 filesystem. /home is in it's own partition.

The exact code I am using is: [COLOR="Green"]rsync -act /home/ /media/backup/$HOSTNAME:\ Home\ Backup/ --exclude=Home\ Backup --exclude=lost+found --include=.aliases --exclude=.*[/COLOR]
What am I doing wrong?

**Turns out I made a mistake in my backup script so that the backup got written to a different file name.**

---

### Post by vikkikanhaua on 2009-06-20
u should use -u option also, along with -act,
which checks for changes in files

---

### Post by Penguin Guy on 2009-06-22
I made stupid mistake in my backup script which resulted in a different file name. Therefore rsync was creating a new file rather than adding to the old one. 
Sorry for wasting your time.

---

