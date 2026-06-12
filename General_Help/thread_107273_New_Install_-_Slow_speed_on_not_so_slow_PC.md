---
title: "New Install - Slow speed on not so slow PC"
date: 2005-12-22
forum: General Help
---

### Post by M3G4 on 2005-12-22
Okay okay I lied a bit in the title but hey...

I've just acquired a system with not-so-bad specs - they are:
- AMD Duron 1GHz
- 192MB RAM
- 40GB HDD
- 24x CD
- O/B Gfx and Sound (8MB assigned to GFX)

I've just installed a copy of Ubuntu onto it and damn does this thing crawl. It's taking ages to render windows and things - well, alot slower than the click-boom actions that I'm used to when running WinXP on it.


Any ideas what I can do to speed this up? It's really crawling, and the system specs can't be that bad? I though linux was meant to be better for slower machines than windows... lol :)

Cheers

---

### Post by Perfect Storm on 2005-12-22
You need to install correct kernel and graphic driver. I'm not sure which driver a GF onboard uses.

To install correct kernel.
Open the terminal (**Application** tab ---> **Accessories** ---> **Terminal**
and write:

```
sudo apt-get install linux-k7
```

accept the extra packeges it asking for.

reboot.

---

### Post by ViGiLnT on 2005-12-22
What about a p3 900mhz ?

---

### Post by M3G4 on 2005-12-23
Hey,

Thanks for the advice, it's downloading now.

I was wondering where I can get the graphics drivers? It's an S3 ProSavage KM133 AGP chipset. Can I just search google for drivers?

---

