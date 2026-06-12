---
title: "Problems with Hourly Cron Job"
date: 2011-02-21
forum: Desktop Environments
---

### Post by noloader on 2011-02-21
Hi All,

I have a script called hourly-update.sh in /etc/cron.hourly/ which I would like to be run hourly. The script simply wraps APT-GET with a cycle of clean, autoclean, update and upgrade.

The script is owned by root, +x, runs fine from a Root Terminal, and runs fine with sudo under a standard account. However according to the Update Manager GUI, it does not appear the script is being executed since the package update information is usually something like 'The package update information was last updated 5 hours ago'.

I've looked at the Cron HowTo ([https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)) and don't see what I am doing wrong:

>  **anacron** offers simple system-wide directories for  running commands hourly, daily, weekly, and monthly.  Scripts to be  executed in said times can be placed in **/etc/cron.hourly/**, **/etc/cron.daily/**, **/etc/cron.weekly/**, and **/etc/cron.monthly/**.  All scripts in each directory are run as root... Any ideas?

Jeff

$ cat /etc/cron.hourly/hourly-update.sh 
#!/bin/bash

/usr/bin/apt-get clean
/usr/bin/apt-get autoclean
/usr/bin/apt-get update
/usr/bin/apt-get upgrade -y
$

---

### Post by DaithiF on 2011-02-21
Hi, rename it to remove the .sh extension.

see my reply to this thread [http://ubuntuforums.org/showthread.php?t=1629301](http://ubuntuforums.org/showthread.php?t=1629301)
for the explanation.

---

### Post by wizard10000 on 2011-02-21
> **noloader said:**
> $ cat /etc/cron.hourly/hourly-update.sh 
#!/bin/bash

/usr/bin/apt-get clean
/usr/bin/apt-get autoclean
/usr/bin/apt-get update
/usr/bin/apt-get upgrade -y
$

Tellya how I do it - I run it as a system cron job in /etc/crontab.  Looks like this and runs every two hours -

```
# apt update
0 */2	* * *	root	apt-get update
```

It's your machine and you can do what you like but I'd recommend pretty strongly against running apt-get clean or apt-get upgrade as a scheduled task.

Occasionally an update will break a machine - it's happened to me several times.  If you don't know *what* got updated you'll play hell troubleshooting it - you could look in apt's log but that's kind of a pain especially if your GUI is broken  ;)

If you're getting anything from  a ppa or otherwise outside of *buntu's repositories an automatic upgrade is an accident waiting to happen  :D

Also, if you're running apt-get clean there's no reason to run autoclean as clean will have removed all your packages and there won't be anything for autoclean to do.

But - do you really want to do this?  Suppose one of these unattended upgrades breaks networking - then you won't be able to reinstall the package unless you download it on another machine or run a live CD to download and reinstall the packages and all their dependencies.  If an automatic upgrade *does* break your machine you won't have the package files to reinstall anything.

Hard drives are cheap - it's just my preference but I prefer to have installed packages available so I'm not dependent on a network connection to reinstall them.  You might consider running autoremove as a cron job instead of clean or autoclean.

Anyway, it's your machine and your choice.  Let's just say I speak from experience when I say maybe automated upgrades aren't a great idea  ;)

cheers -

---

