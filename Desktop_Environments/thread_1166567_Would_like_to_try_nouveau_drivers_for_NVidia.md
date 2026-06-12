---
title: "Would like to try nouveau drivers for NVidia"
date: 2009-05-21
forum: Desktop Environments
---

### Post by fballem on 2009-05-21
I have an NVidia 8600GT card and I'm running ubuntu 9.04. I'm currently using the nvidia proprietary drivers, but I've heard of a project called nouveau that provides open source drivers for nvidia cards.

Does anyone have experience with the nouveau drivers? If so, would you mind sharing your impressions? In addition, I would like to know if these are in the repositories and if so, how do I install them?

Many thanks,

---

### Post by 67GTA on 2009-05-21
I tried it a while back. There is mostly 2D right now. Some common models have limited 3D. I have a GeForce 7150M. They worked okay, but the screen was slightly dimmer than with the nvidia driver. The nouveau drivers need more work. It is in the repos for 9.04. Search for ```
xserver-xorg-video-nouveau
``` This will remove the nvidia driver currently in use.

---

### Post by Chemical Imbalance on 2009-05-21
3D is severely crippled with the nouveau drivers.

I can only recommend it if you don't play games or watch a lot of flash.

---

### Post by fballem on 2009-05-22
The impression that I get is that they're not quite ready for prime time yet. I'll stay with the nvidia drivers and look at it again for koala.

Thanks very much for the help!

---

