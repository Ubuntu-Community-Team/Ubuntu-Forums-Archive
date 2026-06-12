---
title: "Graphics Card"
date: 2007-08-06
forum: Gaming &amp; Leisure
---

### Post by platypuz on 2007-08-06
I have a Nvidia Geforce FX 5500.  My question is a simple one: are there any known issues with this card and wine? Or with this card and Ubuntu in general? The games I play are World of Warcraft, some Starcraft and Counter Strike Source. I haven't been able to find any threads stating any issues with this card but I'm just trying to make sure before I switch over completely to Ubuntu.

---

### Post by cogadh on 2007-08-06
Practically all Nvidia products run perfectly with Ubuntu, as long as you install one of the accelerated drivers for it. Wine takes it's cues from the OS, so if the OS can use it, so can Wine.

---

### Post by platypuz on 2007-08-06
> **cogadh said:**
> Practically all Nvidia products run perfectly with Ubuntu, as long as you install one of the accelerated drivers for it. Wine takes it's cues from the OS, so if the OS can use it, so can Wine.

Where would I find this accelerated drivers. Are they the same as the regular drivers? I have never really be very successful at finding drivers so any help in that department would be great.

---

### Post by cogadh on 2007-08-06
The easiest driver packages to deal with are in the Ubuntu repositories; nvidia-glx, nvidia-glx-new and nvidia-glx-legacy packages. For the 5500, you should use either the nvidia-glx or nvidia-glx-new package.

---

### Post by asleepfromtheday on 2007-08-06
Just dont buy an ATI card at the next upgrade, stick to NVIDIA or INTEL...very important. ATI have no interest in their Linux driver development, People have done wonders with the open driver, but it still lags behind the others

---

