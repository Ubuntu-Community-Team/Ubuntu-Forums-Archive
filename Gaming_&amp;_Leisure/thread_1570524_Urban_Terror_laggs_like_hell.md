---
title: "Urban Terror laggs like hell"
date: 2010-09-08
forum: Gaming &amp; Leisure
---

### Post by JohnHeikkila on 2010-09-08
Okay, so my problem is that Urban Terror laggs like hell. The FPS drops dramatically, but my system's temperature is only 60 degrees Celsius.
System specs:
```
Acer Aspire 5520
AMD Athlon(tm) 64 X2 Dual-Core Processor TK-57
4GB DDR2 Memory
1407MB Graphics cache
Nvidia GeForce 7000M
Atheros AR5001 Wireless (built-in)
```

Usually, it's the CPU that lags. Sometimes the network crashes randomly (my PC's network goes down).

---

### Post by NightwishFan on 2010-09-09
With those specs it has to be network related. My machine that plays Urban Terror has half the CPU/Ram and an old Nvidia 6150. Check the logs for anything unusual, also ensure you have proprietary nvidia drivers installed in System -> Administration -> Hardware Drivers.

---

### Post by Raffles10 on 2010-09-09
You can try turning on Vertical Sync, it reduces fps to 60 but does improve performance.

---

### Post by georgegerm on 2010-09-10
wow i use a dell lappy with 2g ram an celeron n550, on board graphics and even in hotels on wireless it plays smooth
you must have other issues

---

### Post by JohnHeikkila on 2010-09-12
Okay, I got it fixed.

I was using Compiz with a lot of effects. I downloaded Openbox and selected Openbox as my Window manager from fusion-icon and now it runs like a charm.

Though I tend to get lag spikes every 10 seconds.

---

### Post by Glenn nl on 2010-09-12
Try the setting affinity:

[http://dailynade.com/solve-urban-terror-graphic-problems-with-affinity/](http://dailynade.com/solve-urban-terror-graphic-problems-with-affinity/)

(look at the ubuntu fix 2, at the end of the article)

---

