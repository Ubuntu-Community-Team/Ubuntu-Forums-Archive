---
title: "root cron jobs don't run and give &quot;authentication error&quot;"
date: 2009-01-29
forum: General Help
---

### Post by ryanolf on 2009-01-29
Recently (I think since upgrading to Intrepid), root cron jobs have not been running, instead leaving messages like:

```
Jan 29 11:20:01 oxford CRON[11616]: Authentication failure
```

It does not seem to matter whether the job is in root's crontab (with crontab -e), /etc/crontab, or in the /etc/cron.d/ directory. As a consequence, cron.daily, cron.hourly, etc are also not running, since these are invoked as root from /etc/crontab. I thought this might have something to do with pam, but I have another server with an identical /etc/pam.d/cron file, which has no problems. I'm not sure how to check that pam is correctly configured, however.

One thing I did notice, was that the /etc/shadow file did not have a root entry. I changed this (still not allowing logins), but the problem persists. I have tried "apt-get install --reinstall cron" and checking permissions on the cron files. The test job I'm running is really simple:

```
* * * * * root /usr/bin/touch /root/touchme
```

Omitting the "root" if in in the root user crontab, of course. Other cron jobs don't seem to have a problem.

Cron/authentication experts: please help!

---

### Post by khedron on 2009-01-29
Hmm, I'm running a cron job on root and it's fine. But I have a password set for root.

Maybe try setting a password for root and seeing if that's the problem? You can always remove the password with ```
passwd -l
```

---

### Post by ryanolf on 2009-01-29
Interesting. I had noticed before that there was no "root" entry in my /etc/shadow file on the server with the cron problems, while there was on the other (though the password was ! so login was still disabled). I added a root line to the shadow file on the problem computer, and thought that would help (still password disabled) and it didn't.

After your (khedron) suggestion, I tried setting a password for root. This seemed to work (passwd said tokens updated), but the shadow file still showed no password. Weird. I then removed the line I had added to the shadow file, leaving it without a root entry, as before. Then I tried setting the root password once more. Again, passwd was happy, but the shadow file still didn't have line for root. I could not su to root.

I'm not sure this is THE problem, but perhaps it is a symptom of an underlying problem that also affects cron.

Anyone have any ideas? Why would I be unable to add a root password? What might this have to do with cron?

---

### Post by ryanolf on 2009-01-29
Problem solved: the problem had something to do with my shadow files be out of sync with my group and passwd files, probably because I have edited them by hand. I used "shadowconfig on" to identify and fix the problems. After that was done, I was able to create a root password, at which point cron started running root jobs again. I then removed the root password to disable logins, but the cron jobs continue to work.

Thanks to khedron for the inspiration.

---

