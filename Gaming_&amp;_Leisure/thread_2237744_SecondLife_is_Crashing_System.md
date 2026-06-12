---
title: "SecondLife is Crashing System"
date: 2014-08-03
forum: Gaming &amp; Leisure
---

### Post by tsunalugi on 2014-08-03
Hey,

I have been away from Ubuntu for a while. I just did a fresh install to Ubuntu 14.04.1 & thought to play my favorite game, Second Life. I went to run the viewer & the system crashes after a couple minutes each time. I have an NVIDIA GeForce GT620 Graphics Card. I installed the nvidia-current drivers & ubuntu-restricted-extras. I am not sure what I am missing.

Please Help.

Signed,
Tsunalugi.

---

### Post by oldrocker99 on 2014-08-05
Nvidia-current is at 3.04, and the latest driver is 3.40. I had an unrecoverable crash on X-COM until I installed the 3.40.24 drivers from the xorg-edgers PPA, and here's how:

```
sudo apt-add-repository ppa:xorg-edgers/ppa
sudo apt-get update
sudo apt-get install nvidia-graphics-drivers-340
```

You'll have to reboot, of course. See if this eliminates the crashes; I hope so for your sake.

I will also say that the 620 is pretty underpowered, but it should run Second Life, especially with the newest drivers.

---

### Post by oldrocker99 on 2014-08-05
Nvidia-current is at 3.04, and the latest driver is 3.40. I had an unrecoverable crash on X-COM until I installed the 3.40.24 drivers from the xorg-edgers PPA, and here's how:

```
sudo apt-add-repository ppa:xorg-edgers/ppa
sudo apt-get update
sudo apt-get install nvidia-graphics-drivers-340
```

You'll have to reboot, of course. See if this eliminates the crashes; I hope so for your sake.

I will also say that the 620 is pretty underpowered, but it should run Second Life, especially with the newest drivers.

---

