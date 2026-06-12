---
title: "Need Help with Wireless"
date: 2008-04-04
forum: Dell  Ubuntu Support
---

### Post by esimuro on 2008-04-04
I am new to Linux and Ubunto and the Dell Inspiron 1721, I have this set6 up as a duel boot system with Vista and Ubunto 7.10, wireless works perfectly in windows but I can't seem to get it working in Linux.  

I attempted to follow the directions in : HOWTO: Dell Inspiron E1505 Wireless (Broadcom 1390 WLAN) " but this didn't seem to get me any closer to getting wireless running.  I have the 802.11 n wireless card on this system and downloaded the Dell_multi-device_A17_R174292.exe drivers which I used replacing teh drivers in the How to.  I also attemopted to use the drivers in the How to just because.   

The ispci output is 

00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)
00:05.0 PCI bridge: ATI Technologies Inc Unknown device 7915
00:07.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 3)
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon X1200 Series
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:01.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
0b:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)

	tail of /val/log/syslog follows:

Apr  4 21:54:23 Linux-laptop kernel: [254521.890252] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBufferListPool'
Apr  4 21:54:23 Linux-laptop kernel: [254521.890267] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSetMiniportAttributes'
Apr  4 21:54:23 Linux-laptop kernel: [254521.890274] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeIoWorkItem'
Apr  4 21:54:23 Linux-laptop kernel: [254521.890282] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMDeregisterMiniportDriver'
Apr  4 21:54:23 Linux-laptop kernel: [254521.890289] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMRegisterScatterGatherDma'
Apr  4 21:54:23 Linux-laptop kernel: [254521.890297] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSendNetBufferListsComplete'
Apr  4 21:54:23 Linux-laptop kernel: [254521.890310] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateIoWorkItem'
Apr  4 21:54:23 Linux-laptop kernel: [254521.890317] ndiswrapper (load_sys_files:210): couldn't prepare driver 'bcmwl6'
Apr  4 21:54:23 Linux-laptop kernel: [254521.891314] ndiswrapper (load_wrap_driver:112): couldn't load driver bcmwl6; check system log for messages from 'loadndisdriver'
Apr  4 21:54:23 Linux-laptop kernel: [254521.896653] usbcore: registered new interface driver ndiswrapper

	Data from dmsg follows:

[254283.021854] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[254290.341097] eth0: no IPv6 routers present
[254522.029614] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[254521.890080] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSetBusData'
[254521.890095] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMRegisterInterruptEx'
[254521.890103] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMIndicateStatusEx'
[254521.890111] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateMdl'
[254521.890118] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMDeregisterInterruptEx'
[254521.890125] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeMdl'
[254521.890134] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBufferList'
[254521.890141] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferAndNetBufferList'
[254521.890149] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSynchronizeWithInterruptEx'
[254521.890160] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMDeregisterScatterGatherDma'
[254521.890181] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateMemoryWithTagPriority'
[254521.890194] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMOidRequestComplete'
[254521.890201] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisOpenConfigurationEx'
[254521.890208] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMGetBusData'
[254521.890216] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMIndicateReceiveNetBufferLists'
[254521.890223] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisQueueIoWorkItem'
[254521.890237] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferListPool'
[254521.890245] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMRegisterMiniportDriver'
[254521.890252] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBufferListPool'
[254521.890267] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSetMiniportAttributes'
[254521.890274] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeIoWorkItem'
[254521.890282] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMDeregisterMiniportDriver'
[254521.890289] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMRegisterScatterGatherDma'
[254521.890297] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSendNetBufferListsComplete'
[254521.890310] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateIoWorkItem'
[254521.890317] ndiswrapper (load_sys_files:210): couldn't prepare driver 'bcmwl6'
[254521.891314] ndiswrapper (load_wrap_driver:112): couldn't load driver bcmwl6; check system log for messages from 'loadndisdriver'
[254521.896653] usbcore: registered new interface driver ndiswrapper

	output from iwlist scanning:

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.



Can anyone help!!!

---

### Post by cousinavi on 2008-04-06
Check if your use of ndiswrapper was successful by using the command,
```
ndiswrapper -l
```
You should get something similar to,
```
bcmwl5 : driver installed
        device (14E4:4318) present
```
If that is fine make sure the ndiswrapper module is loaded; type,
```
sudo depmod -a
sudo modprobe ndiswrapper
```

If that doesn't help  then check you have installed all the right packages:

```
sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.9 ndisgtk
```

Hopefully your card should now work and network-manager should list the SSIDs in range. Connection should be simple and straightforward.

See my [walkthrough]("http://ubuntuforums.org/showthread.php?t=739286") for a full set of instructions, if required.


**-Avi**

---

### Post by jkeyes0 on 2008-04-07
> **esimuro said:**
> 
[254521.890317] ndiswrapper (load_sys_files:210): couldn't prepare driver '**bcmwl6**'
[254521.891314] ndiswrapper (load_wrap_driver:112): couldn't load driver **bcmwl6**; check system log for messages from 'loadndisdriver'


I think this part is where your problem lies. bcmwl6 is the vista driver, which ndiswrapper won't work with. If you go back to Dell's website and search under XPS laptops for the m1330, then use the Windows XP driver provided there, you should have better results.

---

