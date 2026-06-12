---
title: "Resume from suspend &amp; automatic media recognition &amp; script execution"
date: 2006-07-23
forum: Desktop Environments
---

### Post by mlaverdiere on 2006-07-23
Hi to all,

I'm using Kubuntu Dapper on a new laptop (Compaq Preario V2610CA) I bought this week and I'm lucky enough that suspend-to-ram and suspend-to-disk are working out of the box!  The only annoyance is that after resuming, KDE automatic media (usb, CD-R, etc.) recognition is no longer working.  I've tried to stop and restart udev and hal, without positive results.  I've finally discovered that it is a KDE specific problem, i.e. that in order to reactivate the media support, you can simply stop and restart a KDE session.

In a less time consuming way, you can also stop and restart kded (KDE demon) and Kicker & klapto-check (if like me you're using the Kicker media applet).  All this stuff can be proceeded with the following really simple (and not so elegant, I know) script:

#! /bin/sh

killall kded
wait
killall kicker
wait
kded
wait
kicker
wait
klaptop_check

When executed manualy within KDE, after resuming, this script does its job perfectly and I finally recover automatic media recognition.  The problem is that I can't find a way to have this script automatically executed after resuming.  I've tried to put it it /etc/acpi/resume.d at diffrent number level, and the only result is that after resuming, kicker is not started, and I have to start manually, without getting any automatic media recognition.

Anyone knows how I could have this script automaticaly executed after resuming?  Or any other solution to have automatic media recognition working after resuming in KDE?

Thanks for your help.

---

### Post by z600 on 2007-03-03
I'm also looking for a way to run a script on resume. Any ideas guys?

---

