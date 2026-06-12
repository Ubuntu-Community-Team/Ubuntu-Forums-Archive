---
title: "Monitor won't turn off."
date: 2016-08-16
forum: Desktop Environments
---

### Post by izznogooood on 2016-08-16
I have my monitor set to turn off at 30min but it wont turn off.

Same thing when i ctrl-alt-l the computer, it just fades out, turns the monitor of for 10secs then the cursor is shown with a black screen.

Any idea where to start looking, i dont have this issue in a pararell 16.04 install (Which I've had since release). This showed up after i decided to start fresh.
Both systems are up to date.

---

### Post by CatKiller on 2016-08-16
Signalling for the monitor's power state is done through DPMS. It might be worth looking through the X log (/var/log/Xorg.0.log) for anything related.

Also, there may be other activity logs to see if anything is causing it to wake again. Not sure which ones they would be, but hopefully someone can give you pointers.

---

### Post by izznogooood on 2016-08-16
Thanks for pointing me in the right direction.

I looked in the log-file and found a lot of references to Nouveau (My god thats hard to spell/remember!). Some how i have overlooked Ubuntu has changed back to Nouveau when I installed a 4.6 Kernel (I dont understand how since usually it fails when installing the headers. My guess is this time I installed the new Kernel before the Nvidia driver). I reinstalled the Nvidia driver and broke my system (It loaded the log-in screen over and over after logging in, most of you have seen this i think). Switched to TTY and purged the kernel (4.6) and nvidia drivers. Rebooted  and installed a 4.5 kernel then Nvidia drivers (361) and now everything works.

I then switched back to Nouveau and the same problem reappeared! So the problem is  Nouveau ;)
PS: Ubuntu should really make it easier to report bugs, i just gave up... got the run around

EDI: I filed a bug

Anyway, thanks! :popcorn:

---

### Post by CatKiller on 2016-08-16
Glad you got it fixed, even if you couldn't file the bug report.

---

