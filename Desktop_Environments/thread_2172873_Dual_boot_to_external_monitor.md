---
title: "Dual boot to external monitor?"
date: 2013-09-06
forum: Desktop Environments
---

### Post by skyemoor on 2013-09-06
I have an 24" external monitor that I want to use between two docked, closed laptops (the other one is Win 7 only), switching the monitor, keyboard, mouse with an Iogear 2 port KVM.

Dell Latitude laptop
Ubuntu Studio 13.04
Xfce 4.10
Dual boot with Windows 7
Grub 2.00
NVIDIA Driver Version: 304.88
Server Version Number: 11.0 
GPU: NVS 4200M
 - NVIDIA Corporation GF119M [NVS 4200M] (rev a1
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:16 memory:e4000000-e4ffffff memory:d0000000-dfffffff memory:e0000000-e1ffffff ioport:4000(size=128) memory:e5000000-e507ffff

Displays;
 - LGD (DFP-0),
 - HannStar Display Corp HC194D (CRT-0)
NV CONTROL Version: 1.28
Displays: 1
Switched to Metamode 2880x900
TwinView

I can set the external monitor as the primary display, but during boot with the laptop lid closed, nothing shows on the external monitor (no Bios load or Grub).

How can I boot up with the laptop lid closed, viewing everything from my external monitor?

And then how can the laptop be undocked from time to time, reverting automatically to it's own screen?

**Update**: I can do all the above in the 2880x900 metamode - it seems to work, though I feel like I've only badly jury-rigged it - what metamode should I be in and are there any other changes I should be making?

---

