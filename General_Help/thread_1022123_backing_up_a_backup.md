---
title: "backing up a backup"
date: 2008-12-26
forum: General Help
---

### Post by okpgreg on 2008-12-26
Hey everyone.  I have a situation where I have about a dozen servers that I'm using backup ninja to backup to one central server on a daily basis.  I also want to pull the most recent backup from each of those on a weekly basis to another server.  I was trying to think of the easiest way to do this.  Would I essentially have to write a script that sshed into the main backup server, did a local rdiff -r now to each of the backed up directories, then tar them and scp them back? Or can someone think of a more simple way to do this?   Thanks.

---

### Post by albinootje on 2008-12-26
> **okpgreg said:**
>  Would I essentially have to write a script that sshed into the main backup server, did a local rdiff -r now to each of the backed up directories, then tar them and scp them back? Or can someone think of a more simple way to do this?   Thanks.

You can use rdiff-backup in combination with ssh keys.
Using rsync is also possible, but then you need scripts to create incremental backups of your backup.

[http://www.nongnu.org/rdiff-backup/](http://www.nongnu.org/rdiff-backup/)
[http://packages.ubuntu.com/search?keywords=rdiff-backup](http://packages.ubuntu.com/search?keywords=rdiff-backup)

---

### Post by okpgreg on 2008-12-26
Right, I already have rdiff-backup using ssh w/ keys to connect and make the backups.  To get the latest backup would I have to do rdiff-backup -restore?  Or could I just copy the directory?

---

### Post by albinootje on 2008-12-26
> **okpgreg said:**
> Right, I already have rdiff-backup using ssh w/ keys to connect and make the backups.  To get the latest backup would I have to do rdiff-backup -restore?  Or could I just copy the directory?

Ah.. I didn't know that "backup ninja" uses rdiff-backup.

Using the restore option of rdiff-backup to get a copy of the latest backups would be an interesting idea to also test whether restoring works properly. Why don't you test it, and then perhaps compare with a rsync dry run against a restored backup on the server itself ?

---

