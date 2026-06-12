---
title: "why is my ping so high ?"
date: 2007-03-04
forum: Gaming &amp; Leisure
---

### Post by dbbolton on 2007-03-04
my ISP's "speed test" reports the following for my computer:
1,661.8 Kbits/sec  207.7 Kbytes/sec

also, browsers seem to work at decent speeds. however, the lowest ping i can get on the Servers List in ET is over 300. does anyone know why ?

---

### Post by lloyd_b on 2007-03-04
Try running a "traceroute" to those servers, and see how many "hops" are involved.  Typically, a high ping time mean that either there are a large number of hops between you and the other machine, or that there is an overloaded network segment in that path.  

In short - a fast network connection has only a limited effect on ping time.  It allows packets to move between your computer and your ISP's router more quickly, but the rest of the trip (between the ISP's router and the destination host) will be the take the same amount of time whether your dialing in at 56K or using DSL at 5MiB/s.

Lloyd B.

---

### Post by dbbolton on 2007-03-04
ah ok. i think i understand now. thanks :)

ps- after i restarted my computer, i had plenty of pings in the 20s and 30s

---

