---
title: "Unity GUI Performance"
date: 2011-07-19
forum: Desktop Environments
---

### Post by head-desk on 2011-07-19
Hopefully someone can be of some assistance. I use Ubuntu 11.04 with Unity and quite like it.

Problem is that performance for Unity is terrible. Moving windows about feels sluggish and laggy.

I tried Unity inside a virtual machine on Windows afterwards and its 3D performance is 5x that of native bare metal Unity when using ATI drivers. How can a virtual machine out perform bare metal when it comes to 3d rendering?

Anything I can do to solve the GUI performance? GPU is a Radeon HD 5870

-HeadDesk

---

### Post by Frogs Hair on 2011-07-19
See the third item on this page . [http://www.webupd8.org/2011/04/things-to-tweak-fix-after-installing.html](http://www.webupd8.org/2011/04/things-to-tweak-fix-after-installing.html)

---

### Post by 3Miro on 2011-07-19
> **head-desk said:**
> How can a virtual machine out perform bare metal when it comes to 3d rendering?


Simple: you have a bad driver. 

I would try Unity with and without the proprietary AMD driver (from Additional Drivers). The default AMD driver is pretty good and I have seen it perform sometimes better than the proprietary one.

---

### Post by fjgaude on 2011-07-19
With my Intel CPU with embedded graphics GMA HD I get wonderfully quick movement of windows, etc.

The right driver for your video board should do the job.

---

