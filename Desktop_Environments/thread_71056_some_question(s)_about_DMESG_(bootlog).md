---
title: "some question(s) about DMESG (bootlog)"
date: 2005-10-02
forum: Desktop Environments
---

### Post by flying_nomad on 2005-10-02
I have some questions about some message's i don't understand inside my boot log, viewed by : sudo demsg

I post only the strange parts of it, would be very appriated i some one can give me some insight (want to learn more about how and why :cool: )

thx in advance........

```

patrick@ubuntu:/etc$ sudo dmesg
.
Checking for popad bug... OK.
ACPI: Looking for DSDT in initrd... not found!
ENABLING IO-APIC IRQs
..TIMER: vector=0x31 pin1=2 pin2=-1
checking if image is initramfs...it isn't (bad gzip magic numbers); looks like an initrd
Freeing initrd memory: 4300k freed

```

What exactly is happening here, seems something is going wrong and a workaround is happening.......

```

IP: routing cache hash table of 4096 buckets, 32Kbytes
TCP: Hash tables configured (established 32768 bind 65536)
NET: Registered protocol family 8
NET: Registered protocol family 20
Restarting tasks...<6> Strange, kswapd0 not stopped
 Strange, kseriod not stopped
 done
```

what's about kswapd0 and kseriod ?

```

agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
eth0: no IPv6 routers present
ibm_acpi: ec object not found
NTFS-fs error (device hda1): ntfs_ucstonls(): Unicode name contains characters that cannot be converted to character set cp437.
NTFS-fs error (device hdc1): ntfs_ucstonls(): Unicode name contains characters that cannot be converted to character set cp437.

```

those messages ' NTFS errors'  go on for a while, what's the reason for that ?


---


BC i don't know if it is handy to have the whole boot log by hand i post it as a reply on this post so it may be usefull for any of you who want to put some time into explaining this to me..........


grt, 

Patrick (netherlands)

---

### Post by flying_nomad on 2005-10-02
the whole log posted here


