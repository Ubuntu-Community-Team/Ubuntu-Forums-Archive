---
title: "Gnome session daemon won't start"
date: 2006-12-07
forum: Desktop Environments
---

### Post by jaywhy13 on 2006-12-07
When gnome starts, there seems to be a fight going on on my desktop.. My icons keep changing between one type and another quite rapidly for a couple of seconds... then it dumps an error on me... gnome-session daeemon could not be started and then some of the tray apps spit n error asking if they should be deleted or reloaded... plz help

Root login doesn't give that issue

---

### Post by frodon on 2006-12-07
Please give us the error message, without it it will be difficult to help you.

---

### Post by jaywhy13 on 2006-12-07
> **frodon said:**
> Please give us the error message, without it it will be difficult to help you.

Distribution: Ubuntu 6.10 (edgy)
Gnome Release: 2.16.1 2006-10-02 (Ubuntu)
BugBuddy Version: 2.16.0

Memory status: size: 37818368 vsize: 0 resident: 37818368 share: 0 rss: 11915264 rss_rlim: 0
CPU usage: start_time: 1165457971 rtime: 0 utime: 47 stime: 0 cutime:44 cstime: 0 timeout: 3 it_real_value: 0 frequency: 6

Backtrace was generated from '/usr/bin/gnome-session'

Then lots of errors about no debugging symbols found

---

### Post by jaywhy13 on 2006-12-07
There was an error starting the GNOME Settings Daemon.

Some things, such as themes, sounds, or background settings may not work correctly.

The Settings Daemon restarted too many times.

GNOME will still try to restart the Settings Daemon next time you log in.

That's the exact error

---

### Post by auburn on 2006-12-14
try this
[https://launchpad.net/distros/ubuntu/+source/control-center/+bug/61381](https://launchpad.net/distros/ubuntu/+source/control-center/+bug/61381)

---

