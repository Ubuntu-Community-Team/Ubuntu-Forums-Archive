---
title: "Jaunty 9.04 Won't auto mount USB drives"
date: 2009-05-20
forum: General Help
---

### Post by Staesys on 2009-05-20
After this morning's update, my Jaunty install will no longer auto mount USB thumb drives, CD-ROM's, my external USB hdd or memory cards in my card slot.

This has got to be fixed.

When I try and go to the Computer, under Places it says:

```
Could not display "computer:".

Nautilus cannot handle "computer" locations.
```

When I try to go to my cd drive with a cd in the drive, it says:

```
Unable to mount cdrom0

mount: block device /dev/sr0 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/sr0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

```
dmesg | tail
[  689.602821] end_request: I/O error, dev sr0, sector 745076
[  689.605651] end_request: I/O error, dev sr0, sector 746316
[  689.608625] end_request: I/O error, dev sr0, sector 745068
[  689.611752] end_request: I/O error, dev sr0, sector 1248
[  689.614603] end_request: I/O error, dev sr0, sector 2496
[  689.617574] end_request: I/O error, dev sr0, sector 1248
[  689.620439] end_request: I/O error, dev sr0, sector 2496
[  689.620463] UDF-fs: No partition found (1)
[  689.649473] end_request: I/O error, dev sr0, sector 64
[  689.649498] isofs_fill_super: bread failed, dev=sr0, iso_blknum=16, block=16
```

```
lsusb
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 011: ID 1058:1100 Western Digital Technologies, Inc. 
Bus 001 Device 008: ID 0a5c:2101 Broadcom Corp. A-Link BlueUsbA2 Bluetooth
Bus 001 Device 009: ID 0471:0333 Philips 
Bus 001 Device 007: ID 045e:00e1 Microsoft Corp. Wireless Laser Mouse 6000 Reciever
Bus 001 Device 006: ID 0930:6545 Toshiba Corp. 
Bus 001 Device 005: ID 0781:5406 SanDisk Corp. Cruzer Micro 1/4GB Flash Drive
Bus 001 Device 004: ID 0781:5406 SanDisk Corp. Cruzer Micro 1/4GB Flash Drive
Bus 001 Device 003: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
```

```
lspci
00:00.0 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation MCP67 ISA Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP67 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.3 Co-processor: nVidia Corporation MCP67 Co-processor (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:04.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:04.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP67 IDE Controller (rev a1)
00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP67 PCI Bridge (rev a2)
00:09.0 IDE interface: nVidia Corporation MCP67 AHCI Controller (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation MCP67 Ethernet (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:0d.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:12.0 VGA compatible controller: nVidia Corporation GeForce 7150M (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
02:05.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
02:05.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
02:05.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
02:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
02:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
```

---

### Post by Staesys on 2009-05-20
In addition, I can no longer click on URL's in my email or other programs and have Firefox open them. And did I mention my sounds all buggered up? Yeah, I can hear most stuff fine still, but skype refueses to work with any settings now, and when playing an audio cd (putting the cd in and starting VLC) the sound is very choppy.

At this point, I just want to undo the changes these updates made. At least my computer was 99% working at that point.

---

### Post by cong06 on 2009-07-17
edit: problem not related. Started my own thread.

---

