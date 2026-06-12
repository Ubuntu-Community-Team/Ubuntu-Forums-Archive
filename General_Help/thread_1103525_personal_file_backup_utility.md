---
title: "personal file backup utility"
date: 2009-03-22
forum: General Help
---

### Post by v1nsai on 2009-03-22
I'm looking for a program that would let me select a few folders to watch and automatically sync the contents of that folder with a flash drive, anyone know of something like that?  I wish I had the time to just write one myself but that will be another day...

---

### Post by Squalo_ch on 2009-03-22
Have you tried TimeVault
[https://wiki.ubuntu.com/TimeVault](https://wiki.ubuntu.com/TimeVault)
or BackInTime?
[http://www.le-web.org/back-in-time/#repository](http://www.le-web.org/back-in-time/#repository)

---

### Post by James_Lochhead on 2009-03-22
Sbackup? (in repos)

---

### Post by v1nsai on 2009-03-23
Thanks I'll take a look at them, some of these seem a little overly complicated, I'm not sure what a "snapshot" is in relation to just transferring the files for storage but thanks for the suggestions, 'apt-cache search backup' didn't help much.

---

### Post by Alex Yeh on 2009-03-23
you could do this with rsync, and if you have the flash drive attached at the same place usually, a crontab.

rsync comes with Ubuntu.

---

### Post by v1nsai on 2009-03-26
rsync looks more like what I was looking for, reading the community documentation now, thanks for the tip.

---

