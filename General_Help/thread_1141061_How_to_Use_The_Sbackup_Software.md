---
title: "How to Use The Sbackup Software"
date: 2009-04-28
forum: General Help
---

### Post by suresh_vandiyur on 2009-04-28
how to take backup via sbackup software.. plz guide me..

---

### Post by aaronp on 2009-04-28
It's quite simple and very reliable in my opinion.
Once you have installed it, see System > Administration > Simple Backup Config.

Then you set up your parameters.

First tab is where you choose what settings to use. If you use the recommended settings then you are done.
I use custom settings so I also need to go to the other tabs.

Include - paths or files to include in your backup
Exclude - paths/files or file types to exclude from your backup (these will exclude even if they are in the directories you have included in the pervious step)
Destination - this is where the backups will save to. I save mine to my 'permanently attached' external USB drive.
Time - set how often to backup - cron style format.
Purging - tell the software how often to delete old backups and what to keep/get rid of.

Basically it will perform a full backup of all your inclusions (minus exclusions) first. Then it will perform incremental backups (only files that have changed) as separate backup folders within your backup location. Each backup will basically be a snapshot of what has changed since the previous backup.
Restoring from backup is as easy as using the 'Simple Backup Restore' option on the same menu and choosing the date and file/s you want to restore.

Another good feature is that it always creates a list of all currently installed apps so if you had to do a full reinstall it could restore your system to the exact state (i.e. data + apps)

hope this helps - any trouble, let us know...
Aaron

---

