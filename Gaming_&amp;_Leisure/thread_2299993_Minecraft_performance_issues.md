---
title: "Minecraft performance issues"
date: 2015-10-22
forum: Gaming &amp; Leisure
---

### Post by james_moore2 on 2015-10-22
So I recently got Ubuntu 14.04.3 LTS and I tried running minecraft on my Toshiba Satellite L755-S5112, it will run but it freezes constantly, I have associated 3 gigabytes of 4 gigabytes of my ram, I have an 8gb swap (I know its slower) and I have optifine, is there any thing I can do to stop this major lag? I would like to say too that when I had Windows 7 (before my HDD broke) it was fairly well, and my pagefile was about 6gb.

---

### Post by efflandt on 2015-10-23
You marked this [SOLVED], but did not say what you did to solve it. The **free** command in a terminal would give you an idea of how much of your RAM is available, but I am not sure how that ends up when some RAM is shared for graphics:
"Mobile Intel® HD graphics with 64MB-1696MB shared graphics memory"

So giving java 3 GB for minecraft may be overly optimistic. I would try giving java 1G to 2G and see how that works (or split the difference and try 1526M).

I have run minecraft giving java -Xms768M -Xmx768M on a 2 GB tablet PC which was a bit slow on a 1 GHz 2 core cpu, although, it has a dedicated graphics chip (AMD HD 6250). That tablet PC boots/runs either 64-bit Lubuntu or Ubuntu 12.04 from an SD card slot (its 32 GB SSD has Win7 Pro which runs minecraft a bit slower).

---

