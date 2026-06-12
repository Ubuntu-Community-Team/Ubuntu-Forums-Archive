---
title: "Problem when starting KDE..."
date: 2005-08-01
forum: Desktop Environments
---

### Post by SKampY on 2005-08-01
Hi all,

I have installed Kubuntu 5.04 today and all is perfect except when I type my login and password in kdm, kde desktop takes about 20 minutes to load. I have Kubuntu wallpaper during this 20 minutes ! ](*,)
I don't know if someone knows this problem, but I don't know what to do... 

I don't think it's my video card : ATI MOBILITY RADEON 9700 (I've fglrx installed - DRI activated) nor my internet connection via wifi (Intel Pro 2200BG with ipw2200 installed).


Thanks for your responses.

---

### Post by f1dave on 2005-08-02
What about the rest of your rig, CPU/motherboard etc?

And how does your computer perform in windows or other OSes.

---

### Post by skyboy on 2005-08-02
can you post the result of the command "dmesg" in a console ?
would be a good start

---

### Post by SKampY on 2005-08-02
I don't think it's my config : I have a laptop AOpen 1557-GLS with 1Gb of RAM, CPU: Pentium Centrino 1.8 GHz and HDD 60 GB.
The are no problem with other OSes (Windows XP, Linux FC3, DSL, Knoppix 3.9 tested).

And, apparently, I'm not the only one who have this problem when logged in, in kdm with Kubuntu.

Here's my dmesg :

> 
root@Kubuntu:/ # dmesg
 Looking for DSDT in initrd... not found!
ACPI: setting ELCR to 0200 (from 0c00)
checking if image is initramfs...it isn't (bad gzip magic numbers); looks like an initrd
Freeing initrd memory: 4300k freed
NET: Registered protocol family 16
EISA bus registered
PCI: PCI BIOS revision 2.10 entry at 0xfd7d5, last bus=2
PCI: Using configuration type 1
mtrr: v2.0 (20020519)
ACPI: Subsystem revision 20050211
ACPI: Interpreter enabled
ACPI: Using PIC for interrupt routing
ACPI: PCI Root Bridge [PCI0] (00:00)
PCI: Probing PCI hardware (bus 00)
PCI: Ignoring BAR0-3 of IDE controller 0000:00:1f.1
PCI: Transparent bridge - 0000:00:1e.0
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
ACPI: PCI Interrupt Link [LNKA] (IRQs 10 *11)
ACPI: PCI Interrupt Link [LNKB] (IRQs *10)
ACPI: PCI Interrupt Link [LNKC] (IRQs 10 *11)
ACPI: PCI Interrupt Link [LNKD] (IRQs 10) *11
ACPI: PCI Interrupt Link [LNKE] (IRQs 10 11) *0, disabled.
ACPI: PCI Interrupt Link [LNKF] (IRQs 10 11) *0, disabled.
ACPI: PCI Interrupt Link [LNKG] (IRQs 10 11) *0, disabled.
ACPI: PCI Interrupt Link [LNKH] (IRQs *10 11)
ACPI: Embedded Controller [EC0] (gpe 28)
Linux Plug and Play Support v0.97 (c) Adam Belay
pnp: PnP ACPI init
pnp: PnP ACPI: found 9 devices
PnPBIOS: Disabled by ACPI PNP
PCI: Using ACPI for IRQ routing
** PCI interrupts are no longer routed automatically.  If this
** causes a device to stop working, it is probably because the
** driver failed to call pci_enable_device().  As a temporary
** workaround, the "pci=routeirq" argument restores the old
** behavior.  If this argument makes the device work again,
** please email the output of "lspci" to [email]bjorn.helgaas@hp.com[/email]
** so I can fix the driver.
Simple Boot Flag at 0x36 set to 0x1
audit: initializing netlink socket (disabled)
audit(1122993161.754:0): initialized
VFS: Disk quotas dquot_6.5.1
Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
devfs: boot_options: 0x0
Initializing Cryptographic API
isapnp: Scanning for PnP cards...
isapnp: No Plug & Play device found
i8042.c: Detected active multiplexing controller, rev 1.9.
serio: i8042 AUX0 port at 0x60,0x64 irq 12
serio: i8042 AUX1 port at 0x60,0x64 irq 12
serio: i8042 AUX2 port at 0x60,0x64 irq 12
serio: i8042 AUX3 port at 0x60,0x64 irq 12
serio: i8042 KBD port at 0x60,0x64 irq 1
Serial: 8250/16550 driver $Revision: 1.90 $ 54 ports, IRQ sharing enabled
ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 10
PCI: setting IRQ 10 as level-triggered
ACPI: PCI interrupt 0000:00:1f.6[B] -> GSI 10 (level, low) -> IRQ 10
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
EISA: Detected 0 cards.
NET: Registered protocol family 2
IP: routing cache hash table of 8192 buckets, 64Kbytes
TCP: Hash tables configured (established 262144 bind 65536)
NET: Registered protocol family 8
NET: Registered protocol family 20
Restarting tasks...<6> Strange, kswapd0 not stopped
 Strange, kseriod not stopped
 done
ACPI wakeup devices:
LID0 LANC MODM
ACPI: (supports S0 S3 S4 S5)
RAMDISK: cramfs filesystem found at block 0
RAMDISK: Loading 4300KiB [1 disk] into ram disk... done.
VFS: Mounted root (cramfs filesystem) readonly.
Freeing unused kernel memory: 224k freed
ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
ACPI: Processor [CPU0] (supports 8 throttling states)
ACPI: Thermal Zone [THRC] (32 C)
ACPI: Thermal Zone [THRS] (29 C)
NET: Registered protocol family 1
Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
ICH4: IDE controller at PCI slot 0000:00:1f.1
PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)
ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
PCI: setting IRQ 11 as level-triggered
ACPI: PCI interrupt 0000:00:1f.1[A] -> GSI 11 (level, low) -> IRQ 11
ICH4: chipset revision 3
ICH4: not 100% native mode: will probe irqs later
    ide0: BM-DMA at 0x1860-0x1867, BIOS settings: hda:DMA, hdb:pio
    ide1: BM-DMA at 0x1868-0x186f, BIOS settings: hdc:DMA, hdd:pio
