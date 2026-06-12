---
title: "Problem with wired connection since reboot..."
date: 2007-09-25
forum: Desktop Environments
---

### Post by MaxxJ on 2007-09-25
Everything was working very well before I installed the latest updates available and rebooted because required from the update manager...

Since then, NetworkManager Applet 0.6.4 (GNOME), is acting weird. I have not more Internet on the server... 
Now I rightclick the applet, uncheck "Enable Networking" : no Internet, obviously...
Then I rightclick it again, checking the "Enable Networking" : Internet is working, I can ping whoever I want.
Maybe a minute later, the applet says "Coinnection Established - You are now connected to the wired network", or something like this : no more Internet...

That's driving me crazy...

Here's the setup : eth0 and eth1 are two Ethernet plugs behind the computer, it normally uses eth0 since it's the one connected to the dlink router... (I checked this earlier using ifconfig to see what device was used and how much stuff went through it.)

---

### Post by MaxxJ on 2007-09-26
Here is /var/log/debug if it can help in any way :

```

Sep 26 07:20:08 BlackBox kernel: [    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
Sep 26 07:20:08 BlackBox kernel: [    0.000000] Entering add_active_range(0, 256, 524000) 1 entries of 3200 used
Sep 26 07:20:08 BlackBox kernel: [    0.000000] ACPI: RSDP (v000 Nvidia                                ) @ 0x00000000000f7f70
Sep 26 07:20:08 BlackBox kernel: [    0.000000] ACPI: RSDT (v001 Nvidia AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x000000007fee3040
Sep 26 07:20:08 BlackBox kernel: [    0.000000] ACPI: FADT (v001 Nvidia AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x000000007fee30c0
Sep 26 07:20:08 BlackBox kernel: [    0.000000] ACPI: SRAT (v001 AMD    HAMMER   0x00000001 AMD  0x00000001) @ 0x000000007fee92c0
Sep 26 07:20:08 BlackBox kernel: [    0.000000] ACPI: MCFG (v001 Nvidia AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x000000007fee93c0
Sep 26 07:20:08 BlackBox kernel: [    0.000000] ACPI: MADT (v001 Nvidia AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x000000007fee9200
Sep 26 07:20:08 BlackBox kernel: [    0.000000] ACPI: DSDT (v001 NVIDIA AWRDACPI 0x00001000 MSFT 0x0100000e) @ 0x0000000000000000
Sep 26 07:20:08 BlackBox kernel: [    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
Sep 26 07:20:08 BlackBox kernel: [    0.000000] Entering add_active_range(0, 0, 159) 1 entries of 3200 used
Sep 26 07:20:08 BlackBox kernel: [    0.000000] Entering add_active_range(0, 256, 524000) 1 entries of 3200 used
Sep 26 07:20:08 BlackBox kernel: [    0.000000] NUMA: Using 63 for the hash shift.
Sep 26 07:20:08 BlackBox kernel: [    0.000000] On node 0 totalpages: 523903
Sep 26 07:20:08 BlackBox kernel: [    0.000000]   DMA zone: 56 pages used for memmap
Sep 26 07:20:08 BlackBox kernel: [    0.000000]   DMA zone: 1087 pages reserved
Sep 26 07:20:08 BlackBox kernel: [    0.000000]   DMA zone: 2856 pages, LIFO batch:0
Sep 26 07:20:08 BlackBox kernel: [    0.000000]   DMA32 zone: 7108 pages used for memmap
Sep 26 07:20:08 BlackBox kernel: [    0.000000]   DMA32 zone: 512796 pages, LIFO batch:31
Sep 26 07:20:08 BlackBox kernel: [    0.000000]   Normal zone: 0 pages used for memmap
Sep 26 07:20:08 BlackBox kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Sep 26 07:20:08 BlackBox kernel: [    0.000000] ACPI: IRQ9 used by override.
Sep 26 07:20:08 BlackBox kernel: [    0.000000] ACPI: IRQ14 used by override.
Sep 26 07:20:08 BlackBox kernel: [    0.000000] ACPI: IRQ15 used by override.
Sep 26 07:20:08 BlackBox kernel: [   22.426917] PCI: Probing PCI hardware (bus 00)
Sep 26 07:20:08 BlackBox kernel: [   22.430512] Boot video device is 0000:06:00.0
Sep 26 07:20:08 BlackBox kernel: [   22.430573] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Sep 26 07:20:08 BlackBox kernel: [   22.512467] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
Sep 26 07:20:08 BlackBox kernel: [   22.539142] PCI: Setting latency timer of device 0000:00:09.0 to 64
Sep 26 07:20:08 BlackBox kernel: [   22.539156] PCI: Setting latency timer of device 0000:00:0b.0 to 64
Sep 26 07:20:08 BlackBox kernel: [   22.539162] PCI: Setting latency timer of device 0000:00:0c.0 to 64
Sep 26 07:20:08 BlackBox kernel: [   22.539168] PCI: Setting latency timer of device 0000:00:0d.0 to 64
Sep 26 07:20:08 BlackBox kernel: [   22.539173] PCI: Setting latency timer of device 0000:00:0e.0 to 64
Sep 26 07:20:08 BlackBox kernel: [   31.226292] PCI: Setting latency timer of device 0000:00:0b.0 to 64
Sep 26 07:20:08 BlackBox kernel: [   31.226316] Allocate Port Service[0000:00:0b.0:pcie00]
Sep 26 07:20:08 BlackBox kernel: [   31.226383] PCI: Setting latency timer of device 0000:00:0c.0 to 64
Sep 26 07:20:08 BlackBox kernel: [   31.226404] Allocate Port Service[0000:00:0c.0:pcie00]
Sep 26 07:20:08 BlackBox kernel: [   31.226459] PCI: Setting latency timer of device 0000:00:0d.0 to 64
Sep 26 07:20:08 BlackBox kernel: [   31.226480] Allocate Port Service[0000:00:0d.0:pcie00]
Sep 26 07:20:08 BlackBox kernel: [   31.226539] PCI: Setting latency timer of device 0000:00:0e.0 to 64
Sep 26 07:20:08 BlackBox kernel: [   31.226559] Allocate Port Service[0000:00:0e.0:pcie00]
Sep 26 07:20:08 BlackBox kernel: [   33.017430] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
Sep 26 07:20:08 BlackBox kernel: [   33.017926] PCI: Setting latency timer of device 0000:00:02.0 to 64
Sep 26 07:20:08 BlackBox kernel: [   33.096120] ieee1394: Initialized config rom entry `ip1394'
Sep 26 07:20:08 BlackBox kernel: [   33.221914] PCI: Setting latency timer of device 0000:00:02.1 to 64
Sep 26 07:20:08 BlackBox kernel: [   33.221985] PCI: cache line size of 64 is not supported by device 0000:00:02.1
Sep 26 07:20:08 BlackBox kernel: [   33.342646] libata version 2.20 loaded.
Sep 26 07:20:08 BlackBox kernel: [   33.344545] sata_nv 0000:00:07.0: version 3.3
Sep 26 07:20:08 BlackBox kernel: [   33.345144] PCI: Setting latency timer of device 0000:00:07.0 to 64
Sep 26 07:20:08 BlackBox kernel: [   33.773851] usb-storage: device found at 2
Sep 26 07:20:08 BlackBox kernel: [   33.773853] usb-storage: waiting for device to settle before scanning
Sep 26 07:20:08 BlackBox kernel: [   33.977988] PCI: Setting latency timer of device 0000:00:08.0 to 64
Sep 26 07:20:08 BlackBox kernel: [   34.782219] PCI: Setting latency timer of device 0000:00:0a.0 to 64
Sep 26 07:20:08 BlackBox kernel: [   34.794041] sda: Mode Sense: 00 3a 00 00
Sep 26 07:20:08 BlackBox kernel: [   34.794124] sda: Mode Sense: 00 3a 00 00
Sep 26 07:20:08 BlackBox kernel: [   34.981597] swsusp: Resume From Partition 8:5
Sep 26 07:20:08 BlackBox kernel: [   34.981599] PM: Checking swsusp image.
Sep 26 07:20:08 BlackBox kernel: [   34.981799] PM: Resume from disk failed.
Sep 26 07:20:08 BlackBox kernel: [   35.364017] Probing IDE interface ide0...
Sep 26 07:20:08 BlackBox kernel: [   36.639498] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00012920000344cf]
Sep 26 07:20:08 BlackBox kernel: [   36.788339] Probing IDE interface ide1...
Sep 26 07:20:08 BlackBox kernel: [   38.774563] usb-storage: device scan complete
Sep 26 07:20:08 BlackBox kernel: [   46.068044] irda_init()
Sep 26 07:20:08 BlackBox kernel: [   46.117437] bttv0: gpio: en=00000000, out=00000000 in=00ffffff [init]
Sep 26 07:20:08 BlackBox kernel: [   46.117455] i2c-algo-bit.o: (0) scl=1, sda=1
Sep 26 07:20:08 BlackBox kernel: [   46.117464] i2c-algo-bit.o: (1) scl=1, sda=0
Sep 26 07:20:08 BlackBox kernel: [   46.117472] i2c-algo-bit.o: (2) scl=1, sda=1
Sep 26 07:20:08 BlackBox kernel: [   46.117481] i2c-algo-bit.o: (3) scl=0, sda=1
Sep 26 07:20:08 BlackBox kernel: [   46.117490] i2c-algo-bit.o: (4) scl=1, sda=1
Sep 26 07:20:08 BlackBox kernel: [   46.151319] bttv1: gpio: en=00000000, out=00000000 in=00ffffff [init]
Sep 26 07:20:08 BlackBox kernel: [   46.151339] i2c-algo-bit.o: (0) scl=1, sda=0
Sep 26 07:20:08 BlackBox kernel: [   46.183247] bttv2: gpio: en=00000000, out=00000000 in=00ffffff [init]
Sep 26 07:20:08 BlackBox kernel: [   46.183266] i2c-algo-bit.o: (0) scl=0, sda=0
Sep 26 07:20:08 BlackBox kernel: [   47.032895] bttv3: gpio: en=00000000, out=00000000 in=00ffffff [init]
Sep 26 07:20:08 BlackBox kernel: [   47.032914] i2c-algo-bit.o: (0) scl=0, sda=0
Sep 26 07:20:08 BlackBox kernel: [   47.731074] PCI: Setting latency timer of device 0000:00:04.0 to 64
Sep 26 07:23:11 BlackBox NetworkManager: <debug info>^I[1190805791.614060] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_bluetooth').

```

That last line is weird since I don't have any bluetooth on this computer...

---

### Post by MaxxJ on 2007-09-26
Oh, here is the ifconfig too :

```

eth0      Link encap:Ethernet  HWaddr ********
          inet addr:192.168.0.102  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:56 errors:0 dropped:0 overruns:0 frame:0
          TX packets:92 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:6632 (6.4 KiB)  TX bytes:10717 (10.4 KiB)
          Interrupt:21 Base address:0xe000

eth1      Link encap:Ethernet  HWaddr ********
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:18

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

```

Restarted it again and it takes about 1 min before it gets disconnected...

---

### Post by MaxxJ on 2007-09-29
Wow... didn't think that was such an issue!
I tried some things since then... no success.
Since I'm getting some very weird bugs with unbuntu and that I don't get so much help with it (in general)... I though I might wipe the server (as it was in a very early stage) and try another distribution, to see if the problem is the distro or something else... As I log everything I do and research before doing it, I hardly see how it couldn't be the distribution, but that's the test.

So, if there ever is a genius coming by with an answer to this, still post it, that doesn't mean I won't ever have this problem again, nor that I won't come back to ubuntu someday.

MJ

---

