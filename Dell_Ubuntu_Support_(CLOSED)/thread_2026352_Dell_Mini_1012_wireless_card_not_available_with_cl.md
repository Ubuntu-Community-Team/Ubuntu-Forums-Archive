---
title: "Dell Mini 1012 wireless card not available with clean install 12.04"
date: 2012-07-14
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Salpiche on 2012-07-14
Searched the forums and could not find a solutiion to this so I am asking... Is there another way to get the wireless drivers working on this netbook? I try the b43 and every other solution and I am still with no wireless card.

Clean install 12.04
Dell mini 1012
ethernet works 
wireless card not working
(when I switch HD and put the win7 drive the card works)


```
sudo apt-get install b43-fwcutter firmware-b43-installer
``` did not work.

Help please:(

---

### Post by piperbarb on 2012-07-15
Did you install the "Additional Drivers?"  A little icon should have popped up on the top menu bar.  If you do not have one there, check the system settings.  You have to install/activiate the wireless driver before you can use it.

Hope that helps.

---

### Post by ranger1021994 on 2012-07-15
How about ndiswrapper ??
Manually : [http://archive.ubuntu.com/ubuntu/pool/main/n/ndiswrapper/](http://archive.ubuntu.com/ubuntu/pool/main/n/ndiswrapper/)
Terminal :```
sudo apt-get install ndiswrapper-common
```

---

### Post by Salpiche on 2012-07-15
> **piperbarb said:**
> Did you install the "Additional Drivers?"  A little icon should have popped up on the top menu bar.  If you do not have one there, check the system settings.  You have to install/activiate the wireless driver before you can use it.

Hope that helps.


nope it never showed and to the system menu and going System Settings > Additional Drivers does not work either.

thanks

---

### Post by Salpiche on 2012-07-15
> **ranger1021994 said:**
> How about ndiswrapper ??
Manually : [http://archive.ubuntu.com/ubuntu/pool/main/n/ndiswrapper/](http://archive.ubuntu.com/ubuntu/pool/main/n/ndiswrapper/)
Terminal :```
sudo apt-get install ndiswrapper-common
```

No I have not tried that one, will try it and check back in.

---

### Post by Bucky Ball on 2012-07-15
> **ranger1021994 said:**
> How about ndiswrapper ??
Manually : [http://archive.ubuntu.com/ubuntu/pool/main/n/ndiswrapper/](http://archive.ubuntu.com/ubuntu/pool/main/n/ndiswrapper/)
Terminal :```
sudo apt-get install ndiswrapper-common
```

Avoid at all costs (unless there is the extremely unlikely scenario that your card won't work with the regular drivers). Superceded for the majority of Broadcom cards, if that is what yours is (b43 is for Broadcom). If you have the two b43 packages you suggested installed then leave them there. You are probably not far away.

Please post the result of this:

```
sudo lshw -C network
```;)

---

### Post by Salpiche on 2012-07-15
> **Bucky Ball said:**
> Avoid at all costs (unless there is the extremely unlikely scenario that your card won't work with the regular drivers). Superceded for the majority of Broadcom cards, if that is what yours is (b43 is for Broadcom). If you have the two b43 packages you suggested installed then leave them there. You are probably not far away.

Please post the result of this:

```
sudo lshw -C network
```;)

```
jose@mini1012:~$ sudo lshw -C network
PCI (sysfs)  
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 02
       serial: 5c:26:0a:0b:36:24
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=N/A ip=192.168.0.23 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:43 ioport:2000(size=256) memory:f0f20000-f0f20fff memory:f0f10000-f0f1ffff memory:f0f40000-f0f5ffff
  *-network
       description: Ethernet interface
       physical id: 3
       bus info: usb@1:7
       logical name: wmx0
       serial: 00:1d:e1:39:46:98
       capabilities: ethernet physical
       configuration: driver=i2400m firmware=i6050-fw-usb-1.5.sbcf link=no

```

---

### Post by mrreality13 on 2012-09-23
i have a mini 1012 hers what my synaptic has installed:

fwcutter 
Broadcom 802.11 Linux STA wireless driver source
Common files for the Broadcom STA Wireless driver
Source for the Broadcom STA Wireless driver

BUT im also using pinguy linux witch is ubuntu based

---

