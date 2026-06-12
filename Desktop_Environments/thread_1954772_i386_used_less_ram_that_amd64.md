---
title: "i386 used less ram that amd64?"
date: 2012-04-08
forum: Desktop Environments
---

### Post by Lemuriano on 2012-04-08
I install xubuntu 12.04 i386 on my HTPC connected to a 46¨ full hd tv through HDMI with the following configuration, (Asus AT510NT-I Intel Atom D525 (1.8ghz dual core) BGA 559 Intel NM10 Mini ITX motherboard with 4g of DDR3 800 ram) and the ram use was about 160mb v/s an amd64 installation that use > 350mb. 

Would it be wise to chose 32 bit over 64? This HTPC would be use only for XBMC, Hulu, and XP on a VM to watch Netflix. 

Any advise would be welcome.
[B][SIZE=1]
[/SIZE][/B]

---

### Post by IWantFroyo on 2012-04-08
32 bit systems can only really handle about 2GB of RAM. 64 bits would use your RAM much more efficiently.

---

### Post by 3Miro on 2012-04-08
32-bit regular system can see little over 3GB of RAM.

32-bit PAE kernel will see all of 4GB of RAM, but it will have a small performance loss.

64-bit will be able to handle 4GB of RAM, will come with a performance boost, however, the bare system will use more RAM.

4GB of RAM are more than enough for everything that you need. For that matter, 3GB would also be enough. I would go for 64-bit in your case for the small boost in speed, there is no other significant difference.

---

### Post by Lemuriano on 2012-04-08
Thanks for the advise. :)
I will go with 64 bit with my fingers cross because up until now flash have giving me trouble when using 64 bit, either with Ubuntu or Xubuntu. While using 32 bit, flash has not been perfect either, but at least watchable.

---

### Post by 3Miro on 2012-04-08
Which versions of Ubuntu have you been using. It wasn't until recently that Adobe released an official 64-bit client for flash, so Ubuntu versions prior to 11.10 had to use some emulation which caused problems. You should not have any more 64-bit flash issues.

---

### Post by Lemuriano on 2012-04-09
Hi,

I was using 10.04  amd64 but had no sound with HDMI so I try  11.10 and still no sound and finally decide to try 12.04  even if it is a  work in progress, and happy to say that the sound was laud and clear.

But flash is not stable in full screen when using the resolutions 1920x1080 or 1680x1050, while using Hulu or YouTube.                          But if I lowered to 1600x1024 or less it work, not perfect but very  good. The lower the resolution, it seems to work better . Of course that  1920x1080 is the final objective. 

My first impression between  32 & 64 bit is that 32 play flash better at least with this  particular version, but tomorrow I will try Xubuntu 12.04 amd64 and will  play with the resolutions.
   
    

Perhaps another thread should be open. If that is the case, just let me know.

---

