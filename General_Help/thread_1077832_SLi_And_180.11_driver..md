---
title: "SLi And 180.11 driver."
date: 2009-02-22
forum: General Help
---

### Post by elli222 on 2009-02-22
I recently got two brand new shiney 280 GTX NVIDIA graphics cards from ASUS. They work really well!

Originally SLi (Scalable Link interface) worked with the 177 drivers, but with these new drivers, it fails with this in my Xorg log:
 ```
(EE) NVIDIA(0): Failed to find a valid SLI configuration.
(EE) NVIDIA(0): Invalid SLI configuration 1 of 1:
(EE) NVIDIA(0): GPUs:
(EE) NVIDIA(0):     1) NVIDIA GPU at PCI:4:0:0
(EE) NVIDIA(0):     2) NVIDIA GPU at PCI:5:0:0
(EE) NVIDIA(0): Errors:
(EE) NVIDIA(0):     - Chipset not approved for SLI
(WW) NVIDIA(0): Failed to find a valid SLI configuration for the NVIDIA
(WW) NVIDIA(0):     graphics device PCI:4:0:0. Please see Chapter 25:
(WW) NVIDIA(0):     Configuring SLI and Multi-GPU FrameRendering in the README
(WW) NVIDIA(0):     for troubleshooting suggestions.
(EE) NVIDIA(0): Only one GPU will be used for this X screen.
```

I have it configured with nvidia-xconfig --sli=auto and added BusID "PCI:4:0:0" to the device section so i could actually use X

Any idea what's wrong? I really want SLi enabled!

My xorg.conf is attached. Please help me!

Oh, and seeing this be Chipset related, here is my mother board model:
ASUS M3N-HT Deluxe/Mempipe
It is supposedly capable of 3-way SLi

I have searched for a while and found nothing, so i thought i would come here for help.

---

### Post by elli222 on 2009-02-22
After tonnes of forced package removals, dodgey repos, driver conflicts, and 5 reboots, i found the problem...

nothing to do with drivers, hardware, but a workaround for another driver bug i installed.

i added this to modprobe.conf:

options nvidia NVreg_RegistryDwords="PerfLevelSrc=0x2222"
options nvidia NVreg_Mobile=3

fixes a flickering issue. Completly brakes SLi.

If i could get the two working together, that would be sweet!

Linux4Life!

---

### Post by singedwings on 2009-02-23
I have an asus p6t deluxe. If your board is one with three pci-e ports then the graphics cards should probably be in the top two slots.

```
(EE) NVIDIA(0):     1) NVIDIA GPU at PCI:4:0:0
(EE) NVIDIA(0):     2) NVIDIA GPU at PCI:5:0:0

```

This to me suggests they are in the bottom two. The bottom slot is for when there are three graphics cards.

---

### Post by elli222 on 2009-02-23
they are as far away from one another as possible, and in between is a SCSI card with a ribbon cable connecting it to a tape drive.

There is a onboard graphics card, with 3D accel, mainly for HDMI/Hybrid SLi

dunno if there in the right places, but they work fine, and SLi also works.

Just now i have a flickering when my system isnt doing much!

---

