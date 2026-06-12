---
title: "virtual windows vista or w7"
date: 2009-09-23
forum: Desktop Environments
---

### Post by rmb938 on 2009-09-23
I switched one of my old computers to ubuntu server edition because I am running a server and I have gotten so used to it I rarely use any windows only features any more.

Anyway. I am thinking on installing the desktop edition on my main computer but I still use windows to play my games and stuff. So I was wondering if I virtualize windows vista in ubuntu will I see a major difference in performance? Also what is the best program to have virtualization. 

Here are my current system specs and I am currently running windows vista:

Asus M4N82 Deluxe Motherboard
AMD Phemon II x3 2.6Ghz(tri core) cpu
500 GB HDD
4 GB Ram
Nvidia 8400 GS gfx card

I currently have 64-bit windows vista running on my computer.

I would dual boot like I have before but I don't feel like restarting every time I need to talke to someone on xfire or w.e.

I used wine before but I have run into many problems with games and stuff.

---

### Post by Lars Noodén on 2009-09-23
Check the reviews, neither Vista nor Vista7 give an advantage over XP.  Rather, so far the opposite.  

The package you probably get better use from would be [WINE](http://packages.ubuntu.com/search?keywords=wine&searchon=names&suite=jaunty&section=all)

[http://packages.ubuntu.com/search?keywords=wine&searchon=names&suite=jaunty&section=all](http://packages.ubuntu.com/search?keywords=wine&searchon=names&suite=jaunty&section=all)

See also 
[http://www.winehq.org/](http://www.winehq.org/)

If there is something that doesn't run then try CodeWeaver's Crossover products.

---

### Post by rmb938 on 2009-09-23
well xp lags on my computer since its newer and vista+ was made for all the newer pcs.

I tried wine also. It doesn't work with xfire and some of my games. I looked into Crossover but I don't have money to pay for them since i am 15 with no job yet.

---

### Post by yanceypd on 2009-09-23
I have an older slower 32 bit pc.  While games run in vbox Vista they are slugish on my box.

---

### Post by Lars Noodén on 2009-09-24
> **yanceypd said:**
> I have an older slower 32 bit pc.  While games run in vbox Vista they are slugish on my box.

While Vista has improved some is still considered functionally a failure.  The jury is still out on Vista7, but the prognosis is not much better. Either way, if you work with virtualization you have two systems **and** the hypervisor to worry about and maintain, violating the Keep It Simple principle.  If you run WINE, you have one system to worry about and maintain.  

Using WINE skips the virtualization and allows programs or game that use Windows APIs to run **directly** under Linux.  That eliminates a lot of hassle.  As a bonus, some [ Windows games run better under WINE](http://www.wine-reviews.net/news/linux-has-better-windows-compatibility-than-vista.html).

---

