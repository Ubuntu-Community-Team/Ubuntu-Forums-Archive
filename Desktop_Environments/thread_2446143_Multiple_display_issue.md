---
title: "Multiple display issue"
date: 2020-06-25
forum: Desktop Environments
---

### Post by conniemalan on 2020-06-25
Hardware
Processor: AMD Ryzen 3 3200g with radeon Vega graphics
Graphics: Nvidia Geforce GT630 Rev2
Memory: 16Gb


When running from the live CD Ubuntu 20, all 3 of my displays work, the graphics driver NV108 / AMD Raven

After installation only the on-boards graphics card's monitor works, the graphics driver NVIDIA Geforce GT630 rev2

How do I get all 3 monitor to work ?

BTW: all 3 monitors work in Linux Mint

---

### Post by LongH on 2020-06-25
I fixed it! 

Just had to run
xrandr --output eDP-1-1 --mode 1920x1080 --output HDMI-1-2 --pos 1920x0 --mode 1920x1080

I think my frame buffer was too large.

---

