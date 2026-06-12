---
title: "Unity sidebar help!!!!!"
date: 2011-04-29
forum: Desktop Environments
---

### Post by bzzman on 2011-04-29
I upgraded from 10.10 and I love Unity. But, in the sidebar, there are no icons. The sidebar is there, but no icons. If I roll over where the icons should be, the text displays. This is getting annoying and I can't find anything wrong with my system. Help!!!

Thanks in advance,

Bzzman

---

### Post by mc4man on 2011-04-29
you may be affected by this bug (are you using the 173.... nvidia drivers?
[https://bugs.launchpad.net/ubuntu/+source/nux/+bug/768178](https://bugs.launchpad.net/ubuntu/+source/nux/+bug/768178)
Maybe post what your vidoe card is

```
sudo lshw -C display
```

---

### Post by bzzman on 2011-04-29
I am using an NVIDIA GeForce FX 5100. I have tried the 173 driver, but. When Unity loaded, the icons flashed and disappeared, and the sidebar did not load at all. So I tried the experimental drivers for it, and everything was fine. Then, I noticed that the sidebar icons were not there. Everything else in Unity works seamlessly. No missing icons or anything. I will try the code.

---

### Post by bzzman on 2011-04-29
Ok, so here's EXACTLY what I got from running the code:

  *-display                             
       description: VGA compatible controller
       product: NV34 [GeForce FX 5100]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 32 bits
       clock: 66MHz
       capabilities: pm agp agp-3.0 vga_controller bus_master cap_list rom
       configuration: driver=nouveau latency=64 maxlatency=1 mingnt=5
       resources: irq:18 memory:f1000000-f1ffffff memory:f4000000-f7ffffff memory:f8000000-f801ffff

---

### Post by mc4man on 2011-04-29
here's the no icon in launcher bug for the nouveau 3d drivers
[https://bugs.launchpad.net/unity/+bug/762478](https://bugs.launchpad.net/unity/+bug/762478)

So Atm neither is going to work right

---

### Post by bzzman on 2011-04-29
Ok, I found the next best thing. Unity 2D. Actually faster than GNOME. REALLY like it. Same thing as 3D, but without the 3D. I don't notice any major changes. Ah well. We tried.

---

### Post by mc4man on 2011-04-29
I gather from those 2 bugs that unity 2d will be the recommend for those type cards, ck. them once and a while to see if there was a fix for either or both.
(or you may decide the 2d is best for that hardware..

---

