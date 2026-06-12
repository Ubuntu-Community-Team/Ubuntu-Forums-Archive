---
title: "Dapper randomly freezes"
date: 2006-09-12
forum: Desktop Environments
---

### Post by flashblue on 2006-09-12
Periodically when I am using Dapper it freezes randomly and I have to do a hard reboot. I have 512mb of RAM and Intel Celeron D processor 2.66ghz.  Memtest did not find any errors.

---

### Post by lagagnon on 2006-09-13
Random freezes are usually indicative of hardware faults, not OS faults. I suspect, in this order:

1) bad memory stick (but if memtest OK then maybe not)
2) a failing hard drive (use "smartctl" and your HD manufacturers diagnostic diskette available from their websites).
3) overheating: clean out all fans, reseat CPU, perhaps renew heat sink compound.
4) failing power supply.

---

### Post by DarkStarDeity on 2006-09-13
> **lagagnon said:**
> Random freezes are usually indicative of hardware faults ...

Except that many other users have been reporting random lock-ups since June in [this thread]("http://ubuntuforums.org/showthread.php?t=193283"). There is a poll about it to gather more info for a bug report (has that been done yet?) [here]("http://www.ubuntuforums.org/showthread.php?t=204588").
It's looking like possibly an Xorg problem.

---

### Post by someguyouknow on 2006-09-13
I have a similar problem but less severe. mines seems to freeze randomly every 5-10 minutes but only for a few seconds.

---

### Post by eylisian on 2006-09-13
- Funny that Dapper did the same thing to my Thinkpad T30. Random 'hard" locks that would require "hard" resetting, Never any logging to go off of either, the machine would lock up before anything could be writtem to any logs. Dmesg looked like a bad report card though, there were so many errors (mainly acpi, which I disabled on boot, no luck. I finally dropped back to Breezy out of frustration and at least the badger didn't let me down (it had run well on the same box for close to a year).

- You might just do that, rebuild Breezy and wait for better support for whatever it is thats locking the box. If you have a way of re-installing your home dir after a rebuild it's not that big of a deal.

- Most of all, good luck.

peas.

---

