---
title: "Presario V3010US network and sound issues"
date: 2006-08-03
forum: Desktop Environments
---

### Post by fieldstone on 2006-08-03
Hi, everyone. I just recently (yesterday) picked up a Compaq Presario V3010US computer; it blazes with its Turion 64 X2 processor, though trying to get Ubuntu AMD64 working properly was a nightmare, so I'm back to 32-bit Ubuntu with the K7 kernel image installed.

I've had a few minor issues, though, that I'm hoping someone might be able to help me with. First of all, there doesn't seem to be any way to get the Broadcom 4311-based internal network card to work with ndiswrapper or bcm43xx; I've tried it, using all the support documents I could find, but no luck.

Secondly - My headphone jack doesn't work. Since I have an nForce sound card, I tried installing nvsound (also with a whole bunch of support documents that told me what lines to insert into various files), but still no luck. Would upgrading ALSA have any chance of helping with this? Or is there some other kind of hack I can use to get my headphone jack working?

---

### Post by bigwill_012 on 2006-09-12
I also have the Presario v3010us and was able to get wireless going with ndiswrapper.What i had to do was actually go into wi@$wsXP to the system32 files and copy the .INF and >SYS driver files for the wireless card to a CD after i had those just use ndiswrapper to load drivers and ALL WAS GOOD!!!:biggrin:

---

### Post by fooblah on 2006-10-30
There is now a wiki for V3000 series and other hp laptops at:

[http://hpwiki.cactii.net/hpwiki/Presario_V3%2A%2A%2A]("http://hpwiki.cactii.net/hpwiki/Presario_V3%2A%2A%2A")

We are trying to pool all the specific problems and solutions in one place so check it out and update with fixes as they are found.

thanks.

---

