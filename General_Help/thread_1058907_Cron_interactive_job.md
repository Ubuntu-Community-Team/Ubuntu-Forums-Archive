---
title: "Cron interactive job"
date: 2009-02-03
forum: General Help
---

### Post by yeleek on 2009-02-03
Hi,

Got a .sh backup script that works great (with help from here).  

[PHP]#!/bin/bash
zenity --question --text "Would you like to start the weekly backup?"
result=$?
#echo $result

if [ "$result" = "0" ]; then
	echo Proceed with backup
else
	zenity --info --text "Quitting..."; exit
fi

zenity --info --text "Confirm external hard disk is attached and then click ok"

rsync -a -v -h --delete --itemize-changes /home/ben/ /media/HD-PSU2_/rsync/ > ~/backuplogs/backup-`date +%d-%m-%y`.log[/PHP]

It runs fine from terminal or via double click but from Cron, the zenity boxes do not appear.

Please advise.

Thanks

---

### Post by dagnabit dang doohickey on 2009-02-03
You need to add a DISPLAY environment variable to the cron job.

Example of using anacron to run somescript.sh every week:
```
# period  delay  job-identifier  command
7    20    somescript.weekly    env DISPLAY=:0.0 somescript.sh
```

The only benefit I see of using cron/anacron with your script is it becomes your reminder, you are then free to forget. If that's the case, your script may have something of a shortcoming.

If you skip the backup when offered, the next reminder will be a week later. If that's the desired behavior, that's fine, but if you'd like to be reminded again that a backup is due, say each day after skipping the backup, you would need to modify the script.

A way to go about this is to have the script write a timestamp file after every successful backup, then instead of running the script as a weekly job, run it daily. The first thing the script should do is check the timestamp file. If the timestamp is over a week old, proceed with the backup reminder, else exit.

---

### Post by yeleek on 2009-02-03
Hi,

Thanks for reply

I've tried 

40 19 * * * env DISPLAY=:0. /home/ben/backup.sh

and

45 19 * * * env DISPLAY=:0 && /home/ben/backup.sh

Neither work - executing that script /home/ben/backup.sh from terminal works fine.  What am i doing wrong?

---

### Post by dagnabit dang doohickey on 2009-02-03
You need to specify the full path to the executables somewhere. Either in the script, by expanding of all of them to include the full path (eg. zenity to */path/to/zenity*), or in the crontab file, by adding a PATH environment variable at the top of the crontab file that satisfies all required paths of your script (eg. *PATH=/usr/sbin:/usr/bin:/sbin:/bin*).

---

### Post by dcstar on 2009-02-03
> **yeleek said:**
> Hi,

Thanks for reply

I've tried 

40 19 * * * **env DISPLAY=:0.** /home/ben/backup.sh

and

45 19 * * * **env DISPLAY=:0** && /home/ben/backup.sh

Neither work - executing that script /home/ben/backup.sh from terminal works fine.  What am i doing wrong?

Pity that **neither** of those is exactly what you were instructed to put in, isn't it?

---

### Post by yeleek on 2009-02-04
I can tell you are a particularly helpful individual...

Below taken from [https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto) and I only have one screen.

It is possible to run gui applications via cronjobs. This can be done by telling cron which display to use.

00 06 * * * env DISPLAY=:0. gui_appname

The env DISPLAY=:0. portion will tell cron to use the current display (desktop) for the program "gui_appname".

And if you have multiple monitors, don't forget to specify on which one the program is to be run. For example, to run it on the first screen (default screen) use :
[/B][/B]
00 06 * * * env DISPLAY=:0.0 gui_appname

---

### Post by yeleek on 2009-02-04
> **dagnabit dang doohickey said:**
> You need to specify the full path to the executables somewhere. Either in the script, by expanding of all of them to include the full path (eg. zenity to */path/to/zenity*), or in the crontab file, by adding a PATH environment variable at the top of the crontab file that satisfies all required paths of your script (eg. *PATH=/usr/sbin:/usr/bin:/sbin:/bin*).

OK thanks - will give that a try a bit later :)

---

### Post by yeleek on 2009-02-04
> **dagnabit dang doohickey said:**
> You need to specify the full path to the executables somewhere. Either in the script, by expanding of all of them to include the full path (eg. zenity to */path/to/zenity*), or in the crontab file, by adding a PATH environment variable at the top of the crontab file that satisfies all required paths of your script (eg. *PATH=/usr/sbin:/usr/bin:/sbin:/bin*).

You are a guru - it worked straight away.  many thanks.

---

