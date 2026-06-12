---
title: "Simple Backup Error"
date: 2009-06-09
forum: General Help
---

### Post by Clyktose on 2009-06-09
I recently backed up Ubuntu with sbackup.  I had it backup to the /var/backup directory, and then I copied the folder that had been created to an external hard drive.  Shortly after this back up, I did some very silly things and ended up having to wipe my entire computer and reinstall everything.

After I reinstalled, I moved my backup back onto my hard drive to /var/backup,  but when I open sbackup restore, it keep coming up with"error: no backups found in target directory".

I have been looking for help online, but haven't found any solutions.  I did see some stuff about needing to change permissions for the /var/backup folder, but I wasn't sure what I needed to change the permissions to.

The backup consists of the following files:
excludes
files.tgz
fprops
packages
partitions

If you need any other info, please let me know.

Thanks,
Clyktose

---

### Post by Zill on 2009-06-09
Clyktose:  SBackup saves and restores files as root.  If you have copied the backup files from your external drive as a user then the ownership and/or permissions may not be correct.

I suggest you post the output from the following two commands to show your current permissions:
```
ls -l /var
```
```
ls -l /var/backup
```

---

### Post by Clyktose on 2009-06-09
Output for "ls -l /var"
```
total 48
drwxrwxrwx  3 cullen admin 4096 2009-06-07 05:30 backup
drwxr-xr-x  2 root   root  4096 2009-06-07 05:27 backups
drwxr-xr-x 15 root   root  4096 2009-04-20 10:04 cache
drwxr-xr-x  2 root   root  4096 2009-03-27 04:42 crash
drwxr-xr-x  2 root   root  4096 2009-04-20 10:07 games
drwxr-xr-x 53 root   root  4096 2009-06-07 05:15 lib
drwxr-sr-x  2 root   staff 4096 2009-04-13 05:33 local
drwxr-xr-t  2 root   root    60 2009-06-09 12:40 lock
drwxr-xr-x 13 root   root  4096 2009-06-09 06:51 log
drwxrwxrwx  2 root   mail  4096 2009-04-20 09:59 mail
drwxr-xr-x  2 root   root  4096 2009-04-20 09:59 opt
drwxr-xr-x 18 root   root   740 2009-06-09 12:40 run
drwxr-xr-x  6 root   root  4096 2009-04-20 10:02 spool
drwxr-xr-t  2 root   root  4096 2009-06-09 06:35 tmp

```

Output for "ls -l /var/backup"
```
total 4
drwxrwxrwx 2 cullen admin 4096 2009-05-28 17:47 2009-05-28_17.40.19.566373.CS-Laptop.ful
```

---

### Post by Zill on 2009-06-09
Clyktose:  /var/backup is currently owned by cullen. I believe this should be root for SBackup to work correctly.  The following code should recursively change the ownership of /var/backup back to root:
```
sudo chown -R root /var/backup
```
Hopefully, SBackup will then be able to restore your backup.  Note that this can take quite a while. :icon_frown:

---

### Post by Clyktose on 2009-06-09
I'm still getting the same error.  Am I missing any files?  Something is making me think there was supposed to be an "flist" file, which I don't have.  Could that be causing a problem?

Thanks for the help.

---

### Post by Zill on 2009-06-09
Clyktose:  Yes, there should be an flist file.  FYI, here is a listing from one of my SBackup archives:
```
-rw-r----- 1 root root        221 Jun  1 05:19 excludes
-rw-r----- 1 root root 2090258885 Jun  1 05:19 files.tgz
-rw-r----- 1 root root    2729536 Jun  1 05:19 flist
-rw-r----- 1 root root    1087985 Jun  1 05:19 fprops
-rw-r----- 1 root root      27736 Jun  1 05:19 packages
-rw-r----- 1 root root          4 Jun  1 05:15 ver
```
If you haven't got a full listing then I doubt if SBackup will be able to restore the backup.  However, as I understand it, all the data files are held in the files.tgz file.  If so then you may be able to recover files manually, but I guess it would take quite a while to get things in the right places again. :-(

---

### Post by Clyktose on 2009-06-09
Hmm...distressing.  I suppose I'll start from scratch and just pull in my personal files.  This may actually be good since my last Ubuntu install was a mess because I had absolutely no idea what I was doing.

Thanks again for all the help.

---

