---
title: "How do I connect to my wireless network?"
date: 2009-02-01
forum: General Help
---

### Post by Dustin2128 on 2009-02-01
I have a cable modem/router, with the ethernet plugged up into my computer, and an antenna brodcasting our internet on a secure WEP 128bit 26 digit password network. My computer is running 8.04 and windows xp pro. The laptop is running Vista home premium and Intrepid Ibex (8.10). On vista, it automatically logs on to the network to provide internet, and I know the network is up because I have 2 other windows computers acessing it. (other than the laptop) So how would I have the laptop acess the wireless network?

---

### Post by cariboo on 2009-02-01
When you right click on the network icon in the top panel, do you see any wireless networks? Is the correct driver installed for your wireless adapter. Open a Applications-->Accessories-->Termianl and type:

```
sudo lshw -C network
```

The above command will list the specifics of your network devices and also tell us what driver if any is loaded. Please enclose the output of the above command using the [noparse]```

```[/noparse] tags.

Jim

---

### Post by Dustin2128 on 2009-02-01
```
  *-network               
       description: Ethernet interface 
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller 
       vendor: Realtek Semiconductor Co., Ltd. 
       physical id: 0 
       bus info: pci@0000:11:00.0 
       logical name: eth0 
       version: 01 
       serial: 00:1b:38:b7:04:74 
       capacity: 1GB/s 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation 
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no module=r8169 multicast=yes port=twisted pair 
  *-network UNCLAIMED 
       description: Ethernet controller 
       product: AR242x 802.11abg Wireless PCI Express Adapter 
       vendor: Atheros Communications Inc. 
       physical id: 0 
       bus info: pci@0000:17:00.0 
       version: 01 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm msi pciexpress msix cap_list 
       configuration: latency=0 
  *-network DISABLED 
       description: Ethernet interface 
       physical id: 2 
       logical name: pan0 
       serial: a2:ad:a6:a7:f8:65 
       capabilities: ethernet physical 
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes 

```
can't make heads or tails of this

---

### Post by cariboo on 2009-02-02
There is a driver for your wireless device in the backport modules. To install it, Open a Applications-->Accessories-->Terminal and type:

```
sudo apt-get install linux-backports-modules
```

This should install the new driver for your wirless device after a reboot.

Jim

---

### Post by Dustin2128 on 2009-02-02
> **cariboo907 said:**
> There is a driver for your wireless device in the backport modules. To install it, Open a Applications-->Accessories-->Terminal and type:

```
sudo apt-get install linux-backports-modules
```

This should install the new driver for your wirless device after a reboot.

Jim
couldn't find packages

---

### Post by DonnyB4e56 on 2009-02-05
go into your synaptic package manager and look for it there, just type in backport and it should come up with a few... click the latest one. That's what i'm doing now.

---

