---
title: "Everything Crashes! Ubuntu 8.10"
date: 2009-04-09
forum: General Help
---

### Post by ForMar on 2009-04-09
I have no idea what is going on by every program is crashing on me. It either goes gray until It asks me to force quit, or disappears but never really closes. This is causing hangs during shut down forcing me to manually shutoff the computer. I checked a few of the logs and found a few errors but I have no idea what they mean or if they are related at all. (errors are at end of post)
To give you an idea I mostly use a VM running windows XP , firefox, and Rhythmbox. Not much else. They all crash (firefox the most) and I have also recently been having a lot of audio issues not sure if thats related at all. 

Errors:
Apr  8 19:11:16 toaster kernel: [19503.694650] compiz.real[6269]: segfault at 335f ip 08055c8c sp bfa4b6c0 error 4 in compiz.real[8048000+34000]
//this has repeated a few times , in message log

Apr  5 00:54:07 toaster kernel: [  532.958035] lost page write due to I/O error on sdc1
// this one was in the kern.log, again not sure what is going on, I would guess something with the HD but I dont know :(

Thanks for any help!

---

### Post by khelben1979 on 2009-04-09
Okay, I'm thinking of 2 things:

1. Your computer probably have hardware faults which is causing the Ubuntu system to behave unstable.
2. The Ubuntu Linux kernel don't like your computer hardware.

What computer configuration do you have and how old is it?

---

### Post by ForMar on 2009-04-09
Its about a year and a half old:

 	
-eDimensional AudioFX Pro 5+1 USB (headset)
-COOLER MASTER Real Power Pro RS-650 (power supply)
-EVGA GeForce 8800GTS (G92) 512MB 256-bit GDDR3 (Video Card)
-LITE-ON 20X DVD±R DVD Burner with LightScribe (rm drive)
-Intel Core 2 Duo E8400 Wolfdale 3.0GHz LGA 775 (CPU)
-Seagate Barracuda 7200.10 250GB 7200 RPM SATA 3.0Gb/s (HD)
-ASUS MAXIMUS FORMULA LGA 775 Intel (mobo)
-Patriot Viper 4GB (2 x 2GB) 240-Pin DDR2 SDRAM DDR2 1066 (PC2 8500)

Hope this helps

---

### Post by khelben1979 on 2009-04-09
Have you ever tried looking inside? Maybe some fans is filled with dust which causes overheating? 

Anyway, that's pretty good stuff. Too much heat inside the case is a classic. I recommend that you take a look.

---

