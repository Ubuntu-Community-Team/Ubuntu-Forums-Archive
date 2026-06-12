---
title: "script to automate tasks"
date: 2006-09-09
forum: Desktop Environments
---

### Post by sr243 on 2006-09-09
One program I really miss from windows is Autoit.

It allows me to write a script that can manipulate the mouse and keyboard with simple commandes like MouseMove(455,233) and Send("Hi[ENTER]")

I wonder if there's an equivalent program in Linux.

The specific problem I am trying to solve this time is that my KAlarm alarms don't seem to run when the computer is in screensaver mode.  (I have a pw on my screensaver)

I was hoping to write a script that would automatically type my screensaver password and leave screensaver mode, and kron it right before the KAlarm program starts.
Though I have no idea whether a kcron program would run in screensaver mode, either.

Any hints? Thanks!

---

### Post by sr243 on 2006-09-09
bumpity bump

---

### Post by cwaldbieser on 2006-09-09
> **sr243 said:**
> bumpity bump

You could try using dcop or kdcop which are both part of core KDE libraries.  However, I am wondering if part of your cron script could just kill the screen saver?  That might be a little easier, and you wouldn't have to store your password in a file somewhere.

---

