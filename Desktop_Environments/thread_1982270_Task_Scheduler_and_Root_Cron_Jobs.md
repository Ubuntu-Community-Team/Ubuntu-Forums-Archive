---
title: "Task Scheduler and Root Cron Jobs"
date: 2012-05-18
forum: Desktop Environments
---

### Post by mrcpuhead on 2012-05-18
I'm running kubuntu 12.04 LTS, and just added a root crontab for a daily backup task.  The Task Scheduler within System Settings only shows the personal cron and system cron (which doesn't include the root cron I created).  Is there a way to configure Task Scheduler to show the root cron job(s)?  If not, how can I best check the status of this job?  Can I only do this by waiting for the first run and checking the syslog?

---

### Post by SeijiSensei on 2012-05-18
Ordinary users cannot see root's crontab for obvious security reasons.  

I presume you already ran the backup command manually from root's account either via sudo or su.  If it works there, and you have the time syntax correctly specified, just wait until after it's supposed to run and check the results.

If the command is actually a script, or is easily scriptable, then the standard method for scheduling a daily task with root privileges is to create a symbolic link to the script in /etc/cron.daily.  So if you want to run /usr/local/sbin/backup every night, just do this:

```
cd /etc/cron.daily
sudo ln -s /usr/local/sbin/backup
```

You can adjust the time when scripts in this directory are run by editing (as root) the file /etc/crontab.  Oh, and Debian-based systems like Ubuntu have a bug that requires scripts linked from the cron.* directories not to end in .sh.  So the entry I gave above will work, but not one that points to backup.sh.

---

