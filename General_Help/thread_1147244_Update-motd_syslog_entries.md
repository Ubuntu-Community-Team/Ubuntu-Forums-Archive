---
title: "Update-motd syslog entries"
date: 2009-05-03
forum: General Help
---

### Post by MalcolmR on 2009-05-03
Hi

Still fairly new to Ubuntu so apologies in advance if I am missing the obvious.  I am running 9.04 Server (upgraded from 8.10 about 1 week ago).  Since updating I have noticed that I am getting a lot of entries in the syslog that all seem to come from update-motd:

May  3 14:17:01 NAS-01 /USR/SBIN/CRON[11075]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
May  3 14:20:01 NAS-01 /USR/SBIN/CRON[11100]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
May  3 14:30:01 NAS-01 /USR/SBIN/CRON[11181]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
May  3 14:40:01 NAS-01 /USR/SBIN/CRON[11271]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
May  3 14:50:01 NAS-01 /USR/SBIN/CRON[11358]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
May  3 15:00:01 NAS-01 /USR/SBIN/CRON[11437]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd hourly 2>/dev/null)
May  3 15:00:01 NAS-01 /USR/SBIN/CRON[11449]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
May  3 15:10:01 NAS-01 /USR/SBIN/CRON[11493]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)

This pattern repeats every hour.

When I enter sudo /usr/sbin/update-motd or sudo /usr/sbin/update-motd hourly there is no output and no new entry in the logfile.  Similarly, using webmin to view cron jobs and running this job - [ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null - neither displays a message nor adds an entry to the logfile.

I am working on the assumption that an entry in syslog is something to worry about - should I be worried?

How do I solve this?

Thanks in advance.

---

### Post by MalcolmR on 2009-05-03
PROGRESS

All cron messages are going to the syslog.  In /etc/syslog.conf the entry: "cron.*   /var/log/cron.log" was disabled.  Removing # from the start of the line moved the entries to the cron log.  Next step is to look at the severity of the message and set an appropriate filter so as to only log issues.

---

### Post by gammb on 2009-05-23
Ok, so I can redirect these entries to a different log file.

Mine is a desktop to which I only rarely SSH.  I'd like to stop what strikes me as a pointless waste of resources (not the least of which is the nearly 1MB/month disk-space consumed by these messages).

Where is this cron job buried (so I can kill it) ?

..or, in Jaunty, is this simply a matter of deleting
      /etc/cron.d/update-motd
and restarting crond ?

TIA

---

### Post by fleshins on 2009-09-07
Did you end up figuring out the source of these messages.  It seems like they're cron jobs but crontab shows no jobs for the root user ... totally confused.

---

### Post by gammb on 2009-09-08
The source of the log entries remains a mystery.
It would appear that either few people that know the answer or few people have encountered this thread.

---

### Post by wojox on 2009-09-08
/etc/cron.d/update-motd that's where it's stored.

---

