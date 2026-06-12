---
title: "cron daemon does not executes my crontab"
date: 2006-04-20
forum: Desktop Environments
---

### Post by zod on 2006-04-20
Hello everybody:

I want to schedule a task for running everyday on 4:30 am and using the cron daemon I install a new crontab file on /var/spool/cron/crontabs of course using crontab -e here I list the whole file:

#This is crontab file for zod


SHELL=/bin/sh


#m h d m d
20 4 * * * 	/home/zod/bin/download.sh >> /tmp/download.log

The problem is that ubuntu's cron daemon does not seems check for this file and executes the entries

later I add this line to /var/spool/crontabs/zod

*/5 * * * *	/bin/date >> /tmp/dates

and this doesn't work. Then I decide look for a cron.log in /var/log and doesn't find one there. I already read the manual for cron and it says that cron log it's activities through syslogd daemon so I change /etc/syslogd.conf and uncomment the line:
cron.*				/var/log/cron.log

and restart both daemons syslogd and crond and still cron do not works fine for me. 

Any suggestion will be vere very appreciated
Thanks in advance
Zod

---

### Post by cgjones on 2006-04-20
You could try putting your download script into /etc/cron.daily. Make sure the script is executable.

---

### Post by zod on 2006-04-20
I already do that a few seconds ago so I will wait until tomorrow morning to see if the download succeds. I had to ajust the /etc/crontab file to run anacron at 4:10 am because I am behind a proxy server and the hours available to donwload big volumes of data is from 4:00 am to 7:00 am. I my system seems that anacron is scheduled to run in /etc/crontab

I am still thinking about this strange behavior on my system. Before I was running SuSE linux 9.3 and this works fine for that system.

I am already using a fresh ubuntu breezy installation.

Anyway thanks! :wink:

---

### Post by cgjones on 2006-04-20
Cron and Anacron are two different things. Cron runs things based on the current time, while Anacron runs things based on the time since it was last run. Hopefully it will work though. Good luck.

---

