---
title: "cron won't run my scripts properly!"
date: 2006-05-14
forum: Desktop Environments
---

### Post by Footer on 2006-05-14
I've got a script I wrote to backup my /home partition on a nightly basis.  It worked for awhile but in the past month or two, it only writes 4.3MB when it should be something like 3.7GB.  The script is set to run from cron at 2:00am (I scheduled it using KCron) every day.

I can run this script manually from the command line and it works just fine.  But for some reason, the scheduled cron job only writes 4.3MB and then stops.  I don't know how to monitor this or where to look for the error, if any, that is generated.

Any ideas?

Thanks!

](*,)

---

### Post by IYY on 2006-05-14
Make the script write its output to a log file.

```
scriptname > /location/of/logfile/log.txt
```

Maybe you're out of disk space?

---

### Post by Footer on 2006-05-15
Thanks for the reply/suggestion.  Why didn't I think of that?  :)

Anyway, I'm not sure how useful the log file will be since it's simply a listing of all the files being backed up.  But perhaps if it's stopping at a certain place every time, I can pick that up from the log file.

Right now, I'm a little confused about why this script is now running twice/day.  Yesterday afternoon in my attempts to troubleshoot this problem, I used KCron to schedule the script to run daily in the afternoon (it was set to run at 2:00am every day).  This morning when I looked, there was another 4.3MB file showing it had run at 2:00am again.

So I'm watching to see if it's now running twice/day or if last night was a fluke.  The crontab file shows only one entry for the afternoon run ... hmmmm ...  I'm confused.  :confused:

EDIT:  I'm pretty sure space isn't an issue as it's writing the archive to a 250GB drive/partition with only a few percent used.  :)

---

### Post by Footer on 2006-05-16
Well, I'm not exactly sure what's going on now but it's working properly!  Here's my current crontab:

footer@kubuntu:~$ crontab -l
# Daily Backup
5 16 * * *      /home/footer/backup.sh > /home/footer/backup_log.txt
# Daily Backup @ 2:00am
0 2 * * *       /home/footer/backup.sh > /home/footer/backup_log.txt
# This file was written by KCron. Copyright (c) 1999, Gary Meyer
# Although KCron supports most crontab formats, use care when editing.
# Note: Lines beginning with "#\" indicates a disabled task.

So I've added another backup at 1605 in the afternoon and my normal backup at 0200 in the morning with log files written by both.  Both are working now!  Maybe writing out the log file makes it work?  Don't know but in either case, I'm a happy camper!

Thanks!

:)

---

