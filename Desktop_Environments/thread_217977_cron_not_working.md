---
title: "cron not working"
date: 2006-07-17
forum: Desktop Environments
---

### Post by jdw on 2006-07-17
Hi, I can't get cron to work for some reason.  I noticed that when I shutdown my system, it says that stopping the periodic command executor [failed], so I figure this might be related.

Anyway, here's what I enter for crontab -e:

```

PATH=/usr/sbin:/usr/bin:/sbin:/bin
# m h  dom mon dow   command
40 21 * * * touch /home/isilinde/testing-cron

```

I waited until 9:40 pm to see if the testing-cron file would be created, and nothing happened.  I've tried several times to no avail.

Does anyone know if any detailed information gets logged when you shutdown?  I thought that would be in /var/log/wtmp, but it's a data file of some kind. I haven't been able to find logs on shutdown info anywhere -- in the hope that I could see why cron fails to shutdown properly, which may help explain why I'm having trouble running it.

Any help would be mondo appreciated!  Thanks.

---

### Post by jonrkc on 2006-07-18
Is your crontab located at: /etc/crontab  ?  That's where cron will look for its jobs.  Mine seems to be running OK, and there's output in /var/log/syslog from cron:

```
Jul 18 00:17:01 dragon /USR/SBIN/CRON[8727]: (root) CMD (   run-parts --report /
etc/cron.hourly)


```
I notice in the manual page that you can run cron with an option -f to have it run in the foreground instead of as a daemon.  Would that help in diagnosing the problem?

**EDIT:** The system-wide crontab is at /etc/crontab.  I confess to not knowing how to find my own, although I can edit it--and it works; I just now tested it.

You can put a variable at the top of your crontab: 

```
MAILTO: user
``` where user is your username.  It will mail you the results of jobs it runs from your own crontab.  However, this obviously isn't of much help if it isn't running the jobs in the first place.

I've run out of ideas...

---

