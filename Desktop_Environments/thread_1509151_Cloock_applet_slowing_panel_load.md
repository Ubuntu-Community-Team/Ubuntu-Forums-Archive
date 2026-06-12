---
title: "Cloock applet slowing panel load"
date: 2010-06-13
forum: Desktop Environments
---

### Post by reedk on 2010-06-13
When 3 of the 4 users of my machine log in, the top and bottom panels take a long time (~25 seconds) to load. If I remove the clock applet, they load fine. I tried setting a default location for weather in the applet but it does not help. I also noticed that if I re-add the applet, it takes about 25 secs for it to show up on the panel. I also noticed that if I create a new user the
Any ideas on how to fix or workaround?

---

### Post by reedk on 2010-06-15
Bump. Anyone else having this issue. Is it going to take a total re-install to fix gnome-panel? I've used UNIX for over a decade, and this should be a solvable problem, but I don't know where else to look. My daughter is wondering why we don't just use Windows since "at least it works." This is not looking good.

---

### Post by realzippy on 2010-06-15
*Bump. Anyone else having this issue.*

yes,here is a thread:

[http://ubuntuforums.org/showthread.php?p=9463912#post9463912](http://ubuntuforums.org/showthread.php?p=9463912#post9463912)

---

### Post by reedk on 2010-06-16
Thanks realzippy. Your thread and this [_bug_]("https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/593226?comments=all") lead to a workaround - disabling logins without requiring a password. Disabling passwordless logins also fixed the issues I had with Evolution being unusably slow and the delay in the clock panel applet showing up. Odd.

---

