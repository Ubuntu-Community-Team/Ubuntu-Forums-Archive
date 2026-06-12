---
title: "rsync delete"
date: 2009-01-30
forum: General Help
---

### Post by yeleek on 2009-01-30
Hi,

I want rsync to keep a mirror copy of my home folder on an external disk.  I've read though that the use of the delete parameter with rsync can be risky.

Given this command

rsync -a -v -h /home/ben/ /media/HD-PSU2_/rsync/

would it be ok to just add -delete?

Thanks

---

### Post by sizzam on 2009-01-30
For what its worth, I use the '--delete' flag on my backups every night and have never had a problem.  I backup to a separate rsync server.  Here's the command I run in my scripts nightly:

```
rsync -avr --exclude /home/username/.gvfs --exclude /home/username/.cache --exclude /home/username/mount --delete /etc /opt /home  rsync://backup-server/username

```

Here's my entire nightly backup script, it does the rsync job and then emails the output log file to me:

```
#!/bin/sh

# Setup instructions:
# Cron:
#  00 20 * * * /opt/scripts/nightly_backup.sh > /dev/null 2>&1
#
# sudo apt-get install mailx ssmtp
# configure SMTP server in /etc/ssmtp/ssmtp.conf
# mailhub=your.smtpserver.com:25

TODAY=`date +%D`

/usr/bin/rsync -avr --exclude /home/username/.gvfs --exclude /home/username/.cache --exclude /home/username/mount --delete /etc /opt /home  rsync://backup-server/username > /tmp/nightly_backup_to_backup-server.tmp_$$ 2>&1
ERROR=$?

if [ $ERROR != 0 ] ; then
  STATUS="Failure"
else
  STATUS="Success"
fi

mail -a "From:from@address.com (Firstname Lastname)" -s "$TODAY - $STATUS - nightly backup to backup-server" to@address.com < /tmp/nightly_backup_to_backup-server.tmp_$$

rm /tmp/nightly_backup_to_backup-server.tmp_$$

```

---

### Post by vanadium on 2009-01-30
+1

There is no problem with --delete, except if you yourself make a mistake and swap source and destination on the command line, or specify a wrong destination.

Once you are sure of your script, feel free to add --delete for true mirrorring.

Be aware that -h slows things down quite a bit, so use it only if really relevant.

---

### Post by sedawk on 2009-01-30
Some reasons to recover data from a backup:

1) disk failure
2) data deleted
3) data overwritten

Rsync without "--delete" is good for no. 1+2. Rsync with "--delete" only
for no. 1.
To recover from no. 1+2+3 you need something more like
incremental backup or snapshotting. An interesting read for using rsync to achieve this is
[http://www.mikerubel.org/computers/rsync_snapshots/#Incremental](http://www.mikerubel.org/computers/rsync_snapshots/#Incremental)

If you are sure that no. 2 is (currently) not your problem you can run
rsync once with "--delete" to cleanup the backup on the external disk.

---

### Post by yeleek on 2009-01-31
Thanks for the replies guys.

---

