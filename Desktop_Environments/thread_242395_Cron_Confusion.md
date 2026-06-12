---
title: "Cron Confusion"
date: 2006-08-23
forum: Desktop Environments
---

### Post by firebadger on 2006-08-23
I am using the system wide cron to schedule updates.  I've added an update script to the /etc/cron.daily directory and I have a crontab as shown below.  It looks to me that the cron.daily tasks should run at 4.25am but my update script runs at 7.35am.  I'm a bit perplexed by this.

# /etc/crontab: system-wide crontab
# Unlike any other crontab you don't have to run the `crontab'
# command to install the new version when you edit this file.
# This file also has a username field, that none of the other crontabs do.

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

# m h dom mon dow user  command
17 *    * * *   root    run-parts --report /etc/cron.hourly
25 4    * * *   root    test -x /usr/sbin/anacron || run-parts --report /etc/cron.daily
47 4    * * 7   root    test -x /usr/sbin/anacron || run-parts --report /etc/cron.weekly
52 4    1 * *   root    test -x /usr/sbin/anacron || run-parts --report /etc/cron.monthly
#

---

### Post by firebadger on 2006-08-24
Any thoughts anybody?

---

### Post by firebadger on 2006-08-26
One last bump.

---

### Post by bbukh on 2006-09-18
The tests in the file insure that cron.daily is not run if anacron is installed. And cron.d/anacron says that anacron should be run at 7:30. And /etc/anacrontab says that the actual cron.daily tasks should be run 5 minutes after the anacron is started. Isn't it trivial? Of course, whoever wrote this felt below his dignity to add a pair of comment lines to explain how evaluation of boolean expression in sh works from left to right with early branching that creates this behavior. Grhhhm...

So, any one out there who experiences crashes or hangs or freezes or any other misbehavior at 35 minutes past the hour, usually at 7:35am, or sometimes at 8:35am (it seems to be there being different configuration out there) first thing to do is to look at your cron.daily jobs, and be ruthless with them.

Boris

---

### Post by firebadger on 2006-09-20
Ah, finally - that makes perfect sense.
Thanks!

---

