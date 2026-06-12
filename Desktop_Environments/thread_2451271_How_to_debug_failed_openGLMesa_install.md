---
title: "How to debug failed openGL/Mesa install"
date: 2020-09-30
forum: Desktop Environments
---

### Post by chrisalbertson on 2020-09-30
Here is the problem, cut/pasted from the terminal from a new Ubuntu 20.04.1 install.  The question is "where to start?"

```
chris@Z420:~$ glxinfo
name of display: :1
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  151 (GLX)
  Minor opcode of failed request:  24 (X_GLXCreateNewContext)
  Value in failed request:  0x0
  Serial number of failed request:  41
  Current serial number in output stream:  42
chris@Z420:~$ 
```

Here is my display hardware
```

chris@Z420:~$ sudo lshw -class display
[sudo] password for chris: 
  *-display                 
       description: VGA compatible controller
       product: GP107 [GeForce GTX 1050 Ti]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:61 memory:ee000000-eeffffff memory:d0000000-dfffffff memory:e0000000-e1ffffff ioport:c000(size=128) memory:c0000-dffff
chris@Z420:~$ 
```

---

