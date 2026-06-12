---
title: "Unknown Daemon"
date: 2005-08-15
forum: Desktop Environments
---

### Post by acheun on 2005-08-15
I just notice there are somethings running hourly in my desktop machine.   There are message logs as follows:

localhost CRON[10335] (pam_unix) session opened for user root by (uid=0)
localhost CRON[10335] (pam_unix) session closed for user root

Any one know what they are?  Are they harmful?  Or will it safe to remvoe this cron job?

---

### Post by nad on 2005-08-15
Please see the directory /etc/cron.hourly for anything scheduled by the system to run hourly.

---

### Post by acheun on 2005-08-16
I don't see anything under cron.hourly.  However, when I cat /etc/crontab, I fnd this:

~$ cat /etc/crontab
# /etc/crontab: system-wide crontab
# Unlike any other crontab you don't have to run the `crontab'
# command to install the new version when you edit this file.
# This file also has a username field, that none of the other crontabs do.

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

# m h dom mon dow user  command
17 *    * * *   root    run-parts --report /etc/cron.hourly
25 6    * * *   root    test -x /usr/sbin/anacron || run-parts --report /etc/cron.daily
47 6    * * 7   root    test -x /usr/sbin/anacron || run-parts --report /etc/cron.weekly
52 6    1 * *   root    test -x /usr/sbin/anacron || run-parts --report /etc/cron.monthly
#

Is the cron.hourly related to the log? 
Does this install by Ubuntu by default?

---

### Post by OwlManAtt on 2005-08-16
Those log messages are quite normal. You have nothing to fear. Cron runs anacron to have any scripts in cron.hourly/daily/whateverly. Since there are none, it just starts a root session (because root is the user specified to run anacron in the cron file), looks in the folders, and goes 'uh, i got nothing, kthx' and closes the session.

---

