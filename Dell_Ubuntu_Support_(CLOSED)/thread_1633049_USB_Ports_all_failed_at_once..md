---
title: "USB Ports all failed at once."
date: 2010-11-28
forum: Dell Ubuntu Support (CLOSED)
---

### Post by nate7784 on 2010-11-28
Hi all,

I made the jump to Linux using Ubuntu a few weeks ago for the first time on my old Dell D410 laptop. Love it, but this past week all the USB ports stopped working. I have tried multiple flash drives/devices and the OS does not ever pick up that anything is ever plugged in to any of the ports. As I said, I'm quite novice to Linux but any help would be appreciated, and I'll do my best to provide further details if needed.

Thanks

---

### Post by JC Cheloven on 2010-11-28
Hi,
First thing to see is whether it's a hardware issue or not (it could be). Have you windows installed, or some other live distro to try out if usb ports work?

Also, what is the output of lspci and lsusb (at terminal)?

---

### Post by nate7784 on 2010-11-28
No, all I have on there is Ubuntu 10.10. I can vouch for the workability of the usb devices as they all work on my other computer just fine.

---

### Post by nate7784 on 2010-11-28
ps. the other computer is running windows 7.

---

### Post by JC Cheloven on 2010-11-28
OK, even so, if usb ports worked before, and you have a live CD (from where probably you installed), you could boot that live cd just to see if usb ports work. 
That would discard / confirm the hardware thing.

Mmmm...  could also be a bios setup, as usb are controlled by the bios in modern pc's. But it would be strange unless you changed something there.

---

### Post by nate7784 on 2010-11-28
Actually, there was a bug with the cd install version so I used a USB drive to install 10.10. Consequently I have formatted that USB drive for other uses, so I don't have that either. I have not messed with BIOS and checked to make USB is indeed enabled still in BIOS.

---

### Post by JC Cheloven on 2010-11-29
Fine, but where did you created the usb pendrive from? Not from the bad CD, I hope. Again, if you feel like it, you could:

- Burn any live distro to CD, to try your usb ports. If you don't want a big download, even [SliTaz]("http://www.slitaz.org/") (only 30Mb!) should do. 

- From your installed system, tell us the output of
```
lsusb
```
```
lspci
```

---

### Post by matt_symes on 2010-11-29
Hi

As well as the other commands suggested, when you plug a USB device into a usb port what is the output of (in a terminal)

dmesg | tail -n15

Kind regards

---

### Post by nate7784 on 2010-11-29
@JC, no I used the USB flash install from Ubuntu's website. Also, my cd drive is a USB plug in device as well. So when USB goes down, I have no way to do any input besides the internet. Is there a way for me to boot a separate distro install from the hard-drive? 


@Matt, I'm very much a newbie so how do I get the output in the terminal window to show up?

---

### Post by matt_symes on 2010-11-29
Hi

> **nate7784 said:**
> @JC, no I used the USB flash install from Ubuntu's website. Also, my cd drive is a USB plug in device as well. So when USB goes down, I have no way to do any input besides the internet. Is there a way for me to boot a separate distro install from the hard-drive? 

@Matt, I'm very much a newbie so how do I get the output in the terminal window to show up?

What you need to do is open a terminal and type

lsusb
[FONT=monospace]
[/FONT]Hightlight the text returned by the command using the mouse and press 

shift Ctrl C

at the same time. This will copy it to the clipboard. You can then paste it into the post using 

Ctrl C

Yes. the two sets of key presses are different.

Repeat for lspci and also for dmesg | tail -n15 just after pluging in a USB device. Ths will show if the kernel recoginsed it.

Kind regards

[FONT=monospace]
[/FONT]

---

### Post by nate7784 on 2010-11-29
lsusb:

nate@nate-laptop:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 413c:8103 Dell Computer Corp. Wireless 350 Bluetooth
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 007: ID 0ecd:a100 Lite-On IT Corp. LDW-411SX DVD/CD Rewritable Drive
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

lspci:

nate@nate-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
01:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5751 Gigabit Ethernet PCI Express (rev 01)
02:01.0 CardBus bridge: Texas Instruments PCI6515 Cardbus Controller
02:01.5 Communication controller: Texas Instruments PCI6515 SmartCard Controller
02:03.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

