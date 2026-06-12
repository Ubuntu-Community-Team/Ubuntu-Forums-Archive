---
title: "Dell i14r 2265 Network Unclaimed"
date: 2010-09-20
forum: Dell Ubuntu Support (CLOSED)
---

### Post by javamaniac on 2010-09-20
Hi. I'm trying to get Ubuntu 10.04 on my dell i14r laptop but unfortunately my ethernet network doesn't work properly. This is what I get as an output:

sudo lshw -C network
```

  *-network DISABLED       
       description: Wireless interface 
       product: WiMAX/WiFi Link 6050 Series 
       vendor: Intel Corporation 
       physical id: 0 
       bus info: pci@0000:03:00.0 
       logical name: wlan0 
       version: 57 
       serial: 00:23:15:1b:39:2c 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless 
       configuration: broadcast=yes driver=iwlagn latency=0 multicast=yes wireless=IEEE 802.11abgn 
       resources: irq:32 memory:f0500000-f0501fff 
  *-network UNCLAIMED 
       description: Ethernet controller 
       product: AR8152 v1.1 Fast Ethernet 
       vendor: Atheros Communications 
       physical id: 0 
       bus info: pci@0000:04:00.0 
       version: c1 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm msi pciexpress vpd bus_master cap_list 
       configuration: latency=0 
       resources: memory:f0400000-f043ffff ioport:2000(size=128)  

```

lspci
```

00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 18) 
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 18) 
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06) 
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06) 
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06) 
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06) 
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 06) 
00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 06) 
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06) 
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a6) 
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 06) 
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 6 port SATA AHCI Controller (rev 06) 
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 06) 
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 06) 
03:00.0 Network controller: Intel Corporation WiMAX/WiFi Link 6050 Series (rev 57) 
04:00.0 Ethernet controller: Atheros Communications AR8152 v1.1 Fast Ethernet (rev c1) 
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 05) 
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 05) 
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 05) 
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 05) 
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 05) 
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 05) 

```

Someone please help me with this issue! Thanks in advance.

---

