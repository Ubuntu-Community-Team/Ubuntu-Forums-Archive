---
title: "Hard freeze -- heci maybe?"
date: 2009-05-03
forum: General Help
---

### Post by DorianX on 2009-05-03
I'm occasionally having issues with a system running Mythbuntu 8.10.  Every once in a while, the system will simply lock up, completely solid. It stops responding via the keyboard, mouse, or network, and can only be restarted by power-cycling. This only manifests when a human being is interacting with the machine (ie., I never come home to find that it's locked up during the day).  In most instances, the lockup occurs shortly after inserting a DVD into the DVD-ROM drive, but it recently occured while watching a movie off the hard disk (However, there was a DVD in the drive at the time). 

The only thing I have ever found in the log which is dated to the time of the crash is this:

May  3 09:25:43 mrsmith kernel: [1607906.000546] heci: schedule work the heci_bh_handler failed error=0


These errors occurred for about 30 minutes up to the time of the crash. However, looking through my older logs, I see that I receive those errors every few days with no crash associated.

HP Compaq dc7800p Small Form Factor
 Intel(R) Core(TM)2 Duo CPU     E6750  @ 2.66GHz
 GeForce 8400 GS

Any ideas?

---

### Post by happyhamster on 2009-05-03
Are you using the proprietary Nvidia driver? See:

[https://bugzilla.novell.com/show_bug.cgi?id=467513#c2](https://bugzilla.novell.com/show_bug.cgi?id=467513#c2)

Basically, what they're saying is that linux developers can't fix this, it's up to Nvidia (because of closed source code). Best thing you can do is trying the latest Nvidia drivers, or an open source one (better stability, but worse performance).

Additionally, visit Nvidia's linux forum: 
[http://www.nvnews.net/vbulletin/forumdisplay.php?s=&forumid=14](http://www.nvnews.net/vbulletin/forumdisplay.php?s=&forumid=14)

Good luck.

---

