---
title: "evolution-exchange 2.24.3 still crashes"
date: 2009-02-05
forum: General Help
---

### Post by amosshapira on 2009-02-05
Hello,

After about a week with 8.10 evolution working well with MS Exchange 2003, it started loosing ability to access the exchange server. I noticed errors like the following in the system log:

Feb  6 09:36:13 amos-pc kernel: [ 1239.695461] evolution-excha[6840]: segfault at 9fc0 ip 0805eb9f sp b611b290 error 4 in evolution-exchange-storage[8048000+3c000]

The closest bug report I found in launchpad was [https://launchpad.net/ubuntu/intrepid/+source/evolution-exchange/2.24.3-0ubuntu1](https://launchpad.net/ubuntu/intrepid/+source/evolution-exchange/2.24.3-0ubuntu1) which talks about evolution crashing altogether and seems to suggest that the version I have now (2.24.3) is the latest and greatest with a fix. I couldn't find anything else related to this problem.

I filed bug [325537]("https://bugs.launchpad.net/ubuntu/+source/evolution-exchange/+bug/325537") in launchpad, so far it haven't been touched.

Does anyone know what can I do to make it work again?

I'm using 8.10 i386 on AMD Athlon 64 Processor 3000+

Thanks.

---

