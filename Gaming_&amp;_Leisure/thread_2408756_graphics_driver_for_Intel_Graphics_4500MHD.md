---
title: "graphics driver for Intel Graphics 4500MHD"
date: 2018-12-22
forum: Gaming &amp; Leisure
---

### Post by lukesmiththree on 2018-12-22
Hello. I am very new to linux, and I have a 2008 HP Notebook G60 with an intel graphics media accelerator 4500MHD. I have tried to open War Thunder in steam (on Lubuntu and Manjaro) and with the files downloaded from warthunder.com (on Lubuntu, Manjaro, and Ubuntu.) On each of the listed systems, I have gotten an error window that tells me my "Your video card or it's driver may not be supported. Be sure to install the best driver and try again." So I tried installing different drivers on Manjaro and Lubuntu, and both times the screen would work during boot up, but right before the login screen was shown, the screen would go black. I am not sure which drivers I installed. I was forced to load a different OS because I couldn't find a way to open the terminal without the screen. I tried logging in a minute after the screen went dark, then waiting 30 seconds, and doing ctrl+alt+T (which normally opens a terminal) waiting 15 seconds, typing "sudo reboot"(which worked before I tried the new driver) waiting 5 seconds, and typing my password. Nothing happened. I tried this several times, each with different times between operations and all ending with the same result: nothing. After trying to open war thunder in Ubuntu, (I haven't tried steam yet, but the tar.gz file from warthunder.com kicked the same error report as that in previous systems and in steam did) I decided to try playing an online game. ([Shellshockers]("http://shellshock.io")) It ran at 400 ping and 2 FPS. On my chromebook it ran just fine. (between 5 and 50 ping, and about 30FPS. My chromebook has 4gb RAM, dual core@1.6GHZ and integrated graphics.) I was wondering if anyone knows of a driver that will solve my graphics cards problems or if I need to get a new graphics card. Thank you!

Note: my HP notebook G60 has an intel pentium t4200(dual core @ 2.00 GHZ), and 3GB RAM(500MHZ, I think)

---

### Post by CatKiller on 2018-12-22
The drivers for Intel graphics are included in the kernel. You don't need to install anything else. You have potentially made things worse by trying to.

The Linux version of War Thunder on Steam doesn't say that it works with Intel graphics. 

> NVIDIA 660 with latest proprietary drivers (not older than 6 months) / similar AMD with latest proprietary drivers (not older than 6 months; the minimum supported resolution for the game is 720p)

---

### Post by lukesmiththree on 2018-12-22
So that means that no matter what graphics driver I use, War Thunder won't run? I will have to get a new graphics card?

---

### Post by CatKiller on 2018-12-22
I couldn't say about that game in particular. I'd never heard of it before. Other versions of the game say they can run on Intel graphics, so there might be something specific that could be done - maybe a newer kernel or whatever. The game's developers might tell you where the issue is.

---

### Post by lukesmiththree on 2018-12-23
What do you mean by "newer kernel"? I think that War Thunder stopped supporting Intel Graphics on version 1.6.3, and is now on 1.8.5. I don't know of a way to download a previous version.

---

### Post by CatKiller on 2018-12-23
> **lukesmiththree said:**
> What do you mean by "newer kernel"? I  think that War Thunder stopped supporting Intel Graphics on version  1.6.3, and is now on 1.8.5. I don't know of a way to download a previous  version.

The part that is Linux is the kernel. That's the part that communicates with the hardware. It's changing all the time as things get improved. The drivers for Intel graphics are part of the kernel, so newer versions of the drivers come with newer versions of the kernel.

From what you've said, though, it seems that the game developer has decided to make the game not work on Intel graphics, no matter how capable they are, so there's nothing that can be done.

---

### Post by lukesmiththree on 2018-12-29
OK. Thank you for your time.

---

