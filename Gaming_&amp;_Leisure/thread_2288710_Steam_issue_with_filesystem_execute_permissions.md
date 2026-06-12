---
title: "Steam issue with filesystem execute permissions"
date: 2015-07-29
forum: Gaming &amp; Leisure
---

### Post by radoslavfatura7 on 2015-07-29
Hey there.

I used Steam since January without issue, and today this popped at me:

[B]new steam library folder must be on a filesystem with execute permissions
[/B]I have only one hard drive partitioned like this:
sda1 /
sda2 swap
sda2 home

I I can't play or install anything.
I haven't done any disk operations or anything related to FS.

My HW:
[B]Type: Laptop 
Brand: Acer 
Model: Aspire E1-571G 
OS: Ubuntu 14.04 LTS 64bit 
CPU: Intel Core i3-2328M (2.2 GHz, 3MB L3 cache) 
GPU: NVIDIA 620M (1 GB VRAM) 
Display: 15.6" HD LED LCD 
RAM: 6 GB 
HDD: SAMSUNG Spinpoint M8 (750 GB) [/B]

---

### Post by usr2 on 2015-07-29
The kernel upgrade did this.

Until a fix is pushed out you can select the previous kernel to boot into.

---

### Post by radoslavfatura7 on 2015-07-29
Thanks, it works :)

One thing: Don't you know, why or how this happened, what's the cause or change in the kernel?

---

### Post by Aikar on 2015-07-29
Well this sucks... I just updated my nvidia drivers from 331 to 352 and this update went along with my reboot. I also did an old kernel cleanup too.... rolling back kernel would of been a pain to use new driver anyways :/

this sucks.. 

Is it a kernel bug or a steam bug?

---

### Post by Aikar on 2015-07-30
Per - [https://github.com/ValveSoftware/steam-for-linux/issues/3936](https://github.com/ValveSoftware/steam-for-linux/issues/3936) - issue fixed with -61 kernel.

---

### Post by radoslavfatura7 on 2015-07-30
Thanks for the info.

I can confirm the broken WINE too :/

---

