---
title: "What's with the latest updates ?!?!?"
date: 2008-05-29
forum: Desktop Environments
---

### Post by snakedog on 2008-05-29
I'm running Xubuntu 8.04 on TWO laptops.  One's run fine for weeks and the other just got an install this morning.  Standard installs, both are updated.

Both computers, one a PIII, the other a P4 Celeron, are maxed out on the CPU.  I run 'top' and thunar is using 20-30% and 'dd', the same range.  Then 'klogd' and/or 'syslogd' 35-40% between the two of them.  I've run Linux for years and never seen this kind of CPU usage.  It's just maxed out after a short while, no up-and-down, no spiking in CPU usage like one normally sees.

I can't even run 'kill' which I normally do in these cases.  If I run 'kill pid 6287' to stop thunar, I get the response 'arguments must be process or job IDs'.  And I no idea why 'dd' would be running on both computers not having run it at all.

The PIII is even locked up now and I've had to pull the battery to reboot.  All I can think of is last night's (or yesterday's, whatever) updates, or maybe a USB stick I used on both.

I guess I get a lesson in logging today.  :(

---

### Post by snakedog on 2008-05-29
At first blush, it appears to be a problem with the newest kernel.

I'm running normal on the old PIII after booting to 2.26.24-16 versus booting to 2.6.24.-17.  Haven't viewed any logs yet, but 'top' list thunar differently (new version?) and I am able to kill it now.  No sign off 'dd' (that's really weird that was running).

Think I'll go run Windows for awhile.  Sometimes it's not as frustrating.

---