Probing IDE interface ide0...
hda: HTS726060M9AT00, ATA DISK drive
elevator: using anticipatory as default io scheduler
ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
hda: max request size: 1024KiB
hda: 117210240 sectors (60011 MB) w/7877KiB Cache, CHS=16383/255/63, UDMA(100)
hda: cache flushes supported
 /dev/ide/host0/bus0/target0/lun0: p1 p2
Probing IDE interface ide1...
hdc: DVD+RW RW8165, ATAPI CD/DVD-ROM drive
ide1 at 0x170-0x177,0x376 on irq 15
Probing IDE interface ide2...
Probing IDE interface ide3...
Probing IDE interface ide4...
Probing IDE interface ide5...
Stopping tasks: ==|
Freeing memory... done (458 pages freed)
Restarting tasks... done
EXT3-fs: mounted filesystem with ordered data mode.
kjournald starting.  Commit interval 5 seconds
Adding 498004k swap on /dev/hda2.  Priority:-1 extents:1
EXT3 FS on hda1, internal journal
hdc: ATAPI 24X DVD-ROM CD-R/RW drive, 8192kB Cache
Uniform CD-ROM driver Revision: 3.20
parport: PnPBIOS parport detected.
parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
lp0: using parport0 (interrupt-driven).
mice: PS/2 mouse device common for all mice
Synaptics Touchpad, model: 1
 Firmware: 13.8
 180 degree mounted touchpad
 Sensor: 18
 new absolute packet format
 Touchpad has extended capability bits
 -> 4 multi-buttons, i.e. besides standard buttons
 -> multifinger detection
 -> palm detection
