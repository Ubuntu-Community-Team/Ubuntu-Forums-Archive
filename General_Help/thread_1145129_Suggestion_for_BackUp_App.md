---
title: "Suggestion for BackUp App"
date: 2009-05-01
forum: General Help
---

### Post by n2stc on 2009-05-01
I am looking for an application to do a scheduled backup.  Is "Keep" the best solution?  I've searched these forums in vain.

Thanks,
Stan

---

### Post by Rackstar on 2009-05-01
I liked sbackup (or Simple Backup) it is in the repositories I think. It is easy to configure.

It also allows you to keep incremental backups, and you are able to go back in time.

If speed is needed I would definitely recommend rsync. This just mirrors your files. But really fast. It checks which files are changed and only changes those files.

If you need an app like TimeMachine on Mac, you can try TimeVault, but my experiences weren't that great. I needed it to run through commandline, and this wasn't possible.

It depends on your expertise and demands.

EDIT: never used Keep or heard about it before.

---

### Post by n2stc on 2009-05-01
> **Rackstar said:**
> I liked sbackup (or Simple Backup) it is ...

Thanks I'll check them out.  In UBUNTU 8.1, type keep on a command line.

---

### Post by mb_webguy on 2009-05-01
Keep hasn't been actively developed since 2006.

Try Simple Backup Suite, unless -- as Rackstar said -- speed is an option.  A lot of sysadmins I know use scheduled rsync backups using anacron.  But if you want a GUI solution, Simple Backup Suite seems to be the way to go IMO.

---

### Post by Legace on 2009-05-01
I suggest rsync.
Google rsync tutorial or something like that and you'll find help :)

---

### Post by tom56 on 2009-05-01
Grsync is a great graphical frontend to rsync. I use it for my backups and also for transferring music to my mp3 player.

---

