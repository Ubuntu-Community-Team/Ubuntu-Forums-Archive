---
title: "Resolution problems (driver??)"
date: 2007-05-14
forum: Desktop Environments
---

### Post by makiroll on 2007-05-14
hi! funny story really..

My GF bought a new spanking 17" widescreen 64bit AMD Acer Aspire 9300, got really annoyed with vista and asked me to try install linux on it for her.

so, reaching for a copy of my beloved ubuntu I installed it (6.06 Dapper drake) but the resolution wont change from the standard presets to her actual resolution (1440 900?).

She has a Nvidia graphics driver (although without the computer here its hard for me to ascertain which it is).

anyways. I have tried to sort out the nvidia and tinker with the xorg.conf but everytime it just crashes the X server and I have to reinstigate the xserver.

...and its getting tiresome.

I'm still rather new to linux and not the best of geniuses but would really appriciate the help before she gets pissed off with ubuntu and goes back to using Vista!!

---

### Post by reacocard on 2007-05-14
Have you tried feisty? It might work better since its a newer computer.

---

### Post by starcraft.man on 2007-05-14
Ummm, well I'm pretty sure you can run in the terminal (Applications > Accessories > Terminal):

```
sudo dpkg-reconfigure xserver-xorg
```

Then follow through the prompts until you get to the screen section, you can manually choose to add that resolution if its not automatically detected. That should do it, I think. Its a handy command to have, keep it close :)

---

