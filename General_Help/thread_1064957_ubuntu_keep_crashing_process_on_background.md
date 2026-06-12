---
title: "ubuntu keep crashing process on background"
date: 2009-02-09
forum: General Help
---

### Post by stanikmanik on 2009-02-09
Hi guys, I'm n00b in ubuntu but i'm trying to use one barbone system to play video sequence in loop. I have ver. 8.10 installed with totem-xine and my problem is that video keep crashing all the time. I'm not able to play it 12hours nonstop without restart. I'd tried another computer (very same configuration but it didn't help)

I'm looking at the log files and only one interesting thing is:
anacron[18606]: Job 'cron.daily" terminated
anacron[18606]: Job 'cron.weekly" started
anacron[18946]: updated timestamp for job 'cron.weekly" to 2009-02-09
syslogd 1.5.0#2ubuntu6: restart

Is this crashing my video loop? How can i disable it or make sure that this will not stop process i'm runing on background? 

Many thanks for your advices

---

### Post by jman6495 on 2009-02-09
check the cron to make sure you havent set it so it just lasts twelve hours then stops.



   other than that i'm not sure

    jman6495

---

### Post by stanikmanik on 2009-02-12
Yesterday i spend few hours trying to solve it out, I ran all updates (over 250MB), reading forums about this and nothing help. 
Can anyone help me with this? I'm really loosing patience

What log files do you want to see? Please let me know and i'll attach them. 

In kern.log i found a message:
date:time:user : [37603.248577] totem[5467]: segfault at 0 ip 00000000 sp b33a26ec error 4 in totem-gstreamer [8048000+59000]

In the past i had tried totem-xine as well as Mplayer and they've been crashing even more often than this one. I really need simple loop playing video. Nothing more, nothing less

Many thanks for any assistance

---

