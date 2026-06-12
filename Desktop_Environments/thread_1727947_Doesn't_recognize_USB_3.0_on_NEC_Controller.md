---
title: "Doesn't recognize USB 3.0 on NEC Controller"
date: 2011-04-13
forum: Desktop Environments
---

### Post by der_mythos on 2011-04-13
Hi,

I've installed Kubuntu 10.10 and connected a USB 3.0 Western Digital Device.

Unfortunately the speed suxx  ... under Windows it has awesome speed.

Not shure if I've done anything wrong, cause I'm new to Linux.


here is my lsusb output:
```

Bus 008 Device 002: ID 1058:1130 Western Digital Technologies, Inc. 
Bus 008 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 010: ID 046d:c222 Logitech, Inc. G15 Keyboard / LCD
Bus 001 Device 009: ID 046d:c221 Logitech, Inc. G11/G15 Keyboard / Keyboard
Bus 001 Device 008: ID 046d:c049 Logitech, Inc. G5 Laser Mouse
Bus 001 Device 007: ID 1e3d:6025  
Bus 001 Device 006: ID 046d:c223 Logitech, Inc. G11/G15 Keyboard / USB Hub
Bus 001 Device 005: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 004: ID 0951:1607 Kingston Technology DataTraveler 100
Bus 001 Device 003: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 001 Device 002: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```
here is my lspci output:

```

00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge Alternate
00:01.0 PCI bridge: ASRock Incorporation Device 9602
00:09.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 4)
00:0a.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 5)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [IDE mode] (rev 40)
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 41)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller (rev 40)
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) (rev 40)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller (rev 40)
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (rev 40)
00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller
00:15.0 PCI bridge: ATI Technologies Inc Device 43a0
00:16.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:16.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS880 [Radeon HD 4290]
01:05.1 Audio device: ATI Technologies Inc RS880 Audio Device [Radeon HD 4200]
02:00.0 USB Controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 03)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
04:00.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6315 Series Firewire Controller (rev 01)

```
Hope this helps in any way

---

### Post by der_mythos on 2011-04-15
Nobody got an Idea?

Need any further Informations?

I'm really Stuck here :'(

---

### Post by der_mythos on 2011-04-17
No one?

---

### Post by 3rdalbum on 2011-04-17
NEC USB 3 controller support was implemented in Linux before it was in Windows. One thing springs to mind that might be causing low speed. Is your WD hard disk formatted as NTFS? That puts a severe bottleneck on speed on Linux. It should be formatted as Fat32 (uggh, someone kill it with fire already) or Ext3/4.

---

### Post by der_mythos on 2011-04-18
Hi,

your totaly right, it's ntfs.

Isn't there another way to get this fixxed, cause I have large files on this hd. (12gb+).

So NTFS seems perfect for me.

Fat32 can't take that huge files and Ext ... I would like to use the driver under some Windows Pcs as well.


thank you :)

---

### Post by der_mythos on 2011-04-20
Is there another Solution possible?

---

