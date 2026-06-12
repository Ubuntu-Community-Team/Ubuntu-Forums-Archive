---
title: "2 problems for a new Ubuntu user"
date: 2008-12-27
forum: General Help
---

### Post by Cudaa on 2008-12-27
Ok 1 major problem and 1 minor, I did a dual boot install with XP media edition, now when running Ubuntu 8.10 my Microsoft Intellimouse Explorer 3.0 crashes while moving scroll bars, the pointer will stop moving but the laser light will stay on, unplugging and repulgging the USB wire results in a light out situation, it's like the USB port isn't supplying power anymore.
Second issue is the volume control slider resets to 3/4 full on restart, any way to fix that? I'm not sure what info to give other than the computer is a Velocity Micro running a Intel Core 2 Duo processor E6400, Nvidia Nforce 570 SLI motherboard and a 256 MB Geforce 7600 GS video card. I installed all the updates Ubuntu said I needed, thanks for any input.

---

### Post by SuperSonic4 on 2008-12-27
1. Could be hardware, does any other mouse have the same effect? I believe mouse settings are handled by xorg.conf

2. Open a terminal and type: ```
alsamixer
``` and move them up to the top and press Esc to quit, no idea if it'll work though xD

---

### Post by m_duck on 2008-12-27
After changing the volume controls in alsamixer, to make it persistent, I think you also need to run:```
sudo alsactl store
```

---