dmesg:
[    0.266670] pci 0000:02:01.0:   bridge window [mem 0x88000000-0x8bffffff]
[    0.266676] pci 0000:00:1e.0: PCI bridge to [bus 02-03]
[    0.266678] pci 0000:00:1e.0:   bridge window [io  disabled]
[    0.266685] pci 0000:00:1e.0:   bridge window [mem 0xdfc00000-0xdfcfffff]
[    0.266690] pci 0000:00:1e.0:   bridge window [mem 0x80000000-0x83ffffff pref]
[    0.266713]   alloc irq_desc for 16 on node -1
[    0.266715]   alloc kstat_irqs on node -1
[    0.266724] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.266731] pci 0000:00:1c.0: setting latency timer to 64
[    0.266740] pci 0000:00:1e.0: setting latency timer to 64
[    0.266752] pci 0000:02:01.0: enabling device (0000 -> 0003)
[    0.266757]   alloc irq_desc for 19 on node -1
[    0.266759]   alloc kstat_irqs on node -1
[    0.266764] pci 0000:02:01.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    0.266773] pci_bus 0000:00: resource 0 [io  0x0000-0xffff]
[    0.266776] pci_bus 0000:00: resource 1 [mem 0x00000000-0xffffffff]
[    0.266779] pci_bus 0000:01: resource 1 [mem 0xdfd00000-0xdfdfffff]
[    0.266782] pci_bus 0000:01: resource 2 [mem 0x84000000-0x841fffff 64bit pref]
[    0.266785] pci_bus 0000:02: resource 1 [mem 0xdfc00000-0xdfcfffff]
[    0.266788] pci_bus 0000:02: resource 2 [mem 0x80000000-0x83ffffff pref]
[    0.266790] pci_bus 0000:02: resource 4 [io  0x0000-0xffff]
[    0.266793] pci_bus 0000:02: resource 5 [mem 0x00000000-0xffffffff]
[    0.266796] pci_bus 0000:03: resource 0 [io  0x1400-0x14ff]
[    0.266799] pci_bus 0000:03: resource 1 [io  0x1800-0x18ff]
[    0.266802] pci_bus 0000:03: resource 2 [mem 0x80000000-0x83ffffff pref]
[    0.266804] pci_bus 0000:03: resource 3 [mem 0x88000000-0x8bffffff]
[    0.266852] NET: Registered protocol family 2
[    0.266924] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.267199] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.268362] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.269070] TCP: Hash tables configured (established 131072 bind 65536)
[    0.269074] TCP reno registered
[    0.269080] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.269106] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.269280] NET: Registered protocol family 1
[    0.269311] pci 0000:00:02.0: Boot video device
[    0.269445] PCI: CLS 64 bytes, default 64
[    0.269673] cpufreq-nforce2: No nForce2 chipset.
[    0.269708] Scanning for low memory corruption every 60 seconds
[    0.269914] audit: initializing netlink socket (disabled)
[    0.269931] type=2000 audit(1290993787.264:1): initialized
[    0.281481] Trying to unpack rootfs image as initramfs...
[    0.296104] highmem bounce pool size: 64 pages
[    0.296111] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.304089] VFS: Disk quotas dquot_6.5.2
[    0.304177] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.304889] fuse init (API version 7.14)
[    0.304988] msgmni has been set to 1683
[    0.312490] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.312495] io scheduler noop registered
[    0.312497] io scheduler deadline registered
[    0.312516] io scheduler cfq registered (default)
[    0.312646] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.312695]   alloc irq_desc for 40 on node -1
[    0.312697]   alloc kstat_irqs on node -1
[    0.312712] pcieport 0000:00:1c.0: irq 40 for MSI/MSI-X
[    0.312841] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.312904] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.313566] ACPI: AC Adapter [AC] (off-line)
[    0.313668] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
[    0.314356] ACPI: Lid Switch [LID]
[    0.314411] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1
[    0.314417] ACPI: Power Button [PBTN]
[    0.314467] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input2
[    0.314471] ACPI: Sleep Button [SBTN]
[    0.314655] ACPI: acpi_idle registered with cpuidle
[    0.314875] Marking TSC unstable due to TSC halts in idle
[    0.322948] Switching to clocksource hpet
[    0.346745] thermal LNXTHERM:01: registered as thermal_zone0
[    0.346754] ACPI: Thermal Zone [THM] (48 C)
[    0.352444] ERST: Table is not found!
[    0.352625] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.353058]   alloc irq_desc for 17 on node -1
[    0.353061]   alloc kstat_irqs on node -1
[    0.353071] serial 0000:00:1e.3: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.353079] serial 0000:00:1e.3: PCI INT B disabled
[    0.354268] brd: module loaded
[    0.354834] loop: module loaded
[    0.355050] ata_piix 0000:00:1f.1: version 2.13
[    0.355062] ata_piix 0000:00:1f.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.355111] ata_piix 0000:00:1f.1: setting latency timer to 64
[    0.360038] scsi0 : ata_piix
[    0.364089] isapnp: Scanning for PnP cards...
[    0.372058] scsi1 : ata_piix
[    0.434604] ACPI: Battery Slot [BAT1] (battery absent)
[    0.435138] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xbfa0 irq 14
[    0.435143] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xbfa8 irq 15
[    0.435541] Fixed MDIO Bus: probed
[    0.435579] PPP generic driver version 2.4.2
[    0.435653] tun: Universal TUN/TAP device driver, 1.6
[    0.435655] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.435752] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.435781] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.435803] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.435807] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.435840] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    0.435874] ehci_hcd 0000:00:1d.7: debug port 1
[    0.439778] ehci_hcd 0000:00:1d.7: cache line size of 64 is not supported
[    0.439803] ehci_hcd 0000:00:1d.7: irq 16, io mem 0xffa80800
[    0.451374] ata2: port disabled. ignoring.
[    0.468090] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.468298] hub 1-0:1.0: USB hub found
[    0.468306] hub 1-0:1.0: 8 ports detected
[    0.468402] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.468421] uhci_hcd: USB Universal Host Controller Interface driver
[    0.468477] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.468492] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.468496] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.468543] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.468577] uhci_hcd 0000:00:1d.0: irq 16, io base 0x0000bf80
[    0.468709] hub 2-0:1.0: USB hub found
[    0.468713] hub 2-0:1.0: 2 ports detected
[    0.468776] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.468784] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.468787] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.468822] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    0.468864] uhci_hcd 0000:00:1d.1: irq 17, io base 0x0000bf60
[    0.468984] hub 3-0:1.0: USB hub found
[    0.468994] hub 3-0:1.0: 2 ports detected
[    0.469053]   alloc irq_desc for 18 on node -1
[    0.469056]   alloc kstat_irqs on node -1
[    0.469064] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.469071] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.469075] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.469109] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    0.469147] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000bf40
[    0.469279] hub 4-0:1.0: USB hub found
[    0.469283] hub 4-0:1.0: 2 ports detected
[    0.469340] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.469348] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    0.469352] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    0.469389] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    0.469426] uhci_hcd 0000:00:1d.3: irq 19, io base 0x0000bf20
[    0.469548] hub 5-0:1.0: USB hub found
[    0.469553] hub 5-0:1.0: 2 ports detected
[    0.469687] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    0.476898] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.476910] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.477046] mice: PS/2 mouse device common for all mice
[    0.477264] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    0.477297] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    0.477444] device-mapper: uevent: version 1.0.3
[    0.480831] device-mapper: ioctl: 4.17.0-ioctl (2010-03-05) initialised: [email]dm-devel@redhat.com[/email]
[    0.482094] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    0.485534] device-mapper: multipath: version 1.1.1 loaded
[    0.485538] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.492224] EISA: Probing bus 0 at eisa.0
[    0.492235] Cannot allocate resource for EISA slot 1
[    0.492268] EISA: Detected 0 cards.
[    0.492390] cpuidle: using governor ladder
[    0.492461] cpuidle: using governor menu
[    0.492766] TCP cubic registered
[    0.492912] NET: Registered protocol family 10
[    0.493292] lo: Disabled Privacy Extensions
[    0.493512] NET: Registered protocol family 17
[    0.636653] ata1.00: ATA-6: TOSHIBA MK8026GAX, PA002D, max UDMA/100
[    0.636658] ata1.00: 156301488 sectors, multi 8: LBA 
[    0.644842] ata1.00: configured for UDMA/100
[    0.716117] Using IPI No-Shortcut mode
[    0.716252] PM: Resume from disk failed.
[    0.716265] registered taskstats version 1
[    0.716518]   Magic number: 2:137:358
[    0.716643] rtc_cmos 00:06: setting system clock to 2010-11-29 01:23:08 UTC (1290993788)
[    0.716647] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.716649] EDD information not available.
[    0.725639] ACPI: Battery Slot [BAT0] (battery present)
[    0.807739] usb 1-1: new high speed USB device using ehci_hcd and address 2
[    0.986715] Freeing initrd memory: 10516k freed
[    1.039212] isapnp: No Plug & Play device found
[    1.039443] scsi 0:0:0:0: Direct-Access     ATA      TOSHIBA MK8026GA PA00 PQ: 0 ANSI: 5
[    1.039669] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.039790] sd 0:0:0:0: [sda] 156301488 512-byte logical blocks: (80.0 GB/74.5 GiB)
[    1.039847] sd 0:0:0:0: [sda] Write Protect is off
[    1.039851] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.039876] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.040079]  sda: sda1 sda2 < sda5 >
[    1.123704] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.123724] Freeing unused kernel memory: 684k freed
[    1.124238] Write protecting the kernel text: 4932k
[    1.124277] Write protecting the kernel read-only data: 1976k
[    1.139628] udev[69]: starting version 163
[    1.389271] tg3.c:v3.110 (April 9, 2010)
[    1.389301] tg3 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.389313] tg3 0000:01:00.0: setting latency timer to 64
[    1.404044] usb 3-1: new full speed USB device using uhci_hcd and address 2
[    1.410723] tg3 0000:01:00.0: eth0: Tigon3 [partno(BCM95751) rev 4001] (PCI Express) MAC address 00:12:3f:21:47:fc
[    1.410727] tg3 0000:01:00.0: eth0: attached PHY is 5750 (10/100/1000Base-T Ethernet) (WireSpeed[1])
[    1.410731] tg3 0000:01:00.0: eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1]
[    1.410734] tg3 0000:01:00.0: eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[    1.679757] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[   19.248817] udev[322]: starting version 163
[   19.336998] lp: driver loaded but no devices found
[   19.342129] Adding 3227644k swap on /dev/sda5.  Priority:-1 extents:1 across:3227644k 
[   19.497987] intel_rng: FWH not detected
[   19.529668] Disabling lock debugging due to kernel taint
[   19.577602] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   19.710807] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A03:00/LNXVIDEO:00/input/input4
[   19.710875] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[   19.710906] [Firmware Bug]: Duplicate ACPI video bus devices for the same VGA controller, please try module parameter "video.allow_duplicates=1"if the current driver doesn't work.
[   19.748855] Linux agpgart interface v0.103
[   19.815588] ndiswrapper version 1.56 loaded (smp=yes, preempt=no)
[   19.868783] yenta_cardbus 0000:02:01.0: CardBus bridge found [1028:018f]
[   19.868808] yenta_cardbus 0000:02:01.0: Using CSCINT to route CSC interrupts to PCI
[   19.868811] yenta_cardbus 0000:02:01.0: Routing CardBus interrupts to PCI
[   19.868819] yenta_cardbus 0000:02:01.0: TI: mfunc 0x01111122, devctl 0x64
[   19.883404] cdc_acm 1-1:1.0: ttyACM0: USB ACM device
[   19.887519] usbcore: registered new interface driver cdc_acm
[   19.887523] cdc_acm: v0.26:USB Abstract Control Model driver for USB modems and ISDN adapters
[   19.889394] agpgart-intel 0000:00:00.0: Intel 915GM Chipset
[   19.890047] agpgart-intel 0000:00:00.0: detected 7932K stolen memory
[   19.918167] Bluetooth: Core ver 2.15
[   19.918228] NET: Registered protocol family 31
[   19.918231] Bluetooth: HCI device and connection manager initialized
[   19.918234] Bluetooth: HCI socket layer initialized
[   19.923530] Bluetooth: Generic Bluetooth USB driver ver 0.6
[   19.934586] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xc0000000
[   19.939332] usbcore: registered new interface driver btusb
[   20.024497] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   20.026327] type=1400 audit(1290993807.807:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient3" pid=616 comm="apparmor_parser"
[   20.026968] type=1400 audit(1290993807.807:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=616 comm="apparmor_parser"
[   20.032502] type=1400 audit(1290993807.815:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=616 comm="apparmor_parser"
[   20.100893] yenta_cardbus 0000:02:01.0: ISA IRQ mask 0x0cf8, PCI irq 19
[   20.100900] yenta_cardbus 0000:02:01.0: Socket status: 30000006
[   20.100904] pci_bus 0000:02: Raising subordinate bus# of parent bus (#02) from #03 to #06
[   20.100917] yenta_cardbus 0000:02:01.0: pcmcia: parent PCI bridge window: [mem 0xdfc00000-0xdfcfffff]
[   20.100921] pcmcia_socket pcmcia_socket0: cs: memory probe 0xdfc00000-0xdfcfffff: excluding 0xdfc00000-0xdfc0ffff 0xdfcf0000-0xdfcfffff
[   20.100938] yenta_cardbus 0000:02:01.0: pcmcia: parent PCI bridge window: [mem 0x80000000-0x83ffffff pref]
[   20.100942] pcmcia_socket pcmcia_socket0: cs: memory probe 0x80000000-0x83ffffff: excluding 0x80000000-0x83ffffff
[   20.110439] [drm] Initialized drm 1.1.0 20060810
[   20.224576] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   20.224583] i915 0000:00:02.0: setting latency timer to 64
[   20.230676] [drm] set up 7M of stolen space
[   20.359175] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: excluding 0x170-0x177 0x1f0-0x1f7 0x370-0x377
[   20.361002] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: excluding 0x3f0-0x3f7 0x4d0-0x4d7
[   20.361763] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[   20.362394] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
[   20.363089] pcmcia_socket pcmcia_socket0: cs: memory probe 0x0c0000-0x0fffff: excluding 0xc0000-0xc7fff 0xcc000-0xcffff 0xf0000-0xfffff
[   20.363148] pcmcia_socket pcmcia_socket0: cs: memory probe 0xa0000000-0xa0ffffff: clean.
[   20.363204] pcmcia_socket pcmcia_socket0: cs: memory probe 0x60000000-0x60ffffff: excluding 0x60000000-0x60ffffff
[   20.363260] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[   20.502129] ndiswrapper: driver bcmwl5 (Broadcom,10/12/2006, 4.100.15.5) loaded
[   20.502416] ndiswrapper 0000:02:03.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   20.506627] ndiswrapper: using IRQ 17
[   20.811965] input: DualPoint Stick as /devices/platform/i8042/serio1/input/input5
[   20.835834] input: AlpsPS/2 ALPS DualPoint TouchPad as /devices/platform/i8042/serio1/input/input6
[   21.112851] type=1400 audit(1290993808.895:5): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=821 comm="apparmor_parser"
[   21.119372] type=1400 audit(1290993808.899:6): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=823 comm="apparmor_parser"
[   21.120058] type=1400 audit(1290993808.903:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=823 comm="apparmor_parser"
[   21.132984] type=1400 audit(1290993808.915:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=823 comm="apparmor_parser"
[   21.158308] type=1400 audit(1290993808.939:9): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=826 comm="apparmor_parser"
[   21.181410] type=1400 audit(1290993808.963:10): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-previewer" pid=826 comm="apparmor_parser"
[   21.188636] type=1400 audit(1290993808.971:11): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-thumbnailer" pid=826 comm="apparmor_parser"
[   21.200998] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   21.452604] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[   21.453102] [drm] initialized overlay support
[   21.954177] wlan0: ethernet device 00:0b:7d:1b:16:d2 using NDIS driver: bcmwl5, version: 0x4640f05, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 14E4:4320.5.conf
[   21.983423] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[   21.995884] usbcore: registered new interface driver ndiswrapper
[   22.010144] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   22.360183] Skipping EDID probe due to cached edid
[   22.823729] Console: switching to colour frame buffer device 128x48
[   22.827239] fb0: inteldrmfb frame buffer device
[   22.827241] drm: registered panic notifier
[   22.836018] Slow work thread pool: Starting up
[   22.840170] Slow work thread pool: Ready
[   22.840189] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   22.840425] Intel ICH 0000:00:1e.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   22.840460] Intel ICH 0000:00:1e.2: setting latency timer to 64
[   23.290496] Bluetooth: L2CAP ver 2.14
[   23.290499] Bluetooth: L2CAP socket layer initialized
[   23.300464] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   23.300468] Bluetooth: BNEP filters: protocol multicast
[   23.308438] Bluetooth: SCO (Voice Link) ver 0.6
[   23.308442] Bluetooth: SCO socket layer initialized
[   23.312240] Skipping EDID probe due to cached edid
[   23.579994] Bluetooth: RFCOMM TTY layer initialized
[   23.580321] Bluetooth: RFCOMM socket layer initialized
[   23.580324] Bluetooth: RFCOMM ver 1.11
[   23.668029] intel8x0_measure_ac97_clock: measured 55469 usecs (2672 samples)
[   23.668033] intel8x0: clocking to 48000
[   24.605103] ppdev: user-space parallel port driver
[   25.588221] Skipping EDID probe due to cached edid
[   25.781197] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=600
[   26.300390] Skipping EDID probe due to cached edid
[   27.444325] Skipping EDID probe due to cached edid
[   28.164327] Skipping EDID probe due to cached edid
[   28.872324] Skipping EDID probe due to cached edid
[   29.580319] Skipping EDID probe due to cached edid
[   31.372204] Skipping EDID probe due to cached edid
[   32.527923] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=600
[  327.192365] Skipping EDID probe due to cached edid
[ 2128.939382] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[ 2129.620611] tg3 0000:01:00.0: PME# enabled
[ 2129.620643] tg3 0000:01:00.0: wake-up capability enabled by ACPI
[ 2129.999783] PM: Marking nosave pages: 0000000000002000 - 0000000000010000
[ 2129.999788] PM: Marking nosave pages: 000000000009f000 - 0000000000100000
[ 2129.999791] PM: Basic memory bitmaps created
[ 2129.999793] PM: Syncing filesystems ... done.
[ 2130.283203] Freezing user space processes ... (elapsed 0.01 seconds) done.
[ 2130.296034] Freezing remaining freezable tasks ... (elapsed 0.01 seconds) done.
[ 2130.312041] PM: Preallocating image memory... done (allocated 74979 pages)
[ 2130.392131] PM: Allocated 299916 kbytes in 0.08 seconds (3748.95 MB/s)
[ 2130.392134] Suspending console(s) (use no_console_suspend to debug)
[ 2130.393172] ACPI handle has no context!
[ 2130.393608] sd 0:0:0:0: [sda] Synchronizing SCSI cache
[ 2130.394765] btusb_intr_complete: hci0 urb f3600280 failed to resubmit (1)
[ 2130.403731] ata2: port disabled. ignoring.
[ 2130.403781] ata_piix 0000:00:1f.1: PCI INT A disabled
[ 2130.403996] Intel ICH 0000:00:1e.2: PCI INT A disabled
[ 2130.404761] btusb_bulk_complete: hci0 urb f3600480 failed to resubmit (1)
[ 2130.405761] btusb_bulk_complete: hci0 urb f3600a80 failed to resubmit (1)
[ 2130.405806] PM: freeze of devices complete after 13.397 msecs
[ 2130.406634] PM: late freeze of devices complete after 0.822 msecs
[ 2130.409397] ACPI: Preparing to enter system sleep state S4
[ 2130.409874] PM: Saving platform NVS memory
[ 2130.409891] PM: Saving platform NVS memory
[ 2130.409893] Disabling non-boot CPUs ...
[ 2130.410021] PM: Creating hibernation image:
[ 2130.412078] PM: Need to copy 74777 pages
[ 2130.412078] PM: Normal pages needed: 26880 + 1024, available pages: 200299
[ 2130.412078] PM: Restoring platform NVS memory
[ 2130.412078] Force enabled HPET at resume
[ 2130.412078] ACPI: Waking up from system sleep state S4
[ 2130.416760] i915 0000:00:02.0: restoring config space at offset 0x1 (was 0x900003, writing 0x900007)
[ 2130.417026] pci 0000:00:1e.0: restoring config space at offset 0x6 (was 0x20030200, writing 0x20060200)
[ 2130.417075] Intel ICH 0000:00:1e.2: restoring config space at offset 0x1 (was 0x2900007, writing 0x2900003)
[ 2130.417183] ata_piix 0000:00:1f.1: restoring config space at offset 0x1 (was 0x2880001, writing 0x2880005)
[ 2130.417228] tg3 0000:01:00.0: restoring config space at offset 0xc (was 0x0, writing 0xf7fc0000)
[ 2130.417293] yenta_cardbus 0000:02:01.0: restoring config space at offset 0xf (was 0x74001ff, writing 0x5c001ff)
[ 2130.417319] yenta_cardbus 0000:02:01.0: restoring config space at offset 0x3 (was 0x824010, writing 0x82a810)
[ 2130.417923] PM: early restore of devices complete after 1.279 msecs
[ 2130.452149] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[ 2130.452190] usb usb2: root hub lost power or was reset
[ 2130.452212] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[ 2130.452247] usb usb3: root hub lost power or was reset
[ 2130.452266] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[ 2130.452301] usb usb4: root hub lost power or was reset
[ 2130.452322] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[ 2130.452359] usb usb5: root hub lost power or was reset
[ 2130.452379] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[ 2130.452398] usb usb1: root hub lost power or was reset
[ 2130.456275] ehci_hcd 0000:00:1d.7: cache line size of 64 is not supported
[ 2130.456300] Intel ICH 0000:00:1e.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[ 2130.456307] Intel ICH 0000:00:1e.2: setting latency timer to 64
[ 2130.456343] ata_piix 0000:00:1f.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[ 2130.456348] ata_piix 0000:00:1f.1: setting latency timer to 64
[ 2130.456447] sd 0:0:0:0: [sda] Starting disk
[ 2130.456554] ata1.00: _GTF evaluation failed (AE 0x1001)
[ 2130.456986] ata2: port disabled. ignoring.
[ 2130.460080] i915 0000:00:02.0: setting latency timer to 64
[ 2130.906418] pci 0000:00:1e.0: setting latency timer to 64
[ 2130.906424] PM: restore of drv:pci dev:0000:00:1e.0 complete after 450.140 msecs
[ 2130.906433] PM: restore of drv:yenta_cardbus dev:0000:02:01.0 complete after 450.061 msecs
[ 2130.906438] PM: restore of drv:pci dev:0000:02:01.5 complete after 450.064 msecs
[ 2130.906717] PM: restore of drv:ndiswrapper dev:0000:02:03.0 complete after 450.338 msecs
[ 2130.920459] ata1.00: configured for UDMA/100
[ 2130.980923] PM: restore of drv:sd dev:0:0:0:0 complete after 524.478 msecs
[ 2130.980944] PM: restore of drv:scsi_device dev:0:0:0:0 complete after 524.471 msecs
[ 2131.722044] PM: restore of drv:usb dev:usb4 complete after 1265.621 msecs
[ 2131.722060] PM: restore of drv:usb dev:usb5 complete after 1265.629 msecs
[ 2131.724194] PM: restore of drv:hub dev:4-0:1.0 complete after 1267.765 msecs
[ 2131.724199] PM: restore of drv:hub dev:5-0:1.0 complete after 1267.762 msecs
[ 2131.726688] PM: restore of drv:battery dev:PNP0C0A:00 complete after 1269.168 msecs
[ 2131.764311] PM: restore of drv:i915 dev:0000:00:02.0 complete after 1312.191 msecs
[ 2131.824162] PM: restore of drv:usb dev:usb2 complete after 1367.758 msecs
[ 2131.824170] PM: restore of drv:usb dev:usb3 complete after 1367.757 msecs
[ 2131.824177] PM: restore of drv:hub dev:2-0:1.0 complete after 1367.766 msecs
[ 2131.824182] PM: restore of drv:hub dev:3-0:1.0 complete after 1367.763 msecs
[ 2131.909725] PM: restore of drv:Intel ICH dev:0000:00:1e.2 complete after 1453.435 msecs
[ 2131.944166] PM: restore of drv:usb dev:usb1 complete after 1487.772 msecs
[ 2131.944173] PM: restore of drv:hub dev:1-0:1.0 complete after 1487.773 msecs
[ 2131.944193] PM: restore of drv: dev:ep_81 complete after 214.308 msecs
[ 2132.056167] usb 1-1: reset high speed USB device using ehci_hcd and address 2
[ 2132.188199] usb 1-1: device firmware changed
[ 2132.188212] PM: restore of drv:usb dev:1-1 complete after 1731.736 msecs
[ 2132.188226] PM: restore of drv:cdc_acm dev:1-1:1.0 complete after 1731.746 msecs
[ 2132.188232] PM: restore of drv:cdc_acm dev:1-1:1.1 complete after 1731.749 msecs
[ 2132.188237] PM: restore of drv:usb dev:1-1:1.2 complete after 1731.751 msecs
[ 2132.188243] PM: restore of drv: dev:ep_81 complete after 242.737 msecs
[ 2132.300163] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[ 2132.462985] btusb 3-1:1.0: no reset_resume for driver btusb?
[ 2132.462987] btusb 3-1:1.1: no reset_resume for driver btusb?
[ 2132.712254] PM: restore of drv:usb dev:3-1 complete after 2255.764 msecs
[ 2132.712263] PM: restore of drv:usb dev:3-1:1.0 complete after 2255.770 msecs
[ 2132.712268] PM: restore of drv:usb dev:3-1:1.1 complete after 2255.772 msecs
[ 2132.712273] PM: restore of drv:usb dev:3-1:1.2 complete after 2255.774 msecs
[ 2132.712279] PM: restore of drv: dev:ep_81 complete after 524.008 msecs
[ 2132.852167] PM: restore of drv:pcmcia_socket dev:pcmcia_socket0 complete after 139.810 msecs
[ 2132.852249] PM: restore of devices complete after 2404.176 msecs
[ 2132.852644] PM: Image restored successfully.
[ 2132.852647] Restarting tasks ... done.
[ 2132.852877] PM: Basic memory bitmaps freed
[ 2132.852881] video LNXVIDEO:00: Restoring backlight state
[ 2132.852950] usb 1-1: USB disconnect, address 2
[ 2132.964068] usb 1-1: new high speed USB device using ehci_hcd and address 4
[ 2133.104429] tg3 0000:01:00.0: wake-up capability disabled by ACPI
[ 2133.104442] tg3 0000:01:00.0: PME# disabled
[ 2133.139641] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 2133.141602] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2133.222294] Skipping EDID probe due to cached edid
[ 2133.883792] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[ 2134.538019] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[ 2149.936356] Skipping EDID probe due to cached edid
[ 2150.652427] Skipping EDID probe due to cached edid
[ 2151.364494] Skipping EDID probe due to cached edid
[ 2152.076356] Skipping EDID probe due to cached edid
[ 2154.240233] Skipping EDID probe due to cached edid
[ 2158.492244] Skipping EDID probe due to cached edid
[ 2159.526144] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 2170.448173] wlan0: no IPv6 routers present
[ 2351.804705] usb 1-1: USB disconnect, address 4
[ 2383.000190] usb 1-1: new high speed USB device using ehci_hcd and address 5
[ 2979.200357] Skipping EDID probe due to cached edid
[ 3471.770278] usb 1-1: USB disconnect, address 5
[ 3508.604186] usb 1-1: new high speed USB device using ehci_hcd and address 6
[ 3560.131901] lo: Disabled Privacy Extensions
[ 3713.962339] usb 1-1: USB disconnect, address 6
[ 3716.984050] usb 1-1: new high speed USB device using ehci_hcd and address 7
[ 3784.715137] usb 1-1: USB disconnect, address 7
[ 3788.168203] usb 1-1: new high speed USB device using ehci_hcd and address 8
[ 3810.206189] usb 1-1: USB disconnect, address 8
[ 3840.592187] usb 1-1: new high speed USB device using ehci_hcd and address 9
[ 3882.437630] usb 1-1: USB disconnect, address 9
[ 3885.816056] usb 1-1: new high speed USB device using ehci_hcd and address 10
nate@nate-laptop:~$

