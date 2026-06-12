---
title: "sudo / crontab execution of rsync behaves inconsistently"
date: 2009-03-23
forum: General Help
---

### Post by mbeeby on 2009-03-23
Hi All,

I wondered if anyone could help with a little problem I'm having making backups? I have a crontab set up to do a weekly backup. I have two 1tb disks, with one mounted as the /home directory on the other.

I setup my crontab using "sudo crontab -e". The relevant line looks like this:

```
0 1 * * 0 /usr/local/bin/weekly_backup.sh
```

The file weekly_backup.sh looks like this:

```
#!/bin/sh

echo "===========================" >> /var/log/weekly_backup.log
date >> /var/log/weekly_backup.log

# Backup to weekly_backup1 external drive (all but /home and /jensenX directories)
echo "BACKUP 1" >> /var/log/weekly_backup.log
mount /mnt/weekly_backup1
echo /usr/bin/rsync -avl --delete --exclude="/home" --exclude-from="/usr/local/bin/backup_exclude.list" / /mnt/weekly_backup1 >> /var/log/weekly_backup.log
/usr/bin/rsync -avl --delete --exclude="/home" --exclude-from="/usr/local/bin/backup_exclude.list" / /mnt/weekly_backup1 >> /var/log/weekly_backup.log
umount /mnt/weekly_backup1
echo "FINISHED BACKUP 1" >> /var/log/weekly_backup.log

# Backup /home directory to weekly_backup2 external drive
echo "---------------------------" >> /var/log/weekly_backup.log
date >> /var/log/weekly_backup.log
echo "BACKUP 2" >> /var/log/weekly_backup.log
mount  /mnt/weekly_backup2
echo /usr/bin/rsync -avl --delete --exclude-from="/usr/local/bin/backup_exclude.list" /home /mnt/weekly_backup2 >> /var/log/weekly_backup.log
/usr/bin/rsync -avl --delete --exclude-from="/usr/local/bin/backup_exclude.list" /home /mnt/weekly_backup2 >> /var/log/weekly_backup.log
umount /mnt/weekly_backup2
echo "FINISHED BACKUP 2" >> /var/log/weekly_backup.log

```

Finally, the exclude file, backup_exclude.list, looks like this:

```

/jensen1
/jensen3
/jensen24
/media
/proc
/mnt/backup1
/mnt/backup2
/mnt/weekly_backup1
/mnt/weekly_backup2
```

As can be seen, the backup first backs up essentially all but /home (i.e., it backs up the first hard drive), then it separately backs up the /home directory (i.e., the second hard drive). Executing the individual rsync commands from the command line as sudo works fine. However, running the crontab at 1am every Sunday morning results in some strange behavior: / is backed up fine, but /home isn't backed up. Here's an edited /var/log/weekly_backup.log output file:

```
===========================
Sun Mar 22 01:00:01 PDT 2009
BACKUP 1
/usr/bin/rsync -avl --delete --exclude=/home --exclude-from=/usr/local/bin/backup_exclude.list / /mnt/weekly_backup1
sending incremental file list
dev/pts/0
dev/shm/
dev/shm/pulse-shm-4122677215

[... snip ...]

sys/bus/acpi/drivers/thermal/
sys/bus/acpi/drivers/video/
sys/bus/acpi/drivers/wmi/
FINISHED BACKUP 1
---------------------------
Sun Mar 22 01:00:59 PDT 2009
BACKUP 2
/usr/bin/rsync -avl --delete --exclude-from=/usr/local/bin/backup_exclude.list /home /mnt/weekly_backup2
sending incremental file list
FINISHED BACKUP 2
```

So the problem is that rsync simply says "sending incremental file list", but seems to send no file list. The drives seem to be mounted fine, and the command works if executed as sudo. Can anyone tell me why it doesn't work when run through crontab, despite the first rsync command working fine?

Many thanks!

-Morgan

---

### Post by hyper_ch on 2009-03-23
I'd say problem is this:

```

#!/bin/sh

```

cron and normal user have different shells. Specify bash instead.

---

### Post by mbeeby on 2010-10-21
The shell wasn't the issue...

Turns out the problem was that rsync treats the .gvfs/ directory in the root directory of a user as a real directory, then gets upset. And when rsync gets upset, it doesn't delete any files (as a precautionary measure, apparently).

Adding 

```
--exclude='.gvfs/'
```

to the arguments of my rsync command remedies the problem.

---

