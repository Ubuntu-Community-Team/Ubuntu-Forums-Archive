---
title: "No chain to parent device udevadm info output"
date: 2013-02-15
forum: Desktop Environments
---

### Post by anantha1985 on 2013-02-15
hi,
i am using pci card on linux 2.6.24.2 after installing driver ,i checked card is working fine,
when i entered udevadm info -a -p 'udevadm info -q path -n /dev/adtpm0'
i got the output as,

looking at device '/class/altapmc1553/adtpmc0':
    KERNEL=="adtpmc0"
    SUBSYSTEM=="altapmc1553"
    DRIVER==""
    ATTR{dev}=="252:0"
The problem is the udevadm info not providing the info of parent device.
i wanted to give different name for same card when it is connected to another pci slot(different pci bus address) and it is not possible without info about parent device because the udevadm info is same for different pci slots.
Please suggest me why the udevadm info not providing the parent device info and to resolve the problem ASAP.

---

