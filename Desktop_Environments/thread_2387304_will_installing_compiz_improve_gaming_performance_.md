---
title: "will installing compiz improve gaming performance in LXDE"
date: 2018-03-17
forum: Desktop Environments
---

### Post by Leon8200 on 2018-03-17
So I want to improve gaming performance of lubuntu 16.04, Ive heard that the reason mate, xfce and other DE's run games better is because they have compiz, so does anyone known if this is true from experience?
And if so how would I install it and set it up?

---

### Post by Frogs Hair on 2018-03-17
Compiz uses more resources and may decrease performance on lower spec systems. I don't know about compiz compatibility with LXDE.

---

### Post by #&amp;thj^% on 2018-03-17
> **Frogs Hair said:**
> Compiz uses more resources and may decrease performance on lower spec systems. I don't know about compiz compatibility with LXDE.

i agree with Frogs Hair in regards with hardware specs>>GPU and CPU play a big key in the over all experience with compiz.
But **NOTE:** with the right gear (Hardware) compiz works well enough on LXDE: [https://askubuntu.com/questions/420975/compiz-on-lubuntu](https://askubuntu.com/questions/420975/compiz-on-lubuntu)
Before jumping into installing Compiz you may want to check your system specs.

---

### Post by Autodave on 2018-03-17
Compiz will not make gaming quicker. What are the specs on the machine? What video card is in it and did you install any drivers for it? If so, what one and where did you get it from.

---

### Post by #&amp;thj^% on 2018-03-17
> **Autodave said:**
> Compiz will not make gaming quicker. What are the specs on the machine? What video card is in it and did you install any drivers for it? If so, what one and where did you get it from.

I respectfully beg to differ: [https://www.omgubuntu.co.uk/2012/11/compiz-fix-bringing-better-gaming-performance-to-ubuntu](https://www.omgubuntu.co.uk/2012/11/compiz-fix-bringing-better-gaming-performance-to-ubuntu)
Again though Hardware Hardware Hardware>>>Drivers are also very important to the mix.

---

### Post by Autodave on 2018-03-17
Interesting. However, I have not found that to be true at least on my end. 16.04 Ubuntu and 16.04 Xubuntu. Ubuntu w/Compiz enabled. Same machine: AMD 8 core with 8 gig RAM, 4g Nvidia. Both operating systems on SSD identical drives. While I would not say that Compiz is quicker, I can't really say it is slower either: both playing the same games. I do notice that Compiz uses a good deal more memory though.

---

### Post by #&amp;thj^% on 2018-03-17
Yes I too see a very slight increase in Ram used, and while we do agree on not noticing a speed difference but noticeable in  improving gaming performance.
Best Regards

---

### Post by monkeybrain20122 on 2018-03-17
> **1fallen said:**
> I respectfully beg to differ: [https://www.omgubuntu.co.uk/2012/11/compiz-fix-bringing-better-gaming-performance-to-ubuntu](https://www.omgubuntu.co.uk/2012/11/compiz-fix-bringing-better-gaming-performance-to-ubuntu)
Again though Hardware Hardware Hardware>>>Drivers are also very important to the mix.

I don't game very much but I think the article you cited says that compiz shipped with "undirect fullscreen windows" enabled improves gaming experience comparing to compiz with undirected fullscreen windows disabled, it doesn't say that compiz improves gaming comparing to no compiz.

P.S. I like compiz, it is more than eye candy, it is a very capable window manager that makes my workflow a lot smoother than without. But  not sure about compositing and games..

Cheers.

---

### Post by kostkon on 2018-03-17
Usually, both Unity/Compiz and Gnome Shell outperform other "lighter" DEs on (full screen) games (I base this on some comparison tests done by [Phoronix]("http://www.phoronix.com/")) because they employ undirected rendering of full screen windows by default. As a result their compositor is disabled/bypassed and thus performance is improved when running full screen apps/games.

But, other than that, Compiz will not make them run much faster, and the desktop will feel sluggish if running on old hardware.

So, Compiz will not greatly improve game performance and might decrease your desktop's speed.

---

### Post by mc4man on 2018-03-17
Here compiz typically consumes around 1.2% of 8 gig ram, a rather insignificant amount.

---

### Post by Leon8200 on 2018-03-17
Hi all, thanx for the replies,
So this is my pc

[https://www.cnet.com/products/lenovo-thinkpad-e540-15-6-core-i7-4702mq-4-gb-ram-500-gb-hdd-20c6008qus/specs/](https://www.cnet.com/products/lenovo-thinkpad-e540-15-6-core-i7-4702mq-4-gb-ram-500-gb-hdd-20c6008qus/specs/)

I just want lubuntu to run my games like mubuntu does, I notice maybe a 20% diferance in FPS plus lubuntu seems to run games chopy, Im pretty sure on both lubuntu and mubuntu Im using the same drivers, nothing free, I was told its because LXDE lacks compiz so I thought Id ask here

---

### Post by mc4man on 2018-03-18
> **Leon8200 said:**
> Hi all, thanx for the replies,


I just want lubuntu to run my games like mubuntu does, I notice maybe a 20% diferance in FPS plus lubuntu seems to run games chopy, Im pretty sure on both lubuntu and mubuntu Im using the same drivers, nothing free, I was told its because LXDE lacks compiz so I thought Id ask here

Not sure what mubuntu is, maybe Ubuntu?
Anyway why not just install & switch to compiz & see for yourself..

---

### Post by ank2 on 2018-03-18
Besides what Frogs Hair said, games do not use Compiz. If you are just for games and no "desktop eye candy", don't install Compiz.

---

### Post by #&amp;thj^% on 2018-03-18
OPs GPU chipset is the kicker here. CPU is more than Adequate.
May want to try first with "AccelMethod"  "uxa" in xorg.

---

