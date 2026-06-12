---
title: "Wireless Problem"
date: 2009-03-18
forum: General Help
---

### Post by dixfam on 2009-03-18
I have an old Presario x1000 which was faulty and belonged to my daughter. I managed to fix it for $160, she didn't want it back and gave it me. So I thought I would put Ubuntu 8.10 on it. Everything works good except the broadband wireless which is very very slow. it starts off for about 20 secs then stops for a couple of minutes then starts up again, I have a 100% connection.
Sometimes it's at full speed but then the speed starts going from a norm of 30k a second then to 18, 13, 6, 2. this makes upgrading software a nightmare. I usually have to leave it going overnight.

Has anybody any idea why? I am a newby to Linux so solutions need to take this into account.

---

### Post by geometry_quiz on 2009-03-18
honestly sounds like a hardware issue. do you know if the device is functioning properly with any other computer or operating system?

---

### Post by sailthesea on 2009-03-18
What is your wireless connection?  I'll bet it's a Netgear usb  If it is there is a solution but wireless networking with some stuff is a real pain at the moment If you have a disk for it you can try and install the windows drivers using Ndswrapper in Synaptic 
 Good luck and get back!

---

### Post by dixfam on 2009-03-19
> **geometry_quiz said:**
> honestly sounds like a hardware issue. do you know if the device is functioning properly with any other computer or operating system?

Thanks for your comments. My daughter did use XP Home without any problems. She did have a graphics type problem, so I had to take her laptop apart, maybe I disturbed something fixing it.

I have no propriety drivers installed, relying on the Ubuntu to sort everything out. Everything else works O.K. shame really because Ubuntu looks a good operating system.

---

### Post by dixfam on 2009-03-19
> **sailthesea said:**
> What is your wireless connection?  I'll bet it's a Netgear usb  If it is there is a solution but wireless networking with some stuff is a real pain at the moment If you have a disk for it you can try and install the windows drivers using Ndswrapper in Synaptic 
 Good luck and get back!

Thanks. I do not have any drivers installed at the moment apart from the ones that came with Ubuntu. Do you think I should install the Windows drivers?

---

### Post by acimmarusti on 2009-03-19
Do you know the wireless adapter you are using? is it a PCI card? or USB?

if it's pci please post the output of:

```

lspci -v

```

Maybe you do require the proper firmware to make the device work properly. But I need to model to check that.

---

### Post by dixfam on 2009-03-19
> **acimmarusti said:**
> Do you know the wireless adapter you are using? is it a PCI card? or USB?

if it's pci please post the output of:

```

lspci -v

```

Maybe you do require the proper firmware to make the device work properly. But I need to model to check that.

Thanks this is what I got by putting in your command.

	Kernel modules: ipw2100

02:04.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller
	Subsystem: Compaq Computer Corporation Device 0860
	Flags: bus master, medium devsel, latency 168, IRQ 5
	Memory at 90100000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=02, secondary=03, subordinate=06, sec-latency=176
	Memory window 0: 30000000-33fff000 (prefetchable)
	Memory window 1: 38000000-3bfff000
	I/O window 0: 00002800-000028ff
	I/O window 1: 00002c00-00002cff
	16-bit legacy interface ports at 0001
	Kernel driver in use: yenta_cardbus
	Kernel modules: yenta_socket

03:00.0 Network controller: RaLink RT2561/RT61 802.11g PCI
	Subsystem: Belkin Device 701e
	Flags: bus master, slow devsel, latency 64, IRQ 5
	Memory at 38000000 (32-bit, non-prefetchable) [size=32K]
	Capabilities: <access denied>
	Kernel driver in use: rt61pci
	Kernel modules: rt61pci

---

### Post by acimmarusti on 2009-03-20
ok, now give me the output of these commands:

```

lsmod |grep -i -e rt61pci
lshw -C network

```

Let's see if the driver being used is the proper one.

---

### Post by fieroboom on 2009-03-20
Nevermind, I see where you're going...
:D
-Paul

---

### Post by dixfam on 2009-03-20
> **acimmarusti said:**
> ok, now give me the output of these commands:

