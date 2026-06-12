---
title: "Dell Inspiron 1750 fan settings"
date: 2013-12-01
forum: Dell Ubuntu Support (CLOSED)
---

### Post by antiksp on 2013-12-01
Hallo ubuntu-community,
I use Dell Ispiron 1750 and have a problem with fan/energy setting.

It's well known that Ubuntu doesn't have advanced native power saving. I wasn't satisfy with 1 hour battery work, so I installed tlp. A new problem I got is, that fan is always running on high performance and notebook got hotter, than it was before installing tlp, though battery's life increased.

_lm-sensors_:
acpitz-virtual-0
Adapter: Virtual device
temp1:        +55.5°C  (crit = +105.0°C)

radeon-pci-0100
Adapter: PCI adapter
temp1:        +61.5°C  

coretemp-isa-0000
Adapter: ISA adapter
Core 0:       +50.0°C  (high = +105.0°C, crit = +105.0°C)
Core 1:       +50.0°C  (high = +105.0°C, crit = +105.0°C)

How can I solve problem with fan and temperature?

---