```

patrick@ubuntu:/etc$ sudo dmesg
.
Checking for popad bug... OK.
ACPI: Looking for DSDT in initrd... not found!
ENABLING IO-APIC IRQs
..TIMER: vector=0x31 pin1=2 pin2=-1
checking if image is initramfs...it isn't (bad gzip magic numbers); looks like an initrd
Freeing initrd memory: 4300k freed
NET: Registered protocol family 16
EISA bus registered
PCI: PCI BIOS revision 2.10 entry at 0xfbb60, last bus=2
PCI: Using configuration type 1
mtrr: v2.0 (20020519)
ACPI: Subsystem revision 20050211
ACPI: Interpreter enabled
ACPI: Using IOAPIC for interrupt routing
ACPI: PCI Root Bridge [PCI0] (00:00)
PCI: Probing PCI hardware (bus 00)
PCI: Ignoring BAR0-3 of IDE controller 0000:00:1f.1
PCI: Transparent bridge - 0000:00:1e.0
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 *5 7 9 10 11 12 14 15)
ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 *9 10 11 12 14 15)
ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 7 9 10 11 12 14 15)
ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 *9 10 11 12 14 15)
ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 7 9 10 *11 12 14 15)
ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 7 9 10 *11 12 14 15)
Linux Plug and Play Support v0.97 (c) Adam Belay
pnp: PnP ACPI init
pnp: PnP ACPI: found 15 devices
PnPBIOS: Disabled by ACPI PNP
PCI: Using ACPI for IRQ routing
** PCI interrupts are no longer routed automatically.  If this
** causes a device to stop working, it is probably because the
** driver failed to call pci_enable_device().  As a temporary
** workaround, the "pci=routeirq" argument restores the old
** behavior.  If this argument makes the device work again,
** please email the output of "lspci" to bjorn.helgaas@hp.com
** so I can fix the driver.
pnp: 00:0d: ioport range 0x400-0x4bf could not be reserved
audit: initializing netlink socket (disabled)
audit(1128248319.017:0): initialized
VFS: Disk quotas dquot_6.5.1
Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
devfs: boot_options: 0x0
Initializing Cryptographic API
isapnp: Scanning for PnP cards...
isapnp: No Plug & Play device found
serio: i8042 AUX port at 0x60,0x64 irq 12
serio: i8042 KBD port at 0x60,0x64 irq 1
Serial: 8250/16550 driver $Revision: 1.90 $ 54 ports, IRQ sharing enabled
ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
io scheduler noop registered
io scheduler anticipatory registered
io scheduler deadline registered
io scheduler cfq registered
RAMDISK driver initialized: 16 RAM disks of 8192K size 1024 blocksize
input: AT Translated Set 2 keyboard on isa0060/serio0
EISA: Probing bus 0 at eisa0
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
PCI0 HUB0 UAR1 UAR2 USB0 USB1 USB2 USB3 USBE
ACPI: (supports S0 S3 S4 S5)
RAMDISK: cramfs filesystem found at block 0
RAMDISK: Loading 4300KiB [1 disk] into ram disk... done.
VFS: Mounted root (cramfs filesystem) readonly.
Freeing unused kernel memory: 224k freed
vesafb: framebuffer at 0xf0000000, mapped to 0xe0880000, using 3072k, total 65536k
vesafb: mode is 1024x768x16, linelength=2048, pages=1
vesafb: protected mode interface info at c000:e4e0
vesafb: scrolling: redraw
vesafb: Truecolor: size=0:5:6:5, shift=0:11:5:0
fb0: VESA VGA frame buffer device
Console: switching to colour frame buffer device 128x48
ACPI: Fan [FAN] (on)
ACPI: Thermal Zone [THRM] (22 C)
NET: Registered protocol family 1
Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
ICH5: IDE controller at PCI slot 0000:00:1f.1
ACPI: PCI interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 18
ICH5: chipset revision 2
ICH5: not 100% native mode: will probe irqs later
    ide0: BM-DMA at 0xf000-0xf007, BIOS settings: hda:pio, hdb:pio
    ide1: BM-DMA at 0xf008-0xf00f, BIOS settings: hdc:pio, hdd:pio
Probing IDE interface ide0...
hda: WDC WD400BB-00DEA0, ATA DISK drive
elevator: using anticipatory as default io scheduler
ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
hda: max request size: 128KiB
hda: 78165360 sectors (40020 MB) w/2048KiB Cache, CHS=65535/16/63, UDMA(33)
hda: cache flushes not supported
 /dev/ide/host0/bus0/target0/lun0: p1 p2 p3 < p5 >
Probing IDE interface ide1...
hdc: WDC WD400BB-00DEA0, ATA DISK drive
hdd: LITE-ON DVD SOHD-167T, ATAPI CD/DVD-ROM drive
ide1 at 0x170-0x177,0x376 on irq 15
hdc: max request size: 128KiB
hdc: 78165360 sectors (40020 MB) w/2048KiB Cache, CHS=65535/16/63, UDMA(33)
hdc: cache flushes not supported
 /dev/ide/host0/bus1/target0/lun0: p1
Probing IDE interface ide2...
Probing IDE interface ide3...
Probing IDE interface ide4...
Probing IDE interface ide5...
Stopping tasks: ==|
Freeing memory... done (454 pages freed)
Restarting tasks... done
VFS: Can't find ext3 filesystem on dev hda2.
VFS: Can't find an ext2 filesystem on dev hda2.
ReiserFS: hda2: found reiserfs format "3.6" with standard journal
ReiserFS: hda2: using ordered data mode
ReiserFS: hda2: journal params: device hda2, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
ReiserFS: hda2: checking transaction log (hda2)
ReiserFS: hda2: Using r5 hash to sort names
Adding 979924k swap on /dev/hda5.  Priority:-1 extents:1
hdd: ATAPI 48X DVD-ROM drive, 512kB Cache
Uniform CD-ROM driver Revision: 3.20
parport: PnPBIOS parport detected.
parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
lp0: using parport0 (interrupt-driven).
mice: PS/2 mouse device common for all mice
input: ImExPS/2 Logitech Explorer Mouse on isa0060/serio1
Linux agpgart interface v0.100 (c) Dave Jones
nvidia: module license 'NVIDIA' taints kernel.
ACPI: PCI interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
NVRM: loading NVIDIA Linux x86 NVIDIA Kernel Module  1.0-7174  Tue Mar 22 06:44:39 PST 2005
ts: Compaq touchscreen protocol output
Capability LSM initialized
device-mapper: 4.3.0-ioctl (2004-09-30) initialised: dm-devel@redhat.com
md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
cdrom: open failed.
NTFS driver 2.1.22 [Flags: R/O MODULE].
NTFS volume version 3.1.
NTFS volume version 3.1.
Real Time Clock Driver v1.12
input: PC Speaker
inserting floppy driver for 2.6.10-5-386
FDC 0 is a post-1991 82077
agpgart: Detected an Intel 865 Chipset.
agpgart: Maximum main memory to use for agp memory: 439M
agpgart: AGP aperture is 128M @ 0xe8000000
cpci_hotplug: CompactPCI Hot Plug Core version: 0.2
pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Evaluate _OSC Set fails. Status = 0x0005
pciehp: add_host_bridge: status 5
pciehp: Fails to gain control of native hot-plug
shpchp: shpc_init : shpc_cap_offset == 0
shpchp: shpc_init : shpc_cap_offset == 0
shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
usbcore: registered new driver usbfs
usbcore: registered new driver hub
USB Universal Host Controller Interface driver v2.2
ACPI: PCI interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 16
uhci_hcd 0000:00:1d.0: Intel Corp. 82801EB/ER (ICH5/ICH5R) USB UHCI #1
PCI: Setting latency timer of device 0000:00:1d.0 to 64
uhci_hcd 0000:00:1d.0: irq 16, io base 0xe300
uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
hub 1-0:1.0: USB hub found
hub 1-0:1.0: 2 ports detected
ACPI: PCI interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 19
uhci_hcd 0000:00:1d.1: Intel Corp. 82801EB/ER (ICH5/ICH5R) USB UHCI #2
PCI: Setting latency timer of device 0000:00:1d.1 to 64
uhci_hcd 0000:00:1d.1: irq 19, io base 0xe000
uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
hub 2-0:1.0: USB hub found
hub 2-0:1.0: 2 ports detected
ACPI: PCI interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
uhci_hcd 0000:00:1d.2: Intel Corp. 82801EB/ER (ICH5/ICH5R) USB UHCI #3
PCI: Setting latency timer of device 0000:00:1d.2 to 64
uhci_hcd 0000:00:1d.2: irq 18, io base 0xe100
uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
hub 3-0:1.0: USB hub found
hub 3-0:1.0: 2 ports detected
ACPI: PCI interrupt 0000:00:1d.3[A] -> GSI 16 (level, low) -> IRQ 16
uhci_hcd 0000:00:1d.3: Intel Corp. 82801EB/ER (ICH5/ICH5R) USB UHCI #4
PCI: Setting latency timer of device 0000:00:1d.3 to 64
uhci_hcd 0000:00:1d.3: irq 16, io base 0xe200
uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
hub 4-0:1.0: USB hub found
hub 4-0:1.0: 2 ports detected
ACPI: PCI interrupt 0000:00:1d.7[D] -> GSI 23 (level, low) -> IRQ 23
ehci_hcd 0000:00:1d.7: Intel Corp. 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller
PCI: Setting latency timer of device 0000:00:1d.7 to 64
ehci_hcd 0000:00:1d.7: irq 23, pci mem 0xfc000000
ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
PCI: cache line size of 128 is not supported by device 0000:00:1d.7
ehci_hcd 0000:00:1d.7: USB 2.0 initialized, EHCI 1.00, driver 26 Oct 2004
hub 5-0:1.0: USB hub found
hub 5-0:1.0: 8 ports detected
hw_random: RNG not detected
Evaluate _OSC Set fails. Status = 0x0005
pciehp: add_host_bridge: status 5
pciehp: Fails to gain control of native hot-plug
ACPI: PCI interrupt 0000:00:1f.5[B] -> GSI 17 (level, low) -> IRQ 17
PCI: Setting latency timer of device 0000:00:1f.5 to 64
intel8x0_measure_ac97_clock: measured 49967 usecs
intel8x0: clocking to 48000
8139cp: 10/100 PCI Ethernet driver v1.2 (Mar 22, 2004)
8139cp: pci dev 0000:02:05.0 (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
8139cp: Try the "8139too" driver instead.
8139too Fast Ethernet driver 0.9.27
ACPI: PCI interrupt 0000:02:05.0[A] -> GSI 22 (level, low) -> IRQ 22
eth0: RealTek RTL8139 at 0xd000, 00:04:61:73:e4:75, IRQ 22
eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
NET: Registered protocol family 17
NET: Registered protocol family 10
Disabled Privacy Extensions on device c02f0500(lo)
IPv6 over IPv4 tunneling driver
ACPI: Power Button (FF) [PWRF]
ibm_acpi: ec object not found
apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
apm: overridden by ACPI.
agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
eth0: no IPv6 routers present
ibm_acpi: ec object not found
NTFS-fs error (device hda1): ntfs_ucstonls(): Unicode name contains characters that cannot be converted to character set cp437.
NTFS-fs error (device hdc1): ntfs_ucstonls(): Unicode name contains characters that cannot be converted to character set cp437.
NTFS-fs error (device hdc1): ntfs_ucstonls(): Unicode name contains characters that cannot be converted to character set cp437.
NTFS-fs error (device hdc1): ntfs_ucstonls(): Unicode name contains characters that cannot be converted to character set cp437.
NTFS-fs error (device hdc1): ntfs_ucstonls(): Unicode name contains characters that cannot be converted to character set cp437.
NTFS-fs error (device hdc1): ntfs_ucstonls(): Unicode name contains characters that cannot be converted to character set cp437.
NTFS-fs error (device hdc1): ntfs_ucstonls(): Unicode name contains characters that cannot be converted to character set cp437.
NTFS-fs error (device hdc1): ntfs_ucstonls(): Unicode name contains characters that cannot be converted to character set cp437.
NTFS-fs error (device hdc1): ntfs_ucstonls(): Unicode name contains characters that cannot be converted to character set cp437.
NTFS-fs error (device hdc1): ntfs_ucstonls(): Unicode name contains characters that cannot be converted to character set cp437.
NTFS-fs error (device hdc1): ntfs_ucstonls(): Unicode name contains characters that cannot be converted to character set cp437.
NTFS-fs error (device hdc1): ntfs_ucstonls(): Unicode name contains characters that cannot be converted to character set cp437.
NTFS-fs error (device hdc1): ntfs_ucstonls(): Unicode name contains characters that cannot be converted to character set cp437.
NTFS-fs error (device hdc1): ntfs_ucstonls(): Unicode name contains characters that cannot be converted to character set cp437.
NTFS-fs error (device hdc1): ntfs_ucstonls(): Unicode name contains characters that cannot be converted to character set cp437.
NTFS-fs error (device hdc1): ntfs_ucstonls(): Unicode name contains characters that cannot be converted to character set cp437.
NTFS-fs error (device hdc1): ntfs_ucstonls(): Unicode name contains characters that cannot be converted to character set cp437.
NTFS-fs error (device hdc1): ntfs_ucstonls(): Unicode name contains characters that cannot be converted to character set cp437.
NTFS-fs error (device hdc1): ntfs_ucstonls(): Unicode name contains characters that cannot be converted to character set cp437.
NTFS-fs error (device hdc1): ntfs_ucstonls(): Unicode name contains characters that cannot be converted to character set cp437.
NTFS-fs error (device hdc1): ntfs_ucstonls(): Unicode name contains characters that cannot be converted to character set cp437.
NTFS-fs error (device hdc1): ntfs_ucstonls(): Unicode name contains characters that cannot be converted to character set cp437.
NTFS-fs error (device hdc1): ntfs_ucstonls(): Unicode name contains characters that cannot be converted to character set cp437.
NTFS-fs error (device hdc1): ntfs_ucstonls(): Unicode name contains characters that cannot be converted to character set cp437.
NTFS-fs error (device hdc1): ntfs_ucstonls(): Unicode name contains characters that cannot be converted to character set cp437.
NTFS-fs error (device hdc1): ntfs_ucstonls(): Unicode name contains characters that cannot be converted to character set cp437.
NTFS-fs error (device hdc1): ntfs_ucstonls(): Unicode name contains characters that cannot be converted to character set cp437.
NTFS-fs error (device hdc1): ntfs_ucstonls(): Unicode name contains characters that cannot be converted to character set cp437.
NTFS-fs error (device hdc1): ntfs_ucstonls(): Unicode name contains characters that cannot be converted to character set cp437.
NTFS-fs error (device hdc1): ntfs_ucstonls(): Unicode name contains characters that cannot be converted to character set cp437.
NTFS-fs error (device hdc1): ntfs_ucstonls(): Unicode name contains characters that cannot be converted to character set cp437.
NTFS-fs error (device hdc1): ntfs_ucstonls(): Unicode name contains characters that cannot be converted to character set cp437.
patrick@ubuntu:/etc$


```

