---
title: "Dell studio 1537 with 8.10 -&gt; cron segfault"
date: 2009-02-04
forum: Dell Ubuntu Support (CLOSED)
---

### Post by jeanpaul77 on 2009-02-04
Hi All,

I have installed Ubuntu 8.10 64bit on my Dell 1537 (4GB RAM). 

As soon as a script is executed via the crontab, or by the 'at' command I see the following messages in /var/log/messages:

kernel: [26943.143225] cron[9982]: segfault at 0 ip 0000000000000000 sp 00007fff817f4cf8 error 14 in cron[400000+9000]

Or:

kernel: [  968.708287] atd[8247]: segfault at 0 ip 0000000000000000 sp 00007fffd3f77728 error 14 in atd[400000+5000]

The script I try to execute is quite simple :)
#!/bin/bash
exit 0

So that is not causing any difficulties...

Does anyone have additional information on how to fix or troubleshoot this?

Thanks!

---

