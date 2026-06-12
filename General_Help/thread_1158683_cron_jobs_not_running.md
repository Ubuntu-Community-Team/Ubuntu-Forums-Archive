---
title: "cron jobs not running"
date: 2009-05-13
forum: General Help
---

### Post by muchocoolio on 2009-05-13
Hi, I've been trying to get a cron job to run a shell script file, but it doesn't happen - the cron job is not started.
The cron tab for the job is;
* * * * * /path/job.sh
I don't know what's wrong, since if I execute the command manually, it runs fine, as it should, but the scheduled jobs never happen.

I tried sudo /etc/init.d/cron start because I suspected that crond was not running, and I got;

*Starting periodic command scheduler crond                     [fail]

---

### Post by muchocoolio on 2009-05-13
ok, I don't think the failed start thing was a problem, I'm pretty sure it only failed because it was already started; I tried restarting it, which went fine, but it hasn't caused the job to start running properly...

---

