---
title: "Ubuntu-Gnome 16.04 sticky touchscreen."
date: 2016-11-06
forum: Desktop Environments
---

### Post by kiina on 2016-11-06
This problem occurs only with Gnome. Lxde, Xfce or Mate works fine. Touchscreen buttons stuck and do not respond correctly.

```

$ lsusb
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 8087:0911 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

```

$ lspci
00:00.0 Host bridge: Intel Corporation Atom Processor Z36xxx/Z37xxx Series SoC Transaction Register (rev 0f)
00:02.0 VGA compatible controller: Intel Corporation Atom Processor Z36xxx/Z37xxx Series Graphics & Display (rev 0f)
00:14.0 USB controller: Intel Corporation Atom Processor Z36xxx/Z37xxx, Celeron N2000 Series USB xHCI (rev 0f)
00:1a.0 Encryption controller: Intel Corporation Atom Processor Z36xxx/Z37xxx Series Trusted Execution Engine (rev 0f)
00:1f.0 ISA bridge: Intel Corporation Atom Processor Z36xxx/Z37xxx Series Power Control Unit (rev 0f)

```

```

$ sudo lshw -C display
[sudo] password for oh2emd: 
  *-display               
       description: VGA compatible controller
       product: Atom Processor Z36xxx/Z37xxx Series Graphics & Display
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 0f
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:204 memory:90000000-903fffff memory:80000000-8fffffff ioport:1000(size=8)

```

```

$ xinput
 xinput
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Goodix Capacitive TouchScreen               id=7    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=6    [slave  keyboard (3)]
    &#8627; axp20x-pek                                  id=8    [slave  keyboard (3)]
    &#8627; gpio-keys                                   id=9    [slave  keyboard (3)]

```

---

