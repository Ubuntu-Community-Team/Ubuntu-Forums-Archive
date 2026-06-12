---
title: "League of Legends successfully installed but UI issues when I play"
date: 2014-10-14
forum: Gaming &amp; Leisure
---

### Post by mynameisjeremey on 2014-10-14
Hi Ubuntu Community:

I recently started using Ubuntu 14.04 3 months ago. I enjoy the operating system and the control that I have over my machine. I recently decided to install League of Legends onto my computer using PlayOnLinux, and then I was able to successfully install LoL. Everything runs smoothly until I start a game. There is a problem with the color on the screen: it's all black, with some dull outlines of the map visible. When I press ESC, the options screen/border surrounding the text is all red. It looks like this: [http://imgur.com/bdhnLuN](http://imgur.com/bdhnLuN) . Does anyone know how I could fix this? Thanks!

---

### Post by dannyboy79 on 2014-10-14
What graphics card do you have and which driver are you using?
```
sudo lshw -C display
```

---

### Post by mynameisjeremey on 2014-10-14
I hope this helps! Thanks for helping me to narrow it down!

description: VGA compatible controller
       product: GF108M [GeForce GT 540M]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nouveau latency=0
       resources: irq:52 memory:f0000000-f0ffffff memory:c0000000-cfffffff memory:d0000000-d1ffffff ioport:3000(size=128) memory:f1000000-f107ffff
  *-display
       description: VGA compatible controller
       product: 2nd Generation Core Processor Family Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:49 memory:f1400000-f17fffff memory:e0000000-efffffff ioport:4000(size=64)

---

### Post by dannyboy79 on 2014-10-15
looks like you have a laptop that has an intel internal graphics card AND an nvidia graphics card. i've no experience with those but I believe you have to run something called primus or optirun or something or other. I see currently your computer is using the intel driver (configuration: driver=i915) which isn't optimal because your GT540M is a better graphics card so you need to install a driver for that. just google for it or wait for others to pop in.

---

### Post by oldrocker99 on 2014-10-15
If you look for Additional Drivers in your Preferences, an nVidia driver should show up. You will have to reboot after installation (one of the few times when you need to reboot in Linux).

---

