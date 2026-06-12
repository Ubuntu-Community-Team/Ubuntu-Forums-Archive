---
title: "[Since Edgy] Desktop icons always mixed up on dual screen / twinview"
date: 2007-03-18
forum: Desktop Environments
---

### Post by api2001 on 2007-03-18
Hello folks,

there is a really absolutely annoying bug in the Edgy Kubuntu in dual screen mode with NVidia's twinview. At a few logons to KDE all desktop icons accurately arranged in several hours of work are mixed up at the very right side of the right display :-((
This does not happen at every logon but every let's say 4th. 

This is really annoying but I haven't found threads about that topic yet.
Can anybody help?

With best regards,
Sebastian

---

### Post by api2001 on 2007-03-22
Ok, I've done some more research by myself and did actually two things that might be the solution for the problem (it didn't occur since I changed these things):

1. For using Beryl/AIGLX the linux-restricted-modules (Nvidia driver, ...) of albertomilone.com was installed. I removed that package and installed the original Ubuntu package.

2. The desktop icon position are saved in your home directory in .kde/share/apps/kdesktop/. There were some older IconPositionSFHIASF.new files I deleted. Only the IconPositions file must remain! For having a backup of your icon positions you could copy this file to let's say IconPositions_niceone.

Bye,
APi

---

### Post by api2001 on 2007-03-30
Sorry, it seemed I was too fast writing happily my solution. In the end the desktop icons are still mixed up regularly but I cannot find out when or why.

---

