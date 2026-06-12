---
title: "Alarm notifications not being displayed for Exchange calendar in Evolution."
date: 2006-07-31
forum: Desktop Environments
---

### Post by hashstat on 2006-07-31
I'm using Evolution 2.6.1, which came with Dapper, to connect to my Exchange mailbox at work.  Evolution displays alarm notifications for my personal calendar, but not for my exchange calendar.  Others in the organization are using the same version of Ubuntu and Evolution and are receiving alarm notifications.  The main difference I can think of between our installations is that I compiled a custom kernel while they are using pre-built kernels.

Any thoughts?

---

### Post by sisooktom on 2006-08-22
Anyone ever figure this out?  I don't get any exchange alarms in Evolution either.  If I can't get them to work, I'd just as soon use OWA and not put up with Evolution at all. . .

---

### Post by sisooktom on 2006-08-23
I found it.  There is currently a bug in Evolution that causes your alarms not to show and also breaks the calendar integration with the clock/calendar applet.  It only happens if you don't allow Evolution to save your Exchange password.  Click save password next time and it should be fixed.  Sadly, with my problem du jour fixed, I have to continue to fight with Evolution. . .

---

