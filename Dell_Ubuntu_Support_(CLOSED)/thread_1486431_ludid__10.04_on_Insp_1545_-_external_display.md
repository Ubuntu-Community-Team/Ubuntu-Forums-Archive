---
title: "ludid / 10.04 on Insp 1545 - external display"
date: 2010-05-17
forum: Dell Ubuntu Support (CLOSED)
---

### Post by oradano on 2010-05-17
hi all,

Just installed lucid on my Inspiron 1545 and it doesn't recognize my external monitor.  It displays but doesn't look good on laptop screen and resolution doesn't change b/t laptop / external monitors.  

It's dual-boot'd with windoze and there it's detecting both laptop and external monitor resolution ok.  I think what's missing is the equivalent driver for lucid.

What I know so far is that I might be able to find a driver for this chipset, otherwise create an xorg.conf entry (file) with specific settings.

Any help is very much appreciated.



I ran the following to get details on chipset / drivers
===================================================================================[FONT=monospace]

[/FONT]lshw -C display

*-display:0
       description: VGA compatible controller
       product: Mobile 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 07
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:30 memory:f6c00000-f6ffffff memory:e0000000-efffffff(prefetchable) ioport:efe8(size=8)
[B]  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1[/B]
       bus info: pci@0000:00:02.1
       version: 07
       width: 64 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
       resources: memory:f6b00000-f6bfffff

---

### Post by oradano on 2010-05-21
found a previous thread that resolved this one and got the clear 1280x1024 I was looking for, very very grateful


# get display config info
$ cvt 1280 1024

#create new display mode using config info from above
$ xrandr --newmode (name) (config)

#assign new mode to VGA1
$ xrandr --addmode VGA1 (name)

#set output to new VGA1 mode
$ xrandr --output VGA1 --mode (name)



search  'Increase monitor resolution' to get to the original thread

---

