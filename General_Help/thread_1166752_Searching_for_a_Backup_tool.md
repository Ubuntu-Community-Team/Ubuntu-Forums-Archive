---
title: "Searching for a Backup tool"
date: 2009-05-22
forum: General Help
---

### Post by K. Hendrik on 2009-05-22
Hi,
i'm already working with ubuntu for about two years but now that I'm no longer using windows paralel I need a new Backup tool I always used Acronis True Image or Norton Ghost.
I want to backup the whole drive and it would be nice If I could still use the system during that time. I know I could use dd with a live cd but is there something more intuitive?

---

### Post by colau on 2009-05-22
> **K. Hendrik said:**
> Hi,
i'm already working with ubuntu for about two years but now that I'm no longer using windows paralel I need a new Backup tool I always used Acronis True Image or Norton Ghost.
I want to backup the whole drive and it would be nice If I could still use the system during that time. I know I could use dd with a live cd but is there something more intuitive?
Partimage.
[http://www.sysresccd.org/Download](http://www.sysresccd.org/Download)

---

### Post by kpkeerthi on 2009-05-22
Try [Backintime]("http://backintime.le-web.org/"). Its a pretty nice tool for snapshot-style (differential) backup. It comes with a GUI but is optional and the backup job can be automated as a cron so it won't get in your way.

[http://maketecheasier.com/automate-your-system-backup-with-back-in-time/2009/04/16]("http://maketecheasier.com/automate-your-system-backup-with-back-in-time/2009/04/16")

I personally use rsync with hardlinks for snapshots, since GUI is not important for me, that is loosely based on [this approach]("http://www.mikerubel.org/computers/rsync_snapshots/"). 

You could also try [TimeVault]("http://www.linux.com/archive/feature/150600") and [Flyback]("http://flyback-project.org/").

---

### Post by binbash on 2009-05-22
I am using partimage and it is cool

---

### Post by K. Hendrik on 2009-05-22
Ok, I think I'll try PartImage to make a full Image of my Disk and Backintime for automatik filebackup.

---

### Post by colau on 2009-05-22
> **kpkeerthi said:**
> Try [Backintime]("http://backintime.le-web.org/"). Its a pretty nice tool for snapshot-style (differential) backup. It comes with a GUI but is optional and the backup job can be automated as a cron so it won't get in your way.

[http://maketecheasier.com/automate-your-system-backup-with-back-in-time/2009/04/16]("http://maketecheasier.com/automate-your-system-backup-with-back-in-time/2009/04/16")

I personally use rsync with hardlinks for snapshots, since GUI is not important for me, that is loosely based on [this approach]("http://www.mikerubel.org/computers/rsync_snapshots/"). 

You could also try [TimeVault]("http://www.linux.com/archive/feature/150600") and [Flyback]("http://flyback-project.org/").
Downloaded flyback from [http://code.google.com/p/flyback/](http://code.google.com/p/flyback/)
```

python flyback.py

```
The problem is attached.

---

### Post by gooligan on 2009-05-22
Here is a very simple method, based on tar
[http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)

---

