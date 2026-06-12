---
title: "CPU load &quot;bursts&quot;"
date: 2006-09-01
forum: Desktop Environments
---

### Post by grenness on 2006-09-01
From time to time my Thinkpad X60s with Ubuntu 6.06.1 and 2.6.15-26-686 kernel suddenly enters a CPU load burst phase where the computer freezes for half a second every 5 seconds or so.
The System Monitor CPU History graph shows this as "teeth", and it's very annoying especially when I use the mouse trying to hit icons and buttons.
After using System Monitor to try to identify the suspects I disabled Beagle, but after a few days the annoying bursts were back. A reboot usually fixes things.

Does anyone have any ideas on what this is?

Is it possible to se CPU load history details, like which application/process peaked the CPU two minutes ago?

Thanks,
Christopher

PS. I'm a newbie with Linux, so please be gentle on any Terminal/Shell instructions...

---

### Post by halfvolle melk on 2006-09-01
Hi,
I'm not sure how to log CPU usage, but I did a quick search and found that it's a core duo. Is it? Do you see both CPU's? If not you might want to install linux-686-smp. More on this can be found here:
[http://www.ubuntuforums.org/showthread.php?t=85917](http://www.ubuntuforums.org/showthread.php?t=85917)

---

### Post by greg m on 2006-09-01
in firefox, do you have fireftp in the extensions? if you do, remove it. mine was doing the same thing. until i removed fireftp.

---

### Post by greg m on 2006-09-01
also for cpu usage, in terminal type top. i found out about that two days ago

---

### Post by grenness on 2006-09-01
> **greg m said:**
> also for cpu usage, in terminal type top. i found out about that two days ago
I also just tried top today, but isn't it limited to a snapshot of what's going on right now?
I have tried having top running, as well as System Monitor sorted by CPU load, but I couldn't see which process it is that causes the bursts.

---

### Post by halfvolle melk on 2006-09-01
Check this out:
[http://www.die.net/doc/linux/man/man1/sar.1.html](http://www.die.net/doc/linux/man/man1/sar.1.html)
It's in the sysstat package.

---

