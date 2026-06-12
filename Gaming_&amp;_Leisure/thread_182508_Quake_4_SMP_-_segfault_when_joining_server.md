---
title: "Quake 4 SMP - segfault when joining server"
date: 2006-05-26
forum: Gaming &amp; Leisure
---

### Post by FreakDBB on 2006-05-26
Hello!

I just bought a new cpu (Athlon 62 X2 3800+). After Installing an SMP Kernel (2.6.12-19-k7-smp) and the Quake 4 Patch 1.21 i tested quake with playing the id_demo001 and it worked perfectly in SMP mode, even if I have to admit that the performance boost is not as high as I expected.
After that I tried joining a server and failed, getting the following on the console:

----

reloading gfx/guis/scrollbar_down.
reloading fonts/english/bigchars.
Enabling SMP
signal caught: Segmentation fault
si_code 1
Trying to exit gracefully..
--------------- BSE Shutdown ----------------
---------------------------------------------
double fault Segmentation fault, bailing out
shutdown terminal support
pure virtual method called
terminate called without an active exception
Abgebrochen

---

Already googled and read the Q4 FAQ at zerowing.idsoftware.com but still no solution. Connection with the normal, non smp version of q4 works fine.

Does anyone have an idea or at least got quake4-smp working under kubuntu?

Thanks in Advance,

FreakDBB

---

### Post by FreakDBB on 2006-05-29
Well, at least I found a partial solution for it. See:

[http://www.linux-gamers.net/modules/newbb/viewtopic.php?topic_id=2383&forum=14&post_id=11404]("http://www.linux-gamers.net/modules/newbb/viewtopic.php?topic_id=2383&forum=14&post_id=11404")

for the details.

So long,

FreakDBB

---

