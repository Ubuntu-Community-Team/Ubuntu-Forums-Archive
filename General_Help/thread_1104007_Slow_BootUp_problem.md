---
title: "Slow BootUp problem"
date: 2009-03-23
forum: General Help
---

### Post by totalhum on 2009-03-23
Hi installed a fresh copy of 8.10. All was working fine. Configured static IP and removed network manager. I then did apt-get intall upgrade and suddenly my system is very slow on boot up. After 5 mins the progress bar remains at 1/10 and then suddenly it boots. Can anyone help? I think that this problem is related to the network configuration.

The output  lshw -C network:


  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 02
       serial: 00:19:66:93:64:85
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.104 latency=0 link=yes module=r8169 multicast=yes port=twisted pair speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 3e:21:a4:83:c8:51
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

---

### Post by totalhum on 2009-03-23
Can anyone point me in the right direction pls?

---

