---
title: "Icons Corrupting and Disappearing"
date: 2010-05-15
forum: Desktop Environments
---

### Post by Mr. Wishes on 2010-05-15
I have a clean install of Kubuntu 10.04, and over a period of a few hours, the icons that appear in the system tray/title bars of windows/task manager/kde menu start to get corrupted. Eventually, they all disappear (see attached pic). It's only cosmetic, in that clicking on them still causes the expected behaviour - if you can figure out where to click.

It could be a hardware problem, though nothing else seems to be giving errors. There are no other visual artefacts that I've noticed. I'm running a laptop with an 8600M video card, dual core core2 processor, SSD hard-drive, 4 GB ram. It happens regardless of the monitors I have plugged in (internal laptop screen or two 24-inch screens).

I've changed my video drivers from nouveau to the binary Nvidia drivers, still happens in the same way.

Restarting plasma-desktop fixes the problem temporarily.

The only errors in kdm.log refer to an inability to connect to the ibus-daemon.

There are no errors in Xorg.0.log.

In /var/log/messages, there are the following lines that may be relevant:
> May 15 15:58:47 wade-laptop kernel: [ 4395.140259] CE: hpet increasing min_delta_ns to 22500 nsec
May 15 16:39:27 wade-laptop kernel: [ 6835.094473] virtuoso-t[3310]: segfault at ffffffffffffffff ip 000000000079ccf4 sp 00007fff4a2e15e0 error 6 in virtuoso-t[400000+8aa000]
May 15 17:05:20 wade-laptop kernel: [ 8388.194966] virtuoso-t[4827]: segfault at ffffffffffffffff ip 000000000079ccf4 sp 00007fffad56e250 error 6 in virtuoso-t[400000+8aa000]
May 15 17:16:16 wade-laptop kernel: [ 9044.462599] CE: hpet increasing min_delta_ns to 33750 nsec

That said, the timestamps aren't particularly significant to me - the first corruption that I noticed occurred shortly after logging in at 15:16, and the icons completely disappeared at about 19:00.

Any suggestions would be welcome.

---

