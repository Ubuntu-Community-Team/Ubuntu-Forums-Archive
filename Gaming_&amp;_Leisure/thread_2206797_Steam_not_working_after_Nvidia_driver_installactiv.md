---
title: "Steam not working after Nvidia driver install/activation"
date: 2014-02-20
forum: Gaming &amp; Leisure
---

### Post by tyrel3 on 2014-02-20
Ok. So steam was working ok until I activated a driver for my video card because I thought that would make things better (is that a bad assumption? sorry I am such a noob to all of this.)

I restarted my compy  and then I tried opening steam and it said the OpenGL GLX was not supported on this display. 

Any assistance would be amazing. Thank you.

---

### Post by dannyboy79 on 2014-02-20
can you tell us what gfx card you have and what drivers you installed?
this will tell us that information
```
sudo lshw -C display
```
paste the output of running that command within a terminal

---

### Post by tyrel3 on 2014-02-20
Here it is. 

  *-display               
       description: VGA compatible controller
       product: Haswell-ULT Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:64 memory:f7400000-f77fffff memory:d0000000-dfffffff ioport:f000(size=64)
  *-display UNCLAIMED
       description: 3D controller
       product: GK107M [GeForce GT 745M]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:f6000000-f6ffffff memory:e0000000-efffffff memory:f0000000-f1ffffff ioport:d000(size=128) memory:f7000000-f707ffff

---

### Post by dannyboy79 on 2014-02-20
looks like you have a system with both a built in igpu within your intel cpu AND an nvidia gpu. I am not familiar with that but i've heard others mention bumblebee. Sorry i can't help

---

### Post by mips on 2014-02-21
[https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)

---

### Post by MikeCyber on 2014-02-21
I also have a GTX770 with a Intel integrated graphics. On 12.04 I only use Nvidia but will both work out of the box after a fresh install of upcoming 14.04?

---

### Post by tyrel3 on 2014-02-22
Thank you, That did the trick.

---

### Post by dannyboy79 on 2014-02-22
is it a laptop OR a desktop? I have an i5-4670k and an Nvidia GTX 760, i installed the latest 331.38 Nvidia driver form the website within 13.10 and all works great. I think the issue is on laptops when theres a mix of gpus.

---