```

lsmod |grep -i -e rt61pci
lshw -C network

```

Let's see if the driver being used is the proper one.
Thanks for your help.
This is what I got with your commands

rt61pci                27776  0 
crc_itu_t              10112  1 rt61pci
rt2x00pci              15104  1 rt61pci
rt2x00lib              36224  2 rt61pci,rt2x00pci
eeprom_93cx6           10240  1 rt61pci

Hope this helps

---

### Post by dixfam on 2009-03-20
> **acimmarusti said:**
> ok, now give me the output of these commands:

```

lsmod |grep -i -e rt61pci
lshw -C network

```

Let's see if the driver being used is the proper one.
Sorry as they say on the TV theres more:-

 *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 20
       serial: 00:02:3f:64:a6:35
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139cp driverversion=1.3 latency=128 maxlatency=64 mingnt=32 module=8139cp multicast=yes
  *-network:1
       description: Wireless interface
       product: PRO/Wireless LAN 2100 3B Mini PCI Adapter
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:02:02.0
       logical name: eth1
       version: 04
       serial: 00:04:23:68:c5:2b
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2100 driverversion=git-1.2.2 firmware=712.0.3:3:00000001 ip=192.168.1.100 latency=128 maxlatency=34 mingnt=2 module=ipw2100 multicast=yes wireless=IEEE 802.11b
  *-network
       description: Wireless interface
       product: RT2561/RT61 802.11g PCI
       vendor: RaLink
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wmaster0
       version: 00
       serial: 00:17:3f:29:48:17
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=rt61pci ip=192.168.1.101 latency=64 module=rt61pci multicast=yes wireless=IEEE 802.11bg

---

### Post by acimmarusti on 2009-03-23
that's what I thought. It seems you have two types of drivers loaded for two separate wireless devices...I'm actually confused at this point. The fact that you also have Intel's 2100 pci device is puzzling because it doesn't appear in the lspci -v command output! 

Could you try that again: lspci -v and look carefully for a "second" network wireless controller named Intel PRO/Wireless LAN 2100?

It should be present in the list.. please check

---

### Post by dixfam on 2009-03-23
> **acimmarusti said:**
> that's what I thought. It seems you have two types of drivers loaded for two separate wireless devices...I'm actually confused at this point. The fact that you also have Intel's 2100 pci device is puzzling because it doesn't appear in the lspci -v command output! 

Could you try that again: lspci -v and look carefully for a "second" network wireless controller named Intel PRO/Wireless LAN 2100?

It should be present in the list.. please check

Thanks for trying to help me.

I have put in the command again this is what I got :-
00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 03)
	Subsystem: Compaq Computer Corporation Device 0860
	Flags: bus master, fast devsel, latency 0
	Memory at b0000000 (32-bit, prefetchable) [size=256M]
	Capabilities: <access denied>
	Kernel driver in use: agpgart-intel
	Kernel modules: intel-agp

00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller (rev 03)
	Flags: bus master, 66MHz, fast devsel, latency 128
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 00003000-00003fff
	Memory behind bridge: 90400000-904fffff
	Prefetchable memory behind bridge: 98000000-9fffffff
	Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
	Subsystem: Compaq Computer Corporation Device 0860
	Flags: bus master, medium devsel, latency 0, IRQ 10
	I/O ports at 48c0 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
	Subsystem: Compaq Computer Corporation Device 0860
	Flags: bus master, medium devsel, latency 0, IRQ 5
	I/O ports at 48e0 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
	Subsystem: Compaq Computer Corporation Device 0860
	Flags: bus master, medium devsel, latency 0, IRQ 5
	I/O ports at 4c00 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01) (prog-if 20)
	Subsystem: Compaq Computer Corporation Device 0860
	Flags: bus master, medium devsel, latency 0, IRQ 5
	Memory at a0000000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd
	Kernel modules: ehci-hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=06, sec-latency=32
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: 90000000-903fffff
	Prefetchable memory behind bridge: 30000000-33ffffff
	Kernel modules: shpchp

00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
	Flags: bus master, medium devsel, latency 0
	Kernel modules: iTCO_wdt, intel-rng

