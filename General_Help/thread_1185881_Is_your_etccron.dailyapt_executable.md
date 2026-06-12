---
title: "Is your /etc/cron.daily/apt executable?"
date: 2009-06-12
forum: General Help
---

### Post by dankegel on 2009-06-12
I upgraded my laptop from Ubuntu 8.10 to 9.04 a few 
months ago, and recently I noticed that it wasn't getting
automatically updated.  A little searching found 
[https://bugs.launchpad.net/ubuntu/+source/update-notifier/+bug/356152](https://bugs.launchpad.net/ubuntu/+source/update-notifier/+bug/356152)
in which someone said this was because /etc/cron.daily/apt
wasn't executable.  Sure enough, doing
  sudo chmod 755 /etc/cron.daily/apt
  sudo rm /var/spool/anacron/cron.daily
rebooting and logging in again fixed the problem.

My question is, how widespread is this problem?  Try
$ ls -l /etc/cron.daily/apt
If you see no 'x' permissions, e.g. if you see
-rw-r--r-- 1 root root 8686 2009-04-16 21:27 /etc/cron.daily/apt
then you've got the problem.  Please let me know if 
this affects any of your computers.  Thanks!

---

### Post by dcstar on 2009-06-13
> **dankegel said:**
> I upgraded my laptop from Ubuntu 8.10 to 9.04 a few 
months ago, and recently I noticed that it wasn't getting
automatically updated.  A little searching found 
[https://bugs.launchpad.net/ubuntu/+source/update-notifier/+bug/356152](https://bugs.launchpad.net/ubuntu/+source/update-notifier/+bug/356152)
in which someone said this was because /etc/cron.daily/apt
wasn't executable.  Sure enough, doing
  sudo chmod 755 /etc/cron.daily/apt
  sudo rm /var/spool/anacron/cron.daily
rebooting and logging in again fixed the problem.

My question is, how widespread is this problem?  Try
$ ls -l /etc/cron.daily/apt
If you see no 'x' permissions, e.g. if you see
-rw-r--r-- 1 root root 8686 2009-04-16 21:27 /etc/cron.daily/apt
then you've got the problem.  Please let me know if 
this affects any of your computers.  Thanks!

All are set correctly on my system (fresh install):
```
-rwxr-xr-x 1 root root 8686 2009-04-17 14:26 apt
```

Upgrading may be another situation (I never upgrade because of little issues such as this).

---

### Post by Aaron44126 on 2009-06-23
Did you upgrade via 'do-release-upgrade' (command-line method)?

This happened to me on two machines that were upgraded from 8.10 to 9.04 with this method.  Machines upgraded with the GUI method continue to check for updates fine.

---

