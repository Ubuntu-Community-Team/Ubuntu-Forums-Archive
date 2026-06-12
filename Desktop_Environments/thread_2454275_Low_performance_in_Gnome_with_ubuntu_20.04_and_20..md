---
title: "Low performance in Gnome with ubuntu 20.04 and 20.10"
date: 2020-11-26
forum: Desktop Environments
---

### Post by buburcito on 2020-11-26
I have tested both 20.04 and 20.10 and in both I see how the movements and animations are not smooth. However under windows it works perfectly.
I install the Nvidia drivers in Ubuntu (I have also tried the free drivers) with bad results.
My laptop has an intel that it uses when it doesn't need a lot of power and a GF940MX when it needs something more.
Laptop model is Huawei Matebook with i7, 16Gb DDR4 GF940MX, 256Gb SSD
Any ideas?. 
Thanks a lot.

---

### Post by ajgreeny on 2020-11-26
How did you install the nvidia drivers?

As this is your first post I wonder if you downloaded them from the nvidia website, which is not the way to do this in Ubuntu.
You should go to Additional Drivers from the Activities menu system and install whichever is the recommended driver from there; direct downloads from nvidia will often cause problems whereas those from Additional Drivers  are built specially for Ubuntu and usually work much better.

I am also aware that there are difficulties with Optimus dual graphics systems which used to need bumblebee. I believe this is now much better handled but have no experience of this having never used an nvidia graphic system; nor do I know if your setup is one of the Optimus graphics type.

---

### Post by CelticWarrior on 2020-11-26
This ^^^ and also disable Secure Boot in UEFI.

---

