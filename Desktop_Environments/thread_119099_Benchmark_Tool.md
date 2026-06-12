---
title: "Benchmark Tool"
date: 2006-01-18
forum: Desktop Environments
---

### Post by theQmaster on 2006-01-18
I'm looking for a benchmark tool to see the performance of the 
- ram
- cpu
- network card 

etc.

Also is there a way to see what applications are swapping to disk or what application had to swap to disk in the past ? 

Regards,
Q

Affordable Stock Photography
[http://www.goodstockimages.com](http://www.goodstockimages.com)

---

### Post by kakashi on 2006-02-07
use memtest for ram test.

---

### Post by obx-jdt on 2006-02-11
I'm looking for the samething, with a gui.....command line will work, but I want to see the charts.
memtest at boot up isn't what I'm looking for....

---

### Post by az on 2006-02-12
I think people typically compile a small application (like apache) or something bigger (the kernel) to benchmark their hardware.  This measures cpu and disk-i/o realistically.

tar xvzf
./confgure
time make
(that will compile it and tell you how long it took.  You compare that on different hardware using the same version of the app with the same toolchain)

There are no GUI benchmark tools that are any more current that 2000 because, I guess, people who use linux realise that any metric provided by those tools is useless.  Memtest86 provides detailed information about ram speed - just loot at the top left of your screen.   It typically does not change.

---

