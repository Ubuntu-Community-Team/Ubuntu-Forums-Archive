---
title: "how to get Civ VI working with AMD Radeon graphics?"
date: 2018-03-28
forum: Gaming &amp; Leisure
---

### Post by sgian on 2018-03-28
I have Civ VI and it was working on my desktop with the NVIDIA GT710 and GT610 cards. Unfortunately, I had stability issues between that specific AMD CPU and the NVIDIA cards I believe (regardless of distro), so I put in a Radeon 5450 card to see if it would be more stable with the AMD graphics card. I removed the NVIDIA drivers, reinstalled xorg, installed mesa-utils so far.

The error message is that Civ VI has an unrecoverable error and needs to close.  I then ran steam in terminal, and it says nothing more than the refresh rate.

Specs of the computer
AMD Athlon X4 845 CPU (Carrizo)
MSI A68HM motherboard
8 GB RAM
AMD Radeon R5450 graphics card
Ubuntu 18.04 daily

I know AMD graphics on linux is not officially supported for Civ VI, but I have seen people mention on the internet getting it working on AMD graphics so I was hoping someone would know what to do.

---

### Post by QIII on 2018-03-28
Hello!

Your graphics card, which was an entry-level card for the HD 5000 series to begin with, is no longer supported by anything other than the open source Radeon driver, which may not be capable of supporting your game.  Although that driver is very good for what it is designed to do, it's not really a gamer's dream.

I'm pretty sure that the combination won't be suitable for Steam, either.  When fglrx was available, Steam required that it be used.  Unfortunately, fglrx will not work with the X server that comes with Ubuntu 14.04.2 and later releases.  

Quite simply put, you have a card that is long in the tooth, is not particularly powerful and doesn't have a current driver that is likely to be up to the task.  I'm not sure you can overcome that.

---

### Post by Perfect Storm on 2018-03-29
It's recommandable to get a nvidia for gaming.

---

### Post by kendrick.ong on 2018-04-18
Oh that's why I can't play it, thanks on the advice!

---

