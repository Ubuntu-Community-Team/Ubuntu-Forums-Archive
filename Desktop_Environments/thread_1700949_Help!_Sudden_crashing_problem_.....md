---
title: "Help! Sudden crashing problem ...."
date: 2011-03-05
forum: Desktop Environments
---

### Post by ekoblentz on 2011-03-05
I've been using Ubuntu 10.x for several months without any major problems.  Everything was fine until this week.

In the past few days there's been a strange new problem.  When I turn my computer on, it works fine for 10 minutes, and then the hard drive suddenly starts spinning and won't stop.  While this happens the computer is virtually unusable.  Mouse moves slow and jerky; apps don't respond; and eventually the windows close by themselves, the whole screen goes blank, and the system reboots.  The whole process takes a long time, sometimes 30 minutes.

The only change I made just before this problem started was upgrading Firefox Beta 4 version 10 to the latest version 11.  So, I deleted it, and went back to the latest stable version 3.6.x.  That seemed to fix the problem for a day or so.  But then it started happening again.  I deleted all signs of Firefox; it still happens.  So it's not a browser issue.

I am stumped.  Today I started my computer and just let it sit there without opening any programs at all except the system monitor.  It ran fine for the usual 10-15 minutes, nothing changed out of the ordinary in terms of computer resources used in the system monitor, and then suddenly the drive started spinning wildly again .....

Right now my computer's been on for 10 minutes and I am typing this message .... but who knows what will happen right now.

Someone please help!!!  I really WANT to stay with Linux .... but as bad as Windows was, it was never THIS temperamental.

---

### Post by Krytarik on 2011-03-06
Wow, this is serious!

I'm wondering if the same occurs when you boot with a LiveCD/InstallCD, please try it.

Also have look into the following logs, preferably while that occurs:
- "~/.xsession-errors", respectively "...old"
- "/var/log/Xorg.0.log", respectively older logs (one log per xserver session)
- "/var/log/messages"

---

