---
title: "Can't Get past login screen 11.04"
date: 2011-09-21
forum: Desktop Environments
---

### Post by tmlemm on 2011-09-21
Hi everyone!  I installed Ubuntu 11.04 last week (clean install) and rebooted successfully several times. Today I can't login. System boots and comes up with login screen, I enter password and then get purple flash screen for a long time then screen goes black and login screen reappears. The process repeats with a short display of flash screen. I've tried rebooting in safe graphic mode and also reconfiguring X11 but neither made any difference. Any help appreciated.

---

### Post by mikaelcrocker on 2011-09-21
Is there a different account that you can log-in to.  If so you may be able to just delete and re create the account.  Also, I would check to see if the keyboard layout has by chance changed.  Again this all pending if it's just one account or can not login to any of them.

Also, check the pam.d for the login permissions. If something has changed that may be the problem. So maybe changing whats in there to common-auth as far as naming goes.

---

### Post by tmlemm on 2011-09-21
There was only 1 account on the computer by I went into tty and added a user from there and then switched back to the x session and it did the same thing :(  Any other ideas or should scrub my losses and reinstall?

---

### Post by ODTech on 2011-09-22
I'm pretty new to Ubuntu and i'm sure there are many different scanarios that could make your system not log on but i can share one that happened on my system.

I turned Xinerama and Tearfree on in my ATI Catalyst Control Centre and when i rebooted i got the same problem as you. 

I fixed it by holding shift at bootup to enter recovery mode and select reduced graphics mode. The computer booted normaly to the Desktop which allowed me to turn Xinerama and Tearfree off again.

I hope this helps.

---

### Post by varunendra on 2011-09-22
> **tmlemm said:**
> ...I went into tty and added a user from there and then switched back to the x session and it did the same thing :(  Any other ideas or should scrub my losses and reinstall?
When you get into tty (ctrl+alt+F1), login and enter "**startx**", do you get an error message? If yes, please post what it is.

---

### Post by tmlemm on 2011-09-22
Yes, I tried starting x there but I ran into the error that x is already started.

---

### Post by varunendra on 2011-09-22
Two frequent (but not the only) causes to this problem are:

[LIST=1]
[*]**Full drive.** *(Some files fail to be created during startup due to insufficient space.)* **_Solution_: **Boot into Live Session and create space on the root (/) and /home (if it is separate) partitions.
[*]**Broken Package(s).** (Installation / Removal of some package causing Broken Desktop Installation) **_Solution_:** In recovery mode, drop to root shell prompt, then: ```
apt-get install --reinstall ubuntu-desktop
```
[/LIST]

---