00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01) (prog-if 8a [Master SecP PriP])
	Subsystem: Compaq Computer Corporation Device 0860
	Flags: bus master, medium devsel, latency 0, IRQ 5
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at 4c40 [size=16]
	Memory at 34000000 (32-bit, non-prefetchable) [size=1K]
	Kernel driver in use: ata_piix
	Kernel modules: ata_piix

00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
	Subsystem: Compaq Computer Corporation Device 0860
	Flags: medium devsel, IRQ 10
	I/O ports at 4c20 [size=32]
	Kernel modules: i2c-i801

00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
	Subsystem: Compaq Computer Corporation Device 0860
	Flags: bus master, medium devsel, latency 0, IRQ 10
	I/O ports at 4000 [size=256]
	I/O ports at 4880 [size=64]
	Memory at a0200000 (32-bit, non-prefetchable) [size=512]
	Memory at a0300000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: Intel ICH
	Kernel modules: snd-intel8x0

00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01)
	Subsystem: Compaq Computer Corporation Device 0860
	Flags: medium devsel, IRQ 10
	I/O ports at 4400 [size=256]
	I/O ports at 4800 [size=128]
	Capabilities: <access denied>
	Kernel modules: snd-intel8x0m

01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV250 [Mobility FireGL 9000] (rev 01)
	Subsystem: Compaq Computer Corporation Device 0860
	Flags: bus master, stepping, 66MHz, medium devsel, latency 128, IRQ 10
	Memory at 98000000 (32-bit, prefetchable) [size=128M]
	I/O ports at 3000 [size=256]
	Memory at 90400000 (32-bit, non-prefetchable) [size=64K]
	[virtual] Expansion ROM at 90420000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel modules: radeonfb

02:00.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller (rev 80) (prog-if 10)
	Subsystem: VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller
	Flags: bus master, medium devsel, latency 128, IRQ 10
	Memory at 90200000 (32-bit, non-prefetchable) [size=2K]
	I/O ports at 2400 [size=128]
	Capabilities: <access denied>
	Kernel driver in use: ohci1394
	Kernel modules: ohci1394

02:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 20)
	Subsystem: Compaq Computer Corporation Device 0860
	Flags: bus master, medium devsel, latency 128, IRQ 10
	I/O ports at 2000 [size=256]
	Memory at 90300000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: 8139cp
	Kernel modules: 8139cp, 8139too

02:02.0 Network controller: Intel Corporation PRO/Wireless LAN 2100 3B Mini PCI Adapter (rev 04)
	Subsystem: Intel Corporation Device 2522
	Flags: bus master, medium devsel, latency 128, IRQ 5
	Memory at 90000000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: ipw2100
	Kernel modules: ipw2100

02:04.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller
	Subsystem: Compaq Computer Corporation Device 0860
	Flags: bus master, medium devsel, latency 168, IRQ 5
	Memory at 90100000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=02, secondary=03, subordinate=06, sec-latency=176
	Memory window 0: 30000000-33fff000 (prefetchable)
	Memory window 1: 38000000-3bfff000
	I/O window 0: 00002800-000028ff
	I/O window 1: 00002c00-00002cff
	16-bit legacy interface ports at 0001
	Kernel driver in use: yenta_cardbus
	Kernel modules: yenta_socket

03:00.0 Network controller: RaLink RT2561/RT61 802.11g PCI
	Subsystem: Belkin Device 701e
	Flags: bus master, slow devsel, latency 64, IRQ 5
	Memory at 38000000 (32-bit, non-prefetchable) [size=32K]
	Capabilities: <access denied>
	Kernel driver in use: rt61pci
	Kernel modules: rt61pci

graham@graham-laptop:~$ 
The line I'M looking for seems to be there (Intel Corporation PRO/Wireless LAN 2100 3B) so I hope this helps.

---

### Post by acimmarusti on 2009-03-26
sorry I've been very busy.

I've been checking the specs on the presario x1000 and it seems it should only have one wireless network adapter...the Intel 2100. I don't know why it's detecting the other one, nor do I know if this issue could be causing your connection problems. If you receive no help from someone more knowledgeable, try posting again

---

