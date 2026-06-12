---
title: "problem with awstats cronjob"
date: 2009-02-04
forum: General Help
---

### Post by coCoKNIght on 2009-02-04
Hi I have a LAMP and Awstats all installed through apt-get on my 8.10 Intrepid Server.
I have configured Awstats alright and when I enter ```
sudo /usr/lib/cgi-bin/awstats.pl -config=my.domain.com -update
``` Awstats looks through the logs of Apache and updates the statistics.
I edited the automatically generated cronjob in **/etc/cron.d/awstats** so it would execute the exact same command however it doesn't work.
Using **root** as the cronjob user, **syslog** returns: "Authentication failure"
Using the default **www-data** user, **syslog** returns the command and all looks good except that the statistics are not updated.
I tried ```
sudo -u www-data /usr/lib/cgi-bin/awstats.pl -config=my.domain.com -update
``` and Awstats returns ```
Error: Couldn't open server log file "/var/log/apache2/access.log" : Permission denied
```
**access.log** is **root:adm** but even if I change it to **root:www-data** I get the same permission denied error. And if I try the cronjob with user **adm** I get a bad user message in **syslog**.
Anybody got any hint as to what I can do to get this cronjob worknig?

---

### Post by coCoKNIght on 2009-02-09
Ok, it now works for me after changing the rights to **root:www-data** not only for the logfile but also the directories **/var/log** and **/var/log/apache2**.

Does anybody know if this is bad practice? / a security vulnerability?

Also, I still don't understand why the command wouldn't work with the user **root** so if you have a clue I'd be glad to read your reply.

---

### Post by bennychidge on 2009-02-15
is there an answer on security for this?

I had the same problem - did as you suggested and it now updates daily on the cron job......

thanks

---

### Post by l337dexter on 2009-04-20
I am running into similar problems and would love to know if their is an answer out there...

---

### Post by bennychidge on 2009-04-21
my awstats was actually being run weekly (not daily) even though i put it in cron daily tasks and I checked the daily timings in my crontab and that all looked fine. 

Didnt really get to the bottom of it as I decided awstats was to much hassle and have moved to webalizer.

---

### Post by mister_p_1998 on 2009-04-21
could you run it by editing /etc/cron?
I do that to do timed shutdowns..

# Shutdown Weekdays Monday - Thursday
29 16 * * 1-4 root /sbin/shutdown -h now

Steve

---

### Post by coCoKNIght on 2009-04-30
My logfile's been reset to root:adm
Might have been an Apache2 update but I'm not sure, so check if your stats are still up to date.

---

### Post by bennychidge on 2009-05-03
simply my logroate was calling awstats update in cron.daily. But my logrotate for apache was only running weekly

Amazing how confusing something is when you dont know how to do it!

Coming from windows - ubuntu is amazing :)

---

### Post by coCoKNIght on 2009-09-08
It seems that since I upgraded to 9.04, the logfile's not being reset to root:adm anymore. That's one problem that seems to have solved by itself...

---

