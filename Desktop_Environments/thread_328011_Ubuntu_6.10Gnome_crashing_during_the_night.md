---
title: "Ubuntu 6.10/Gnome crashing during the night"
date: 2006-12-30
forum: Desktop Environments
---

### Post by plaa on 2006-12-30
I installed Ubuntu 6.10 a few days ago to replace my previous Debian installation (fresh install, not on top) which I had had up and running for ~six years, and on the whole I love it.  However, I keep my computer on 24/7 because it also functions as a web server, and already twice after the night I am greeted by the login window instead of the desktop as I left it.  Also the system has totally frozen up once.  I'm used to having my system up and running 100-150 days or more at a time, and now Ubuntu has crashed in a few days more than my machine previously did in a year.

I'm not sure what happens during the night, but when I turn on my monitor in the morning it is waiting at the login screen.  After logging in the system works as normal, but I often leave programs open on the desktops which I then have to restart etc.  I've tried to remove all hibernating and other power saving options, the screensaver is a blank screen after 10 minutes and switching the monitor off after 20min.  I've had the computer on now for three nights with Ubuntu, and after two of them the desktop had crashed.  The first time it happened I was using the default Metacity window manager and the second time Sawfish, so the window manager is not the problem.

The problem is, I don't really have any diagnostics about what has crashed and why.  I'll try to remember to change to a text console and read .xsession-errors the next time it happens, but does anybody have any other suggestions how to find the culprit?

The time the whole system crashed I had multiple programs running, including TVtime and I just started watching a video from Youtube in FF.  The entire system froze up, and the sound started looping a half second piece of audio meaning that even the IRQ/DMA-handlers in the Kernel were not running.  I had temperature sensors on the panel and the CPU wasn't overheating.  I don't see this as a major issue unless it starts doing it more often - nonetheless it gives a bad feeling about Ubuntu.

I'm leaving tomorrow for the New Year but will be back on Wednesday, so I'll answer questions today or after the holiday.  Happy New Year to all!

---

### Post by plaa on 2006-12-30
Just now the computer halted again.  I was doing nothing out-of-the-ordinary, a few downloads going and editing text.  The CPU temperature was around 50C, so that's not a problem.  There was nothing notable stored either in .xsession-errors (I checked using a text console) or /var/log/messages.

Any ideas what might be causing these crashes?  My previous Debian installation was rock solid, and the only changes to the hardware are an additional harddisk (RAID-1 with the previous disk) and an A-Link USB 2.0 -card.

---

### Post by neighborlee on 2006-12-30
> **plaa said:**
> I installed Ubuntu 6.10 a few days ago to replace my previous Debian installation (fresh install, not on top) which I had had up and running for ~six years, and on the whole I love it.  However, I keep my computer on 24/7 because it also functions as a web server, and already twice after the night I am greeted by the login window instead of the desktop as I left it.  Also the system has totally frozen up once.  I'm used to having my system up and running 100-150 days or more at a time, and now Ubuntu has crashed in a few days more than my machine previously did in a year.

I'm not sure what happens during the night, but when I turn on my monitor in the morning it is waiting at the login screen.  After logging in the system works as normal, but I often leave programs open on the desktops which I then have to restart etc.  I've tried to remove all hibernating and other power saving options, the screensaver is a blank screen after 10 minutes and switching the monitor off after 20min.  I've had the computer on now for three nights with Ubuntu, and after two of them the desktop had crashed.  The first time it happened I was using the default Metacity window manager and the second time Sawfish, so the window manager is not the problem.

The problem is, I don't really have any diagnostics about what has crashed and why.  I'll try to remember to change to a text console and read .xsession-errors the next time it happens, but does anybody have any other suggestions how to find the culprit?

The time the whole system crashed I had multiple programs running, including TVtime and I just started watching a video from Youtube in FF.  The entire system froze up, and the sound started looping a half second piece of audio meaning that even the IRQ/DMA-handlers in the Kernel were not running.  I had temperature sensors on the panel and the CPU wasn't overheating.  I don't see this as a major issue unless it starts doing it more often - nonetheless it gives a bad feeling about Ubuntu.

I'm leaving tomorrow for the New Year but will be back on Wednesday, so I'll answer questions today or after the holiday.  Happy New Year to all!

are you using beryl  by chance...are you dual booting windows and seeing this at all ?
sometimes i've had similar issues, and at that time it was due to bad ram.

You might checkout /var/log/messages and see if anything there gives you insight into what happened...

sorry you had trouibles, but I hope you can find out what caused it and stop it.

cheers and happy new years!

neighborlee

---

### Post by plaa on 2006-12-30
> **neighborlee said:**
> are you using beryl  by chance...are you dual booting windows and seeing this at all ?
sometimes i've had similar issues, and at that time it was due to bad ram.

No, I'm using the default X.Org/Gnome installation, and I've used both Metacity (the default WM) and Sawfish and have had one crashed desktop and one halted system with both.  Ubuntu is also the only OS on the system right now.

I ran Memtest86+ for an hour (one full test cycle) and it didn't find anything wrong.  The Debian system I had previously was rock solid, and I easily had over 100 days uptime with both the system and desktop without problems.  At the same time as installing Ubuntu I added a new 400GB harddisk, removed one old HD, configured the RAID-1 system and added an A-Link USB 2.0 PCI-card.

/var/log/messages and .xsession-errors were of no use after the system halt (at that point the system probably couldn't write anything to them anyway).  However, in the case of the desktop crash on both occasions the following lines appear in /var/log/messages:

```
Dec 30 06:32:09 eddie -- MARK --
Dec 30 06:42:29 eddie gconfd (sampo-21418): Received signal 15, shutting down cleanly
Dec 30 06:42:29 eddie gconfd (sampo-21418): Exiting
Dec 30 06:42:32 eddie kernel: [17203605.744000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
Dec 30 06:42:32 eddie kernel: [17203605.744000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 1x mode
Dec 30 06:42:32 eddie kernel: [17203605.744000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 1x mode
Dec 30 07:12:09 eddie -- MARK --
```

As I said, I haven't remembered to check .xsession-errors using a text console in these cases, I'll do that the next time it happens.

I'm leaving now for the holidays, so I'll check back on Wednesday.  Happy New Year, and thanks for any help!

---