---

### Post by skoal on 2005-10-02
I'll take a stab at your NTFS errors.  What does your /etc/fstab mount points for those 2 partitions (hda1, hdc1) look like?  Post that back here...

I would think just these options: ro,user,nls=utf8,uid=1000,gid=1000
...would be sufficient.

Are you using 'iocharset=', 'nls=', or 'utf8=true' options in fstab? NTFS stores all it's filenames in unicode.  If you're using something other than utf8, I think that's where the NLS translation is bombing, apparenlty on 1 spot on hda1 and several on hdc1.  I dunno.  I don't use NTFS or any NLS translations for that matter.

\\//_

---

### Post by Zwack on 2005-10-02
First, initramfs... initramfs is a cpio archive.  What this is telling you is that your initrd image is not a compressed archive so it can't be an initramfs image... 

[http://packages.debian.org/unstable/utils/initramfs-tools]("http://packages.debian.org/unstable/utils/initramfs-tools")

Nothing to see here, move along...

kswapd0 and kseriod are kernel processes that, I think, provide swap management and serial I/O (?).  Something is trying to restart them (for some reason) but can't.  It wouldn't make sense that certain kernel processes should be restarted which may explain these warnings.  I get the same thing and it doesn't worry me...

NTFS errors... You're trying to mount an NTFS filesystem.  Your system is set up to use Code Page 437... NTFS is using Unicode... it's probably complaining that some of the file/directory names are using characters that it can't convert...

None of this looks serious.

I hope that this helps,

Z.

---

### Post by flying_nomad on 2005-10-02
Thankyou for this insight information,

unfortunately just a couple of minutes after posting this i used 'synaptic' because there was a message at the right top of the screen telling me that there were upgrade's available......

:(  anyway, it ended me using windows again, because it damaged my Ubuntu hoary and i can't get X working anymore,

if interested see my topic *(it's so ugly if you don't know enough to resolve this issue's by yourself, i like Linux but i feel a real beginner like i was once long way back in time !!!)*
[http://ubuntuforums.org/showthread.php?t=71226](http://ubuntuforums.org/showthread.php?t=71226)

---

