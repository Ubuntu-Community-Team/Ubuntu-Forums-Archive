---
title: "Need ideass for backup system"
date: 2009-02-11
forum: General Help
---

### Post by MountainX on 2009-02-11
Is there a way to meet the following backup requirements?

1. all new or changed files copied to another HDD periodically (say every hour)

2. Directories that are moved on the original, are moved on the back up copy too. Directory structure on backup matches source structure.

3. files deleted on the original are NOT deleted immediately on backup. A user specified delay (from a minute to never) is applied before deleting files from backup.

4. backup has versioning - X number of versions of changed files are saved for Y number of days.

5. the backup destination contains uncompressed, unarchived files.

---

### Post by x C0MMAND0 x on 2009-02-11
First, mount your external hard drive (which I'm assuming you are backing up to).

Second, download rsync, or if you prefer grysnc

```
sudo apt-get install grsync
```

Configure your settings using (g)rsync to exactly as you specified with all of the options your want. 

Set it up as a Cron job so it automatically repeats and whatever interval you want.

[http://www.cyberciti.biz/faq/how-do-i-add-jobs-to-cron-under-linux-or-unix-oses/](http://www.cyberciti.biz/faq/how-do-i-add-jobs-to-cron-under-linux-or-unix-oses/)

That link will show you how to set up a cron job if you aren't already familiar.

Be sure to backup your HOME directory, and your /etc/ directory, as that has many settings.  I would also recommend using a dpkg tool, or APtonCD to get a list of all installed applications you have you you can easily do a re-install if needed.

enjoy!

---

### Post by MountainX on 2009-02-11
> **x C0MMAND0 x said:**
> 

Configure your settings using (g)rsync to exactly as you specified with all of the options your want. 



Thank you. I did some reading on grsync and rsync. It looks like I will have to use rsync to get the functionality I require.

So the trick to making this work will be how to configure rsync.

I will pay if someone wants to help me implement this.

---

### Post by x C0MMAND0 x on 2009-02-11
rsync -r -n -t -v /SOURCE/DIRECTORY/ /BACKUP/DEVICE/DESTINATION

Set that up in a Cron job.

---

### Post by MountainX on 2009-02-11
> **x C0MMAND0 x said:**
> rsync -r -n -t -v /SOURCE/DIRECTORY/ /BACKUP/DEVICE/DESTINATION

Set that up in a Cron job.

Thanks. Do I understand the options correctly? It looks like -n makes a "dry run". (Maybe that's why some people say they do backups with rsync and have no luck when trying to restore?)

 -r, --recursive             recurse into directories
 -n, --dry-run               show what would have been transferred
 -t, --times                 preserve times
 -v, --verbose               increase verbosity

From reading the rsync man page, I still have no clue how to implement my backup requirements, especially:

2. Directories that are moved on the original, are moved on the back up copy too. Directory structure on backup matches source structure.

3. files deleted on the original are NOT deleted immediately on backup. A user specified delay (from a minute to never) is applied before deleting files from backup.

4. backup has versioning - X number of versions of changed files are saved for Y number of days.

---

### Post by MountainX on 2009-03-21
OK, I finally found a great backup solution after a lot of looking. My other backup thread is here:
[http://ubuntuforums.org/showpost.php?p=6933657&postcount=9](http://ubuntuforums.org/showpost.php?p=6933657&postcount=9)

My solution is  [storeBackup]("http://savannah.nongnu.org/projects/storebackup") - [http://savannah.nongnu.org/projects/storebackup](http://savannah.nongnu.org/projects/storebackup)

(and see the documentation here: [http://www.nongnu.org/storebackup/](http://www.nongnu.org/storebackup/))

---

