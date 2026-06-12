---
title: "Annoying Lock Ups 12.04"
date: 2015-11-16
forum: Desktop Environments
---

### Post by Geoff_Lane on 2015-11-16
My main system is Ubuntu 12.04

I have a triple boot machine and as well as Ubuntu 12.04 I also have 14.04 and Vista

I've resisted upgrading from 12.04 as all my settings are there and it has worked well BUT of late I have had a few lock ups.

My screen freezes and Ctrl-Alt-F1 doesn't even get me a terminal to do a proper reboot; I have to resort to a POWER OFF reboot.

So unusual for a Linux system to completely lock like that, has anyone any clues as to possible problem or remedy.

Geffers

---

### Post by Geoff_Lane on 2015-11-16
Just read a tip about pressing Alt-SysReq(Print Screen).

haven't tried it yet as not in 12.04 but SysReq and Print Screen are two different keys on my HP Pavilion.

Geffers

---

### Post by tgalati4 on 2015-11-16
What is the make and model of the computer and how old is it?  Check the power supply.  Hard lockups tend to be power issues, but let's look at a few things.  Go through your logs:

```
more /var/log/syslog
```

---

### Post by Geoff_Lane on 2015-11-17
Went in to 14.04 and later back to 12.04, did sudo apt-get update then upgrade.

All seems to be working now.

As for syslog, unfortunately I cannot recall time it locked so not sure what to look for.

Geffers

---

