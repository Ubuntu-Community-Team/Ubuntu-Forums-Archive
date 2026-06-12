---
title: "Lock Screen not working"
date: 2014-07-31
forum: Desktop Environments
---

### Post by crowscare863 on 2014-07-31
Hi, I'm a new linux user and I just installed Lubuntu on my Dell laptop yesterday. I've noticed that Lubuntu doesn't lock when I put the laptop to sleep or click the lock screen button. Is there a fix for this issue?

---

### Post by LubLearner on 2014-08-04
Hi.

I recommend you to check two things:

1) Light-locker and "lock on suspend" are enabled at Light-locker settings in the preferences sub-menu

2) The "Disable autostarted applications?" setting is set as "no" at the autostart tab of "Default applications for LXSession", which is also in the preferences sub-menu. And there ensure that a application with a name similar to "screen blocker" is enabled among the known applications (I am sorry I use Lubuntu in another language).

The changes have effect after logging in again.

---

