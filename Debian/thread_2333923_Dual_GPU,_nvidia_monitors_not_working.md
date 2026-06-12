---
title: "Dual GPU, nvidia monitors not working"
date: 2016-08-14
forum: Debian
---

### Post by gremious on 2016-08-14
Okay, so I have an AMD and an NVidia card, AMD housing one monitor and NVidia 2.
I installed the NVidia driver as the debian wiki said, through jessie-backports seems like there was no errors.
I'm running the most recent Debian Jessie stable release with non-free.
The AMD monitor and card work perfectly fine.

The 2 monitors connected to the NVidia card are not working and not detected. I would like to know how to make them work, please.
Thank you.

here's the lshw if needed.
```
*-display               
       description: VGA compatible controller
       product: Hawaii XT [Radeon R9 290X]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:89 memory:b0000000-bfffffff memory:c0000000-c07fffff ioport:e000(size=256) memory:fe400000-fe43ffff memory:fe440000-fe45ffff
  *-display
       description: VGA compatible controller
       product: GF106 [GeForce GTS 450]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:28 memory:fc000000-fdffffff memory:c8000000-cfffffff memory:d0000000-d3ffffff ioport:d000(size=128) memory:fe000000-fe07ffff


```
Gnome does the "Oh no! Smething has gone wrong!" and is unusable but  xfce works fine, if you guys knows for a fix to that it would be nice  but that's not my main concern.

If I install and run the nvidia-xconfig, after reboot it just breaks the x-server and does the blank screen with a blinking "_" and I have to remove it and re-install to make it work again.

---

