---
title: "What is a good backup to USB program?"
date: 2009-05-24
forum: General Help
---

### Post by gymophett on 2009-05-24
Is there a program that will back up all the files I want to USB other than drag n' drop?

---

### Post by Tibuda on 2009-05-24
I use [grsync]("apt:grsync"). It's a friendly interface for the powerful command line tool rsync.

---

### Post by unutbu on 2009-05-24
```
sudo rsync -a --delete /source/ /target/
```
will copy all files in /source and place them in /target.

The --delete flag tells rsync to delete files in /target that are not also in /source. This is helpful if you want to keep /target looking exactly like /source.

Once you mount the USB drive, it gets a mount point which you could use for /target.

---

