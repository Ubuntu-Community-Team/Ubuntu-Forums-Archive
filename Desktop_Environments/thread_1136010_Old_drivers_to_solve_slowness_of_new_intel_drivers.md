---
title: "Old drivers to solve slowness of new intel drivers?"
date: 2009-04-24
forum: Desktop Environments
---

### Post by wisam on 2009-04-24
Arch Linux solved the problem of the slow intel drivers by providing the old drivers under the name [xf86-video-intel-legacy]("http://www.archlinux.org/packages/extra/i686/xf86-video-intel-legacy/").

Is there a chance that somebody build the old driver (version 2.3.2 which is that last non-slow version) for Jaunty?

I removed the new drivers and tried grabbing the old driver package from 8.04 but it failed to get installed due to conflicts with existing packages. Besides, even if it get installed it won't probably work due to different library versions, right?

Would anybody please build the old drivers for Jaunty?

---

### Post by wisam on 2009-04-24
It seems that it's already been done.

From the release notes:
> If none of the above helps, some users reported success with using an older driver version. 

Old drivers ported to Jaunty
[https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4](https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4)

---

### Post by cariboo on 2009-04-24
I would suggest you have a look at this [thread=1130582]guide[/thread]

---

### Post by binbash on 2009-04-25
read this : [http://www.ubuntu-inside.me/2009/04/how-to-boost-your-intel-cards.html](http://www.ubuntu-inside.me/2009/04/how-to-boost-your-intel-cards.html)

---

### Post by wisam on 2009-04-26
> **cariboo907 said:**
> I would suggest you have a look at this [thread=1130582]guide[/thread]

> **binbash said:**
> read this : [http://www.ubuntu-inside.me/2009/04/how-to-boost-your-intel-cards.html](http://www.ubuntu-inside.me/2009/04/how-to-boost-your-intel-cards.html)

Thanks I'll try that, both are basically the same.

I tried to revert to 2.4 driver, it's even worse.

Why weren't the old 2.3 drivers just built for intrepid or jaunty?
That would have saved us the trouble of using the experimental UXA and a development kernel, right?

---

