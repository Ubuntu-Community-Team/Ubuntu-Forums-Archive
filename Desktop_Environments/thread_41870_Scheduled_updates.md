---
title: "Scheduled updates"
date: 2005-06-15
forum: Desktop Environments
---

### Post by paulm on 2005-06-15
I am changing my internet connection to one with peak and off peak allowances and I want to try and ensure that as much as possible happens during off-peak times (midnight to 7am).

Thus in "Software updates"->Preferences->Settings I want to turn "Automatically check for updates" turned on and "download available updates" turned on but I want to make sure the check and download happens at 1am.

Any suggestions?

---

### Post by invalid on 2005-06-15
The best thing to do would probably sen up a cronjob. You can specify the time and day, plus set repeat cycles (for every night). Just have it run "apt-get update && apt-get dist-upgrade" as the root cron user.

If you aren't familiar with cron, there are many posts available. I suggest kcron for a graphical interface.

Cheers

---

### Post by FLeiXiuS on 2005-06-15
Doing 
```
$ apt-get update; apt-get upgrade; apt-get dist-upgrade
```

There's still one thing which your missing.  You know how apt prompts you whether you'd to install it with (yes/no).  You have to tell apt yes every time.  Also, be sure to have this cron ran as root rather then your default user.
```
$ apt-get update; apt-get upgrade -y; apt-get dist-upgrade -y
```

Also for a quick run by of cron.  Basically, crontabs allow you to setup scheduled tasks.

```
$ man crontab 
```

---

### Post by paulm on 2005-06-15
[QUOTE=invalid]The best thing to do would probably sen up a cronjob. You can specify the time and day, plus set repeat cycles (for every night). Just have it run "apt-get update && apt-get dist-upgrade" as the root cron user.

If you aren't familiar with cron, there are many posts available. I suggest kcron for a graphical interface.

Cheers[/QUOTE]
 I could probably set up a cron job, I figured:
apt-get update
apt-get -d upgrade
would probably download but not install updates.

I was just wondering if there was a more "friendly" way though. I figured the update manager must be choosing it's "once a day" somehow....

---

### Post by paulm on 2005-06-15
Ok, I think I've worked out what is already happening with a bit of detective work.

I think setting "download available updates" configures the apt-config variables so after doing the configuration in my first post:
```
$ apt-config shell UpdateInterval APT::Periodic::Update-Package-Lists DownloadUpgradeableInterval APT::Periodic::Download-Upgradeable-Packages
UpdateInterval='1'
DownloadUpgradeableInterval='1'
``` 

The daily job that does the automatic checks pays attention to those variables and seems to be
/etc/cron.daily/apt

which according to 
/etc/anacrontab
will be run daily by anacron

The only issue seems to be that it seems to run them after 7am:
```
$ ls -lt /var/spool/anacron/cron.daily
-rw-------  1 root root 9 2005-06-15 07:42 /var/spool/anacron/cron.daily
$ grep cron /var/log/syslog.0
Jun 15 07:30:01 localhost /USR/SBIN/CRON[21137]: (root) CMD (test -x /etc/init.d/anacron && /usr/sbin/invoke-rc.d anacron start >/dev/null)
Jun 15 07:30:02 localhost anacron[21161]: Anacron 2.3 started on 2005-06-15
Jun 15 07:30:02 localhost anacron[21161]: Will run job `cron.daily' in 5 min.
```

So now I have to work out what causes that to run at 7:30 and push it forward a few hours......as long as that doesn't look like it will hurt the other daily jobs...

---

### Post by nocturn on 2005-06-15
Be carefull with automatic updetes (not downloads).
This could go wrong (bad kernel update, ..., switching off the machine while it is updating).

---

### Post by paulm on 2005-06-15
Final part of the puzzle was
/etc/cron.d/anacron

If I change that to run at 3:30 rather than 7:30 I reckon I'll be happy :)

---

