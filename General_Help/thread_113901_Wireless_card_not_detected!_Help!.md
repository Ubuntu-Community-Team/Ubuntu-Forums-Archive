---
title: "Wireless card not detected! Help!"
date: 2006-01-07
forum: General Help
---

### Post by jesse on 2006-01-07
Could someone please help me? I've looked at online howtos and think I can get my wireless connection set up fine...

....If only I could just get my Gericom laptop to detect my wireless pcmia card. 

When I type the command 

          sudo cardctl ident

I get the following output

Socket 0:
  product info: "WavePlus Technology", "WLAN PC Card WP1200", "Version 01.00", ""
  manfid: 0x0000, 0x0000
  function: 6 (network)


BUT... When I open Gnome network settings it lists only 

ethernet connection
the interface eth0 is active

modem connection
the interface ppp0 is not configured


My wireless card is not listed even as a choice for me to configure, as if it's not detected. Meanwhile the wireless card is plugged in and it's little green light is flashing. 

I'm at a loss as to how to solve this problem. I've searched forum threads and found useful howtos, but I can never get any farther than where it says something like "once you see that your device is detected you can move on to the next step." 

How on Earth can I get this fricking Ubuntu system to at least detect that my wireless card hardware exists and is plugged in. 

Any help would be appreciated. 

Thanks. 

:rolleyes:

---

### Post by aserre on 2006-01-07
I just had this happen to me.... do you have the drives??

---

### Post by aserre on 2006-01-07
ok make a folder on your desktop called 'driver'  and copy your windows driver files (the .inf and the .sys) into the driver folder and then open terminal and type the following commands:
cd Desktop/driver/
sudo ndiswrapper -i <driver>.inf
sudo ndiswrapper -i <driver>.sys
sudo modprobe ndiswrapper



close the terminal and go to administration, then to networking and then you should see it there and just activate it

---

### Post by jesse on 2006-01-07
Do you mean drivers? I found a link to a zip file containing windows drivers for the waveplus wireless card, but when I use ndisgtk to try to install a driver it shows the driver as "installed" but says "hardware found: no"

:confused:

---

### Post by jesse on 2006-01-07
jesse@GericomLaptop:~$ sudo ndiswrapper -i /home/jesse/Desktop/Driver/Winxp/netwg311.inf
Password:
Installing netwg311

jesse@GericomLaptop:~$ sudo ndiswrapper -i /home/jesse/Desktop/Driver/Winxp/wg311nd5.sys
Installing wg311nd5.sys

jesse@GericomLaptop:~$ sudo modprobe ndiswrapper
jesse@GericomLaptop:~$


All of that seemed to go ok, BUT...

network settings shows only the following 

ethernet connection
the interface eth0 is active

modem connection
the interface ppp0 is not configured


The wireless card is still not shown

---

### Post by aserre on 2006-01-07
well I'm new to this found the commands that I gave you online but I wishI had more ideas

---

### Post by jesse on 2006-01-07
I appreciate you trying to help me. Hopefully someone will know the answer.

---

### Post by dotdot on 2006-01-07
can you let us see the output from

1/ iwconfig

2/ dmesg

cheers

..

---

### Post by jesse on 2006-01-07
jesse@GericomLaptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

jesse@GericomLaptop:~$ dmesg
 entries: 16384 (order: 4, 65536 bytes)
