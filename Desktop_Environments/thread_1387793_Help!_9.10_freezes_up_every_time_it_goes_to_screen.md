---
title: "Help! 9.10 freezes up every time it goes to screensaver"
date: 2010-01-22
forum: Desktop Environments
---

### Post by starsprout on 2010-01-22
Hi -

I just installed 9.10 on my HP Desktop on Monday (dual-boot, win XP on other partition, yecch!)

Ubuntu is excellent and I'm really happy with it. It took a bit, but I even managed to get my ATI Radeon card to run a dual-display setup (tried for 3 but gave up).

Unfortunately, no matter what I try, the system freezes up after going into screensaver, and I have to do a hard reboot and sometimes even lose data. Could this be from the dual monitor setup? Any other idea? What log(s) can I examine and share to figure out what's causing this to crash every time?

Thanks!

---

### Post by warfacegod on 2010-01-22
It is possible that your dual monitor setup is the culprit. For the moment I suggest disabling the screensaver if you haven't already: System> Preferences> Screensaver. Also, check to see if "Lock screen when screensaver is active" is checked and uncheck it if it is, that might be the problem too.

---

### Post by starsprout on 2010-01-22
Yes - I think it's the dual-monitor setup (probably the software).

Someone told me that I'm better off using the Open Source drivers for my video card as opposed to the proprietery ATI drivers I installed.

I  disabled screensaver before I left the house this morning and am headed back soon, so I'll know if that helps. Previously I had disabled the power management feature but that did not help. I would obviously like to have a working screensaver; hence I wish to get to the bottom of this.

What log file or files can I read to confirm exactly what causes the error when the machine crashes or freezes?

---

### Post by warfacegod on 2010-01-22
> **starsprout said:**
> Yes - I think it's the dual-monitor setup (probably the software).

Someone told me that I'm better off using the Open Source drivers for my video card as opposed to the proprietery ATI drivers I installed.

I  disabled screensaver before I left the house this morning and am headed back soon, so I'll know if that helps. Previously I had disabled the power management feature but that did not help. I would obviously like to have a working screensaver; hence I wish to get to the bottom of this.

What log file or files can I read to confirm exactly what causes the error when the machine crashes or freezes?

There isn't too much reason to use a screensaver these days unless you are using an old CRT "backbreaker" monitor. Newer LCD's don't really burn in anymore although it's still theoretically possible.

I don't know what error logs to tell you to look at. I've just seen unchecking Lock screen.... work for a few folks. Best I can do, sorry.

---

### Post by pavi_elex on 2011-11-08
system --> preferences --> screen saver --> power management

computer to sleep when inactive for - set never
display to sleep  when inactive for- set never

---

