---
title: "System sporadically freezes"
date: 2012-02-02
forum: Desktop Environments
---

### Post by Alekix on 2012-02-02
I'm running Gnome3 on Ubuntu 11.10 with an ATI graphics card using the Radeon driver.

I'm experiencing sporadic freezes (ranging in frequency from every couple of days to multiple times per day) of the system.  When it freezes, the system is completely unresponsive to mouse/keyboard input, as well as SSH/ping.  It often freezes while interacting with the shell (for example, immediately after opening the dash), but not always.

Nothing (that I've found) is recorded in any system logs when it freezes, and no crash dump is saved by linux-crashdump.

Any ideas for what I can try to isolate the cause?  Any information I should post?

---

### Post by 67GTA on 2012-02-02
This is a problem for a lot of people since kernel 3.0. I had to install 2.6.39 to have a stable 11.10. [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.39.4-oneiric/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.39.4-oneiric/") It is the last kernel without this bug. There is a bug report here that is likely the cause: [https://lists.launchpad.net/ubuntu-x-swat/msg144964.html](https://lists.launchpad.net/ubuntu-x-swat/msg144964.html)

---

### Post by 67GTA on 2012-02-02
Sorry, that was a link to the mailing list. Here is the bug report: [https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/881526](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/881526) You can watch the kernel messages by turning off the screensaver and leaving a terminal open running ```
sudo tail -f /var/log/kern.log
``` You will be able to see the last kernel messages right before the crash. I'm like you. I get no log messages, but it always crashes right after ""INFO: rcu_sched_state detected stall on CPU  (t=15000 jiffies)

---

### Post by Alekix on 2012-02-03
Thanks for the suggestion.  Unfortunately, it doesn't seem to have helped.  I installed that kernel, and it still froze after ~2h.

I'm running with a terminal open now (forgot to last time, ahem).

---

### Post by paradigm2 on 2012-02-03
It's always good idea to run the memtest from the install CD when this sort of thing happens just to eliminate bad memory from being the cause.  Another common cause is overheating.

Also if you cannot find another cause it might be a good idea to do a visual inspection of your motherboard and graphics adapter to check for [leaking or bulging capacitors](http://en.wikipedia.org/wiki/Capacitor_plague).  This is especially true if your hardware was made prior to 2005.  Often this can result in these sorts of problems and it can be very tricky to isolate.  Usually it will eventually fail for good but it's possible to go for years with intermittent problems.  It's far more common than people think on older hardware.  I've personally had two bad capacitors on a old Nvida graphics adapter cause intermittent kernel panics and hard freezes.

> 
The capacitor plague[1] (also known as bad capacitors[2]) is a problem with a large number of premature failures of aluminium electrolytic capacitors with non solid or liquid electrolyte of certain brands especially from Taiwan manufacturers.[3] The first flawed capacitors were seen in 1999, but most of the affected capacitors failed in the early to mid 2000s. They failed in various electronics equipment, particularly motherboards, video cards, compact fluorescent lamp ballasts, LCD monitors, and power supplies of personal computers. News of the failures (usually after a few years of use) forced most manufacturers to repair the defects. The problem seems to be ongoing; faults were still being reported as of 2010.[4]


> 
As the capacitor ages, its capacitance decreases and its ESR increases. When this happens, the capacitors no longer adequately serve their purpose of filtering the direct current voltages on the motherboard, and system instability results. Some common symptoms are:

- Not turning on all the time; having to hit reset or try turning the computer on again
- Instabilities (hangs, BSODs, kernel panics, etc.), especially when symptoms get progressively more frequent over time
- Memory errors, especially ones that get more frequent with time
- Spontaneous restarts or resets
- In case of on-board video cards, unstable image in some video modes
- Failing to complete the POST, or rebooting before it is completed
- Never starting the POST; fans spin but the system appears dead
- Capacitors with high ESR can make power supplies malfunction, sometimes causing further circuit damage. CPU core voltage or other system voltages may fluctuate or go out of range, possibly with an increase in CPU temperature as the core voltage rises.


[http://en.wikipedia.org/wiki/Capacitor_plague](http://en.wikipedia.org/wiki/Capacitor_plague)

---

### Post by Alekix on 2012-02-03
Thanks for the suggestions!

Sorry, I should probably have listed what I've already tried:

+ I've run memtest overnight, and no errors were reported.
+ The system also doesn't freeze in Windows, so I'd be surprised if it were an issue with defective hardware.  The computer's about a year old.
+ I tried older Radeon drivers in case that were an issue (I went back to 6.14.1); no change.

Overheating is an interesting idea... I installed lm-sensors, and my CPU is at 30C, GPU at 53C, so that's not the problem. :(

---

