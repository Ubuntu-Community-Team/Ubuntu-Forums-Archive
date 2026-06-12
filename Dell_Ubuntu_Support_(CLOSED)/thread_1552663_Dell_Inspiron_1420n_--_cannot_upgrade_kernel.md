---
title: "Dell Inspiron 1420n -- cannot upgrade kernel"
date: 2010-08-13
forum: Dell Ubuntu Support (CLOSED)
---

### Post by nixscripter on 2010-08-13
I've been stuck at kernel 2.6.22.11-generic for a long time (originally from gusty), because there was apparently some proprietary hack to the snd-hda-intel driver that only works in in 2.6.22. I moved a peculiar version of this driver up the 2.6.22 kernel upgrades until it broke at the next major version.

I'd really like to upgrade to 2.6.24-rt, but both the Ubuntu and ALSA-built driver will either cause no sound, or (in a different kernel) kernel oops when probed. Anyone know what I can do?

**sudo lshw -C sound**

```

  *-multimedia            
       description: Audio device
       product: 82801H (ICH8 Family) HD Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=HDA Intel latency=0 module=snd_hda_intel

```

UPDATE: fixed typo in kernel version, added lshw.

---

### Post by nixscripter on 2010-08-15
My bad. I forgot about the linux-ubuntu-modules package.

I upgraded a little to 2.6.24-16-rt, installed that, and it works now.

Doh!

---

