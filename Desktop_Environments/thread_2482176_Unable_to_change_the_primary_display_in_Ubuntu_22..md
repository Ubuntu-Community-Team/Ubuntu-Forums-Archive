---
title: "Unable to change the primary display in Ubuntu 22.04 (using Wayland)"
date: 2022-12-22
forum: Desktop Environments
---

### Post by goodstuff9 on 2022-12-22
Ubuntu 22.04 (wayland).  


This is a fresh installation of Ubuntu.  In Settings >> Displays, I have the display landscape as shown in the attached screenshot here:  


[IMG]https://ubuntuforums.org/attachment.php?attachmentid=291443&stc=1[/IMG]


As you can see, I have display #1 (third from the left) set as the primary display, and that is the display on which the top bar/panel should appear.  However, Ubuntu simply will not obey this setting.  It treats display #4 (leftmost) display as the primary display, and that is where the top bar appears.  I tried modifying the monitors.xml file as discussed on this site in a few places, but nothing seems to work.  I'm not a computer expert, so I don't know what other information might be needed.  Thanks in advance to anyone who will help me with this vexing problem.  


I don't know if this helps, in case it does:  


```
main1@system1:~$ sudo lshw -c video
[sudo] password for main1: 
  *-display                 
       description: VGA compatible controller
       product: GK208B [GeForce GT 730]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: /dev/fb1
       logical name: /dev/fb0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom fb
       configuration: depth=32 driver=nouveau latency=0 mode=1360x768 resolution=1920,1080 visual=truecolor xres=1360 yres=768
       resources: iomemory:600-5ff iomemory:600-5ff irq:146 memory:41000000-41ffffff memory:6000000000-6007ffffff memory:6008000000-6009ffffff ioport:4000(size=128) memory:42000000-4207ffff
  *-display
       description: VGA compatible controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       logical name: /dev/fb0
       version: 0c
       width: 64 bits
       clock: 33MHz
       capabilities: pciexpress msi pm vga_controller bus_master cap_list rom fb
       configuration: depth=32 driver=i915 latency=0 resolution=1920,1080
       resources: iomemory:600-5ff iomemory:400-3ff irq:147 memory:600a000000-600affffff memory:4000000000-400fffffff ioport:5000(size=64) memory:c0000-dffff memory:4010000000-4016ffffff memory:4020000000-40ffffffff
main1@system1:~$
```

---

