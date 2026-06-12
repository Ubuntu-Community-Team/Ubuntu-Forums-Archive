---
title: "How to do automated incremental backups?"
date: 2008-12-10
forum: General Help
---

### Post by AceRimmer on 2008-12-10
I want to back up one drive to another drive of the same size.  Is there a package that will do automatic incremental backups?  Or do I have to write a script to do it?

---

### Post by northern lights on 2008-12-10
If you're looking to synchronize two folders / partitions / drives you might want to take a look at *unison* as available from the repos.

---

### Post by DGortze380 on 2008-12-10
don't really need a 'script' per say.. but you can easily do this with a one command long 'script' and a cron job

put the following into a file in you home directory. modify the directories to match what you need:

```

#!/bin/bash

rsync -ax /path/to/source /path/to/dest

```

save the file as backup.sh

run the following commands in order:
cd ~
chmod 770 backup.sh
sudo mv backup.sh /usr/bin/backup.sh

man crontab to learn how to configure it. It's not hard.
sudo crontab -e
allows you to edit roots crontab.
add /usr/bin/backup.sh to run at the times you want.

This will do a full backup of source to destination the first time, then add new files, and update changed files subsequent times. Note the -x flag limits the command to one file system. To automatically delete files from the dest which have been deleted on the source add the --delete flag after -ax.

---

### Post by AceRimmer on 2008-12-12
Thank you both.

---

### Post by AceRimmer on 2009-02-25
Another question related. I have the home folder rsynch'd to the backup drive fine btw.  So suppose drive 'B' is mounted in /backup and drive 'A' is the master disc that is booted from and all that.  So if I set the source in my rsync command to '/' and the destination '/backup' but excluded the /backup folder would it create a mirror of 'A' in that folder?  Would that be bootable in the event 'A' crashed?

---

### Post by DGortze380 on 2009-02-25
> **AceRimmer said:**
> Another question related. I have the home folder rsynch'd to the backup drive fine btw.  So suppose drive 'B' is mounted in /backup and drive 'A' is the master disc that is booted from and all that.  So if I set the source in my rsync command to '/' and the destination '/backup' but excluded the /backup folder would it create a mirror of 'A' in that folder?

Yes

> **AceRimmer said:**
> 
Would that be bootable in the event 'A' crashed?

Depends, possibly.

> **AceRimmer said:**
> 
excluded the /backup folder

the -x flag takes care of that. limits you to 1 file system.

---

