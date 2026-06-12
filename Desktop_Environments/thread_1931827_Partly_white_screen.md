---
title: "Partly white screen"
date: 2012-02-26
forum: Desktop Environments
---

### Post by bjerge on 2012-02-26
Randomly my ubuntu machine give me a partly white screen like shown in this youtube video i have made:
[http://www.youtube.com/watch?v=xn6Rp9w38QQ&context=C34c1cc2ADOEgsToPDskJbmoLvorA_rfURQ1SiSFrg](http://www.youtube.com/watch?v=xn6Rp9w38QQ&context=C34c1cc2ADOEgsToPDskJbmoLvorA_rfURQ1SiSFrg)

Here is my HW details:
```
sudo lshw -C video
   *-display               
        description: VGA compatible controller
        product: GT218 [ION]
        vendor: nVidia Corporation
        physical id: 0
        bus info: pci@0000:04:00.0
        version: a2
        width: 64 bits
        clock: 33MHz
        capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
        configuration: driver=nouveau latency=0
        resources: irq:16 memory:fd000000-fdffffff memory:d0000000-dfffffff memory:ce000000-cfffffff ioport:ec00(size=128) memory:feb00000-feb7ffff

```
I'm runing ubuntu 11.10

Anybody who has seen this also, and know what to do?

---

### Post by grahammechanical on 2012-02-26
I see that you are using the Nouveau video driver for your Nvidia GT218. It is commendable that you have choosen to use an opensource driver and not the proprietary driver from Nvidia.

I have the Nvidia GT 220 and I am using the Nvidia 295.20 driver which came with a recent update.

I suggest that you go to Additional Drivers and activate the Nvidia proprietary driver. You may find that this solves the problem.

Regards.

---

### Post by bjerge on 2012-02-27
Thanks, i have installed the driver, and hope that works.

It hasn't crashed yet :-)

---

