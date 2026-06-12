---
title: "/var/lib/AccountingServices/users   profile being reset randomly"
date: 2014-10-19
forum: Desktop Environments
---

### Post by 316479 on 2014-10-19
I finally figured out how to get gdm to run xfce-session by modifying the
XSession variable in    /var/lib/AccountingServices/users/<ME> to read

XSession=xfce

This works fine for a while, but somehow it is periodically, randomly being reset
to 

XSession=gnome

Happens about once a week.
Since the whole Accounting Services mechanism is so poorly documented
I can't figure out how/why this is happening.
If a cron job is doing this, I can't find it.

I never run gnome-session

Any suggestions?

---

