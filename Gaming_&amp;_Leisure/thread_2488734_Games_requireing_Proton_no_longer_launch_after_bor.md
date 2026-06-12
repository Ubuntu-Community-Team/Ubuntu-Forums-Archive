---
title: "Games requireing Proton no longer launch after borked Ubuntu upgrade."
date: 2023-07-13
forum: Gaming &amp; Leisure
---

### Post by herorareheart on 2023-07-13
Hello,
I switched my brothers PC over to Ubuntu 23.04 a little while back and it's been running excellently, however recently we had an issue. Yesterday we were playing Risk of Rain 2 and after we finished a run he went to install a system upgrade, everything seemed ok. Upon a reboot however only one display was working and his PC indicated it was using software rendering. After a bunch of troubleshooting, such as trying different NVIDIA driver versions and reinstalling a few graphics related packages, I realized it was an issue surrounding secure boot and driver signing so I decided to just turn off secure boot, afterwards the PC appeared to behave like normal. After that no significant changes were made, if any at all, and he didn't try to play any games.
Today when he tried to play a game, he did not tell me which one, that was already installed and previously working it failed to launch. I advised him to install a Linux native game, he chose Team Fortress 2, and it ran fine. After that I advised him to install a game the required Proton to function, he picked Bloons TD 6, and it wouldn't launch either. I believe something has gone wrong either with the upgrade or we did something during our troubleshooting process that either removed or broke a package/dependency that is required for Proton to function and I am unsure where to go from here. Does anyone have advice on where we should begin to troubleshoot? He is using the Steam snap and his relevant PC specs are roughly listed below;

-One 1TB NVME SSD and one 250GB NVME SSD mashed together w/LVFS
-2x8GB DDR4 RAM
-i5 7600K CPU
-NVIDIA GTX 1080 GPU

I do not recall exactly what we tried when we were troubleshooting after the upgrade but if helpful to include it I can retrace our steps and include what exactly we did.

---

### Post by herorareheart on 2023-07-13
We found an erroneous sources file in /etc/apt/sources.list.d/. Unsure how it got there but after removing it and updating the OS it magically started to work again. No idea if it was that or the updates but it's all good now.

---

