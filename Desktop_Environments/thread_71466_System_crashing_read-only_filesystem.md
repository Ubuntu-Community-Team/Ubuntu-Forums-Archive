---
title: "System crashing: read-only filesystem"
date: 2005-10-03
forum: Desktop Environments
---

### Post by elgaelo on 2005-10-03
Hi everybody...
It seems that little problems are now growing up to the total crash. If someone could help me, I would apreciate so much... 
1st, Just after installing Kubuntu 5.04 there was problems with the Kcontrol like the Networking Panel. It couldn't be able to change value without runing the KControl from the kconsole with **sudo kcontrol**
2st, almost 1 month later (so 5 days ago) there are problems with the sound server. At startup in order to avoid the long waiting when the system is "Configuiring network interfaces" I use **Ctrl+C** as I read in this forum. Don't know if there's a link between both actions but sometimes I fix the problem don't know how...f*ck!!
3st, A change in the look and feel of the windows makes me to see a message in the KDE session startup. No problem, it seems. I try to fix it doing **chown **cause I see a sort of root:root owner in several config files in HOME/.kde. Doesn't work..I try doing **fsck -p** several times and I receive at the shutdown some ext2 errors. DEFINITELY THE PROBLEM IS THAT THE FILESYSTEM IS MOUNTED AS READ ONLY. Why??
There's the **dmesg **output here. The last line shows how it mount the system as read only.
```
Linux version 2.6.10-5-386 (buildd@terranova) (gcc version 3.3.5 (Debian 1:3.3.5-8ubuntu2)) #1 Tue Apr 5 12:12:40 UTC 2005
BIOS-provided physical RAM map:
BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
BIOS-e820: 00000000000d4000 - 00000000000d8000 (reserved)
BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
BIOS-e820: 0000000000100000 - 000000001fef0000 (usable)
BIOS-e820: 000000001fef0000 - 000000001fefb000 (ACPI data)
BIOS-e820: 000000001fefb000 - 000000001ff00000 (ACPI NVS)
BIOS-e820: 000000001ff00000 - 0000000020000000 (reserved)
BIOS-e820: 00000000fec10000 - 00000000fec20000 (reserved)
BIOS-e820: 00000000ff800000 - 00000000ffc00000 (reserved)
BIOS-e820: 00000000fffffc00 - 0000000100000000 (reserved)
510MB LOWMEM available.
On node 0 totalpages: 130800
DMA zone: 4096 pages, LIFO batch:1
Normal zone: 126704 pages, LIFO batch:16
HighMem zone: 0 pages, LIFO batch:1
DMI present.
ACPI: RSDP (v000 TOSCPL                                ) @ 0x000f6970
ACPI: RSDT (v001 TOSCPL          0x06040000  LTP 0x00000000) @ 0x1fef522c
ACPI: FADT (v001 TOSCPL MONTARA  0x06040000 PTL  0x00000050) @ 0x1fefaeec
ACPI: MADT (v001 INTEL  MONTARA  0x06040000 LOHR 0x00000064) @ 0x1fefaf98
ACPI: SSDT (v001  PmRef  Cpu0Ist 0x00003000 INTL 0x20030224) @ 0x1fef5655
ACPI: SSDT (v001  PmRef  Cpu0Cst 0x00003001 INTL 0x20030224) @ 0x1fef547d
ACPI: SSDT (v001  PmRef    CpuPm 0x00003000 INTL 0x20030224) @ 0x1fef5264
ACPI: DSDT (v001 TOSCPL MONTARAG 0x06040000 MSFT 0x0100000e) @ 0x00000000
ACPI: PM-Timer IO Port: 0x1008
ACPI: Local APIC address 0xfee00000
ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Processor #0 6:13 APIC version 20
ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] disabled)
ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
ACPI: IRQ0 used by override.
ACPI: IRQ2 used by override.
ACPI: IRQ9 used by override.
Enabling APIC mode:  Flat.  Using 1 I/O APICs
Using ACPI (MADT) for SMP configuration information
Built 1 zonelists
Kernel command line: BOOT_IMAGE=Linux ro root=305
mapped APIC to ffffd000 (fee00000)
mapped IOAPIC to ffffc000 (fec00000)
Initializing CPU#0
PID hash table entries: 2048 (order: 11, 32768 bytes)
Detected 1599.193 MHz processor.
Using pmtmr for high-res timesource
Console: colour VGA+ 80x25
Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
Memory: 511236k/523200k available (1436k kernel code, 11416k reserved, 754k data, 224k init, 0k highmem)
Checking if this processor honours the WP bit even in supervisor mode... Ok.
Calibrating delay loop... 3170.30 BogoMIPS (lpj=1585152)
Security Framework v1.0.0 initialized
SELinux:  Disabled at boot.
Mount-cache hash table entries: 512 (order: 0, 4096 bytes)
CPU: After generic identify, caps: afe9fbbf 00000000 00000000 00000000 00000180 00000000
CPU: After vendor identify, caps: afe9fbbf 00000000 00000000 00000000 00000180 00000000
CPU: L1 I cache: 32K, L1 D cache: 32K
CPU: L2 cache: 2048K
CPU: After all inits, caps: afe9fbbf 00000000 00000000 00000040 00000180 00000000
CPU: Intel(R) Pentium(R) M processor 1.60GHz stepping 06
Enabling fast FPU save and restore... done.
Enabling unmasked SIMD FPU exception support... done.
Checking 'hlt' instruction... OK.
Checking for popad bug... OK.
ACPI: Looking for DSDT in initrd... not found!
ENABLING IO-APIC IRQs
..TIMER: vector=0x31 pin1=2 pin2=-1
checking if image is initramfs...it isn't (bad gzip magic numbers); looks like an initrd
Freeing initrd memory: 4248k freed
NET: Registered protocol family 16
EISA bus registered
PCI: PCI BIOS revision 2.10 entry at 0xfd962, last bus=2
PCI: Using configuration type 1
mtrr: v2.0 (20020519)
ACPI: Subsystem revision 20050211
ACPI: Interpreter enabled
ACPI: Using IOAPIC for interrupt routing
ACPI: PCI Root Bridge [PCI0] (00:00)
PCI: Probing PCI hardware (bus 00)
PCI: Ignoring BAR0-3 of IDE controller 0000:00:1f.1
PCI: Via IRQ fixup
PCI: Transparent bridge - 0000:00:1e.0
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGPB._PRT]
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 *10 12 14 15)
ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 *11 12 14 15)
ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 *4 5 6 7 10 12 14 15)
ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 *5 6 7 11 12 14 15)
ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 *11 12 14 15)
ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 7 *11 12 14 15)
ACPI: Embedded Controller [EC0] (gpe 28)
Linux Plug and Play Support v0.97 (c) Adam Belay
pnp: PnP ACPI init
pnp: PnP ACPI: found 11 devices
PnPBIOS: Disabled by ACPI PNP
PCI: Using ACPI for IRQ routing
** PCI interrupts are no longer routed automatically.  If this
** causes a device to stop working, it is probably because the
** driver failed to call pci_enable_device().  As a temporary
** workaround, the "pci=routeirq" argument restores the old
** behavior.  If this argument makes the device work again,
** please email the output of "lspci" to [email]bjorn.helgaas@hp.com[/email]
** so I can fix the driver.
audit: initializing netlink socket (disabled)
audit(1128363491.766:0): initialized
VFS: Disk quotas dquot_6.5.1
Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
devfs: boot_options: 0x0
Initializing Cryptographic API
isapnp: Scanning for PnP cards...
isapnp: No Plug & Play device found
i8042.c: Detected active multiplexing controller, rev 1.1.
serio: i8042 AUX0 port at 0x60,0x64 irq 12
serio: i8042 AUX1 port at 0x60,0x64 irq 12
serio: i8042 AUX2 port at 0x60,0x64 irq 12
serio: i8042 AUX3 port at 0x60,0x64 irq 12
serio: i8042 KBD port at 0x60,0x64 irq 1
Serial: 8250/16550 driver $Revision: 1.90 $ 54 ports, IRQ sharing enabled
ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
ACPI: PCI interrupt 0000:00:1f.6[B] -> GSI 17 (level, low) -> IRQ 17
io scheduler noop registered
io scheduler anticipatory registered
io scheduler deadline registered
io scheduler cfq registered
RAMDISK driver initialized: 16 RAM disks of 8192K size 1024 blocksize
input: AT Translated Set 2 keyboard on isa0060/serio0
EISA: Probing bus 0 at eisa0
Cannot allocate resource for EISA slot 1
Cannot allocate resource for EISA slot 2
Cannot allocate resource for EISA slot 3
Cannot allocate resource for EISA slot 4
EISA: Detected 0 cards.
NET: Registered protocol family 2
IP: routing cache hash table of 4096 buckets, 32Kbytes
TCP: Hash tables configured (established 32768 bind 65536)
NET: Registered protocol family 8
NET: Registered protocol family 20
Restarting tasks...<6> Strange, kswapd0 not stopped
Strange, kseriod not stopped
done
ACPI wakeup devices: 
ELAN USB1 USB2 USB3 EUSB MODM 
ACPI: (supports S0 S3 S4 S5)
RAMDISK: cramfs filesystem found at block 0
RAMDISK: Loading 4248KiB [1 disk] into ram disk... done.
VFS: Mounted root (cramfs filesystem) readonly.
Freeing unused kernel memory: 224k freed
ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3] C4[C3])
ACPI: Processor [CPU0] (supports 8 throttling states)
NET: Registered protocol family 1
Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
ICH4: IDE controller at PCI slot 0000:00:1f.1
PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)
ACPI: PCI interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 18
ICH4: chipset revision 3
ICH4: not 100% native mode: will probe irqs later
ide0: BM-DMA at 0x1860-0x1867, BIOS settings: hda:DMA, hdb:pio
ide1: BM-DMA at 0x1868-0x186f, BIOS settings: hdc:DMA, hdd:pio
Probing IDE interface ide0...
hda: TOSHIBA MK6025GAS, ATA DISK drive
elevator: using anticipatory as default io scheduler
ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
hda: max request size: 128KiB
hda: 117210240 sectors (60011 MB), CHS=65535/16/63, UDMA(100)
hda: cache flushes supported
/dev/ide/host0/bus0/target0/lun0: p1 p2 < p5 p6 p7 >
Probing IDE interface ide1...
hdc: MATSHITADVD-RAM UJ-831S, ATAPI CD/DVD-ROM drive
ide1 at 0x170-0x177,0x376 on irq 15
Probing IDE interface ide2...
Probing IDE interface ide3...
Probing IDE interface ide4...
Probing IDE interface ide5...
Stopping tasks: ==|
Freeing memory...  done (455 pages freed)
Restarting tasks... done
Adding 2104472k swap on /dev/hda6.  Priority:-1 extents:1
hdc: ATAPI 24X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache
Uniform CD-ROM driver Revision: 3.20
parport: PnPBIOS parport detected.
parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP]
lp0: using parport0 (interrupt-driven).
mice: PS/2 mouse device common for all mice
input: PS/2 Generic Mouse on isa0060/serio4
ieee1394: Initialized config rom entry `ip1394'
SCSI subsystem initialized
sbp2: $Rev: 1219 $ Ben Collins <bcollins@debian.org>
Capability LSM initialized
ts: Compaq touchscreen protocol output
device-mapper: 4.3.0-ioctl (2004-09-30) initialised: [email]dm-devel@redhat.com[/email]
md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
cdrom: open failed.
FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
Real Time Clock Driver v1.12
Linux agpgart interface v0.100 (c) Dave Jones
agpgart: Detected an Intel 855GM Chipset.
agpgart: Maximum main memory to use for agp memory: 438M
agpgart: AGP aperture is 256M @ 0xe0000000
cpci_hotplug: CompactPCI Hot Plug Core version: 0.2
pci_hotplug: PCI Hot Plug PCI Core version: 0.5
shpchp: shpc_init : shpc_cap_offset == 0
shpchp: shpc_init : shpc_cap_offset == 0
shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Evaluate _OSC Set fails. Status = 0x0005
pciehp: add_host_bridge: status 5
pciehp: Fails to gain control of native hot-plug
usbcore: registered new driver usbfs
usbcore: registered new driver hub
USB Universal Host Controller Interface driver v2.2
ACPI: PCI interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 16
uhci_hcd 0000:00:1d.0: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1
PCI: Setting latency timer of device 0000:00:1d.0 to 64
uhci_hcd 0000:00:1d.0: irq 16, io base 0x1800
uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
hub 1-0:1.0: USB hub found
hub 1-0:1.0: 2 ports detected
ACPI: PCI interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 19
uhci_hcd 0000:00:1d.1: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2
PCI: Setting latency timer of device 0000:00:1d.1 to 64
uhci_hcd 0000:00:1d.1: irq 19, io base 0x1820
uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
hub 2-0:1.0: USB hub found
hub 2-0:1.0: 2 ports detected
ACPI: PCI interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
uhci_hcd 0000:00:1d.2: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3
PCI: Setting latency timer of device 0000:00:1d.2 to 64
uhci_hcd 0000:00:1d.2: irq 18, io base 0x1840
uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
hub 3-0:1.0: USB hub found
hub 3-0:1.0: 2 ports detected
usb 3-1: new low speed USB device using uhci_hcd and address 2
ACPI: PCI interrupt 0000:00:1d.7[D] -> GSI 23 (level, low) -> IRQ 23
ehci_hcd 0000:00:1d.7: Intel Corp. 82801DB/DBM (ICH4/ICH4-M) USB 2.0 EHCI Controller
PCI: Setting latency timer of device 0000:00:1d.7 to 64
ehci_hcd 0000:00:1d.7: irq 23, pci mem 0xd0000000
ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
PCI: cache line size of 32 is not supported by device 0000:00:1d.7
ehci_hcd 0000:00:1d.7: USB 2.0 initialized, EHCI 1.00, driver 26 Oct 2004
hub 4-0:1.0: USB hub found
hub 4-0:1.0: 6 ports detected
Evaluate _OSC Set fails. Status = 0x0005
pciehp: add_host_bridge: status 5
pciehp: Fails to gain control of native hot-plug
hw_random: cannot enable RNG, aborting
usb 3-1: new low speed USB device using uhci_hcd and address 3
usbcore: registered new driver hiddev
input: USB HID v1.10 Mouse [Genius       NetScroll+Mini Traveler] on usb-0000:00:1d.2-1
usbcore: registered new driver usbhid
drivers/usb/input/hid-core.c: v2.0:USB HID core driver
ACPI: PCI interrupt 0000:00:1f.5[B] -> GSI 17 (level, low) -> IRQ 17
PCI: Setting latency timer of device 0000:00:1f.5 to 64
intel8x0_measure_ac97_clock: measured 49473 usecs
intel8x0: clocking to 48000
ohci1394: $Rev: 1223 $ Ben Collins <bcollins@debian.org>
ACPI: PCI interrupt 0000:02:00.0[A] -> GSI 20 (level, low) -> IRQ 20
ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[20]  MMIO=[d0201000-d02017ff]  Max Packet=[2048]
8139too Fast Ethernet driver 0.9.27
ACPI: PCI interrupt 0000:02:01.0[A] -> GSI 21 (level, low) -> IRQ 21
eth0: RealTek RTL8139 at 0x4000, 00:0f:b0:5a:5c:2c, IRQ 21
eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
8139cp: 10/100 PCI Ethernet driver v1.2 (Mar 22, 2004)
ieee80211_crypt: registered algorithm 'NULL'
ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 0.19
ipw2200: Copyright(c) 2003-2004 Intel Corporation
ACPI: PCI interrupt 0000:02:02.0[A] -> GSI 22 (level, low) -> IRQ 22
ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
eth0: link down
Linux Kernel Card Services
options:  [pci] [cardbus] [pm]
ACPI: PCI interrupt 0000:02:04.0[A] -> GSI 16 (level, low) -> IRQ 16
Yenta: CardBus bridge found at 0000:02:04.0 [1179:ff01]
Yenta: ISA IRQ mask 0x0000, PCI irq 16
Socket status: 30000006
ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00023f52654119e7]
NET: Registered protocol family 17
ACPI: AC Adapter [ACAD] (on-line)
ACPI: Battery Slot [BAT1] (battery present)
ACPI: Power Button (FF) [PWRF]
ACPI: Lid Switch [LID]
ibm_acpi: ec object not found
ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
apm: overridden by ACPI.
NET: Registered protocol family 10
IPv6 over IPv4 tunneling driver
EXT2-fs error (device hda5): ext2_readdir: zero-length directory entry
Remounting filesystem read-only 

