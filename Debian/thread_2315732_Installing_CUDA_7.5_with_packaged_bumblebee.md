---
title: "Installing CUDA 7.5 with packaged bumblebee"
date: 2016-03-02
forum: Debian
---

### Post by ljungkvist on 2016-03-02
Technically, I'm running Debian, but since it is about apt dependencies etc I think it is still relevant for Ubuntu.

My laptop, which runs Debian Jessie, has switchble graphics cards (intel + Nvidia GT 520M), and for this I have installed Bumblebee & Primus, which depends on the Nvidia driver in the package manager. Now I need to install CUDA 7.5, and therefore need a more recent driver (the newest one is still only from CUDA 7.0). However, to install the one bundled with CUDA, I need to remove the one from the package manager, which is not allowed due to the dependency. How can I make the packaged bumblebee work while using a non packaged driver?

---