---

### Post by nate7784 on 2010-11-29
The tail -n15 command did not do anything so I must be doing that wrong but thats my output for the other ones.

---

### Post by matt_symes on 2010-11-29
Hi

Have a look at this.

[http://www.absolutelytech.com/2010/04/18/solved-unable-to-enumerate-usb-device-disabling-ehci_hcd/](http://www.absolutelytech.com/2010/04/18/solved-unable-to-enumerate-usb-device-disabling-ehci_hcd/)

It seems some USB devices have problems with ehci_hcd. This may or may not fix it, as was for karmic.

Kind regards

---

### Post by nate7784 on 2010-11-29
I ran the script and it didn't seem to work. However, I do know that my laptop is too old to have usb 2.0 so that may still have something to do with it.

---

### Post by matt_symes on 2010-11-29
Hi

Have a look at these

[http://www.webupd8.org/2010/05/fix-usb-devices-automount-not-working.html](http://www.webupd8.org/2010/05/fix-usb-devices-automount-not-working.html)

[http://ubuntuforums.org/showthread.php?t=1477330](http://ubuntuforums.org/showthread.php?t=1477330)

The problem is it could be a number of things.

Kind regards

---

### Post by nate7784 on 2010-11-29
I tried both fixes to no avail. On the BIOS floppy option, I don't have a floppy section on my BIOS as stated in the instructions, so i ran the script and it gave me an error message saying "All config files need .config: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release."

As for the GRUB fix, I altered the code as instructed but still no usb device is picked up...

---

### Post by matt_symes on 2010-11-29
Hi

What version of Ubuntu are you using?

Can you boot into an old version of the kernel and try that from the grub menu. If you can, what version of the kernel is giving you the problem?

Kind regards

---

### Post by nate7784 on 2010-11-29
10.10. I did make a boot cd for SliTaz and everything works fine. It recognizes my lite on external burner, usb flash, etc.

---

### Post by JC Cheloven on 2010-11-29
EDIT: SORRY, YOU POSTED THE SLITAZ THING WHILE I WROTE THIS (I ASSUME YOU BURNT THE SLITAZ ISO ON ANOTHER PC?). SO A HARDWARE FAILURE IS DISCARDED. I DON'T DELETE THE FOLLOWING ORIGINAL POST JUST IN CASE IT SERVES TO ANYTHING, BUT IT NO LONGER APPLIES REALLY.

> **nate7784 said:**
> I ran the script and it didn't seem to work. However, I do know that my laptop is too old to have usb 2.0 so that may still have something to do with it.

As for what I've seen so far, you have a special piece of hardware: a laptop which is aged enough to have only 1.0 usb ports (not usb 2.0) usually don't have a usb-capable bios either. 
But you don't even have an internal cd unit. So it's sure that you installed through usb, so the usb is indeed managed by the bios... never mind.

To check whether it's a hardware failure or not, it is enough to use your bios (as we "know" it handles usb). If you can read anything (music...) or boot anything (live cd) using your cd drive, or a usb pendrive for that matter, this would be enough to discard a hardware failure.
It's convenient to do so before getting mad trying to solve by software a hardware problem (would not be the 1st time here lol).

---

### Post by nate7784 on 2010-11-29
Yes, I know she's old but I still love her and treat her well.;)

I am 99% positive it is not a hardware failure as I can boot SliTaz from my external burner and once in SliTaz it recognizes anything USB just fine. Also, I don't know if this info helps or not, but I can charge my cell phone using USB in Ubuntu so the ports have power, just no reaction in the OS to anything being plugged in....mysteries abound.

---

### Post by matt_symes on 2010-11-29
Hi

Because it stopped suddenly, i am wondering if it is due to a software update. Did you install any software updates when it stopped working?

Can you boot into an old version of the kernel in 10.10?

Looking at dmesg, it looks like it loading the correct usb drivers and finding the hardware correctly.

Kind regards

---

### Post by nate7784 on 2010-11-29
> **matt_symes said:**
> Hi

Because it stopped suddenly, i am wondering if it is due to a software update. Did you install any software updates when it stopped working?

Can you boot into an old version of the kernel in 10.10?

Looking at dmesg, it looks like it loading the correct usb drivers and finding the hardware correctly.

Kind regards
Yeah, I install all updates when prompted, but I can't pinpoint a specific one that could have stopped the usb from functioning as I don't often use a flash drive with the laptop. On booting from an old version of the kernal how do I determine which kernal I am using now so I'll know how far back to go?

---

### Post by nate7784 on 2010-11-29
Surprise, now USB is functional in Ubuntu!!!:P

I have no idea why though. I just rebooted out of slitaz and on the homescreen of ubuntu there was my cd drive and flash drive ready and waiting. So I unplug my usb devices and restart. Upon restart, I again cannot plug in any USB devices in Ubuntu. Again I leave USB devices plugged in before restarting again, and everything works fine. So, for some reason Ubuntu is only recognizing my USB devices if they are plugged in before start up.

---

### Post by JC Cheloven on 2010-11-29
> **nate7784 said:**
> Surprise, now USB is functional in Ubuntu!!!:P

I have no idea why though. I just rebooted out of slitaz and on the homescreen of ubuntu there was my cd drive and flash drive ready and waiting. So I unplug my usb devices and restart. Upon restart, I again cannot plug in any USB devices in Ubuntu. Again I leave USB devices plugged in before restarting again, and everything works fine. So, for some reason Ubuntu is only recognizing my USB devices if they are plugged in before start up.

OK, nice. At least you have a workaround to use your cd now. I think we are getting somewhere: I suspect it's a matter of some kernel module being incorrectly not loaded (or yes), due to some obscure reason. Perhaps a "guilty update" as matt said, or a malfunction with your hardware of discover-modprobe (which honestly I don't know yet how to fix). I'm not smart enough either to remember/guess by memory which kernel modules may be involved in your particular problem, only can guess "usb_storage". So I'm thinking of a method to find out which modules play a role here... I propose the folowing:

1) Boot your system with nothing plugged at usb's. Run at terminal ```
lsmod > from_hd.txt
```
This will create the file from_hd.txt with a list of your modules, in your home directory. 
2) Boot your system, this time with the cd usb unit plugged (no need of disc on it, I think), your pendrive, and whatever you use often. Run at terminal ```
lsmod > from_hd_with_stuff.txt
```
3) Compare both module lists. Those what are missing in the first but are present in the second, have to be included in the file /etc/modules, so that they load at startup. Those what are in the first but not in the second, have to be included in /etc/modprobe.d/blacklist.conf, so that they don't load. Please have a look [here]("https://help.ubuntu.com/community/Loadable_Modules") to find out the correct syntax for including module names in these files. Also you'll learn a bit! 

Well... I realize this is not the smarter solution. Ubuntu is supposed to manage modules dynamically. Perhaps someone else can think of something smarter (?)

Greetings

---

### Post by nate7784 on 2010-11-30
Well I gave it a shot, but no dice.

I did see the USB flash drive on the second txt file and it was on module 2. I ran the modprobe command for module 2, but i got an error message saying "all config files need .config: /etc/modprobe.d.ndiswrapper, it will be ignored in a future release"

---

### Post by JC Cheloven on 2010-11-30
Ok, difficult to explain/comunicate/understand by talking that way. Better attach both files so we can have a look, please.

---

### Post by nate7784 on 2010-11-30
from_hd.txt
Module                  Size  Used by
parport_pc             26058  0 
ppdev                   5556  0 
rfcomm                 33811  4 
binfmt_misc             6599  1 
sco                     7998  2 
bnep                    9542  2 
l2cap                  37008  16 rfcomm,bnep
joydev                  8735  0 
snd_intel8x0           25632  2 
snd_ac97_codec         99227  1 snd_intel8x0
ac97_bus                1014  1 snd_ac97_codec
i915                  291004  3 
snd_pcm                71475  2 snd_intel8x0,snd_ac97_codec
snd_seq_midi            4588  0 
snd_rawmidi            17783  1 snd_seq_midi
drm_kms_helper         30200  1 i915
pcmcia                 35973  0 
snd_seq_midi_event      6047  1 snd_seq_midi
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
snd_timer              19067  2 snd_pcm,snd_seq
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
drm                   168054  4 i915,drm_kms_helper
btusb                  10969  2 
ndiswrapper           184207  0 
snd                    49006  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_algo_bit            5168  1 i915
yenta_socket           21518  0 
pcmcia_rsrc            10566  1 yenta_socket
intel_agp              26360  2 i915
bluetooth              50500  9 rfcomm,sco,bnep,l2cap,btusb
dell_laptop             5730  0 
pcmcia_core            14657  3 pcmcia,yenta_socket,pcmcia_rsrc
psmouse                59033  0 
dcdbas                  5402  1 dell_laptop
soundcore                880  1 snd
snd_page_alloc          7120  2 snd_intel8x0,snd_pcm
serio_raw               4022  0 
video                  18712  1 i915
agpgart                32011  2 drm,intel_agp
output                  1883  1 video
lp                      7342  0 
parport                31492  3 parport_pc,ppdev,lp
tg3                   123310  0 

from_hd_with_stuff.txt
Module                  Size  Used by
nls_iso8859_1           3261  1 
nls_cp437               4931  1 
isofs                  30022  1 
vfat                    9201  1 
fat                    48240  1 vfat
parport_pc             26058  0 
ppdev                   5556  0 
rfcomm                 33811  4 
binfmt_misc             6599  1 
sco                     7998  2 
bnep                    9542  2 
l2cap                  37008  16 rfcomm,bnep
joydev                  8735  0 
snd_intel8x0           25632  2 
snd_ac97_codec         99227  1 snd_intel8x0
ac97_bus                1014  1 snd_ac97_codec
snd_pcm                71475  2 snd_intel8x0,snd_ac97_codec
i915                  291004  3 
snd_seq_midi            4588  0 
snd_rawmidi            17783  1 snd_seq_midi
drm_kms_helper         30200  1 i915
snd_seq_midi_event      6047  1 snd_seq_midi
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
snd_timer              19067  2 snd_pcm,snd_seq
pcmcia                 35973  0 
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
drm                   168054  4 i915,drm_kms_helper
btusb                  10969  2 
ndiswrapper           184207  0 
bluetooth              50500  9 rfcomm,sco,bnep,l2cap,btusb
dell_laptop             5730  0 
intel_agp              26360  2 i915
dcdbas                  5402  1 dell_laptop
psmouse                59033  0 
snd                    49006  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
yenta_socket           21518  0 
pcmcia_rsrc            10566  1 yenta_socket
i2c_algo_bit            5168  1 i915
soundcore                880  1 snd
serio_raw               4022  0 
video                  18712  1 i915
snd_page_alloc          7120  2 snd_intel8x0,snd_pcm
agpgart                32011  2 drm,intel_agp
pcmcia_core            14657  3 pcmcia,yenta_socket,pcmcia_rsrc
output                  1883  1 video
lp                      7342  0 
parport                31492  3 parport_pc,ppdev,lp
usb_storage            40172  2 
tg3                   123310  0

---

### Post by JC Cheloven on 2010-12-01
Thanks.

Please find enclosed a speadsheet with a bit of processing on your data. 

As you can see, the "D" column contain the names of the modules which are loaded with the stuff plugged in, but not when nothing is plugged. 

On the other hand, every module which is loaded without stuff plugged is also present when stuff is plugged. 

So, you can edit your /etc/modules file, and add there the modules you'll need when you will plug some of your stuff. This way you'll be able (hopefully) to connect such devices also once the system has booted. 

=======================================================
Instructions to do so:

- Open a terminal (Accesories-terminal in the nemu)
- Type in (give your password when prompted)
```
gksudo gedit /etc/modules
```
- Add the following lines to the end of the file
```
fat
isofs
nls_cp437
nls_iso8859_1
usb_storage
vfat
```
- Save and exit the editor
- Reboot
- Test that it worked
=======================================================

Again, this solution will (hopefully) make work your USUAL devices when plugged once the system has booted, but may not work for a new different device.
The optimal solution would be to actually restore your ubuntu to the default (correct) behaviour, of recognising needed modules dynamically and loading them. If someone takes the plunge... ;)

Cheers
JC

---