```
now, I'm using Windows XP to write this post trying to receive some kind of help from you, the community. I really want to use KUBUNTU but, how to use if the problems are so hard to fix. Ok, I'm not a experimented user but sh*t, it's imposible!!!
Thanks a lot !!!

---

### Post by mlomker on 2005-10-03
Apparently fsck didn't fix it.  I'd recommend booting up to a Knoppix CD and then running fsck against the drive.  The drive is *supposed* to be ext3 so the fact that it is seeing it as a damaged ext2 shows that it still has a problem.

---

### Post by !nkubus on 2005-10-04
I saw thet a lot of times... DARN I tought it was my hard drive thet was dying..

I usually fix it by booting a live CD  and run fsck -f /dev/hdaSomething

It happens usually when there is a power outage or my computer not rebooted cleanly

---

### Post by mlomker on 2005-10-04
[QUOTE=!nkubus]I saw thet a lot of times... DARN I tought it was my hard drive thet was dying..[/QUOTE]

Once you get it to mount then type the **mount** command and verify that it is ext3.  If it shows as ext2 then the journal was damaged.  You can [look here]("http://www.ubuntuforums.org/showthread.php?p=370532#post370532") for instructions on adding the journal back.

---

### Post by elgaelo on 2005-10-04
Thanks for your help...

I'll try tonight and I'll tell you what happens!! :razz:

---

### Post by !nkubus on 2005-10-04
Thanks a lot. it shows ext3 :)

---

### Post by elgaelo on 2005-10-13
I can't run the UBUNTU Live CD even in expert mode to try to fix the hard drive. There's a problem with the PCMCIA interfaces and it doesn't run belong this point... another idea? Try with KNOPPIX?

Thanks 4 all

---

