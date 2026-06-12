---
title: "Desktop not working after wakeup from sleep"
date: 2015-08-31
forum: Desktop Environments
---

### Post by Alberto_Taiuti on 2015-08-31
Hello everyone,

I have recently installed Lubuntu 14.01 on my Dell Latitude E5450, of which the specs are:
- Intel Core i7-5600U CPU
- Intel HD Graphics 5500 Integrated GPU
- Nvidia GeForce 840M GPU
- 8 GB RAM
- 256 GB SSD

The installation completes fine; I have created 3 partitions for these mount points/swap: swap, /home, and / (root).
After installation, the system works fine apart from one thing: when I use the xorg drivers, or the nvidia ones with the Intel integrated GPU selected, my system doesn't recover after setting it into sleep mode. Instead, if I am using the Nvidia drivers with the Nvidia GPU selected, this problem is not reproduced.

I have attached some screenshots showing my drivers configuration, but what I mean by that is: when the system boots up from a shutdown, I am presented with the login splash screen, and I can login, then use my system normally, using the Intel GPU (after selecting the Intel GPU from the nvidia GUI manager):

[ATTACH=CONFIG]264128[/ATTACH][ATTACH=CONFIG]264129[/ATTACH][ATTACH=CONFIG]264130[/ATTACH]

If then I set the system into sleep mode, when I wake it up the GUI is all messed up and the only visible and working thing is the mouse pointer; the OS is still working below the mess: if I manage to click on the right buttons (even though I have no idea what I am clicking on as the GUI is all messed up and doesn't load) the system will perform the action, but it looks as if the OS stops from further loading the GUI as the more I move the mouse, the more it disappears.

I have managed to take a screenshot of what it looks like when this reproduces:

[ATTACH=CONFIG]264127[/ATTACH]

I had previously installed Lubuntu 15.x but since I could not find a solution, I thought to give a try to the LTS version. However, the issue is still there.

Thanks in advance to everyone, and if you need me to paste any logs/info don't hesitate to ask.

---

### Post by timotheus3 on 2016-01-14
my old acer laptop never wakes up. my IBM x Server dosent seem to want to sleep at all.. both running lubuntu, maybe report a bug? i should also

---

