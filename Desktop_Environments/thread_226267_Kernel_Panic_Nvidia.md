---
title: "Kernel Panic Nvidia"
date: 2006-07-31
forum: Desktop Environments
---

### Post by dibblego on 2006-07-31
I have installed Dapper desktop and performed a apt-get upgrade.
I am running 2.6.15-23-386 kernel and a NVidia PCX5300 graphics card.

I have tried installing the NVidia driver (apt-get install nvidia-glx and all that) and each time I do, the machine kernel panics upon reboot. I have also tried installing from the driver that is available on the NVidia website (1.0.8762), which installs files to the wrong locations, but after symlinking, I get the same problem on boot.

When I switch xorg.conf back to the "nv" driver (not the "nvidia" driver), booting is successful. The "nvidia" driver is guaranteed to produce a kernel panic on boot i.e. the problem is consistently reproducible.

Hints?

---

