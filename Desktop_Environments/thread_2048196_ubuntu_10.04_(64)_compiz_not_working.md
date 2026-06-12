---
title: "ubuntu 10.04 (64) compiz not working"
date: 2012-08-26
forum: Desktop Environments
---

### Post by linux83 on 2012-08-26
Hello Friends,
i decided to install ubuntu 10.04 (64) bit instead of (32) that limit my memory size. what i notice that compiz is not working at all, and i got this error:
Desktop effects could not be enabled
 and each time i try to select normal compiz effect it try to search for driver while the same driver
working fine on (32bit) on the same laptop.

could any one help me resolve this problem, my laptop is lenovo T420.

>         *-display
             description: VGA compatible controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 09
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:18 memory:f0000000-f03fffff memory:e0000000-efffffff ioport:5000(size=64)> 00:02.0 VGA compatible controller [0300]: Intel Corporation Device [8086:0116] (rev 09)when i run compiz test i got:

> Gathering information about your system...

 Distribution:          Ubuntu 10.04
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation Device 0116 (rev 09)
 Driver in use:         vesa
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...  [SKIP]

 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: vesa driver in use 


Update: this seem driver issu and not compiz, thus i need to get proper driver.

linux83.

---

