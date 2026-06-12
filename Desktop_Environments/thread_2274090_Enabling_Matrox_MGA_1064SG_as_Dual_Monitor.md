---
title: "Enabling Matrox MGA 1064SG as Dual Monitor"
date: 2015-04-17
forum: Desktop Environments
---

### Post by hundred1906 on 2015-04-17
To make life easier while learning FreeCAD scripting I plugged in a second monitor using an old Matrox Mystique 1064SG pci card. The card is seen but I cannot get it recognised by the SystemSettings/Screen Display utility.

```
lspci | grep VGA
01:00.0 VGA compatible controller: NVIDIA Corporation GT218 [GeForce 210] (rev a2)
05:02.0 VGA compatible controller: Matrox Electronics Systems Ltd. MGA 1064SG [Mystique] (rev 02)
```

More detail shows that the card is Unclaimed

```
sudo lshw -C video
 
  *-display               
       description: VGA compatible controller
       product: GT218 [GeForce 210]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nouveau latency=0
       resources: irq:45 memory:ed000000-edffffff memory:d0000000-dfffffff memory:e8000000-e9ffffff ioport:dc00(size=128) memory:eed00000-eed7ffff
  *-display UNCLAIMED
       description: VGA compatible controller
       product: MGA 1064SG [Mystique]
       vendor: Matrox Electronics Systems Ltd.
       physical id: 2
       bus info: pci@0000:05:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: vga_controller
       configuration: latency=64
       resources: memory:efff8000-efffbfff memory:eb800000-ebffffff memory:ef000000-ef7fffff memory:effe0000-effeffff
```

For this card a MGA driver is needed. When I look in the Software Centre I see that the driver is already installed on my system.

So how do I get it enabled?

There is posted advice regarding modifying Xorg.conf.d but there is also advice stating that "Today's X rarely requires manual configuration. X now automatically configures itself with reasonable defaults." My system appears not to have a pre-existing Xorg.conf.d. Learning FreeCAD is problem enough so if this is really complex or dangerous I think I would rather take the easy route and buy a new dual head video card.

---

### Post by dino99 on 2015-04-18
is not the GT218 able to have 2 monitors plugged ?
as i see from synaptic , xserver-xorg-video-mga is the driver to use with a matrox card; and matroxset let you tweak more details.

i suppose that your issue can be solve inside the xorg.conf (but it needs to be precise, and mistake free)

---

### Post by hundred1906 on 2015-04-18
9d9 thank you for replying. In fact I have just previously discovered/realised for myself that the GT218 already supports two outputs (not well documented) and I was about to update my original post.

So although the original problem of how to enable the Matrox driver is not resolved my actual need has gone away so I am marking this thread as solved.

---

