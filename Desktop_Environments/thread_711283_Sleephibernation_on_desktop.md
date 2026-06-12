---
title: "Sleep/hibernation on desktop"
date: 2008-02-29
forum: Desktop Environments
---

### Post by Staach on 2008-02-29
I know a lot of users has problems with sleep/hibernation on their laptops. However, my sleep/hibernation problem is on my desktop! Can any one help me getting sleep and hibernation workin?
MB: A8R-MVP
RAM: 2 GB
Graphics: Nvidia 6600 
SW:
7.10 Gutsy
Kernel 2.6.22-14-generic

---

### Post by spupy on 2008-02-29
Try these commands (as root):
```
echo -n "disk" > /sys/power/state
```
It starts hibernation on my PC. Replace "disk" with "mem" for suspend. 
I'm not sure if it will work, tho. Don't hold on me if it doesn't! ;) (Better yet, wait for someone else to confirm these commands. In some cases, they may be harmful, i.e. it wont boot.)
This is just one of the ways of doing suspend/hibernation. There are others, but i don't know them since i don't use them.

---

### Post by Staach on 2008-03-06
Well..for sure it wasn't the trick on my pc..It gave a lot of blinking, different collored ascii characters. But I just found out that my pc actually can start "sleep" by itself. Now I only need it to go into hibernation..Can someone help? Please.

---

