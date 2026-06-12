---
title: "/etc/crontab not working"
date: 2008-09-07
forum: Desktop Environments
---

### Post by dgermann on 2008-09-07
Hi--

I have this line in my /etc/crontab file, in 8.04.1:
```
* * * * * root touch /sam/vol22/data/todo/bak/1crontest
```

However, it is not working. On another 8.04.1 machine I have, /etc/crontab is working.

I did crontab -e and added a line like that to create 2crontest: 
```
doug@doug2:/sam/vol22/data/todo/bak$ sudo crontab -l
7 0 * * * /etc/webmin/cron/tempdelete.pl
* * * * * touch /sam/vol22/data/todo/bak/2crontest

```

Immediately, this file is touched.

I have reinstalled cron and anacron, and /etc/crontab still does not work.

1. What is /etc/crontab for, compared to crontab -e?

2. How can I get it working?

Thanks!

---

### Post by pdk on 2008-09-08
Try the full pathname for touch. Probably /usr/bin/touch
Peter

---

### Post by dgermann on 2008-09-08
pdk--

You are right about the location. Unfortunately, adding that did not help.

The fact is that nothing in this crontab is running, only the one accessed via crontab -e.

Other ideas?

Thanks, pdk!

---

### Post by dgermann on 2008-09-08
Hello all--

OK, the issue is half solved!

My /etc/crontab had probably 15 or 20 lines in it, among which was this line. Can you catch what is wrong with it?
```
31 01 18 2,4,6,8,,10,12 * root /etc/cron.doug/bkmonthtwo
```

I didn't, and this one line wrong meant that cron would not run anything from this crontab. I removed the extra comma and now all of it is running, at least so much of it as the time for which has arrived.

So there is in that a little lesson for others, I hope: make sure every line is right or the whole crontab fails.

But the other half of my question remains: Why are there these two crontabs, the one in /etc/crontab and the one reached via sudo crontab -e? Do you use one for one thing, one for another? Do they have different things they can do?

Thanks!

---

### Post by Justin Ryan on 2008-10-21
> **dgermann said:**
> But the other half of my question remains: Why are there these two crontabs, the one in /etc/crontab and the one reached via sudo crontab -e? Do you use one for one thing, one for another? Do they have different things they can do?

Even though Ubuntu doesn't by default have the root user account enabled, there is still a root user on the system, and that user has all the various knobs and twiddly bits that any user has. The crontab you reach via *sudo crontab -e* is the root user's crontab - anything entered there will be run as the root user, just as putting it in your own crontab would cause it to be run as your account.

/etc/crontab, on the other hand, is part of anacron, which handles cron tasks on machines that don't run continuously. The /etc/crontab file is used to call the sub-directories that contain the tasks anacron will run - it runs with root privileges, just like root's crontab, but is specifically for anacron tasks. It's generally advised that you not add entries to /etc/crontab because it is subject to being overwritten by updates, which would cause your entries to be lost, and if the tasks are relatively transparent, it could be some time before you discover that it's been overwritten.

The Community wiki has more information on the various cron locations ([https://help.ubuntu.com/community/CronHowto);]("https://help.ubuntu.com/community/CronHowto%29;") the basic gist, though, is to put anything that needs to run with root's privileges in root's crontab and leave /etc/crontab for anacron.

---

### Post by dgermann on 2008-10-22
Justin Ryan--

Thank you. That helps a lot!

Guess I have some work to do to move my commands out of /etc/crontab to the root crontab.

One little point: I just did a dummy crontab -e and then did a sudo updatedb and a locate crontab, but nothing different from a locate command I did before the new crontab was installed. Where is it really located?

Thanks, Justin!

---

