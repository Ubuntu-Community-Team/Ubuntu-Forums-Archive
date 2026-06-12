---
title: "esd process killing my flash sound"
date: 2006-09-29
forum: Desktop Environments
---

### Post by jimbob on 2006-09-29
When I boot Ubuntu, for some reason the system will start (2) identical processes shown as [COLOR="Blue"]/usr/bin/esd -terminal -nobeeps -as 1 -spawnfd 18
[/COLOR]  This is before anything has been started by me other than the clean boot up.

When I see these by using the ps command I know that any flash videos I run will have no sound.

The cure is to kill these two processes (the second one appears to be a child) and then flash audio plays fine with no other ill effects on anything I subsequently do.

My questions are:

1)  What is starting this process (which rc?.d script) and why do I need it, and

2)  Is this a reportable bug?
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by skymt on 2006-09-29
As I recall, gdm starts esd on launch. I'm not on an Ubuntu box right now, but it should be in /etc/gdm. Grep for esd there. Also, on my Edgy box, I've found that ESD, ALSA, and OSS all mix. So you may want to just wait for the Edgy release, or upgrade now.

---

