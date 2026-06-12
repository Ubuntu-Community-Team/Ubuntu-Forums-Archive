---
title: "AMD Radeon M375 on Ubuntu Bionic Beaver 18.04.2"
date: 2019-09-02
forum: Gaming &amp; Leisure
---

### Post by v1p3r00 on 2019-09-02
I have serious problems with my graphics card under Ubuntu 18.04.2., I did my research,tried various installs of amdgpu, amdgpu-pro, xorg but nothing really worked. The dedicated graphics on my Lenovo Z51-70 just isn't working, it uses my integrated graphics for games too.

```
lshw -c video   *-display
description: VGA compatible controller       product: HD Graphics 5500       vendor: Intel Corporation       physical id: 2       bus info: pci@0000:00:02.0       version: 09       width: 64 bits       clock: 33MHz       capabilities: msi pm vga_controller bus_master cap_list rom       configuration: driver=i915 latency=0       resources: irq:49 memory:d0000000-d0ffffff memory:c0000000-cfffffff ioport:5000(size=64) memory:c0000-dffff  *-display       description: Display controller       product: Venus XTX [Radeon HD 8890M / R9 M275X/M375X]       vendor: Advanced Micro Devices, Inc. [AMD/ATI]       physical id: 0       bus info: pci@0000:04:00.0       version: 81       width: 64 bits       clock: 33MHz       capabilities: pm pciexpress msi bus_master cap_list rom       configuration: driver=radeon latency=0       resources: irq:50 memory:b0000000-bfffffff memory:d1000000-d103ffff ioport:3000(size=256) memory:d1040000-d105ffff
```

---

### Post by guiverc on 2019-09-02
also asked via [https://askubuntu.com/questions/1170390/amd-radeon-m375-on-ubuntu-bionic-beaver-18-04-2](https://askubuntu.com/questions/1170390/amd-radeon-m375-on-ubuntu-bionic-beaver-18-04-2)

---

### Post by QIII on 2019-09-02
v1p3r00:

Please use the default font and color unless you have a particularly pressing reason to draw attention to a particular part of your post.

Also, please enclose all terminal commands and results in code tags.  That will preserve formatting.  Unfortunately, you didn't do that and adding code tags will not automatically do that.

You would do yourself a favor if you issued the command again, then pasted the results between the code tags I have added.

---

