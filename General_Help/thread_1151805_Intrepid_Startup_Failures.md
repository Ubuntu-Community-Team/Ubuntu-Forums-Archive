---
title: "Intrepid Startup Failures"
date: 2009-05-07
forum: General Help
---

### Post by kw1502 on 2009-05-07
I’ve started to have problems with my Intrepid installation. The system had been stable for quite a while up until recently. The problem is when I power-on the system, sometimes the monitor goes black, the Num Loc and Caps keyboard keys blink and nothing else works. I have to recycle power  and reboot again to recover. I keep my software up to date, so one of the updates may be the problem but I have no way of knowing which one.

This happens about 20% of the time I turn the system on. I don’t think it’s hardware as Windows XP boots fine all the time.

What can I look at/for to determine what is going wrong? 

One possible clue is an entry in /var/log/sylog  init: rc2 main process (****) killed by SEGV signal. This entry is not logged each time the problem occurs but may be of some help.

---

