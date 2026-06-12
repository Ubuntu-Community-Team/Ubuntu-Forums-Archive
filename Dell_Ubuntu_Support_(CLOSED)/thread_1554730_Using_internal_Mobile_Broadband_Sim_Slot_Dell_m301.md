---
title: "Using internal Mobile Broadband Sim Slot Dell m301z"
date: 2010-08-17
forum: Dell Ubuntu Support (CLOSED)
---

### Post by seemore on 2010-08-17
I have a Dell m301z that has an internal slot for a mobile Broadband sim card. I am using 10.04 desktop 64-bit.

When I insert my sim, ubuntu does not recognise the slot or sim or anything. If I use the sim with my friend's USB mobile broadband modem then everything works fine and I have no problem setting it up. So this seems to be a driver problem.

I have installed the broadcom STA driver.

My laptop has the dell 1501 b/g/n wireless card and the Dell Bluetooth Internal (2.1 + EDR) mini card.

I am new to linux and if I have not provided enough details to solve the problem, I apologise in advance and will paste any required printouts from terminal commands as requested. I'll start with a few commands that I have picked up.....

Output of lspci:

> 
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge Alternate
00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (int gfx)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 41)
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) (rev 40)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller (rev 40)
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (rev 40)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc M880G [Mobility Radeon HD 4200]
01:05.1 Audio device: ATI Technologies Inc RS880 Audio Device [Radeon HD 4200]
02:00.0 Network controller: Broadcom Corporation Device 4727 (rev 01)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 04)
03:00.1 Class ff00: Realtek Semiconductor Co., Ltd. Device 5288 (rev 01)]

Output of ifconfig:

> eth0      Link encap:Ethernet  HWaddr 00:26:b9:70:37:42  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:26 Base address:0x6000 

eth1      Link encap:Ethernet  HWaddr 70:f1:a1:92:25:f3  
          inet addr:10.0.0.2  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::72f1:a1ff:fe92:25f3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:17322 errors:0 dropped:0 overruns:0 frame:18088
          TX packets:19224 errors:30 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:12013845 (12.0 MB)  TX bytes:3713691 (3.7 MB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1186 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1186 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:67906 (67.9 KB)  TX bytes:67906 (67.9 KB)


---

### Post by seemore on 2010-08-17
It would appear that dell just leave a fake slot in the chassis for my country (Australia) and leave the instructions to use it in the manual. There was no option to purchase a WWAN adapter during the buying process. Thanks DELL!!!

---

