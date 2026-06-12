---
title: "True RAID controllers - which ones?"
date: 2006-06-26
forum: Desktop Environments
---

### Post by Panhead Bill on 2006-06-26
In reading the forums, I have learned that there are True RAID controllers and Fake Raid controllers.

A while back I purchased a RAID controller on E-bay, with the intention of setting up a raid-0 or raid-5 on my Ubuntu PC, but it turns out that it is most likely a fake raid controller.

What brands/models are true raid controllers?  Are any of the true RAID controllers designed for Parallel ATA drives?

---

### Post by JoWilly on 2006-06-26
The brand  (in ATA/SATA controllers)  with the best reputation and almost always (could I say always (?)) the best in the benchmarks on the web is 3Ware. Also features trouble free support on linux, with excellent drivers.

---

### Post by JoWilly on 2006-06-26
But if you are not running a sever that is maxing cpu and disk activity out all the time, the software linux raid is the best price/qualitly/performance/features wise you can get. You wont need a hardware raid for normal operation.

Regarding fakeraid : the best is also to put it in IDE mode, and to put linux raid on the disks.

You install your system on a linux software raid with the ubuntu alternate install cd.

---

