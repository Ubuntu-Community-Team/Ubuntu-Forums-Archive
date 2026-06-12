---
title: "Correct back-up procedure for evolution e-mail files"
date: 2018-05-04
forum: Desktop Environments
---

### Post by cigtoxdoc on 2018-05-04
Now that evolution 3.28.1-2 is part of the official software for 18.04 LTS, I am hoping that I can get help on correct procedure for doing daily backup of at least the e-mail files for evolution.  For example, at say 3 a.m. every day, I would like evolution to do a File - Backup Evolution data, use the default filname and location, do the backup and start evolution again.  The gurus on the evolution support group have claimed in the past that they know nothing about Ubuntu and that the file backup evolution data is only for transferring evolution from one pc to another.

We all know the importance of daily backups of critical data.  My evolution e-mail data is mission-critical to my business.  How do I do a daily backup other than start it manually?

John

---

### Post by sevendogsbsd on 2018-05-05
I thought Ubuntu had a backup application that does scheduled backups, no? I played with it once, it did a backup of my entire /home directory. Problem with it is you can't restore individual files, or at least I couldn't figure out how to.

Personally, I backup with rsync to other discs: some internal, some external and this works perfectly. In my case, I only keep the latest copy and don't have incremental copies by date, although this is possible. I do mine manually but they can certainly be scripted with cron or another means if your machine runs 24x7. I also believe there are graphical back up apps out there for Linux although I have no experience with them. Someone else may chime in with another solution.

The Evolution files are, I believe under ~/.config and ~/.local/share but don't quote me on that as I don't use Evolution. Of course if you have local mail folders, they will be wherever you put those.

---

### Post by PaulW2U on 2018-05-05
> **sevendogsbsd said:**
> I thought Ubuntu had a backup application that does scheduled backups, no? I played with it once, it did a backup of my entire /home directory. Problem with it is you can't restore individual files, or at least I couldn't figure out how to.
Ubuntu does have a backup application - it's called Backups, aka as Deja Dup and can perform backups on a regular or scheduled basis.

Restoring individual files is possible although you need to initiate the process from nautilus, right-click a file and restore a previous version.

Confused? Yeah, me too. :D

---

### Post by cigtoxdoc on 2018-05-11
Thank you.  It appears that only reasonable recourse is to manually start the backup and the end of each day.  Make sure the back up worked, and then delete the previous day's backup.

John

---

### Post by SeijiSensei on 2018-05-11
I run nightly backups with a script that runs from cron.  I'd just back up your entire /home partition every night.  I write my backups to a 4 GB external drive.  It's large enough that I can keep multiple days of backups in date-labelled directories, e.g., /backup/20180510/.  The code looks like this:

```

#!/bin/bash
LOGDIR=/var/log/backup

# backups stored in this directory
DESTDIR=/mybackups  

# how many days to preserve
ROTATE=5


TODAY=$(date +%y%m%d)
STALE=$(date +%y%m%d --date="$ROTATE days ago")

LOG="${LOGDIR}/${TODAY}.log"
echo "$(date +%c) - Backup starting" > $LOG

cd /

STALEDIR="${DESTDIR}/${STALE}"

# keep one backup and log each month
if [ "$(date +%d)" != "01" ]
then
        echo "Deleting stale backup $STALEDIR" >> $LOG
        rm -rf $STALEDIR
        
        echo "Deleting stale log $STALE" >> $LOG
        rm -f $LOGDIR.$STALE.log
fi

DEST="${DESTDIR}/${TODAY}"
echo "Creating new backup directory $DEST" >> $LOG
mkdir -p $DEST

rsync -av home $DEST


```
This is only for guidance; you'd need to adapt the code to your specific purposes.  The script creates a directory each night, and deletes the stale directory from five days earlier. It keeps the backup from the first of each month as an archive. It then uses rsync to copy the contents of /home to the backup directory.

---

### Post by Holger_Gehrke on 2018-05-12
Unless something has changed from evolution 3.26.1-1 (which I am using on XUbuntu 17.10) to the 3.28.1-2 you're using, the menu item in evolution actually calls a separate program named 'evolution-backup' located in '/usr/lib/evolution/evolution-backup' (found this out by looking at the output of ps while the backup was running and then looking for 'evolution-backup' with find). Calling this program with the option '--help' yields
```

$ LANG=C /usr/lib/evolution/evolution-backup --help
Usage:
  evolution-backup [OPTION?]

Help Options:
  -h, --help               Show help options
  --help-all               Show all help options
  --help-gtk               Show GTK+ Options

Application Options:
  --backup                 Back up Evolution directory
  --restore                Restore Evolution directory
  --check                  Check Evolution Back up
  --restart                Restart Evolution
  --gui                    With Graphical User Interface
  --display=DISPLAY        X display to use

```
What this help doesn't mention is that the program also needs the name (and path) of the file to backup to, which is an xz compressed tar-file, so the extension .tar.xz would be a good idea (but not mandatory).

The advantage of using this over other methods is that it stops evolution before doing the backup (and can optionally restart it afterwards) to avoid producing inconsistent backups if evolution were to fetch new mails while the backup is running. It also gets the configuration-data from dconf and saves that in the clear in the archive.

Holger

---