[4294667.713000] Memory: 218364k/229312k available (1632k kernel code, 10324k reserved, 740k data, 168k init, 0k highmem)
[4294667.713000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[4294667.713000] Calibrating delay loop... 2375.68 BogoMIPS (lpj=1187840)
[4294667.737000] Security Framework v1.0.0 initialized
[4294667.737000] SELinux:  Disabled at boot.
[4294667.737000] Mount-cache hash table entries: 512
[4294667.737000] CPU: After generic identify, caps: 0383f9ff c1cbf9ff 00000000 00000000 00000000 00000000 00000000
[4294667.737000] CPU: After vendor identify, caps: 0383f9ff c1cbf9ff 00000000 00000000 00000000 00000000 00000000
[4294667.737000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[4294667.737000] CPU: L2 Cache: 256K (64 bytes/line)
[4294667.737000] CPU: After all inits, caps: 0383f9ff c1cbf9ff 00000000 00000020 00000000 00000000 00000000
[4294667.737000] Intel machine check architecture supported.
[4294667.737000] Intel machine check reporting enabled on CPU#0.
[4294667.737000] CPU: AMD mobile AMD Athlon(tm) XP 1400+ stepping 00
[4294667.737000] Enabling fast FPU save and restore... done.
[4294667.737000] Enabling unmasked SIMD FPU exception support... done.
[4294667.737000] Checking 'hlt' instruction... OK.
[4294667.741000] checking if image is initramfs... it is
[4294668.534000] Freeing initrd memory: 5515k freed
[4294668.535000] ACPI: Looking for DSDT in initrd... not found!
[4294668.621000]  not found!
[4294668.631000] ACPI: setting ELCR to 0200 (from 0600)
[4294668.632000] NET: Registered protocol family 16
[4294668.632000] ACPI: bus type pci registered
[4294668.633000] PCI: PCI BIOS revision 2.10 entry at 0xfdb51, last bus=1
[4294668.633000] PCI: Using configuration type 1
[4294668.633000] mtrr: v2.0 (20020519)
[4294668.633000] ACPI: Subsystem revision 20050729
[4294668.658000] ACPI: Interpreter enabled
[4294668.658000] ACPI: Using PIC for interrupt routing
[4294668.658000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[4294668.658000] PCI: Probing PCI hardware (bus 00)
[4294668.658000] ACPI: Assume root bridge [\_SB_.PCI0] segment is 0
[4294668.663000] Boot video device is 0000:01:00.0
[4294668.702000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[4294668.703000] ACPI: Power Resource [URP1] (off)
[4294668.703000] ACPI: Power Resource [URP2] (off)
[4294668.703000] ACPI: Power Resource [FDDP] (off)
[4294668.703000] ACPI: Power Resource [LPTP] (off)
[4294668.705000] burst-mode-ec-10-Aug
[4294668.705000] ACPI: Embedded Controller [EC0] (gpe 5)
[4294668.711000] ACPI: PCI Interrupt Link [LNKA] (IRQs 5 *9 10 11 14 15)
[4294668.712000] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 9 10 11 14 15) *0, disabled.
[4294668.712000] ACPI: PCI Interrupt Link [LNKC] (IRQs 5 9 *10 11 14 15)
[4294668.713000] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 9 *10 11 14 15)
[4294668.713000] ACPI: Power Resource [FN10] (on)
[4294668.713000] Linux Plug and Play Support v0.97 (c) Adam Belay
[4294668.713000] pnp: PnP ACPI init
[4294668.719000] pnp: PnP ACPI: found 10 devices
[4294668.719000] PnPBIOS: Disabled by ACPI PNP
[4294668.719000] PCI: Using ACPI for IRQ routing
[4294668.719000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[4294668.721000] Simple Boot Flag at 0x7c set to 0x1
[4294668.722000] audit: initializing netlink socket (disabled)
[4294668.722000] audit: initialized
[4294668.722000] VFS: Disk quotas dquot_6.5.1
[4294668.722000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[4294668.722000] devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
[4294668.722000] devfs: boot_options: 0x0
[4294668.722000] Initializing Cryptographic API
[4294668.722000] Applying VIA southbridge workaround.
[4294668.722000] isapnp: Scanning for PnP cards...
[4294669.076000] isapnp: No Plug & Play device found
[4294669.100000] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[4294669.105000] i8042.c: Detected active multiplexing controller, rev 1.0.
[4294669.106000] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[4294669.106000] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[4294669.106000] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[4294669.107000] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[4294669.107000] serio: i8042 KBD port at 0x60,0x64 irq 1
[4294669.107000] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
[4294669.107000] ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[4294669.110000] ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[4294669.110000] io scheduler noop registered
[4294669.110000] io scheduler anticipatory registered
[4294669.110000] io scheduler deadline registered
[4294669.110000] io scheduler cfq registered
[4294669.111000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[4294669.111000] NET: Registered protocol family 2
[4294669.121000] IP: routing cache hash table of 2048 buckets, 16Kbytes
[4294669.121000] TCP established hash table entries: 8192 (order: 4, 65536 bytes)
[4294669.121000] TCP bind hash table entries: 8192 (order: 3, 32768 bytes)
[4294669.121000] TCP: Hash tables configured (established 8192 bind 8192)
[4294669.121000] NET: Registered protocol family 8
[4294669.121000] NET: Registered protocol family 20
[4294669.122000] ACPI wakeup devices:
[4294669.122000]  EC0  USB USB1  AC9  MC9 VT94 ILAN  LID SLPB
[4294669.122000] ACPI: (supports S0 S1 S4 S5)
[4294669.122000] Freeing unused kernel memory: 168k freed
[4294669.150000] vga16fb: initializing
[4294669.150000] vga16fb: mapped to 0xc00a0000
[4294669.275000] Console: switching to colour frame buffer device 80x30
[4294669.275000] fb0: VGA16 VGA frame buffer device
[4294669.523000] input: AT Translated Set 2 keyboard on isa0060/serio0
[4294670.408000] Capability LSM initialized
[4294670.426000] NET: Registered protocol family 1
[4294670.445000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[4294670.445000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[4294670.446000] ACPI: bus type ide registered
[4294670.455000] VP_IDE: IDE controller at PCI slot 0000:00:11.1
[4294670.455000] PCI: Via IRQ fixup for 0000:00:11.1, from 255 to 0
[4294670.455000] VP_IDE: chipset revision 6
[4294670.455000] VP_IDE: not 100% native mode: will probe irqs later
[4294670.455000] VP_IDE: VIA vt8231 (rev 10) IDE UDMA100 controller on pci0000:00:11.1
[4294670.455000]     ide0: BM-DMA at 0xfc00-0xfc07, BIOS settings: hda:DMA, hdb:pio
[4294670.455000]     ide1: BM-DMA at 0xfc08-0xfc0f, BIOS settings: hdc:DMA, hdd:pio
[4294670.455000] Probing IDE interface ide0...
[4294670.839000] hda: HITACHI_DK23DA-20, ATA DISK drive
[4294671.451000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[4294671.451000] Probing IDE interface ide1...
[4294672.243000] hdc: TOSHIBA DVD-ROM SD-C2402, ATAPI CD/DVD-ROM drive
[4294672.865000] ide1 at 0x170-0x177,0x376 on irq 15
[4294672.866000] Probing IDE interface ide2...
[4294673.378000] Probing IDE interface ide3...
[4294673.890000] Probing IDE interface ide4...
[4294674.402000] Probing IDE interface ide5...
[4294674.919000] hda: max request size: 128KiB
[4294674.920000] hda: 39070080 sectors (20003 MB) w/2048KiB Cache, CHS=38760/16/63, UDMA(100)
[4294674.920000] hda: cache flushes supported
[4294674.920000]  /dev/ide/host0/bus0/target0/lun0: p1 p2 < p5 >
[4294675.010000] hdc: ATAPI 24X DVD-ROM drive, 128kB Cache
[4294675.010000] Uniform CD-ROM driver Revision: 3.20
[4294675.465000] Attempting manual resume
[4294675.472000] swsusp: Suspend partition has wrong signature?
[4294675.559000] usbcore: registered new driver usbfs
[4294675.559000] usbcore: registered new driver hub
[4294675.560000] USB Universal Host Controller Interface driver v2.2
[4294675.561000] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 10
[4294675.561000] PCI: setting IRQ 10 as level-triggered
[4294675.561000] ACPI: PCI Interrupt 0000:00:11.2[D] -> Link [LNKD] -> GSI 10 (level, low) -> IRQ 10
[4294675.561000] uhci_hcd 0000:00:11.2: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
[4294675.623000] uhci_hcd 0000:00:11.2: new USB bus registered, assigned bus number 1
[4294675.623000] uhci_hcd 0000:00:11.2: irq 10, io base 0x0000d400
[4294675.623000] hub 1-0:1.0: USB hub found
[4294675.623000] hub 1-0:1.0: 2 ports detected
[4294675.626000] ACPI: PCI Interrupt 0000:00:11.3[D] -> Link [LNKD] -> GSI 10 (level, low) -> IRQ 10
[4294675.626000] uhci_hcd 0000:00:11.3: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (#2)
[4294675.688000] uhci_hcd 0000:00:11.3: new USB bus registered, assigned bus number 2
[4294675.688000] uhci_hcd 0000:00:11.3: irq 10, io base 0x0000d800
[4294675.688000] hub 2-0:1.0: USB hub found
[4294675.688000] hub 2-0:1.0: 2 ports detected
[4294675.753000] via-rhine.c:v1.10-LK1.2.0-2.6 June-10-2004 Written by Donald Becker
[4294675.753000] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 9
[4294675.753000] PCI: setting IRQ 9 as level-triggered
[4294675.753000] ACPI: PCI Interrupt 0000:00:12.0[A] -> Link [LNKA] -> GSI 9 (level, low) -> IRQ 9
[4294675.757000] eth0: VIA Rhine II at 0x1d000, 00:a0:cc:db:20:ea, IRQ 9.
[4294675.758000] eth0: MII PHY found at address 1, status 0x7869 advertising 05e1 Link 45e1.
[4294675.796000] usb 1-1: new full speed USB device using uhci_hcd and address 2[4294676.157000] usb 2-1: new full speed USB device using uhci_hcd and address 2[4294676.246000] hub 2-1:1.0: USB hub found
[4294676.248000] hub 2-1:1.0: 4 ports detected
[4294676.541000] usb 2-1.4: new low speed USB device using uhci_hcd and address 3
[4294677.820000] usbcore: registered new driver hiddev
[4294677.838000] input: USB HID v1.10 Mouse [Acrox USB & PS/2 Mouse] on usb-0000:00:11.3-1.4
[4294677.838000] usbcore: registered new driver usbhid
[4294677.838000] drivers/usb/input/hid-core.c: v2.01:USB HID core driver
[4294678.399000] ACPI: Fan [FAN1] (off)
[4294678.404000] ACPI: CPU0 (power states: C1[C1] C2[C2])
[4294678.410000] ACPI: Thermal Zone [THRM] (49 C)
[4294678.613000] Attempting manual resume
[4294678.613000] swsusp: Suspend partition has wrong signature?
[4294678.632000] kjournald starting.  Commit interval 5 seconds
[4294678.632000] EXT3-fs: mounted filesystem with ordered data mode.
[4294680.610000] md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
[4294686.180000] Adding 658624k swap on /dev/hda5.  Priority:-1 extents:1
[4294686.563000] EXT3 FS on hda1, internal journal
[4294695.500000] parport_pc: VIA 686A/8231 detected
[4294695.500000] parport_pc: probing current configuration
[4294695.500000] parport_pc: Current parallel port base: 0x378
[4294695.500000] parport0: PC-style at 0x378 (0x778), irq 7, using FIFO [PCSPP,TRISTATE,COMPAT,ECP]
[4294695.583000] parport_pc: VIA parallel port: io=0x378, irq=7
[4294695.594000] lp0: using parport0 (interrupt-driven).
[4294695.655000] mice: PS/2 mouse device common for all mice
[4294695.777000] ieee1394: Initialized config rom entry `ip1394'
[4294695.796000] SCSI subsystem initialized
[4294695.805000] sbp2: $Rev: 1219 $ Ben Collins <bcollins@debian.org>
[4294696.512000] Synaptics Touchpad, model: 1, fw: 4.1, id: 0x848a1, caps: 0x0/0x0
[4294696.519000] input: SynPS/2 Synaptics TouchPad on isa0060/serio2
[4294696.990000] ts: Compaq touchscreen protocol output
[4294698.803000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]
[4294700.407000] cdrom: open failed.
[4294704.041000] Linux agpgart interface v0.101 (c) Dave Jones
[4294704.057000] agpgart: Detected VIA Twister-K/KT133x/KM133 chipset
[4294704.066000] agpgart: AGP aperture is 64M @ 0xe0000000
[4294704.233000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[4294704.258000] shpchp: shpc_init : shpc_cap_offset == 0
[4294704.258000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[4294704.397000] Linux Kernel Card Services
[4294704.397000]   options:  [pci] [cardbus] [pm]
[4294704.427000] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 11
[4294704.427000] PCI: setting IRQ 11 as level-triggered
[4294704.427000] ACPI: PCI Interrupt 0000:00:08.0[A] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
[4294704.427000] Yenta: CardBus bridge found at 0000:00:08.0 [1584:3000]
[4294704.427000] Yenta O2: res at 0x94/0xD4: 00/ea
[4294704.427000] Yenta O2: enabling read prefetch/write burst
[4294704.547000] Yenta: ISA IRQ mask 0x0020, PCI irq 11
[4294704.547000] Socket status: 30000811
[4294704.742000] ohci1394: $Rev: 1250 $ Ben Collins <bcollins@debian.org>
[4294704.742000] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 10
[4294704.742000] ACPI: PCI Interrupt 0000:00:10.0[A] -> Link [LNKC] -> GSI 10 (level, low) -> IRQ 10
[4294704.806000] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[10]  MMIO=[dffff800-dfffffff]  Max Packet=[2048]
[4294705.043000] irda_init()
[4294705.043000] NET: Registered protocol family 23
[4294705.901000] ACPI: PCI Interrupt 0000:00:11.5[C] -> Link [LNKC] -> GSI 10 (level, low) -> IRQ 10
[4294705.901000] PCI: Setting latency timer of device 0000:00:11.5 to 64
[4294706.073000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00030d433412fbcf][4294707.553000] ACPI: PCI Interrupt 0000:00:11.6[C] -> Link [LNKC] -> GSI 10 (level, low) -> IRQ 10
[4294707.554000] PCI: Setting latency timer of device 0000:00:11.6 to 64
[4294710.307000] drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 2 if 0 alt 0 proto 2 vid 0x03F0 pid 0x7304
[4294710.321000] usbcore: registered new driver usblp
[4294710.321000] drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driver
[4294710.684000] Real Time Clock Driver v1.12
[4294710.903000] input: PC Speaker
[4294711.144000] Floppy drive(s): fd0 is 1.44M
[4294711.158000] FDC 0 is a post-1991 82077
[4294714.308000] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[4294714.325000] NET: Registered protocol family 17
[4294717.995000] NET: Registered protocol family 10
[4294717.995000] Disabled Privacy Extensions on device c0321b80(lo)
[4294717.995000] IPv6 over IPv4 tunneling driver
[4294719.686000] ACPI: AC Adapter [AC0] (on-line)
[4294719.777000] ACPI: Battery Slot [BAT0] (battery present)
[4294719.812000] ACPI: Power Button (FF) [PWRF]
[4294719.812000] ACPI: Power Button (CM) [PWRB]
[4294719.812000] ACPI: Lid Switch [LID]
[4294719.812000] ACPI: Sleep Button (CM) [SLPB]
[4294719.997000] ibm_acpi: ec object not found
[4294728.530000] eth0: no IPv6 routers present
[4294732.154000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[4294732.154000] apm: overridden by ACPI.
[4294733.180000] ip_tables: (C) 2000-2002 Netfilter core team
[4294733.228000] ip_conntrack version 2.1 (1791 buckets, 14328 max) - 248 bytes per conntrack
[4294735.230000] cs: IO port probe 0x100-0x4ff: excluding 0x408-0x40f 0x4d0-0x4d7
[4294735.232000] cs: IO port probe 0xc00-0xcf7: clean.
[4294735.233000] cs: IO port probe 0xa00-0xaff: clean.
[4294735.235000] cs: memory probe 0xa0000000-0xa0ffffff: clean.
[4294737.073000] powernow: PowerNOW! Technology present. Can scale: frequency and voltage.
[4294737.078000] Detected 1200.213 MHz processor.
[4294737.085000] powernow: SGTC: 13333
[4294737.085000] powernow: Minimum speed 800 MHz. Maximum speed 1200 MHz.
[4294741.513000] Bluetooth: Core ver 2.7
[4294741.513000] NET: Registered protocol family 31
[4294741.513000] Bluetooth: HCI device and connection manager initialized
[4294741.513000] Bluetooth: HCI socket layer initialized
[4294741.770000] Bluetooth: L2CAP ver 2.7
[4294741.770000] Bluetooth: L2CAP socket layer initialized
[4294741.840000] Bluetooth: RFCOMM ver 1.5
[4294741.840000] Bluetooth: RFCOMM socket layer initialized
[4294741.840000] Bluetooth: RFCOMM TTY layer initialized

---

### Post by jesse on 2006-01-07
I know I didn't find it listed there either. Did anyone else?

---

### Post by dotdot on 2006-01-07
iwconfig - isn't telling us anything - it can't see it


dmesg - isn't seemingly  picking  it up either.

- 
what about lspci ?



i can only assume it's not being built by the kernel when it's (not) being probed.

..(I'm new to this myself only my usb wireless thingy is working fine..)

..cheeers 

..

---

### Post by jesse on 2006-01-07
Ok. Here's what it gives me. 

0000:00:00.0 Host bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133] (rev 80)
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133 AGP]
0000:00:08.0 CardBus bridge: O2 Micro, Inc. OZ6912 Cardbus Controller
0000:00:10.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)
0000:00:11.0 ISA bridge: VIA Technologies, Inc. VT8231 [PCI-to-ISA Bridge] (rev 10)
0000:00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
0000:00:11.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1e)
0000:00:11.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1e)
0000:00:11.4 Bridge: VIA Technologies, Inc. VT8235 ACPI (rev 10)
0000:00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT82C686 AC97 Audio Controller (rev 40)
0000:00:11.6 Communication controller: VIA Technologies, Inc. Intel 537 [AC97 Modem] (rev 20)
0000:00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 51)
0000:01:00.0 VGA compatible controller: S3 Inc. VT8636A [ProSavage KN133] AGP4X VGA Controller (TwisterK) (rev 01)


My kernel is the latest breezy version, and I think I have all of the packages installed that are supposed to be. I've tried rebooting too, and nothing.

---

### Post by dotdot on 2006-01-07
ok ... i've checked a few things out - try this (no solutions .. yet)

lshal - dump it and put it up - there a lot of data btw.
i thought about greping out some stuff then though nah just paste it all.

basically for each pci device picked up there should be several links to everything to hook it into the kernel.

..  for the firefire card i'm using, for example, it shows  up like...

udi = '/org/freedesktop/Hal/devices/pci_104c_8021'
  info.udi = '/org/freedesktop/Hal/devices/pci_104c_8021'  (string)
  linux.subsystem = 'pci'  (string)
  linux.hotplug_type = 1  (0x1)  (int)
  pci.subsys_product = 'Unknown (0x0000)'  (string)
  pci.subsys_vendor = 'Unknown (0x0000)'  (string)
  info.product = 'TSB43AA22 IEEE-1394 Controller (PHY/Link Integrated)'  (string)
  pci.product = 'TSB43AA22 IEEE-1394 Controller (PHY/Link Integrated)'  (string)
  info.vendor = 'Texas Instruments'  (string)
  pci.vendor = 'Texas Instruments'  (string)
  pci.device_protocol = 16  (0x10)  (int)
  pci.device_subclass = 0  (0x0)  (int)
  pci.device_class = 12  (0xc)  (int)
  pci.subsys_vendor_id = 0  (0x0)  (int)
  pci.subsys_product_id = 0  (0x0)  (int)
  pci.vendor_id = 4172  (0x104c)  (int)
  pci.product_id = 32801  (0x8021)  (int)
  info.linux.driver = 'ohci1394'  (string)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:0c.0/0000:02:00.0'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_1180_478_0'  (string)
  info.bus = 'pci'  (string)
  linux.sysfs_path_device = '/sys/devices/pci0000:00/0000:00:0c.0/0000:02:00.0'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:0c.0/0000:02:00.0'  (string)

- we need to check your pci card out likewise.

hope this helps...

..

---

### Post by Jammy_Stuff on 2006-01-07
Do you find that it takes a long time to carry out the loading modules stage at boot up? I had a similar problem with my USB wireless adapter. Fixed itself though.

---

### Post by jesse on 2006-01-07
I tried posting the whole thing but Ubuntuforums told me it was too long to post. 

Should I narrow it down using a different command, or post in sections.

---

### Post by jesse on 2006-01-07
No, I don't find that booting takes a long time. It's blazing fast.

---

### Post by dotdot on 2006-01-07
ok cut out a section - like the one i cut out above - for your  card.

..

---

### Post by jesse on 2006-01-07
Ok, I think this is the card, but I'm not sure. It might be some other piece of hardware. I'm not sure I can tell what's what. 

udi = '/org/freedesktop/Hal/devices/ieee1394_guid_30d433412fbcf'
  info.udi = '/org/freedesktop/Hal/devices/ieee1394_guid_30d433412fbcf'  (string)
  linux.subsystem = 'ieee1394'  (string)
  linux.hotplug_type = 1  (0x1)  (int)
  info.product = 'Unknown (0x00030d)'  (string)
  info.vendor = 'Unknown (0x00030d)'  (string)
  ieee1394.product = 'Unknown (0x00030d)'  (string)
  ieee1394.product_id = 0  (0x0)  (int)
  ieee1394.vendor = 'Unknown (0x00030d)'  (string)
  ieee1394.version = 1  (0x1)  (int)
  ieee1394.specifier_id = 94  (0x5e)  (int)
  ieee1394.vendor_id = 781  (0x30d)  (int)
  ieee1394.guid = 859007217761231  (0x30d433412fbcf)  (uint64)
  info.parent = '/org/freedesktop/Hal/devices/pci_1106_3044'  (string)
  info.bus = 'ieee1394'  (string)
  linux.sysfs_path_device = '/sys/devices/pci0000:00/0000:00:10.0/fw-host0/00030d433412fbcf/00030d433412fbcf-0'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:10.0/fw-host0/00030d433412fbcf/00030d433412fbcf-0'  (string)

---

### Post by dotdot on 2006-01-07
ok hang on - my fault - can you put up the list for the card you're having problems with

ie 

 product info: "WavePlus Technology", "WLAN PC Card WP1200", "Version 01.00"

we need the section with this inside. (if there is one.)

..thanks.

..

---

### Post by jesse on 2006-01-07
When I type the command

sudo cardctl ident

I get the following output

Socket 0:
product info: "WavePlus Technology", "WLAN PC Card WP1200", "Version 01.00", ""
manfid: 0x0000, 0x0000
function: 6 (network)



But when I type 

lshal

I get a list to long for Ubuntu forums to allow me to post it all. 

I looked through that list and it contains no reference to WavePlus or the card. I posted what I thought was the closest thing, but it says "unknown"

---

### Post by jesse on 2006-01-07
Ok. I found a program called hwinfo and installed it using synaptic. Then I typed it in the terminal and here's what it gives me about the card. 

35: PCMCIA 00.0: 0280 Network controller
  [Created at pcmcia.120]
  Unique ID: K1pk.CkjMD_CqGZ9
  Parent ID: RE4e.USAHT5beq3D
  Hardware Class: network
  Model: "WavePlus WLAN PC Card WP1200"
  Hotplug: PCMCIA
  Socket: 0
  Vendor: pcmcia 0x0000 "WavePlus Technology"
  Device: pcmcia 0x0000 "WLAN PC Card WP1200"
  Extra Info: WavePlus Technology, WLAN PC Card WP1200, Version 01.00
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #14 (CardBus bridge)


Yet, when I go to network settings it still doesn't show up as detected. ndisgtk also shows "hardware present: no"

---

### Post by jesse on 2006-01-10
Ok. I discovered something else. when I reboot I see some error message as the system is shutting down saying wireless daemon eth0 fails to shut down and then "no such file or directory" ???:confused: 

Why is the wireless card eth0 and not wlan0? 

Only eth0 and ppp0 still show up as choices to configure in gnome network settings. The wireless card is not listed separately. 

Are the wireless card and wired connection supposed to share eth0? 

If not, does anyone know how I can create wlan0 or whatever is necessary? 

This is driving me mad.

---

### Post by carlosqueso on 2006-01-10
what does ```
ndiswrapper -l
```give you?

---

### Post by jesse on 2006-01-10
ndiswrapper -l
Installed ndis drivers:
bcmwl5          driver present
bcmwl5a         driver present
netwg311                driver present
wpndis51                driver present


I just logged into x as root (by booting in recovery mode) and changed the configuration of the wireless access point roaming daemon to wlan0, but the wireless card still doesn't show up as present or show up in network settings as something with the option to configure. And now when I reboot it says "stopping wireless access point roaming: failed to kill daemon (file or directory does not exist) wlan0"

I'm totally at a loss.

---

### Post by dotdot on 2006-01-10
ok jesse - i think you may have just too many cards installed.

on my box for ref heres what i see.

$ sudo ndiswrapper -l
Installed ndis drivers:
netrtusb        driver present, hardware present


- i remeber looking through the 'start of this saga' - and saw you installed the sys file as well - i don't think was required.

think you may have to take them all out then just put in the one.

..

---

### Post by carlosqueso on 2006-01-10
okay...try uninstalling any of the drivers that you aren't using with ```
sudo ndiswrapper -e <driver name>
``` and then type ```
sudo modprobe ndiswrapper
```

---

### Post by jesse on 2006-01-10
Ok. Now I have just one driver installed, and I just looked at the driver itself as displayed as a text file in firefox and it's the right one for the card I have. 

Here's what I get now: 

jesse@GericomLaptop:~$ sudo modprobe ndiswrapper
jesse@GericomLaptop:~$ sudo ndiswrapper -l
Installed ndis drivers:
wpndis51                driver present


Notice mine doesn't say "hardware present"
That, I think, is the root of the problem, and I can't figure out why it says this when the card is inserted and it's light blinks.

---

### Post by dotdot on 2006-01-10
get into networking and disable eth0

... then bounce it - now what do you see ?

..

---

### Post by jesse on 2006-01-10
Ok. I just called Netgear technical support, the maker of my wireless router not the wireless card, both of which I bought on eBay (I guess that wasn't the way to go). 

Some guy in India providing Netgear technical support determined that my wireless router is defective and offered to replace it. So I'll have to wait for the replacement router to arrive before I can see if the wireless card can actually connect. 

I wish I had known about the router problem before this "saga" began :o 

Would it be normal though for ndiswrapper and ndisgtk not to show that the card is present even though pcmcia seems to work because the light on the card blinks when inserted? Does the router have to be sending a signal to the card in order for Linux to say that the "hardware is present"?

Thanks everyone for your efforts to help.

---

### Post by jesse on 2006-01-10
Apparently I'm not the only one having this problem. See link

[http://www.linuxquestions.org/questions/showthread.php?t=382032](http://www.linuxquestions.org/questions/showthread.php?t=382032)

---

### Post by lindejos on 2006-01-11
Have you looked into [madwifi]("http://madwifi.org/")?  

I used this utitlity to install my wireless card as another device called ath0.  I'm currently using a netgear card, and a netgear router with WEP encryption and it seems to work just fine.  Admittedly my card is installed in a pc and not a pcmcia adapter.  But it's worth a look.

---

### Post by jesse on 2006-01-14
Ok. Now I'm trying to set up madwifi, but I only get this far. 

I'm following the instructions at 
[http://madwifi.org/wiki/UserDocs/FirstTimeHowTo#BuildingMADWiFi](http://madwifi.org/wiki/UserDocs/FirstTimeHowTo#BuildingMADWiFi)


After doing everything else listed, when I type 

sudo wlanconfig ath0 create wlandev wifi0 wlanmode sta

I get the following error message: 

wlanconfig: ioctl: No such device

I can't get past this error. 

What the Hell is ioctl and how do I get it? This is nerve racking.

---

