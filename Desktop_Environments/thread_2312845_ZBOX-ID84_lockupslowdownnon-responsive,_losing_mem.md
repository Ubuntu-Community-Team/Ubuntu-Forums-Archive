---
title: "ZBOX-ID84 lockup/slowdown/non-responsive, losing memory?"
date: 2016-02-07
forum: Desktop Environments
---

### Post by yonnie on 2016-02-07
I installed this ZBOX, put wine on it and am running a server in client mode and connecting via VPN to the server.  This has been running fairly well for about a year until some updates a few months ago.  The unit was installed with 2GB of ram, a 300GB WDC sata drive (I know, complete overkill).  OS version Linux 3.13.0-77-generic, KDE SC version 4.13.2 (Your basic Kubuntu 14.04LTS).

I discovered in the Kinfo center there would be 3-400 MB free and no usage of swap space.  After unit had been running for awhile (few hours) I noticed the free memory is dropping down to none.  Then I see the problem.  I replaced the 2GB of ram with 4GB.  Now the system doesn't seem to lockup anymore.  However, the swap space is still not being used or not reporting properly and the free memory starts out around 1.5GB and slowly gets smaller.  Unit has been running for about 4 days and present free memory is about 300MB.  Free swap is at 99%.  It looks to me that this unit does not make use of Swap and it is not properly handling physical memory.  I just did a reboot to see where the physical memory used amount starts out at.  It starts out at 1.6GB of free physical space

6 hours later the free memory is down to 1.2GB

A day later and it's down to 800MB

14 hours later it's down to 520MB

Closed the vpn tunnel, closed the server app, closed FF, ran updates, re-opened the previous apps.  Free Memory now at 628MB

---

