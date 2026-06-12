---
title: "mystery cron"
date: 2009-02-25
forum: General Help
---

### Post by adult swim on 2009-02-25
ive got  a server set up and have changed nothing since the initial install.  there is a cron job that runs every 10 minutes and i cannot for the life of me figure out what it is.  the output from my auth.log is 
```
Feb 24 23:30:01 server CRON[17374]: pam_unix(cron:session): session opened for user root by (uid=0)
Feb 24 23:30:01 server CRON[17374]: pam_unix(cron:session): session closed for user root
```
my crontab -l for root and user reports that there is no crontab.  does anyone know what this could be?

---

### Post by nelskurian on 2009-02-25
I think its system internal cron.No need to worry.If you have any troubles with this then pls tell whats it..

---

### Post by adult swim on 2009-02-25
ive got no troubles with it, im just a little paranoid i guess ;)  i had the box connected to the internet without my ssh configured for a night so that got my wheels turning :)

---

### Post by heindsight on 2009-02-25
Appart from the user crontabs that are set/viewed using the crontab command, there are also system wide crontabs under /etc. Specifically /etc/crontab and the files in /etc/cron.d. 

Having a look at those files should help you figure out what the cron jobs are that are showing up in your logs. You could also look in /var/log/syslog for cron related entries at the same times as the cron entries in auth.log (those should give an indication of the command cron was running).

I'm sure at least some of the entries you are seeing are from the default hourly cronjob (defined in /etc/crontab it tries to run all scripts/programs in /etc/cron.hourly/, once per hour).

---

### Post by adult swim on 2009-02-25
ahh thank you heindsight!  it is the motd updating that runs so often

---

### Post by heindsight on 2009-02-25
> **adult swim said:**
> ahh thank you heindsight!  it is the motd updating that runs so often

OK, I'd say that's a bit strange though. I can't imagine why motd would need to be updated that frequently.

---

### Post by adult swim on 2009-02-25
for some reason it was set to 10 minutes. i changed that to a greater amount.  thanks for your help!

---

