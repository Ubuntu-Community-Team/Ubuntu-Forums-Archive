---
title: "HD sleeping with hdparm in 9.04"
date: 2009-05-14
forum: General Help
---

### Post by TheHoff2 on 2009-05-14
Hey everyone --

I have two harddrives in my machine. One of them is pretty noisy and used mostly for backup, so I like to spin it down on boot. On 8.10 I was able to accomplish this with a "hdparm -Y <device>" in /etc/rc.local. But on 9.04 (via upgrade on 8.10) this causes the drive to spin down and then *immediately* spin back up, whether done at boot time or any other time. I have also tried "hdparm -S1 <device>" but that seems to do nothing at all. Any advice? What additional information would be helpful?

-- John

---

