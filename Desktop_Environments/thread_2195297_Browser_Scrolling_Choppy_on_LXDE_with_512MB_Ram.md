---
title: "Browser Scrolling Choppy on LXDE with 512MB Ram"
date: 2013-12-23
forum: Desktop Environments
---

### Post by genivasla on 2013-12-23
I'm using Chromium on a LXDE Desktop. Pages load fast, but the scrolling is lagging and pretty choppy. I've tried enabling GPU Composition and Threaded Composition in Chromium, which seemed to help a little bit. Any other tips?

---

### Post by Bucky Ball on 2013-12-23
What are you using lxde desktop on? Ubuntu?

---

### Post by genivasla on 2013-12-23
Yes, Ubuntu.

---

### Post by Bucky Ball on 2013-12-23
Well, that is not going to run well on 512mb of RAM, even though that is stated as a minimum system requirement, if at all, regardless of the desktop environment you're using. 

Try installing Lubuntu or Xubuntu. There are lighter ones also. 

Have you got the correct video drivers installed? Please give the output of this:

```
sudo lshw -C video
```

---

### Post by genivasla on 2013-12-23
Hey Bucky Ball, I guess the low RAM is probably the case. I thought LXDE was lighter than those two options, but I'll give them a try.

The code your provided got Command Not Found.

Edit: I tried on a VPS with 1GB of RAM and same issue. XFCE wasn't any better.

---

### Post by Bucky Ball on 2013-12-23
> **genivasla said:**
> 
The code your provided got Command Not Found.



? That is mighty strange. You should be seeing something like this:

```
*-display               
       description: VGA compatible controller
       product: RV710/M92 [Mobility Radeon HD 4530/4570/545v]
       vendor: Hynix Semiconductor (Hyundai Electronics)
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=fglrx_pci latency=0
       resources: irq:46 memory:c0000000-cfffffff ioport:4000(size=256) memory:d6000000-d600ffff memory:d6020000-d603ffff

```

Not sure what you mean when you say you tried it on a VPS with one gig of RAM, but thinking we need to have a look at your card and driver as this is another likely cause. Have you got any graphics drivers enabled in 'Additional Drivers'?

---

### Post by genivasla on 2013-12-23
That's my mistake... I left out an important point. This is a desktop environment on Ubuntu server that I access with VNC. I'm not seeing in LXDE how to view installed drivers and it's probably likely that there isn't a graphics card installed on the machine.

---

### Post by genivasla on 2013-12-23
With chromium running I'm using 250 of the 512 RAM. I also noticed that when I change the color depth of the VNC Viewer from 16 bits to 8, things move much faster. Scrolling is normal. I checked bandwidth and everything is solid there. Is this just the nature of VNC or is it possible to get the 8 bit performance with 16 bit color depth?

Also, increasing RAM to 1gb did not seem to make any improvements. Minor, if anything.

---

