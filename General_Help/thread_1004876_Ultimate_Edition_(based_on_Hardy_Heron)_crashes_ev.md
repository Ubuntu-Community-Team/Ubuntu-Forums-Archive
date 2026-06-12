---
title: "Ultimate Edition (based on Hardy Heron) crashes every few days at random"
date: 2008-12-07
forum: General Help
---

### Post by csc2ya on 2008-12-07
I'm having a problem with ubuntu crashing every few days.

It seems to be completely random as to when it will crash. I usually leave my laptop on 24 hours a day, and only reboot it if there's a kernel update or the available memory starts getting too low. Sometimes it will make it to three days, sometimes 4, and earlier today it had been less than 24 hours since the last reboot.

When it crashes, the screen will go blank, and any sound will stop and it will basically go completely unresponsive. The only way to get it going again, is to turn it off by holding down the power button, then turning it on again.

The only error messages I can find are the following:

Syslog:

> Dec  7 21:34:36 Laptop gdm[6329]: WARNING: gdm_slave_xioerror_handler: Fatal X error - Restarting :0 
Dec  7 21:36:17 Laptop syslogd 1.5.0#1ubuntu1: restart.

Xorg.1.log:

> (WW) intel(0): PRB0_CTL (0x0001f001) indicates ring buffer enabled
(WW) intel(0): PRB0_HEAD (0x7ea1eaf4) and PRB0_TAIL (0x0001eb00) indicate ring buffer not flushed
(WW) intel(0): Existing errors found in hardware state.

Has anyone got any idea what's likely to be causing it, as it gets annoying when i'm doing something and it will suddenly freeze.

One thing that may be relevant (i'm not sure though) is that it is configured to triple boot with windows vista and macosx on the internal drive, and ubuntu on an external USB drive.

i've run memtest to rule out any memory issues, and that hasn't detected anything that may be amiss.

---

