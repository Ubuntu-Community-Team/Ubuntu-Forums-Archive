---
title: "Stuttering in games every  7 minutes"
date: 2013-02-06
forum: Gaming &amp; Leisure
---

### Post by Zirts on 2013-02-06
So I have this problem that whenever I play a game on my Linux machine, it stutters every 7 minutes or so for about 5 seconds. Seems like not a serious problem but it is still a bit annoying. So any ideas on how to even trace the cause of that bug and then maybe try to fix it too.

I have Ubuntu 12.10 installed on my Acer aspire 5552g which has a

AMD 2.20 GHz proccessor Radeon HD 5650 with the latest AMD proprietary drivers. 4 GB of RAM DE: Gnome 3

---

### Post by Arthur_D on 2013-02-06
Not to make you nervous, but last time I had something similar was because the processor was going defunct. Though that was an Intel desktop processor, and stuttering were more regular than that, so presumably there's something else with your computer.

Good luck on the debugging.

---

### Post by holastickboy on 2013-02-06
It could also be the "swappiness" setting of your installation (Ubuntu puts it at a default of 60, which means lots of swapping to hard drive and RAM, etc).  I found that whenever my computer was loading information on my hard drives, it was slowing right down (think loading textures and areas of games). This caused my gaming to exhibit problems like you are explaining on here.

Anyway, I changed my "swappiness" setting to 10, and it doesn't happen anymore. I can also copy large files around with no slowdown at all.  Here is a link on how to do it:
[https://help.ubuntu.com/community/SwapFaq#What_is_swappiness_and_how_do_I_change_it.3F](https://help.ubuntu.com/community/SwapFaq#What_is_swappiness_and_how_do_I_change_it.3F)

---

### Post by Zirts on 2013-02-07
At first try it seemed like the problem was fixed but after awhile it comes back but with lower stutterings, i turned it to 10. But turning it to 0 would be to oextreme too i guess..

---

