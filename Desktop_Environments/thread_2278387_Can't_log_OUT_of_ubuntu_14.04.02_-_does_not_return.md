---
title: "Can't log OUT of ubuntu 14.04.02 - does not return to login screen"
date: 2015-05-16
forum: Desktop Environments
---

### Post by phil_elvey on 2015-05-16
Hi Guys,

Hope your weekend is going well!

I have been using Ubuntu for a long time now.  My wife and I both use it, each having our own logins.

A couple of months ago after running some standard updates, I lost the ability to log out.

Since then, when click the "log out" button, everything disappears from the screen except my own wallpaper, and it just hangs there instead of going back to the login screen.

I'd really appreciate some help to try and nail it down.  What logs should I collect to help pinpoint the problem?

I have tried searching, but I haven't been able to find anyone else with the same problem, which is puzzling.  If there is a post already about this, please point me in the right direction

Many thanks

---

### Post by dino99 on 2015-05-16
if an app or process is still active, then you get such issue. System-monitor can be checked before shutting down ( or htop), and the dmesg log should have some usefull warnings/errors to dig around that problem. Also the cdrom/dvd should not be mounted by default into /etc/fstab, the system is able to know if a device is active by itself and do the required stuff

---

### Post by phil_elvey on 2015-05-23
Thanks for your reply.  I went to have a look at this again this morning to check through dmesg.

Just to clarify, it was shutting down absolutely fine, it was just logging out that was a problem.

There happened to be some updates this morning, and it seems after running these updates it is now logging out again - hooray!  I like an easy fix!

---

