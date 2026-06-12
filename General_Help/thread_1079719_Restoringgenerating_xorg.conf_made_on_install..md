---
title: "Restoring/generating xorg.conf made on install."
date: 2009-02-24
forum: General Help
---

### Post by WastePotato on 2009-02-24
Hi,

I'm currently using Ubuntu 8.10 with the fglrx proprietary driver, and wish to switch back to the driver that was supplied and configured at the time of install. I'm assuming it's an open source driver; it worked out of the box, including 3D/DRI. I switched to the fglrx driver in persuit of stability, but found myself unsatisfied with its performance in comparison to the open source driver. I've attempted to utilise previous xorg.conf backups, but they do not provide 3D acceleration.

So the question is, how do I restore/generate an xorg.conf that is identical to the one made on installation of Ubuntu 8.10?

Graphics card specifications are detailed below.

>            *-display
                description: VGA compatible controller
                product: RS690M [Radeon X1200 Series]
                vendor: ATI Technologies Inc
                physical id: 5
                bus info: pci@0000:01:05.0
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=fglrx_pci latency=64 module=fglrx


Thanks in advance for any help. :)

---

### Post by ddrichardson on 2009-02-25
Try
```
sudo X -configure
```That'll give you an autoprobed one (in the folder you run it in).

Reconfiguring through dpkg does much the same:
```
sudo /etc/init.d/gdm stop
sudo dpkg-reconfigure xserver-xorg
sudo /etc/init.d/gdm start
```

---

### Post by Yellow Pasque on 2009-02-25
If you want to use the open-source radeon driver, make sure you purge the fglrx driver from your system.

---

