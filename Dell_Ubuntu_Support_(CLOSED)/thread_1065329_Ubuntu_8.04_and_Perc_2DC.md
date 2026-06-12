---
title: "Ubuntu 8.04 and Perc 2/DC"
date: 2009-02-09
forum: Dell Ubuntu Support (CLOSED)
---

### Post by agentfubu on 2009-02-09
Hey,

I know Perc 2 is outdated, but here's my problem. I have an old poweredge 6450 server and a Perc 2/DC controller. I have 4 SCSI hard drivers using the onboard controller without any problems. I wanted to add some external arrays so I put in an unused Perc 2/DC controller card. The card is unrecognized by the system so my drives aren't recognized. Is there anything I can try or is my card just incompatible with Ubuntu? Thanks.

If you need any more info to help just tell me.

---

### Post by agentfubu on 2009-02-11
I found out the answer on my own. If anyone else is having problems with this you're out of luck. On the new kernel, the old megaraid driver has been scrapped for a new one which doesn't support older perc cards which is pretty much ridiculous if you ask me.

---

### Post by Krokido on 2009-05-01
Thanks for this post! I've got perc 3 raid controllers and I've been trying just about anything to get Ubuntu 8.10 working on my poweredge 6450. it simply doesn't want to go on/in by machine :S. Ah well, we'll try some other Ubuntu release, 6.06 does work if you have a cdrom drive i.s.o. a dvd drive in the poweredge 6450.

---

