---
title: "Sound device not detected after kernel upgrade"
date: 2009-04-08
forum: General Help
---

### Post by Zeedok on 2009-04-08
I have a new Mythbuntu system (+Ubuntu desktop) with the following specs:

```
Antec Micro Fusion 350 HTPC Case
Intel Core 2 Duo E8400 CPU 3.0 GHz
Gigabyte GA-EG41M-S2H Mainboard
4GB DDR2 PC6400 (2x2GB) Dual Channel RAM
8X Dual Layer DVD+RW + 20X DVD+-RW + CD-RW Combo Drive
1TB 7200RPM SATA HDD
512MB NVIDIA Geforce 8400GS
Gigabit Ethernet
Hauppauge Nova-T-500 MCE Dual DVBT SD/HD tuner
```

I upgraded today to the latest kernel which was just pushed out and now the "Sound" configuration window and the volume panel app say that my sound card (Intel HDA  . . .) is not detected.  Even when  I select the "Autodetect", "ALSA" or any other option I just get an error message.

I don't even know how to start working out where the problem is.  I'd be grateful for any pointers and help.

PS I didn't build the system, I am not sure whether the guy who did (I've emailed him) had to customise any drivers or files - maybe something he did was broken by the kernel upgrade.

---

### Post by klemes on 2009-04-08
I had the same issue exactly with the same sound card except it was on a generic i386 kernel system (not a server).It was promptly solved when I manually apt-get installed the corresponding kernel modules for my kernel
(sudo apt-get install linux-ubuntu-modules-2.6.24-24-generic or something like that I think).Then on next reboot sound was working fine again...

---

### Post by Zeedok on 2009-04-09
I eventually solved this by installing the latest alsa-driver.  [There are terrific instructions on how to do this here]("http://www.linlap.com/wiki/configuring+the+audio+and+updating+alsa+for+ubuntu+8.10").

---

