---
title: "startup &amp; standby automatically at certain hours"
date: 2009-08-04
forum: Desktop Environments
---

### Post by walter_073 on 2009-08-04
Dears,
 
I want my desktop to go into standby at 10PMh and come back alive at 6PM.
Some questions :
1. Is this possible?
2. If yes, How?
 
When starting up is it possible to open a certain file with openoffice?
 
Thansk for support

---

### Post by Andreas1 on 2009-08-04
i heard of a scheduler called "cron", so far haven't used it though

```
man cron
man anacron
```

EDIT: did a little search, there seems to be a graphical frontend for cron called "gnome-schedule", it is in the repositories.

---

### Post by kpkeerthi on 2009-08-04
Most BIOS will have an option to AutoStart the PC at a specificied time. 

You can add shutdown/suspend command to [crontab]("https://help.ubuntu.com/community/CronHowto")

---

### Post by gcvisel on 2009-08-04
Yeah but...
 
With auto-login now requiring passwords since Jaunty, it would just start and sit waiting for the pw.  Any way around that?

---

