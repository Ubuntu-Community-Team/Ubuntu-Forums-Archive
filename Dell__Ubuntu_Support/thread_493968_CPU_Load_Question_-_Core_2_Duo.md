---
title: "CPU Load Question - Core 2 Duo"
date: 2007-07-06
forum: Dell  Ubuntu Support
---

### Post by Burbank on 2007-07-06
I'm a fairly new user with an Intel Core 2 Duo Processor. I don't know if this is an Ubuntu thing or not, but it seems that my overall processor load (during very CPU intensive operations) tends to hover at around 50%. If I graph the load of both CPU's, they seem to "take turns" doing the work. See the image below. Is this normal? Can I make both CPU's work hard at the same time?

[IMG]http://www.burbankconsultants.com/downloads/Screenshot-gkrellm.png[/IMG]

Dave Burbank

Dell Dimension E520N
Intel Core 2 Duo Processor E6320
(1.86GHz,1066FSB) with 4MB cache
3GB DDR2 SDRAM at 667MHz
22 in E228WFPWide Aspect Digital Flat Panel
256MB nVidia GeForce 7300LE TurboCache
2 x 250GB SATA II Hard Drive (7200RPM)
2 Optical Drives: 16X DVD-ROM and 16X DVD+/-RW
Ubuntu Linux Desktop Edition version 7.04
No Microsoft Software

---

### Post by jongkind on 2007-07-06
Yes, that is normal. To my understanding most of the software nowadays only use 1 processor at a time. There are only  a few Windows games that can use both processors at the same time. Others will follow, but that is yet not the case.

---

### Post by jacob01 on 2007-07-06
mine does the same thing and i dont think there is a way to make both cores work equally but it must be normal.
when the processing power is needed both core should max out  

[IMG]/home/jacob/Desktop/Screenshot.png[/IMG]

---

### Post by Rocket2DMn on 2007-07-06
The technical explanation is that the programs running need to be multithreaded.  This means that they have to be programmed in such a manner so that they can perform operations in parallel.  Not too many programs are written like this since it is very hard to do correctly and opens up an entirely new range of problems with sharing memory and other timing issues.
However, in the future we will see more multithreaded programs since multi-core computers seem to be the future of computing.

---

### Post by walkerk on 2007-07-06
Hmm.. My cores run balanced..

---

### Post by Rocket2DMn on 2007-07-06
> **walkerk said:**
> Hmm.. My cores run balanced..

This is either because you are running multi-threaded type processes or you just have multiple processes running at the same time.

---

### Post by atlfalcons866 on 2007-07-06
is hyperthreading the same as having 2 cores?

---

### Post by Rocket2DMn on 2007-07-06
I think hyperthreading is like simulated multi-threading that happens on a processor with a single core (like pentium 4's).  While not true multi-threading, it can increase performance on computers with single core processors that are running programs written to be able to multi-thread.

So no, it is not the same, but it is better than just a plain old single core processor.

---

