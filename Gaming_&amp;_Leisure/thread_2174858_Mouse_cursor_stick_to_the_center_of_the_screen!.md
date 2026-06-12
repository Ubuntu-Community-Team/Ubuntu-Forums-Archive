---
title: "Mouse cursor stick to the center of the screen!"
date: 2013-09-16
forum: Gaming &amp; Leisure
---

### Post by mbnoimi on 2013-09-16
Most OpenGL games unable to use the mouse through it because it always stick to the center of the screen!

How can I fix this issue?

P.S.
[list]
[*]For example supertux suffer from this issue while supertuxkart works fine!.
[*]This issue appears in Full Screen mode.
[*]I faced this issue on different PCs with different hardware.
[/list]

---

### Post by mbnoimi on 2013-10-26
Bump it :( I'm still stuck to this issue

---

### Post by dannyboy79 on 2013-10-27
what GPU do you have?
```
sudo lshw -C display
```

---

### Post by mbnoimi on 2013-10-27
```
*-multimedia            
       description: Audio device
       product: 6 Series/C200 Series Chipset Family High Definition Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 04
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=snd_hda_intel latency=0
       resources: irq:45 memory:f7400000-f7403fff
```

---

### Post by dannyboy79 on 2013-10-27
for future reference, when someone asks about your GPU that means they want to know what Graphics Card you're using. GPU stands for Graphics Processing Unit. So what you pasted is your Audio card. I made a mistake and asked for the wrong class from lshw, I need to see the display class. My fault.
```
sudo lshw -C display
```

Mine returns
```
*-display               
       description: VGA compatible controller
       product: GT218 [GeForce 8400 GS Rev. 3]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: a2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:24 memory:fd000000-fdffffff memory:c0000000-cfffffff memory:dc000000-ddffffff ioport:cc00(size=128) memory:fe980000-fe9fffff

```

---

### Post by mbnoimi on 2013-10-27
Oh silly me :)

```
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
       resources: irq:49 memory:fe000000-fe3fffff memory:c0000000-cfffffff ioport:f000(size=64)
```

---