input: SynPS/2 Synaptics TouchPad on isa0060/serio4
ieee1394: Initialized config rom entry `ip1394'
SCSI subsystem initialized
sbp2: $Rev: 1219 $ Ben Collins <bcollins@debian.org>
fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[fglrx] Maximum main memory to use for locked dma buffers: 805 MBytes.
ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
ACPI: PCI interrupt 0000:01:00.0[A] -> GSI 11 (level, low) -> IRQ 11
[fglrx] module loaded - fglrx 8.8.25 [Jan 14 2005] on minor 0
ieee80211_crypt: registered algorithm 'NULL'
ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 0.19
ipw2200: Copyright(c) 2003-2004 Intel Corporation
PCI: Enabling device 0000:02:06.0 (0000 -> 0002)
ACPI: PCI Interrupt Link [LNKE] enabled at IRQ 10
ACPI: PCI interrupt 0000:02:06.0[A] -> GSI 10 (level, low) -> IRQ 10
ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
ts: Compaq touchscreen protocol output
Capability LSM initialized
device-mapper: 4.3.0-ioctl (2004-09-30) initialised: [email]dm-devel@redhat.com[/email]
md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
cdrom: open failed.
Real Time Clock Driver v1.12
Linux agpgart interface v0.100 (c) Dave Jones
agpgart: Detected an Intel 855PM Chipset.
agpgart: Maximum main memory to use for agp memory: 816M
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
ACPI: PCI interrupt 0000:00:1d.0[A] -> GSI 11 (level, low) -> IRQ 11
uhci_hcd 0000:00:1d.0: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1
PCI: Setting latency timer of device 0000:00:1d.0 to 64
uhci_hcd 0000:00:1d.0: irq 11, io base 0x1800
uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
hub 1-0:1.0: USB hub found
hub 1-0:1.0: 2 ports detected
ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 10
ACPI: PCI interrupt 0000:00:1d.1[B] -> GSI 10 (level, low) -> IRQ 10
uhci_hcd 0000:00:1d.1: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2
PCI: Setting latency timer of device 0000:00:1d.1 to 64
uhci_hcd 0000:00:1d.1: irq 10, io base 0x1820
uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
hub 2-0:1.0: USB hub found
hub 2-0:1.0: 2 ports detected
ACPI: PCI interrupt 0000:00:1d.2[C] -> GSI 11 (level, low) -> IRQ 11
uhci_hcd 0000:00:1d.2: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3
NET: Registered protocol family 17
PCI: Setting latency timer of device 0000:00:1d.2 to 64
uhci_hcd 0000:00:1d.2: irq 11, io base 0x1840
uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
hub 3-0:1.0: USB hub found
hub 3-0:1.0: 2 ports detected
usb 1-1: new low speed USB device using uhci_hcd and address 2
ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 10
ACPI: PCI interrupt 0000:00:1d.7[D] -> GSI 10 (level, low) -> IRQ 10
ehci_hcd 0000:00:1d.7: Intel Corp. 82801DB/DBM (ICH4/ICH4-M) USB 2.0 EHCI Controller
PCI: Setting latency timer of device 0000:00:1d.7 to 64
ehci_hcd 0000:00:1d.7: irq 10, pci mem 0xd0000000
ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
PCI: cache line size of 32 is not supported by device 0000:00:1d.7
ehci_hcd 0000:00:1d.7: USB 2.0 initialized, EHCI 1.00, driver 26 Oct 2004
hub 4-0:1.0: USB hub found
hub 4-0:1.0: 6 ports detected
usb 1-1: device descriptor read/all, error -71
Evaluate _OSC Set fails. Status = 0x0005
pciehp: add_host_bridge: status 5
pciehp: Fails to gain control of native hot-plug
hw_random: RNG not detected
usb 1-1: new low speed USB device using uhci_hcd and address 4
usb 2-1: new full speed USB device using uhci_hcd and address 2
usbcore: registered new driver hiddev
input: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1d.0-1
usbcore: registered new driver usbhid
drivers/usb/input/hid-core.c: v2.0:USB HID core driver
Initializing USB Mass Storage driver...
ACPI: PCI interrupt 0000:00:1f.5[B] -> GSI 10 (level, low) -> IRQ 10
PCI: Setting latency timer of device 0000:00:1f.5 to 64
scsi0 : SCSI emulation for USB Mass Storage devices
usbcore: registered new driver usb-storage
USB Mass Storage support registered.
usb-storage: device found at 2
usb-storage: waiting for device to settle before scanning
AC'97 0 analog subsections not ready
intel8x0_measure_ac97_clock: measured 49481 usecs
intel8x0: clocking to 48000
b44.c:v0.95 (Aug 3, 2004)
ACPI: PCI interrupt 0000:02:05.0[A] -> GSI 10 (level, low) -> IRQ 10
PCI: Setting latency timer of device 0000:02:05.0 to 64
eth0: Broadcom 4400 10/100BaseT Ethernet 00:0a:e4:55:93:b9
Linux Kernel Card Services
  options:  [pci] [cardbus] [pm]
PCI: Enabling device 0000:02:09.0 (0000 -> 0002)
ACPI: PCI Interrupt Link [LNKF] enabled at IRQ 11
ACPI: PCI interrupt 0000:02:09.0[A] -> GSI 11 (level, low) -> IRQ 11
Yenta: CardBus bridge found at 0000:02:09.0 [17c0:3301]
Yenta: ISA IRQ mask 0x0038, PCI irq 11
Socket status: 30000006
ACPI: PCI interrupt 0000:02:09.1[B] -> GSI 10 (level, low) -> IRQ 10
Yenta: CardBus bridge found at 0000:02:09.1 [17c0:3301]
Yenta: ISA IRQ mask 0x0038, PCI irq 10
Socket status: 30000006
ohci1394: $Rev: 1223 $ Ben Collins <bcollins@debian.org>
ACPI: PCI Interrupt Link [LNKG] enabled at IRQ 11
ACPI: PCI interrupt 0000:02:09.2[C] -> GSI 11 (level, low) -> IRQ 11
PCI: Setting latency timer of device 0000:02:09.2 to 64
ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[11]  MMIO=[d0203000-d02037ff]  Max Packet=[2048]
ieee1394: Host added: ID:BUS[0-00:1023]  GUID[04e40a0087111019]
NET: Registered protocol family 10
Disabled Privacy Extensions on device c02f0500(lo)
IPv6 over IPv4 tunneling driver
eth1: duplicate address detected!
  Vendor: NEC       Model: USB UF000x        Rev: 1.50
  Type:   Direct-Access                      ANSI SCSI revision: 00
  Vendor: NEC       Model: USB UF000x        Rev: 1.50
  Type:   Direct-Access                      ANSI SCSI revision: 00
  Vendor: NEC       Model: USB UF000x        Rev: 1.50
  Type:   Direct-Access                      ANSI SCSI revision: 00
  Vendor: NEC       Model: USB UF000x        Rev: 1.50
  Type:   Direct-Access                      ANSI SCSI revision: 00
ACPI: AC Adapter [ADP1] (on-line)
ACPI: Battery Slot [BAT0] (battery present)
ACPI: Power Button (FF) [PWRF]
ACPI: Lid Switch [LID0]
ACPI: Sleep Button (CM) [SLPB]
ibm_acpi: ec object not found
ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
Attached scsi removable disk sda at scsi0, channel 0, id 0, lun 0
Attached scsi removable disk sdb at scsi0, channel 0, id 0, lun 1
apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
apm: overridden by ACPI.
Attached scsi removable disk sdc at scsi0, channel 0, id 0, lun 2
Attached scsi removable disk sdd at scsi0, channel 0, id 0, lun 3
  Vendor: NEC       Model: USB UF000x        Rev: 1.50
  Type:   Direct-Access                      ANSI SCSI revision: 00
Attached scsi removable disk sde at scsi0, channel 0, id 0, lun 4
  Vendor: NEC       Model: USB UF000x        Rev: 1.50
  Type:   Direct-Access                      ANSI SCSI revision: 00
cs: IO port probe 0x0100-0x04ff: excluding 0x4d0-0x4d7
cs: IO port probe 0x0800-0x08ff: excluding 0x800-0x80f
cs: IO port probe 0x0c00-0x0cff: clean.
cs: IO port probe 0x0a00-0x0aff: clean.
Attached scsi removable disk sdf at scsi0, channel 0, id 0, lun 5
  Vendor: NEC       Model: USB UF000x        Rev: 1.50
  Type:   Direct-Access                      ANSI SCSI revision: 00
Attached scsi removable disk sdg at scsi0, channel 0, id 0, lun 6
  Vendor: NEC       Model: USB UF000x        Rev: 1.50
  Type:   Direct-Access                      ANSI SCSI revision: 00
Attached scsi removable disk sdh at scsi0, channel 0, id 0, lun 7
usb-storage: device scan complete
allocation failed: out of vmalloc space - use vmalloc=<size> to increase size.
Fire GL built-in AGP-support
Based on agpgart interface v0.99 (c) Jeff Hartmann
agpgart: Maximum main memory to use for agp memory: 816M
agpgart: Detected an Intel 855PM Chipset, no integrated grapics found.
agpgart: Detected Intel i855PM chipset
agpgart: AGP aperture is 256M @ 0xe0000000
Power management callback for AGP chipset installed
[fglrx] AGP detected, AgpState   = 0x1f000217 (hardware caps of chipset)
AGP: Found 2 AGPv2 devices
AGP: Doing enable for AGPv2
[fglrx] AGP enabled,  AgpCommand = 0x1f000314 (selected caps)
[fglrx] free  AGP = 256126976
[fglrx] max   AGP = 256126976
[fglrx] free  LFB = 114274304
[fglrx] max   LFB = 114274304
[fglrx] free  Inv = 0
[fglrx] max   Inv = 0
[fglrx] total Inv = 0
[fglrx] total TIM = 0
[fglrx] total FB  = 0
[fglrx] total AGP = 65536



Thanks for your replies !

---

### Post by skyboy on 2005-08-03
ok, few things :

Dunno really but first,  could you also post the result of lspci please.

Second, did you install the package laptop-mode ?? and the linux-headers-686 ?? those headers contains all necessary info for laptops. Maybe you have some kind of conflict in kde config (eventhough i doubt ...).

Then, can you trace at what specific moment the computer hold on ??

Last but not the least, check your /etc/kde3/kdm/kdmrc file for any crazy things. This file is the kdm config. Or just post it too.


good luck :)

---

### Post by skyboy on 2005-08-03
there was another post in the forum and that is what was suggested : $> Try deleting the following directories:

> rm -rf ~/.kde/socket-<hostname>
> rm -rf ~/.kde/tmp-<hostname>
> rm -rf ~/.kde/cache-<hostname>

This deletes all cached and temporary information for kde, and you may have better luck when restarting.

If not, check the permissions and ownership of ~/.ICEauthority. You should own and have read/write access to this file. This file having bad permissions is a common cause of kde login issues.

Hope one of these works. They're (in my experience) the two most common causes of KDE problems.

---

### Post by SKampY on 2005-08-03
> 
 Try deleting the following directories:

> rm -rf ~/.kde/socket-<hostname>
> rm -rf ~/.kde/tmp-<hostname>
> rm -rf ~/.kde/cache-<hostname>

This deletes all cached and temporary information for kde, and you may have better luck when restarting.

If not, check the permissions and ownership of ~/.ICEauthority. You should own and have read/write access to this file. This file having bad permissions is a common cause of kde login issues.

Hope one of these works. They're (in my experience) the two most common causes of KDE problems.

This is done, but it takes again 20 minutes to load KDE after logged in, in kdm.


Here's my lspci :
> 
root@Kubuntu:~ # lspci
0000:00:00.0 Host bridge: Intel Corp. 82855PM Processor to I/O Controller (rev 21)
0000:00:01.0 PCI bridge: Intel Corp. 82855PM Processor to AGP Controller (rev 21)
0000:00:1d.0 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
0000:00:1d.1 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
0000:00:1d.2 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
0000:00:1d.7 USB Controller: Intel Corp. 82801DB/DBM (ICH4/ICH4-M) USB 2.0 EHCI Controller (rev 03)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev 83)
0000:00:1f.0 ISA bridge: Intel Corp. 82801DBM LPC Interface Controller (rev 03)
0000:00:1f.1 IDE interface: Intel Corp. 82801DBM (ICH4) Ultra ATA Storage Controller (rev 03)
0000:00:1f.3 SMBus: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
0000:00:1f.6 Modem: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]
0000:02:05.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)
0000:02:06.0 Network controller: Intel Corp. PRO/Wireless 2200BG (rev 05)
0000:02:09.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ac)
0000:02:09.1 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ac)
0000:02:09.2 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 04)

But I don't see any trouble in it.


Last but not least, my /etc/kde3/kdm/kdmrc :
> 
root@Kubuntu:~ # cat /etc/kde3/kdm/kdmrc
# KDM master configuration file
#
# Definition: the greeter is the login dialog, i.e., the part of KDM
# which the user sees.
#
# You can configure every X-display individually.
# Every display has a display name, which consists of a host name
# (which is empty for local displays specified in {Static|Reserve}Servers),
# a colon, and a display number. Additionally, a display belongs to a
# display class (which can be ignored in most cases; the control center
# does not support this feature at all).
# Sections with display-specific settings have the formal syntax
# "[X-" host [":" number [ "_" class ]] "-" sub-section "]"
# You can use the "*" wildcard for host, number, and class. You may omit
# trailing components; they are assumed to be "*" then.
# The host part may be a domain specification like ".inf.tu-dresden.de".
# It may also be "+", which means non-empty, i.e. remote displays only.
# From which section a setting is actually taken is determined by these
# rules:
# - an exact match takes precedence over a partial match (for the host part),
#   which in turn takes precedence over a wildcard ("+" taking precedence
#   over "*")
# - precedence decreases from left to right for equally exact matches
# Example: display name "myhost:0", class "dpy".
# [X-myhost:0_dpy] precedes
# [X-myhost:0_*] (same as [X-myhost:0]) precedes
# [X-myhost:*_dpy] precedes
# [X-myhost:*_*] (same as [X-myhost]) precedes
# [X-+:0_dpy] precedes
# [X-*:0_dpy] precedes
# [X-*:0_*] (same as [X-*:0]) precedes
# [X-*:*_*] (same as [X-*])
# These sections do NOT match this display:
# [X-hishost], [X-myhost:0_dec], [X-*:1], [X-:*]
# If a setting is not found in any matching section, the default is used.
#
# Every comment applies to the following section or key. Note that all
# comments will be lost if you change this file with the kcontrol frontend.
# The defaults refer to KDM's built-in values, not anything set in this file.
#
# Special characters need to be backslash-escaped (leading and trailing
# spaces (\s), tab (\t), linefeed (\n), carriage return (\r) and the
# backslash itself (\\)).
# In lists, fields are separated with commas without whitespace in between.
# Some command strings are subject to simplified sh-style word splitting:
# single quotes (') and double quotes (") have the usual meaning; the backslash
# quotes everything (not only special characters). Note that the backslashes
# need to be doubled because of the two levels of quoting.

[General]
# This option exists solely for the purpose of a clean automatic upgrade.
# Do not even think about changing it!
ConfigVersion=2.3
# List of permanent displays. Displays with a hostname are foreign. A display
# class may be specified separated by an underscore.
# Default is ":0"
StaticServers=:0
# List of on-demand displays. See StaticServers for syntax.
# Default is ""
ReserveServers=:1,:2,:3
# VTs to allocate to X-servers. A negative number means that the VT will be
# used only if it is free. If all VTs in this list are used up, the next free
# one greater than the last one in this list will be allocated.
# Default is ""
ServerVTs=-7
# TTYs (without /dev/) to monitor for activity while in console mode.
# Default is ""
ConsoleTTYs=tty1,tty2,tty3,tty4,tty5,tty6
# Where KDM should store its PID (do not store if empty).
# Default is ""
PidFile=/var/run/kdm.pid
# Whether KDM should lock the PID file to prevent having multiple KDM
# instances running at once. Do not change unless you are brave.
# Default is true
#LockPidFile=false
# Where to store authorization files.
# Default is "/var/run/xauth"
#AuthDir=/tmp
# Whether KDM should automatically re-read configuration files, if it
# finds them having changed.
# Default is true
#AutoRescan=false
# Additional environment variables KDM should pass on to all programs it runs.
# LD_LIBRARY_PATH and XCURSOR_THEME are good candidates;
# otherwise, it should not be necessary very often.
# Default is ""
#ExportList=LD_LIBRARY_PATH,ANOTHER_IMPORTANT_VAR
# A character device KDM should read entropy from.
# Empty means use the system's preferred entropy device.
# Default is ""
#RandomDevice=/dev/altrandom
# Where the command FiFos should be created; make it empty to disable
# them.
# Default is "/var/run/xdmctl"
#FifoDir=/tmp
# The group to which the global command FiFo should belong;
# can be either a name or a numerical ID.
# Default is 0
#FifoGroup=xdmctl
# The directory in which KDM should store persistent working data.
# Default is "/var/lib/kdm"
#DataDir=
# The directory in which KDM should store users' .dmrc files. This is only
# needed if the home directories are not readable before actually logging in
# (like with AFS).
# Default is ""
#DmrcDir=/nfs-shared/var/dmrcs

[Xdmcp]
# Whether KDM should listen to incoming XDMCP requests.
# Default is true
Enable=false
# The UDP port on which KDM should listen for XDMCP requests. Do not change.
# Default is 177
#Port=177
# File with the private keys of X-terminals. Required for XDM authentication.
# Default is ""
#KeyFile=/etc/kde3/kdm/kdmkeys
# XDMCP access control file in the usual XDM-Xaccess format.
# Default is "/etc/kde3/kdm/Xaccess"
#Xaccess=
# Number of seconds to wait for display to respond after the user has
# selected a host from the chooser.
# Default is 15
#ChoiceTimeout=10
# Strip domain name from remote display names if it is equal to the local
# domain.
# Default is true
#RemoveDomainname=false
# Use the numeric IP address of the incoming connection on multihomed hosts
# instead of the host name.
# Default is false
#SourceAddress=true
# The program which is invoked to dynamically generate replies to XDMCP
# DirectQuery or BroadcastQuery requests.
# If empty, no program is invoked and "Willing to manage" is sent.
# Default is ""
Willing=/etc/kde3/kdm/Xwilling

[Shutdown]
# The command (subject to word splitting) to run to halt the system.
# Default is "/sbin/halt"
#HaltCmd=
# The command (subject to word splitting) to run to reboot the system.
# Default is "/sbin/reboot"
#RebootCmd=
# Whether it is allowed to shut down the system via the global command FiFo.
# Default is false
#AllowFifo=true
# Whether it is allowed to abort active sessions when shutting down the
# system via the global command FiFo.
# Default is true
#AllowFifoNow=false
# The boot manager KDM should use for offering boot options in the
# shutdown dialog.
# "None" - no boot manager
# "Grub" - Grub boot manager
# "Lilo" - Lilo boot manager (Linux on i386 &amp; x86-64 only)
# Default is None
#BootManager=Grub

# Rough estimations about how many seconds KDM will spend at most on
# - opening a connection to the X-server (OpenTime) if the attempt
#   - times out: OpenTimeout
#   - is refused: OpenRepeat * OpenDelay
# - starting a local X-server (ServerTime):
#   ServerAttempts * (ServerTimeout + OpenDelay)
# - starting a display:
#   - local display: ServerTime + OpenTime
#   - foreign display: StartAttempts * OpenTime
#   - XDMCP display: OpenTime (repeated indefinitely by client)

# Core config for all displays
[X-*-Core]
# How long to wait before retrying to connect a display.
# Default is 15
#OpenDelay=15
# How long to wait before timing out a display connection attempt.
# Default is 120
#OpenTimeout=120
# How many connection attempts to make during a start attempt. Note that
# a timeout aborts the entire start attempt.
# Default is 5
#OpenRepeat=5
# Try at most that many times to start a display. If this fails, the display
# is disabled.
# Default is 4
#StartAttempts=4
# Ping remote display every that many minutes.
# Default is 5
#PingInterval=5
# Wait for a Pong that many minutes.
# Default is 5
#PingTimeout=5
# The name of this X-server's Xauth file.
# If empty, a random name in the AuthDir directory will be used.
# Default is ""
#AuthFile=
# Specify a file with X-resources for the greeter, chooser and background.
# The KDE frontend does not use this file, so you do not need it unless you
# use another background generator than krootimage.
# Default is ""
#Resources=
# The xrdb program to use to read the above specified recources.
# Subject to word splitting.
# Default is "/usr/X11R6/bin/xrdb"
#Xrdb=
# A program to run before the greeter is shown. Can be used to start an
# xconsole or an alternative background generator. Subject to word splitting.
# Default is ""
Setup=/etc/kde3/kdm/Xsetup
# A program to run before a user session starts. Subject to word splitting.
# Default is ""
Startup=/etc/kde3/kdm/Xstartup
# A program to run after a user session exits. Subject to word splitting.
# Default is ""
Reset=/etc/kde3/kdm/Xreset
# The program which is run as the user which logs in. It is supposed to
# interpret the session argument (see SessionsDirs) and start an appropriate
# session according to it. Subject to word splitting.
# Default is "/usr/X11R6/bin/xterm -ls -T"
Session=/etc/kde3/kdm/Xsession
# The program to run if Session fails.
# Default is "/usr/X11R6/bin/xterm"
#FailsafeClient=
# The PATH for the Session program.
# Default is "/usr/local/bin:/usr/bin:/bin:/usr/X11R6/bin:/usr/games"
#UserPath=
# The PATH for Setup, Startup and Reset, etc.
# Default is "/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/X11R6/bin"
#SystemPath=
# The default system shell.
# Default is "/bin/sh"
#SystemShell=/bin/bash
# Where to put the user's X-server authorization file if ~/.Xauthority
# cannot be created.
# Default is "/tmp"
#UserAuthDir=
# Whether to automatically restart sessions after X-server crashes.
# Note that enabling this makes circumventing screen lockers other than
# KDE's built-in one possible!
# Default is false
#AutoReLogin=true
# Allow root logins?
# Default is true
AllowRootLogin=false
# Allow to log in, when user has set an empty password?
# Default is true
AllowNullPasswd=false
# Who is allowed to shut down the system. This applies both to the
# greeter and to the command FiFo.
# "None" - no "Shutdown..." menu entry is shown at all
# "Root" - the root password must be entered to shut down
# "All" - everybody can shut down the machine
# Default is All
AllowShutdown=Root
# Who is allowed to abort active sessions when shutting down.
# "None" - no forced shutdown is allowed at all
# "Root" - the root password must be entered to shut down forcibly
# "All" - everybody can shut down the machine forcibly
# Default is All
#AllowSdForceNow=Root
# The default choice for the shutdown condition/timing.
# "Schedule" - shut down after all active sessions exit (possibly at once)
# "TryNow" - shut down, if no active sessions are open; otherwise, do nothing
# "ForceNow" - shut down unconditionally
# Default is Schedule
#DefaultSdMode=ForceNow
# How to offer shutdown scheduling options:
# "Never" - not at all
# "Optional" - as a button in the simple shutdown dialogs
# "Always" - instead of the simple shutdown dialogs
# Default is Never
#ScheduledSd=Optional
# The directories containing session type definitions in .desktop format.
# Default is "/usr/share/apps/kdm/sessions"
SessionsDirs=/etc/X11/sessions,/usr/share/xsessions
# The file (relative to $HOME) to redirect the session output to. This is
# a printf format string; one %s will be replaced with the display name.
# Default is ".xsession-errors"
ClientLogFile=.xsession-errors-%s
# Whether KDM's built-in utmp/wtmp/lastlog registration should be used.
# Default is true
#UseSessReg=false

# Greeter config for all displays
[X-*-Greeter]
# Widget style of the greeter. "" means the built-in default which currently
# is "Plastik".
# Default is ""
#GUIStyle=Windows
# Widget color scheme of the greeter. "" means the built-in default which
# currently is yellowish grey with some light blue and yellow elements.
# Default is ""
#ColorScheme=Pumpkin
# What should be shown in the greeter's logo are:
# "None" - nothing
# "Logo" - the image specified by LogoPixmap
# "Clock" - a neat analog clock
# Default is Clock
LogoArea=Logo
# The image to show when LogoArea=Logo.
# Default is ""
LogoPixmap=/usr/share/apps/kdm/pics/kdelogo.png
# The relative coordinates (X,Y in percent) of the center of the greeter.
# Default is "50,50"
#GreeterPos=30,40
# The screen the greeter should be displayed on in multi-headed and Xinerama
# setups. The numbering starts with 0. For Xinerama, it corresponds to the
# listing order in the active ServerLayout section of XF86Config; -1 means
# to use the upper-left screen, -2 means to use the upper-right screen.
# Default is 0
#GreeterScreen=-1
# The headline in the greeter. The following character pairs are replaced:
# - %d -> current display
# - %h -> host name, possibly with domain name
# - %n -> node name, most probably the host name without domain name
# - %s -> the operating system
# - %r -> the operating system's version
# - %m -> the machine (hardware) type
# - %% -> a single %
# Default is "Welcome to %s at %n"
#GreetString=K Desktop Environment (%n)
# The font for the greeter headline.
# Default is "charter,24,bold"
#GreetFont=charter,20,5,0,50,0
# The normal font used in the greeter.
# Default is "helvetica,12"
#StdFont=helvetica,10,5,0,50,0
# The font used for the "Login Failed" message.
# Default is "helvetica,12,bold"
#FailFont=helvetica,10,5,0,75,0
# Whether the fonts used in the greeter should be antialiased.
# Default is false
#AntiAliasing=true
# What to do with the Num Lock modifier for the time the greeter is running:
# "Off" - turn off
# "On" - turn on
# "Keep" - do not change the state
# Default is Keep
#NumLock=Off
# Language and locale to use in the greeter, encoded like $LC_LANG.
# Default is "en_US"
#Language=de_DE
# Enable autocompletion in the username line edit.
# Default is false
#UserCompletion=true
# Enable user list (names along with images) in the greeter.
# Default is true
#UserList=false
# User selection for UserCompletion and UserList:
# "NotHidden" - all users except those listed in HiddenUsers
# "Selected" - only the users listed in SelectedUsers
# Default is NotHidden
#ShowUsers=Selected
# For ShowUsers=Selected. @<group> means all users in that group.
# Default is ""
#SelectedUsers=root,johndoe
# For ShowUsers=NotHidden. @<group> means all users in that group.
# Default is ""
#HiddenUsers=root
# Special case of HiddenUsers: users with a non-zero UID less than this number
# will not be shown as well.
# Default is 0
MinShowUID=1000
# Complement to MinShowUID: users with a UID greater than this number will
# not be shown as well.
# Default is 65535
MaxShowUID=29999
# If false, the users are listed in the order they appear in /etc/passwd.
# If true, they are sorted alphabetically.
# Default is true
#SortUsers=false
# Specify, where the users' pictures should be taken from.
# "AdminOnly" - from <FaceDir>/$USER.face[.icon]
# "PreferAdmin" - prefer <FaceDir>, fallback on $HOME
# "PreferUser" - ... and the other way round
# "UserOnly" - from the user's $HOME/.face[.icon]
# Default is AdminOnly
#FaceSource=PreferUser
# The directory containing the user images if FaceSource is not UserOnly.
# Default is "/usr/share/apps/kdm/faces"
#FaceDir=/usr/share/faces
# Specify, if/which user should be preselected for log in.
# "None" - do not preselect any user
# "Previous" - the user which successfully logged in last time
# "Default" - the user specified in the DefaultUser option
# Default is None
#PreselectUser=Previous
# If this is true, the password input line is focused automatically if
# a user is preselected.
# Default is false
#FocusPasswd=true
# The password input fields cloak the typed in text. Specify, how to do it:
# "OneStar" - <literal>*</literal> is shown for every typed letter
# "ThreeStars" - <literal>***</literal> is shown for every typed letter
# "NoEcho" - nothing is shown at all, the cursor does not move
# Default is OneStar
#EchoMode=NoEcho
# If true, krootimage will be automatically started by KDM; otherwise, the
# Setup script should be used to setup the background.
# Default is true
#UseBackground=false
# The configuration file to be used by krootimage.
# Default is "/etc/kde3/kdm/backgroundrc"
#BackgroundCfg=
# Hold the X-server grabbed the whole time the greeter is visible. This
# may be more secure, but it will disable any background and other
# X-clients started from the Setup script.
# Default is false
#GrabServer=true
# How many seconds to wait for grab to succeed.
# Default is 3
#GrabTimeout=3
# Warn, if display has no X-authorization (local auth cannot be created,
# XDMCP display wants no auth, or display is foreign from StaticServers).
# Default is true
#AuthComplain=false
# Random seed for forging saved session types, etc. of unknown users.
# This value should be random but constant across the login domain.
# Default is 0
ForgingSeed=1112755402
# Specify conversation plugins for the login dialog. Each plugin can be
# specified as a base name (which expands to $kde_modulesdir/kgreet_$base)
# or as a full pathname.
# Default is "classic"
#PluginsLogin=sign
# Same as PluginsLogin, but for the shutdown dialog.
# Default is "classic"
#PluginsShutdown=modern
# A list of options of the form Key=Value. The conversation plugins can query
# these settings; it is up to them what possible keys are.
# Default is ""
#PluginOptions=SomeKey=randomvalue,Foo=bar
# Show the "Console Login" action in the greeter (if ServerTTY/ConsoleTTYs
# is configured).
# Default is true
#AllowConsole=false
# A program to run while the greeter is visible. It is supposed to preload
# as much as possible of the session that is going to be started (most
# probably).
# Default is ""
Preloader=/usr/bin/preloadkde
# Whether the greeter should be themed.
# Default is false
UseTheme=true
# The theme to use for the greeter. Can point to either a directory or an XML
# file.
# Default is ""
Theme=/usr/share/apps/kdm/themes/kubuntu

# Core config for local displays
[X-:*-Core]
# How often to try to run the X-server. Running includes executing it and
# waiting for it to come up.
# Default is 1
#ServerAttempts=1
# How long to wait for a local X-server to come up.
# Default is 15
#ServerTimeout=15
# The command line to start the X-server, without display number and VT spec.
# This string is subject to word splitting.
# Default is "/usr/X11R6/bin/X"
ServerCmd=/usr/X11R6/bin/X
# Additional arguments for the X-servers for local sessions.
# This string is subject to word splitting.
# Default is ""
ServerArgsLocal=-nolisten tcp
# Additional arguments for the X-servers for remote sessions.
# This string is subject to word splitting.
# Default is ""
#ServerArgsRemote=
# Restart instead of resetting the local X-server after session exit.
# Use it if the server leaks memory etc.
# Default is false
#TerminateServer=true
# The signal needed to reset the local X-server.
# Default is 1 (SIGHUP)
#ResetSignal=1
# The signal needed to terminate the local X-server.
# Default is 15 (SIGTERM)
#TermSignal=15
# Create X-authorizations for local displays.
# Default is true
#Authorize=false
# Which X-authorization mechanisms should be used.
# Default is "MIT-MAGIC-COOKIE-1"
#AuthNames=
# Need to reset the X-server to make it read initial Xauth file.
# Default is false
#ResetForAuth=true
# See above
AllowNullPasswd=true
# See above
AllowShutdown=All
# Enable password-less logins on this display. USE WITH EXTREME CARE!
# Default is false
#NoPassEnable=true
# The users that do not need to provide a password to log in. NEVER list root!
# "*" means all non-root users. @<group> means all users in that group.
# Default is ""
#NoPassUsers=fred,ethel

# Greeter config for local displays
[X-:*-Greeter]
# See above
PreselectUser=Previous
# See above
FocusPasswd=true
# Specify whether the greeter of local displays should start up in host chooser
# (remote) or login (local) mode and whether it is allowed to switch to the
# other mode.
# "LocalOnly" - only local login possible
# "DefaultLocal" - start up in local mode, but allow switching to remote mode
# "DefaultRemote" - ... and the other way round
# "RemoteOnly" - only choice of remote host possible
# Default is LocalOnly
LoginMode=DefaultLocal
# A list of hosts to be automatically added to the remote login menu. The
# special name "*" means broadcast.
# Default is "*"
#ChooserHosts=*,ugly,sky,dino,kiste.local,login.crap.com
# Show the "Restart X Server"/"Close Connection" action in the greeter.
# Default is true
AllowClose=false

# Core config for 1st local display
[X-:0-Core]
# The VT the X-server should run on. Better use ServerVTs.
# Default is 0
#ServerVT=7
# Enable automatic login. USE WITH EXTREME CARE!
# Default is false
#AutoLoginEnable=true
# The user to log in automatically. NEVER specify root!
# Default is ""
#AutoLoginUser=fred
# The password for the user to log in automatically. This is NOT required
# unless the user is logged into a NIS or Kerberos domain. If you use this
# option, you should "chmod 600 kdmrc" for obvious reasons.
# Default is ""
#AutoLoginPass=secret!
# See above
ClientLogFile=.xsession-errors

# Greeter config for 1st local display
[X-:0-Greeter]
# See above
#PreselectUser=Default
# The user to preselect if PreselectUser=Default.
# Default is ""
#DefaultUser=johndoe

But, I don't understand the whole file !


Thanks again for your help !

---

### Post by skyboy on 2005-08-09
nothing wrong jumps to my eyes here !!
check the .xsession-errors file in your home directory, you might get more clues

---

### Post by joebrandt on 2005-09-02
Did you load Kubuntu or build KDE on top of Gnome?

---

