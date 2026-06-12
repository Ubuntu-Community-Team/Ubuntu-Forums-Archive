---
title: "Problem with Ubuntu in Dell Vostro 1014"
date: 2010-11-07
forum: Dell Ubuntu Support (CLOSED)
---

### Post by linu&gt;&lt;en on 2010-11-07
Hi Everybody.
I've installed Ubuntu 8.10 in my Dell Vostro 1014 side-by-side with Windows 7. The problem is that wireless network is not working in ubuntu, while in windows its fine. I've an wired network which is working in both the os. I've run **iwconfig** and the output is 

[I]lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

ppp0      no wireless extensions.

[/I]For **lshw -c network** I got

[I]  *-network UNCLAIMED     
       description: Network controller
       product: Atheros Communications Inc.
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 03
       serial: 00:26:b9:23:f0:db
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full latency=0 link=yes module=r8169 multicast=yes port=twisted pair speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: a6:da:fd:1f:bd:b8
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

[/I]I am a novice in Ubuntu. Can anybody please help?:confused:

Thanks in advance.

---

### Post by ugm6hr on 2010-11-07
Do you really mean Ubuntu 8.10?
How did you install Ubuntu? From within Windows (wubi), or true dual-boot.

---

### Post by linu&gt;&lt;en on 2010-11-07
My version is Ubuntu 8.10 and its a true dual boot installation.

---

### Post by sikander3786 on 2010-11-07
> **linu><en said:**
> My version is Ubuntu 8.10 and its a true dual boot installation.
8.10 is no longer supported. It would be better to install 10.04 or 10.10 as they are the latest versions and support much more hardware.

And a clean install would be better than upgrade.

---

### Post by linu&gt;&lt;en on 2010-11-09
Thanks for your help. I have updated to Ubuntu 10.10. The network bug is fixed in this version. Its awesome. Thanks anyway.

---

