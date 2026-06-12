---
title: "Minecraft (1.13.2, 1.14.1) freezing Ubuntu 18.04 (NVIDIA GT 730 with Nouveau)"
date: 2019-05-27
forum: Gaming &amp; Leisure
---

### Post by temmokan on 2019-05-27
I know this question re-emerges from time to time, but perhaps someone will recommend what to try to handle that.

After recent updates (I use Ubuntu 18.04 64-bit desktop, default Gnome environment, all latest updates) I noticed that Minecraft (Java Edition) began to sporadically freeze Ubuntu system.

Looks like it only freezes GUI, since I can log on to the system via SSH from another computer, kill the application and reboot the system without data loss. However, this is extremely annoying and I would like to handle it somehow.

I use NVIDIA GT 730-based video card and default ("Nouveau") driver for it.

What I tried with only partial success:
- I tried bundled Java, external Oracle Java 8 and OpenJDK Java 11 - no visible difference
- tried raising FPS parameter  in Minecraft video settings - partially helped, game stopped freezing when there were too many mobs nearby
- tried switching Vsync on and off - no difference

I would appreciate pieces of advice on this. Game may run for hours without problems, but may freeze in a few minutes (I can't say what exactly triggers the problem).

---

### Post by mastablasta on 2019-05-27
i would install the nvidia drivers from the repositories. with them you can run also some other things (oblivion, skyrim, Portal, Team Fortress 2, half life 2, left4dead...).

when you SSH into computer you can check what is happening and why GUI crashed (htop, logs...) and also the temperature (lm sensors...).

i am running old Single core CPU with GT 730. newer minecraft versions run a bit slow. but i think it's the CPU's fault, because the game is not that graphically intensive. plus there is same issue on windows side of the disk drive.

---

### Post by oldrocker99 on 2019-05-27
To install the official Ubuntu nVidia drivers, do NOT download them from nVidia's website. Do this:```
sudo add-apt-repository ppa:graphics-drivers/ppa
sudo apt update
sudo apt install nvidia-390
```
Reboot, and you'll be all set. Only nVidia requires proprietary drivers, and they are **much** better than the open-source Nouveau drivers.

The opposite is true of AMD/ATI cards, because the open-source radeon driver is top-notch. Intel graphics drivers have always been open-source.

---

