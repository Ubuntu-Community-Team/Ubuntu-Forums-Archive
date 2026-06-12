---
title: "Game runs slowly on ubuntu"
date: 2019-10-19
forum: Gaming &amp; Leisure
---

### Post by nibz-au on 2019-10-19
Im on a gaming laptop of which ive installed ubuntu
when i try to play the game 7 days to die, it is really slow and laggy almost like its ignoring my nvidia 1050 and trying to use the onboard graphics

how can i tell if my graphics are being used correctly

---

### Post by deadflowr on 2019-10-19
*Thread moved to **Gaming and Leisure***

---

### Post by oldrocker99 on 2019-10-19
If you get into the BIOS, the onboard graphics may enabled, instead of the nVidia. That's all I can think of.

---

### Post by CatKiller on 2019-10-20
Unless you've installed the proprietary driver and set things up to use your NVidia device, it can't be used.

Optimus setups are a pain. You may find that [the nvidia-optimus panel applet](https://www.omgubuntu.co.uk/2019/09/nvidia-optimus-linux-switching-applet) makes things easier.

---

### Post by zimbuf on 2019-10-21
As CatKiller pointed out, Ubuntu doesn't have the proprietary driver enabled by default. Specifically, this is true for versions prior to 19.04. To help resolve this issue, try opening "Additional Drivers" from your start menu. Select the latest NVIDIA driver you see once it finishes loading. After this, you may need to restart. This should enable the NVIDIA driver. Let me know if you have any problems.

---

### Post by owenhe on 2019-10-25
Then it's better to play single player games, so there's no software problem.

---

