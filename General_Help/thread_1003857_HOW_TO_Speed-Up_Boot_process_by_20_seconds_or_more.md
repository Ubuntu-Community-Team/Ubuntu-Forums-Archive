---
title: "HOW TO: Speed-Up Boot process by 20 seconds or more"
date: 2008-12-06
forum: General Help
---

### Post by nunnst on 2008-12-06
I happen to be one of those GNU/Linux users that reboots my computer several times per day, mainly because I don't see any reason to waste electricity when I'm not using the computer.  As such, I am always looking for ways to speed-up the boot process.  I have finally found a tip that had a MAJOR impact on the speed.  I found it on Lifehacker at [http://lifehacker.com/5098369/more-ubuntu-kung-fu](http://lifehacker.com/5098369/more-ubuntu-kung-fu).

The tip is by Keir Thomas, author of the book Ubuntu Kung Fu.  THANK YOU, Keir.

The one I implemented was, "Run Boot-Time Scripts in Parallel".  It is only useful on multi-core processors. On my computer, this simple tip cut almost 30 seconds of my boot time.

To make the change, type the following to open the necessary configuration file in Gedit:

```
gksu gedit /etc/init.d/rc
```
[COLOR="Red"][I]
Note: Always make a back-up of the file BEFORE you make the change.[/I][/COLOR]


Look for the line that reads [COLOR="Blue"]CONCURRENCY=none[/COLOR], and change it so it reads [COLOR="Blue"]CONCURRENCY=shell[/COLOR]. Then save the file and reboot your computer. 

ENJOY!

---

