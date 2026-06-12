---
title: "Quadro FX 3800 on LTS 12.04 with Nouveau"
date: 2012-04-30
forum: Desktop Environments
---

### Post by deadonarrival on 2012-04-30
I'm daily switching between dual-monitor and single monitor, and using the nvidia-settings panel each time is really annoying.

I would like to switch to the Nouveau driver. I tried to switch during the upgrade from 11.10 to 12.04, but could only get 1024x768 as resolution after the upgrade. Both monitors are 1900x1200.

Any suggestions on how to solve this? If not, is there a simpler way to switch between dual and single screen?

It's a dual head Quadro FX 3800M.

---

### Post by drdnl on 2012-07-28
I've done the same thing (also a Quadro) for pretty much the same reasons.

First, remove all nvidia drivers via 'additional drivers' (and optionally purge nvidia-settings just to be sure)

then, you already have the 2d nouveau, you need the experimental mesa bit for 3d (and full resolution)

I installed these two, the first one just to be sure
```
sudo apt-get install libgl1-mesa-dri libgl1-mesa-dri-experimental
```

And rebooted, instant 3d accelerated nouveau. I'm actually quite impressed, in my case it plays 1080p video without a problem. Especially hope it eases dual monitor and stops crashing...
([https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/973096](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/973096))

---

