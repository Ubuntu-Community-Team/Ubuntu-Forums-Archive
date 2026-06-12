---
title: "So I guess there is no way to use old ATI 9200 drivers in Karmic, eh?"
date: 2010-02-27
forum: Desktop Environments
---

### Post by Redsandro on 2010-02-27
Hi, 

I have this problem where my **nVidia 5200 FX** fried it's hardware acceleration so I could only use it with the open software driver. That's when my very generous friend gave me an **Asus A9250 (ATI 9200 Pro)**. It was supported by **ATI's fglrx proprietary driver**, but support for it stopped after version **8.28.8** and it's now considered **Radion Legacy**, [as you can read here]("http://wiki.cchtml.com/index.php/Hardware").

The installer is still [available here]("https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8.28.8.run"), but it quits after saying that **No X-Server was detected**.

Karmic, bleeding edge as it is, does not support legacy drivers out of the box. I cannot find information about it on this forum.

Does anyone know a way of getting it to work in Karmic?

Also, all sites I found say something similar to *If you own one this card, it is highly recommended that you use the "radeon" Open source drivers.*

Why? 5 year old proprietary technology still kicks modern open driver's *** speedwise. a 1500% speed increase in UT, for example. :)

---

### Post by warp99 on 2010-02-28
It won't work because those modules are compiled against a previous version of Xorg. This is why you get the error no X-server available.

---

### Post by Redsandro on 2010-02-28
Oooh! That explains it. That's too bad. Now I have two videocards that cannot drive my mediacenter. :(

---

