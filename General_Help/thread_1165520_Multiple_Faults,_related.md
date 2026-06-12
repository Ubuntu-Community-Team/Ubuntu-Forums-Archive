---
title: "Multiple Faults, related?"
date: 2009-05-20
forum: General Help
---

### Post by adam@home on 2009-05-20
Hi, I've upgraded from previous versions of Ubuntu in the past without no problem until now. I had a stable Intrepid Ibex install and went with the flow of upgrading to Jaunty. Now have random lock-ups, crashes, segfaults, etc. The details of known faults:

Firefox - will randomly crash, no message logged in dmessg/syslog and no feedback when run from a Terminal.

Random Segfaults in various applications, found in log files

GDM crashes with Segfault randomly but infrequently

XServer will restart randomly but infrequently

For some reason the CPU scaling has been enabled and if I let the system take control it will crash, I never used this in the past as my CPU is over-clocked and stable at it's current speed. I can't find the simple answer of removing it, just to lock it to performance.

Recently I was playing a music file and I got a 'disconnected' error -the drive was not on a network share! I opened the file in Audacious and that segfaulted too... tried 3rd time and it played but had disappered from the "open with" on right click!

Firefox today refused to open so I executed killall firefox command from ALT+F2 then opened firefox and it caused a system crash/restart!

Notes: My hardware config has not changed, nor partitions or peripherals. Voltages, Temps all under constant control. FSCK'd the disk on runlevel 0 after umount -a .

I'm really tempted to shove the 8.10 LTS CD in the drive and watch Jaunty go to dust as it is proving to be extremely unstable for an unknown (to my knowledge) reason.

Also, I have Wine installed and have a lot of .exe's running from it even on boot. I have itunes, Dreamweaver, IEs4Linux, FF for M$ Window$ installed there.

Any advice apart from re-install??!!

---

### Post by adam@home on 2009-05-21
Any ideas?

---

