---
title: "powernowd"
date: 2005-12-26
forum: General Help
---

### Post by digitalkarabao on 2005-12-26
when i run powernowd, i receive this:

powernowd: PowerNow Daemon v0.96, (c) 2003-2005 John Clemens
WARN: ncpus(1) is not a multiple of threads_per_core(2)!
WARN: Assuming 1.
powernowd: Found 1 cpu:  -- 1 thread (or core) per physical cpu
powernowd:   cpu0: 2250Mhz - 3000Mhz (3 steps)

i would like to believe i should be concerned with the above warnings because my alienware portable crashes when the CPU throttles to 100%.

what should i do to get better CPU performance? overall performance.

dmesg output below:

00:03.3: new USB bus registered, assigned bus number 4
[4294680.704000] ehci_hcd 0000:00:03.3: irq 23, io mem 0xdffed000
[4294680.704000] PCI: cache line size of 128 is not supported by device 0000:00:03.3
[4294680.704000] ehci_hcd 0000:00:03.3: USB 2.0 initialized, EHCI 1.00, driver 10 Dec 2004
[4294680.705000] hub 4-0:1.0: USB hub found
[4294680.705000] hub 4-0:1.0: 6 ports detected
[4294680.790000] r8169 Gigabit Ethernet driver 2.2LK loaded
[4294680.790000] ACPI: PCI Interrupt 0000:00:0a.0[A] -> GSI 19 (level, low) -> IRQ 19
[4294680.792000] eth0: Identified chip type is 'RTL8169s/8110s'.
[4294680.792000] eth0: RTL8169 at 0xf8890c00, 00:03:0d:10:57:e0, IRQ 19
[4294681.132000] usb 1-1: new low speed USB device using ohci_hcd and address 3
[4294682.918000] usbcore: registered new driver hiddev
[4294682.927000] input: USB HID v1.10 Mouse [Genius NetScroll] on usb-0000:00:03.0-1
[4294682.927000] usbcore: registered new driver usbhid
[4294682.927000] drivers/usb/input/hid-core.c: v2.01:USB HID core driver
[4294683.864000] ACPI: CPU0 (power states: C1[C1])
[4294683.864000] ACPI: Processor [CPU1] (supports 8 throttling states)
[4294683.866000] ACPI: Thermal Zone [THRM] (75 C)
[4294684.400000] Attempting manual resume
[4294684.400000] swsusp: Suspend partition has wrong signature?
[4294684.424000] kjournald starting.  Commit interval 5 seconds
[4294684.424000] EXT3-fs: mounted filesystem with ordered data mode.
[4294685.832000] md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
[4294691.412000] Adding 1622524k swap on /dev/hda5.  Priority:-1 extents:1
[4294691.766000] EXT3 FS on hda1, internal journal
[4294703.956000] parport: PnPBIOS parport detected.
[4294703.956000] parport0: PC-style at 0x378 (0x778), irq 7, using FIFO [PCSPP,TRISTATE,COMPAT,EPP,ECP]
[4294704.046000] lp0: using parport0 (interrupt-driven).
[4294704.089000] mice: PS/2 mouse device common for all mice
[4294704.190000] ieee1394: Initialized config rom entry `ip1394'
[4294704.206000] SCSI subsystem initialized
[4294704.213000] sbp2: $Rev: 1219 $ Ben Collins <bcollins@debian.org>
[4294704.291000] p4-clockmod: has N60 errata - disabling frequencies below 2.0 GHz
[4294704.291000] p4-clockmod: disabling frequency 375000
[4294704.291000] p4-clockmod: disabling frequency 750000
[4294704.291000] p4-clockmod: disabling frequency 1125000
[4294704.291000] p4-clockmod: disabling frequency 1500000
[4294704.291000] p4-clockmod: disabling frequency 1875000
[4294704.310000] p4-clockmod: P4/Xeon(TM) CPU On-Demand Clock Modulation available
[4294704.356000] i2c-sis96x version 1.0.0
[4294704.360000] sis96x_smbus 0000:00:02.1: SiS96x SMBus base address: 0x0c00
[4294707.729000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]
[4294709.511000] cdrom: open failed.
[4294712.588000] Linux agpgart interface v0.101 (c) Dave Jones
[4294712.598000] agpgart: Detected SiS 648 chipset
[4294712.634000] agpgart: AGP aperture is 256M @ 0xe0000000
[4294712.734000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[4294712.752000] shpchp: shpc_init : shpc_cap_offset == 0
[4294712.752000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[4294712.954000] ohci1394: $Rev: 1250 $ Ben Collins <bcollins@debian.org>
[4294712.954000] ACPI: PCI Interrupt 0000:00:02.3[B] -> GSI 17 (level, low) -> IRQ 17
[4294712.961000] ohci1394: fw-host0: Unexpected PCI resource length of 1000!
[4294713.017000] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[17]  MMIO=[dffe9000-dffe97ff]  Max Packet=[2048]
[4294713.377000] ACPI: PCI Interrupt 0000:00:02.7[C] -> GSI 18 (level, low) -> IRQ 18
[4294713.936000] intel8x0_measure_ac97_clock: measured 49419 usecs
[4294713.936000] intel8x0: clocking to 48000
[4294714.312000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00030d53766026c7][4294714.688000] Linux Kernel Card Services
[4294714.688000]   options:  [pci] [cardbus] [pm]
[4294714.703000] ACPI: PCI Interrupt 0000:00:09.0[A] -> GSI 17 (level, low) -> IRQ 17
[4294714.704000] Yenta: CardBus bridge found at 0000:00:09.0 [1584:3005]
[4294714.704000] Yenta O2: res at 0x94/0xD4: 00/ea
[4294714.704000] Yenta O2: enabling read prefetch/write burst
[4294714.824000] Yenta: ISA IRQ mask 0x0a38, PCI irq 17
[4294714.824000] Socket status: 30000006
[4294714.842000] ACPI: PCI Interrupt 0000:00:09.1[A] -> GSI 17 (level, low) -> IRQ 17
[4294714.842000] Yenta: CardBus bridge found at 0000:00:09.1 [1584:3005]
[4294714.962000] Yenta: ISA IRQ mask 0x0a38, PCI irq 17
[4294714.962000] Socket status: 30000006
[4294715.211000] ath_hal: module license 'Proprietary' taints kernel.
[4294715.216000] ath_hal: 0.9.14.9 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413)
[4294715.223000] wlan: 0.8.6.0 (EXPERIMENTAL)
[4294715.228000] ath_rate_sample: 1.2
[4294715.237000] ath_pci: 0.9.6.0 (EXPERIMENTAL)
[4294715.242000] ACPI: PCI Interrupt 0000:00:0b.0[A] -> GSI 17 (level, low) -> IRQ 17
[4294715.522000] Build date: Nov 22 2005
[4294715.522000] Debugging version (IEEE80211)
[4294715.522000] ath0: 11a rates: 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[4294715.522000] ath0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
[4294715.522000] ath0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[4294715.522000] ath0: turboA rates: 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[4294715.522000] ath0: H/W encryption support: WEP AES AES_CCM TKIP
[4294715.522000] ath0: mac 5.6 phy 4.1 5ghz radio 1.7 2ghz radio 2.3
[4294715.522000] ath0: Use hw queue 1 for WME_AC_BE traffic
[4294715.522000] ath0: Use hw queue 0 for WME_AC_BK traffic
[4294715.522000] ath0: Use hw queue 2 for WME_AC_VI traffic
[4294715.522000] ath0: Use hw queue 3 for WME_AC_VO traffic
[4294715.522000] ath0: Use hw queue 8 for CAB traffic
[4294715.522000] ath0: Use hw queue 9 for beacons
[4294715.522000] Debugging version (ATH)
[4294715.522000] ath0: Atheros 5212: mem=0xdfff0000, irq=17
[4294717.177000] Real Time Clock Driver v1.12
[4294717.305000] input: PC Speaker
[4294717.694000] ts: Compaq touchscreen protocol output
[4294718.344000] NET: Registered protocol family 17
[4294785.503000] ACPI: AC Adapter [AC0] (off-line)
[4294785.564000] ACPI: Battery Slot [BAT0] (battery present)
[4294785.589000] ACPI: Power Button (FF) [PWRF]
[4294785.589000] ACPI: Lid Switch [LID]
[4294785.589000] ACPI: Sleep Button (CM) [SLPB]
[4294785.589000] ACPI: Power Button (CM) [PWRB]
[4294785.683000] ibm_acpi: ec object not found
[4294785.806000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[4294787.786000] ACPI: PCI Interrupt 0000:00:02.6[C] -> GSI 18 (level, low) -> IRQ 18
[4294792.070000] [fglrx] Maximum main memory to use for locked dma buffers: 930 MBytes.
[4294792.070000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[4294792.070000] [fglrx] module loaded - fglrx 8.16.20 [Aug 16 2005] on minor 0
[4294792.083000] [fglrx] Internal AGP support requested, but kernel AGP support active.
[4294792.083000] [fglrx] Have to use kernel AGP support to avoid conflicts.
[4294792.083000] [fglrx] Kernel AGP support doesn't provide agplock functionality.
[4294792.083000] [fglrx] AGP detected, AgpState   = 0x1f004e0b (hardware caps of chipset)
[4294792.084000] agpgart: Found an AGP 3.5 compliant device at 0000:00:00.0.
[4294792.084000] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[4294792.084000] agpgart: SiS delay workaround: giving bridge time to recover.
[4294792.095000] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
[4294792.095000] [fglrx] AGP enabled,  AgpCommand = 0x1f004302 (selected caps)
[4294792.109000] NET: Registered protocol family 10
[4294792.110000] Disabled Privacy Extensions on device c02eb280(lo)
[4294792.110000] IPv6 over IPv4 tunneling driver
[4294792.123000] [fglrx] free  AGP = 256126976
[4294792.123000] [fglrx] max   AGP = 256126976
[4294792.123000] [fglrx] free  LFB = 110219264
[4294792.123000] [fglrx] max   LFB = 110219264
[4294792.123000] [fglrx] free  Inv = 0
[4294792.123000] [fglrx] max   Inv = 0
[4294792.123000] [fglrx] total Inv = 0
[4294792.123000] [fglrx] total TIM = 0
[4294792.123000] [fglrx] total FB  = 0
[4294792.123000] [fglrx] total AGP = 65536
[4294796.180000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[4294796.180000] apm: overridden by ACPI.
[4294797.177000] cs: IO port probe 0x100-0x4ff: excluding 0x480-0x48f 0x4d0-0x4d7
[4294797.179000] cs: IO port probe 0x100-0x4ff: excluding 0x480-0x48f 0x4d0-0x4d7
[4294797.182000] cs: IO port probe 0xc00-0xcf7: clean.
[4294797.182000] cs: IO port probe 0xc00-0xcf7: clean.
[4294797.183000] cs: IO port probe 0xa00-0xaff: clean.
[4294797.184000] cs: IO port probe 0xa00-0xaff: clean.
[4294797.722000] r8169: eth0: PHY reset until link up
[4294799.721000] Bluetooth: Core ver 2.7
[4294799.721000] NET: Registered protocol family 31
[4294799.721000] Bluetooth: HCI device and connection manager initialized
[4294799.721000] Bluetooth: HCI socket layer initialized
[4294799.787000] Bluetooth: L2CAP ver 2.7
[4294799.787000] Bluetooth: L2CAP socket layer initialized
[4294799.835000] Bluetooth: RFCOMM ver 1.5
[4294799.835000] Bluetooth: RFCOMM socket layer initialized
[4294799.835000] Bluetooth: RFCOMM TTY layer initialized
[4294802.195000] eth0: no IPv6 routers present
[4294802.637000] ath0: no IPv6 routers present
[4294807.722000] r8169: eth0: PHY reset until link up
[4294817.722000] r8169: eth0: PHY reset until link up
[4294827.722000] r8169: eth0: PHY reset until link up
[4294837.722000] r8169: eth0: PHY reset until link up
[4294847.722000] r8169: eth0: PHY reset until link up
[4294857.722000] r8169: eth0: PHY reset until link up
[4294867.722000] r8169: eth0: PHY reset until link up
[4294877.722000] r8169: eth0: PHY reset until link up
[4294887.722000] r8169: eth0: PHY reset until link up
[4294897.722000] r8169: eth0: PHY reset until link up
[4294907.722000] r8169: eth0: PHY reset until link up
[4294917.722000] r8169: eth0: PHY reset until link up
[4294927.723000] r8169: eth0: PHY reset until link up
[4294937.723000] r8169: eth0: PHY reset until link up
[4294947.723000] r8169: eth0: PHY reset until link up
[4294957.723000] r8169: eth0: PHY reset until link up
[4294967.723000] r8169: eth0: PHY reset until link up
[4294968.259000] CSLIP: code copyright 1989 Regents of the University of California
[4294968.265000] PPP generic driver version 2.4.2
[4294975.571000] PPP BSD Compression module registered
[4294975.616000] PPP Deflate Compression module registered
[4294977.723000] r8169: eth0: PHY reset until link up
[4294979.542000] ip_tables: (C) 2000-2002 Netfilter core team
[4294979.580000] ip_conntrack version 2.1 (8190 buckets, 65520 max) - 248 bytes per conntrack
[4294987.723000] r8169: eth0: PHY reset until link up
[4294997.723000] r8169: eth0: PHY reset until link up
[4295000.137000] Inbound IN=ppp0 OUT= MAC= SRC=202.78.85.52 DST=202.78.106.88 LEN=48 TOS=0x00 PREC=0x00 TTL=124 ID=18785 DF PROTO=TCP SPT=4604 DPT=135 WINDOW=8760 RES=0x00 SYN URGP=33016
[4295007.723000] r8169: eth0: PHY reset until link up
[4295017.723000] r8169: eth0: PHY reset until link up
[4295027.723000] r8169: eth0: PHY reset until link up
[4295037.723000] r8169: eth0: PHY reset until link up
[4295047.723000] r8169: eth0: PHY reset until link up
[4295057.723000] r8169: eth0: PHY reset until link up
[4295067.723000] r8169: eth0: PHY reset until link up
[4295077.723000] r8169: eth0: PHY reset until link up
[4295087.723000] r8169: eth0: PHY reset until link up
[4295097.723000] r8169: eth0: PHY reset until link up
[4295107.723000] r8169: eth0: PHY reset until link up
[4295117.723000] r8169: eth0: PHY reset until link up
[4295127.723000] r8169: eth0: PHY reset until link up
[4295137.723000] r8169: eth0: PHY reset until link up
[4295147.723000] r8169: eth0: PHY reset until link up
[4295157.723000] r8169: eth0: PHY reset until link up
[4295167.723000] r8169: eth0: PHY reset until link up
[4295177.723000] r8169: eth0: PHY reset until link up
[4295187.723000] r8169: eth0: PHY reset until link up
[4295197.723000] r8169: eth0: PHY reset until link up
[4295207.723000] r8169: eth0: PHY reset until link up
[4295217.723000] r8169: eth0: PHY reset until link up
[4295227.723000] r8169: eth0: PHY reset until link up
[4295235.305000] Inbound IN=ppp0 OUT= MAC= SRC=202.78.209.208 DST=202.78.106.88 LEN=48 TOS=0x00 PREC=0x00 TTL=118 ID=45449 DF PROTO=TCP SPT=1566 DPT=135 WINDOW=16384 RES=0x00 SYN URGP=0
[4295237.723000] r8169: eth0: PHY reset until link up
[4295247.723000] r8169: eth0: PHY reset until link up
[4295257.723000] r8169: eth0: PHY reset until link up
[4295267.723000] r8169: eth0: PHY reset until link up
[4295277.723000] r8169: eth0: PHY reset until link up
[4295287.723000] r8169: eth0: PHY reset until link up
[4295292.175000] Inbound IN=ppp0 OUT= MAC= SRC=202.78.73.13 DST=202.78.106.88 LEN=48 TOS=0x00 PREC=0x00 TTL=124 ID=20291 DF PROTO=TCP SPT=1701 DPT=135 WINDOW=16384 RES=0x00 SYN URGP=0
[4295297.723000] r8169: eth0: PHY reset until link up
[4295307.723000] r8169: eth0: PHY reset until link up
[4295317.723000] r8169: eth0: PHY reset until link up
[4295327.723000] r8169: eth0: PHY reset until link up
[4295337.723000] r8169: eth0: PHY reset until link up
[4295347.723000] r8169: eth0: PHY reset until link up
[4295353.565000] Inbound IN=ppp0 OUT= MAC= SRC=202.78.85.229 DST=202.78.106.88 LEN=48 TOS=0x00 PREC=0x00 TTL=124 ID=7013 DF PROTO=TCP SPT=3649 DPT=135 WINDOW=8760 RES=0x00 SYN URGP=18200
[4295357.723000] r8169: eth0: PHY reset until link up
[4295367.723000] r8169: eth0: PHY reset until link up
[4295377.723000] r8169: eth0: PHY reset until link up
[4295387.723000] r8169: eth0: PHY reset until link up
[4295397.723000] r8169: eth0: PHY reset until link up
[4295407.723000] r8169: eth0: PHY reset until link up
[4295416.672000] Inbound IN=ppp0 OUT= MAC= SRC=202.78.86.248 DST=202.78.106.88 LEN=48 TOS=0x00 PREC=0x00 TTL=124 ID=52069 PROTO=TCP SPT=4132 DPT=135 WINDOW=65535 RES=0x00 SYN URGP=0
[4295417.723000] r8169: eth0: PHY reset until link up
[4295427.723000] r8169: eth0: PHY reset until link up
[4295437.723000] r8169: eth0: PHY reset until link up
[4295447.723000] r8169: eth0: PHY reset until link up
[4295457.723000] r8169: eth0: PHY reset until link up
[4295467.723000] r8169: eth0: PHY reset until link up
[4295477.723000] r8169: eth0: PHY reset until link up
[4295487.723000] r8169: eth0: PHY reset until link up
[4295497.723000] r8169: eth0: PHY reset until link up
[4295507.723000] r8169: eth0: PHY reset until link up
[4295517.723000] r8169: eth0: PHY reset until link up
[4295527.723000] r8169: eth0: PHY reset until link up
[4295537.723000] r8169: eth0: PHY reset until link up
[4295547.723000] r8169: eth0: PHY reset until link up
[4295548.586000] Inbound IN=ppp0 OUT= MAC= SRC=221.1.204.251 DST=202.78.106.88 LEN=502 TOS=0x00 PREC=0x00 TTL=49 ID=0 DF PROTO=UDP SPT=32982 DPT=1026 LEN=482
[4295557.723000] r8169: eth0: PHY reset until link up
[4295562.238000] Inbound IN=ppp0 OUT= MAC= SRC=202.78.83.71 DST=202.78.106.88 LEN=48 TOS=0x00 PREC=0x00 TTL=124 ID=32230 DF PROTO=TCP SPT=1868 DPT=135 WINDOW=8760 RES=0x00 SYN URGP=0
[4295567.723000] r8169: eth0: PHY reset until link up
[4295568.514000] Inbound IN=ppp0 OUT= MAC= SRC=202.78.85.52 DST=202.78.106.88 LEN=48 TOS=0x00 PREC=0x00 TTL=124 ID=29824 DF PROTO=TCP SPT=1837 DPT=135 WINDOW=8760 RES=0x00 SYN URGP=0
[4295577.723000] r8169: eth0: PHY reset until link up
[4295587.723000] r8169: eth0: PHY reset until link up
[4295597.723000] r8169: eth0: PHY reset until link up
[4295607.723000] r8169: eth0: PHY reset until link up
[4295617.723000] r8169: eth0: PHY reset until link up
[4295627.723000] r8169: eth0: PHY reset until link up

---

