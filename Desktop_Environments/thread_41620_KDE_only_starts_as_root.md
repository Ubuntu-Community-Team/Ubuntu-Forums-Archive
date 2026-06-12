---
title: "KDE only starts as root"
date: 2005-06-14
forum: Desktop Environments
---

### Post by Hanj on 2005-06-14
After a few hours of trying to install the fglrx drivers for my radeon card, I finally got it to work, only to discover that KDE will no longer start when I'm logged in as a regular user.  This is what happens: the X server starts, a message box with an error message flashes by and then the KDE splash screen freezes (I can still kill X with Ctrl-Shift-Backspace). 

The error message dissapears before I can read it, but it says something about me not having permission to read/write to some file (I haven't been able to read which). This sort of makes sense, because KDE starts up just fine when I start it as root.

Anyone know what change I might have made to cause this (it used to work fine)? Or at least how I can read that error message and change the permissions?

EDIT: Finally solved it. The error message was in ~/,xsession-errors, so I could just find the file and do a chmod 666, and KDE booted up.

---

