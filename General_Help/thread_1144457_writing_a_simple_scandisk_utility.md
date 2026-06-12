---
title: "writing a simple scandisk utility"
date: 2009-04-30
forum: General Help
---

### Post by liketofindoutwhy on 2009-04-30
how long to write a simple scandisk utility that merely does

sudo touch /forcefsck

and display "you need to reboot Ubuntu for the filesystem check to start"?

probably will take 2 hours at most?

how many people can you save from them using 

sudo fsck

and destroying all their data?  Maybe 10% of users -- 100,000 people?  Maybe 1% of users, 10,000 people?  If so, why not write that utility?

---

### Post by skymera on 2009-04-30
Ubuntu scans automatically on boot.

A "simple scandisk utility" isn't needed.

Mine automatically runs FSCK every 23 boots.

---

### Post by liketofindoutwhy on 2009-04-30
> **skymera said:**
> Ubuntu scans automatically on boot.

A "simple scandisk utility" isn't needed.

Mine automatically runs FSCK every 23 boots.

so what if you take the laptop on a trip and either the car trip or the plane security check was pretty rough and when you arrive you just want to do a scan disk to make sure the hard disk will be in good order?

---

