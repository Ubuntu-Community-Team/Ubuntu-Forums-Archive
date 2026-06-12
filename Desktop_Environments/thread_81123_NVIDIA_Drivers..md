---
title: "NVIDIA Drivers."
date: 2005-10-23
forum: Desktop Environments
---

### Post by Shroomer on 2005-10-23
I can't get the drivers to work for my grafix card. I have tried everything from the install file from invidia and apt-get. Dod anyone else have issues installing the drivers? :(

---

### Post by ltmon on 2005-10-23
Do you have an older nvidia card?

In this version of Kubuntu there are now two versions of the nvidia drivers.  One of the drivers is called "legacy" because is supports older cards.  The standard drivers no longer support some older cards.

If you have an older card, try:

- removing nvidia-glx
- installing nvidia-glx-legacy
- installing linux-restricted-modules-[your kernel version]-nvidia

And restarting the computer.

L.

---

