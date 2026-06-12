---
title: "Cron Stopped Running"
date: 2009-04-08
forum: General Help
---

### Post by measekite on 2009-04-08
I have had 5 Cron jobs via gnome-scheduler running for 2 years without any problems:

For the past couple of weeks the new files are not copied to my backup device using grsync and rsync.  If I execute them manually all is fine.

What do I need to do to get gnome_scheduler CRON to work as before and why would it stop working all of  a sudden?

---

### Post by rafemonkey on 2009-04-08
Did any of your paths change? If I recall, cron runs under it's own shell, which wont have access path aliases. So, while the command might work fine from a terminal, if the cron jobs don't have the full or correct path they wont run. If that's not the case try: ```
grep CRON /var/log/syslog
```to get a look at any possible error messages.

---

### Post by measekite on 2009-04-08
> **rafemonkey said:**
> Did any of your paths change? If I recall, cron runs under it's own shell, which wont have access path aliases. So, while the command might work fine from a terminal, if the cron jobs don't have the full or correct path they wont run. If that's not the case try: ```
grep CRON /var/log/syslog
```to get a look at any possible error messages.

Paths have not changed.

Nothing in syslog that match the times the jobs were to run.

---

