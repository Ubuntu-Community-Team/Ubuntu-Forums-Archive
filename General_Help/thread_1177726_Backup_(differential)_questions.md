---
title: "Backup (differential) questions"
date: 2009-06-03
forum: General Help
---

### Post by boban on 2009-06-03
Hi!

I am stuck with a problem of how to create differential backup. Basically, I want to accomplish the following things:
[LIST]
[*] Backup mysql dumps of (almost) every database on a server. I want to do full backup once a week, and differential on the daily basis(real, content-based differential backups). 
[*] Backup subversion dumps (in a similar way to mysql)
[*] Backup bunch of a directories in the filesystem (like /home, /var/www, etc.). This can be done on a monthly basis with incremental backup in-between. I do not need real differential backups, so this can be done fully by tar. 
[*] Sync this backup to another server. Here I think that rscync will be sufficient.
[/LIST]

Basically, first two points (svn and mysql) are almost alike, and problematic. Lets assume that I have a dump directory, i.e. /backup/dumps. Cron is running my backup script, which first generate dumps. So I end up with bunch of files, e.g.:

/backup/dumps/mysql/first_db.sql
/backup/dumps/mysql/second_db.sql
/backup/dumps/mysql/third_db.sql
/backup/dumps/svn/first_repo.dump
/backup/dumps/svn/second_repo.dump
/backup/dumps/svn/third_repo.dump

Now i want to compress them and move to other directory. On the other day another script will do the same thing, but I want to preserve only differences between files. I cannot use tar for this purpose, because those files are generated. 
I tried to use dar for this. But it was no good also. When I tested this solution and changed something at the begining of the dumps, the behaviour was correct - differential backup were quite small. But after I created dumps again, dar was unable to handle changes well ( mysqldump adds time of dumping to the files) - dar figured out that all files were changed, but it didn't preserve only diffs but created full copies of every file. So I ended up with "differential backups" that were slightly larger than the full backup.

After searching for a few hours I came to conclusion that I have to combine: tar + rdiff + 7z (or other compression utiltiy) to accomplish simple(?) differential backup. I ended with a complicated script that: creates dumps, tars them into two archives (one for mysql and one for svn), and:
[LIST]
[*] for full backups: creates signatures with rdiff, compresses tars with 7z and moves to backup directory
[*] for incremental backups: creates deltas to last signature, compresses them and moves to backup directory
[/LIST]

And I think that this solution is a little bit overcomplicated. Perhaps there is simpler way to accomplish this task? Any suggestion will be appreciated...

---

