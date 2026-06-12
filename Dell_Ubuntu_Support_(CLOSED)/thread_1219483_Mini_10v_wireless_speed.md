---
title: "Mini 10v wireless speed"
date: 2009-07-21
forum: Dell Ubuntu Support (CLOSED)
---

### Post by bri5569 on 2009-07-21
Just received my Mini 10v this afternoon with Ubuntu installed. Here's some of my findings. Deleted the Dell 8.04 after about  10 mins as wireless connection to internet kept dropping. Had tried 9.04 (Live) which at least stayed connected so I have installed that. Everything works perfectly except my wireless connection which can only get 44Mbs even though it's the Dell 1510 card which is 800.11n which I had asked for. Most times it sits at 22 Mbs.
As a releveant newbie to Ubuntu I hope you can help me get this speed up a bit. My Mrs has the exact same Dell (10v) only with Xp but her internet is connectiong at 125Mbs. I hate to say this but I now wish I had gone down the same path so I call upon your good selves to help me out. Thanks in anticipation.

---

### Post by MartynT on 2009-07-22
Hi,

I have a similar problem described here

[http://ubuntuforums.org/showthread.php?t=1219713]("http://ubuntuforums.org/showthread.php?t=1219713")

I think the officially supported, "free" drivers probably only support 802.11b.  Not g or n.  Hence the slow speed for you and no connection at all for me (I think my router might be in 'n' only mode).

If this is the case then a possible solution is to use a windows driver.  This is done with ndiswrapper.

I haven't tried this yet so I don't know if it's easy or even if it will work.

There's a comprehensive "How To" about ndiswrapper in the Networking & Wireless forum.

[http://ubuntuforums.org/showthread.php?t=885847]("http://ubuntuforums.org/showthread.php?t=885847")

---

