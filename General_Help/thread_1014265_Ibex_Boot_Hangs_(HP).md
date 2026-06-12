---
title: "Ibex Boot Hangs (HP)"
date: 2008-12-17
forum: General Help
---

### Post by FlyingIsFun1217 on 2008-12-17
Hey!

I've got an HP laptop, and every time at boot, I get a system that hangs. When the progress bar comes up, it sticks during it's back-and-forth phase.

Pressing and holding any key makes it move (and at a certain point, it will go by itself), and pressing the power button does the same thing as pressing and holding keys (except I don't have to hold it).

Is this a common problem? I've NEVER had this issue with Ubuntu before!

Thanks!
FlyingIsFun1217

---

### Post by FlyingIsFun1217 on 2008-12-18
Does anybody even have some ideas to figure out whats going on? It's just a *little* annoying...

FlyingIsFun1217

---

### Post by molo on 2009-01-01
I have this exact same problem, also on an HP laptop.  If someone has an idea about how to solve it, I would also appreciate the help.

My laptop is an HP dv6812nr.  Specs are:

AMD Turion TL-60 processor
3 Gb RAM
250 Gb HDD (140 or so used for Ubuntu)
NVIDIA GeForce Go 7150M

---

### Post by dexter on 2009-01-01
Try booting without the splash screen. This will give you some more info at what point it goes wrong. 

When grub comes up, select your kernel line and press 'e' (edit), remove the "splash" and "quiet" words from the line, press enter to confirm and press 'b' to boot. You will now get a textual startup with info about what is going on in the startup process.

---

### Post by molo on 2009-01-04
Hi,

Thanks for the suggestion.  I tried looking at the boot messages, but I'm still not sure what's causing it to hang.

It first stops at a place related to a USB hub.  This is the first line in the message log output pasted below.  There was nothing plugged into the laptop at this point (no external USB hubs), so I think this is the internal laptop USB hub.

The interesting part is that there is no difference in the timestamp for the message afterwards (they are all 12:15:02).  I was sure that I paused for at least a second before pressing the keyboard to make the boot continue.

I'm wondering if this is maybe related to IRQ settings for the keyboard or this USB hub?  Is there a utility that will allow me to change IRQs in Ubuntu, or do I have to do this in the BIOS (not sure if the laptop BIOS even has this capability)?

Message log attached below, first line is where the boot hangs for the first time.

If I press a key on the laptop keyboard, it will continue booting until I release the key (then it stops again).  I have to continue holding the key until the "loading bar" on the splash screen starts loading (rather than going back and forth), which I think indicates a second phase in the boot process.  I'm not sure on which line this happens in the log below, but I'll do another boot and post the results.

Quite an odd problem, if anyone has any suggestions I'd love to hear them.

Thanks,
molo

```
Jan  4 12:15:02 molo-laptop kernel: [    2.770360] hub 3-0:1.0: 7 ports detected
Jan  4 12:15:02 molo-laptop kernel: [   19.349560] ACPI: PCI Interrupt Link [Z018] enabled at IRQ 18
Jan  4 12:15:02 molo-laptop kernel: [   19.349630] ohci_hcd 0000:00:04.0: PCI INT A -> Link[Z018] -> GSI 18 (level, low) -> IRQ 18
Jan  4 12:15:02 molo-laptop kernel: [   19.349722] ohci_hcd 0000:00:04.0: OHCI Host Controller
Jan  4 12:15:02 molo-laptop kernel: [   19.349819] ohci_hcd 0000:00:04.0: new USB bus registered, assigned bus number 4
Jan  4 12:15:02 molo-laptop kernel: [   19.349905] ohci_hcd 0000:00:04.0: irq 18, io mem 0xf6487000
Jan  4 12:15:02 molo-laptop kernel: [   19.452064] Clocksource tsc unstable (delta = 4398045831259 ns)
Jan  4 12:15:02 molo-laptop kernel: [   19.454174] usb usb4: configuration #1 chosen from 1 choice
Jan  4 12:15:02 molo-laptop kernel: [   19.454268] hub 4-0:1.0: USB hub found
Jan  4 12:15:02 molo-laptop kernel: [   19.454336] hub 4-0:1.0: 2 ports detected
Jan  4 12:15:02 molo-laptop kernel: [   21.361624] ACPI: PCI Interrupt Link [LSI0] enabled at IRQ 23
Jan  4 12:15:02 molo-laptop kernel: [   21.361697] pata_acpi 0000:00:09.0: PCI INT A -> Link[LSI0] -> GSI 23 (level, low) -> IRQ 23
Jan  4 12:15:02 molo-laptop kernel: [   21.361796] pata_acpi 0000:00:09.0: PCI INT A disabled
Jan  4 12:15:02 molo-laptop kernel: [   21.361878] ahci 0000:00:09.0: PCI INT A -> Link[LSI0] -> GSI 23 (level, low) -> IRQ 23
Jan  4 12:15:02 molo-laptop kernel: [   21.362024] ahci 0000:00:09.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl IDE mode
Jan  4 12:15:02 molo-laptop kernel: [   21.362100] ahci 0000:00:09.0: flags: 64bit sntf led clo pmp pio slum part 
Jan  4 12:15:02 molo-laptop kernel: [   21.362526] scsi0 : ahci
Jan  4 12:15:02 molo-laptop kernel: [   21.362716] scsi1 : ahci
Jan  4 12:15:02 molo-laptop kernel: [   21.363219] scsi2 : ahci
Jan  4 12:15:02 molo-laptop kernel: [   21.363355] scsi3 : ahci
Jan  4 12:15:02 molo-laptop kernel: [   21.363514] ata1: SATA max UDMA/133 abar m8192@0xf6484000 port 0xf6484100 irq 221
Jan  4 12:15:02 molo-laptop kernel: [   21.363589] ata2: SATA max UDMA/133 abar m8192@0xf6484000 port 0xf6484180 irq 221
Jan  4 12:15:02 molo-laptop kernel: [   21.363663] ata3: SATA max UDMA/133 abar m8192@0xf6484000 port 0xf6484200 irq 221
Jan  4 12:15:02 molo-laptop kernel: [   21.363737] ata4: SATA max UDMA/133 abar m8192@0xf6484000 port 0xf6484280 irq 221
Jan  4 12:15:02 molo-laptop kernel: [   36.529128] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Jan  4 12:15:02 molo-laptop kernel: [   36.529518] ata1.00: ATA-8: WDC WD2500BEVS-60UST0, 01.01A01, max UDMA/100
Jan  4 12:15:02 molo-laptop kernel: [   36.529584] ata1.00: 488397168 sectors, multi 16: LBA48 
Jan  4 12:15:02 molo-laptop kernel: [   36.530102] ata1.00: configured for UDMA/100
Jan  4 12:15:02 molo-laptop kernel: [   37.895812] ata2: SATA link down (SStatus 0 SControl 300)
Jan  4 12:15:02 molo-laptop kernel: [   40.374299] ata3: SATA link down (SStatus 0 SControl 300)
Jan  4 12:15:02 molo-laptop kernel: [   41.272666] ata4: SATA link down (SStatus 0 SControl 300)
Jan  4 12:15:02 molo-laptop kernel: [   41.272794] scsi 0:0:0:0: Direct-Access     ATA      WDC WD2500BEVS-6 01.0 PQ: 0 ANSI: 5
Jan  4 12:15:02 molo-laptop kernel: [   41.272976] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.61.
Jan  4 12:15:02 molo-laptop kernel: [   41.273483] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 20
Jan  4 12:15:02 molo-laptop kernel: [   41.273559] forcedeth 0000:00:0a.0: PCI INT A -> Link[LMAC] -> GSI 20 (level, low) -> IRQ 20
Jan  4 12:15:02 molo-laptop kernel: [   45.907994] forcedeth 0000:00:0a.0: ifname eth0, PHY OUI 0x732 @ 1, addr 00:1e:68:4b:c2:a9
Jan  4 12:15:02 molo-laptop kernel: [   45.908084] forcedeth 0000:00:0a.0: highdma pwrctl mgmt timirq lnktim msi desc-v3
Jan  4 12:15:02 molo-laptop kernel: [   45.910850] ohci1394 0000:02:05.0: enabling device (0100 -> 0102)
Jan  4 12:15:02 molo-laptop kernel: [   45.911351] ACPI: PCI Interrupt Link [LNK1] enabled at IRQ 5
Jan  4 12:15:02 molo-laptop kernel: [   45.911425] ohci1394 0000:02:05.0: PCI INT A -> Link[LNK1] -> GSI 5 (level, low) -> IRQ 5
Jan  4 12:15:02 molo-laptop kernel: [   45.963230] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[5]  MMIO=[f6100000-f61007ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
Jan  4 12:15:02 molo-laptop kernel: [   45.983904] scsi4 : pata_amd
Jan  4 12:15:02 molo-laptop kernel: [   45.984051] scsi5 : pata_amd
Jan  4 12:15:02 molo-laptop kernel: [   45.984530] ata5: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x30c0 irq 14
Jan  4 12:15:02 molo-laptop kernel: [   45.984596] ata6: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0x30c8 irq 15
Jan  4 12:15:02 molo-laptop kernel: [   46.002928] scsi 0:0:0:0: Attached scsi generic sg0 type 0
Jan  4 12:15:02 molo-laptop kernel: [   46.015813] Driver 'sd' needs updating - please use bus_type methods
Jan  4 12:15:02 molo-laptop kernel: [   46.016023] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
Jan  4 12:15:02 molo-laptop kernel: [   46.016110] sd 0:0:0:0: [sda] Write Protect is off
Jan  4 12:15:02 molo-laptop kernel: [   46.016212] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jan  4 12:15:02 molo-laptop kernel: [   46.016363] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
Jan  4 12:15:02 molo-laptop kernel: [   46.016446] sd 0:0:0:0: [sda] Write Protect is off
Jan  4 12:15:02 molo-laptop kernel: [   46.016547] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jan  4 12:15:02 molo-laptop kernel: [   46.016624]  sda: sda1 sda2 sda3 < sda5<6>ata5.00: ATAPI: HL-DT-ST DVDRAM GSA-T20N, WC05, max MWDMA2
Jan  4 12:15:02 molo-laptop kernel: [   46.327984]  sda6 >
Jan  4 12:15:02 molo-laptop kernel: [   46.328356] sd 0:0:0:0: [sda] Attached SCSI disk
Jan  4 12:15:02 molo-laptop kernel: [   50.313755] ata5.00: configured for MWDMA2
Jan  4 12:15:02 molo-laptop kernel: [   50.317431] scsi 4:0:0:0: CD-ROM            HL-DT-ST DVDRAM GSA-T20N  WC05 PQ: 0 ANSI: 5
Jan  4 12:15:02 molo-laptop kernel: [   50.317690] scsi 4:0:0:0: Attached scsi generic sg1 type 5
Jan  4 12:15:02 molo-laptop kernel: [   50.341054] Driver 'sr' needs updating - please use bus_type methods
Jan  4 12:15:02 molo-laptop kernel: [   50.352791] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
Jan  4 12:15:02 molo-laptop kernel: [   50.352871] Uniform CD-ROM driver Revision: 3.20
Jan  4 12:15:02 molo-laptop kernel: [   50.813195] PM: Starting manual resume from disk
Jan  4 12:15:02 molo-laptop kernel: [   50.863652] kjournald starting.  Commit interval 5 seconds
Jan  4 12:15:02 molo-laptop kernel: [   50.863728] EXT3-fs: mounted filesystem with ordered data mode.
Jan  4 12:15:02 molo-laptop kernel: [   74.491265] udevd version 124 started
Jan  4 12:15:02 molo-laptop kernel: [   75.056698] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
Jan  4 12:15:02 molo-laptop kernel: [   75.084029] ACPI: Power Button (FF) [PWRF]
Jan  4 12:15:02 molo-laptop kernel: [   75.084222] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input3
Jan  4 12:15:02 molo-laptop kernel: [   75.100021] ACPI: Sleep Button (CM) [SLPB]
Jan  4 12:15:02 molo-laptop kernel: [   75.100172] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input4
Jan  4 12:15:02 molo-laptop kernel: [   75.100733] ACPI: Lid Switch [LID]
Jan  4 12:15:02 molo-laptop kernel: [   75.100952] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input5
Jan  4 12:15:02 molo-laptop kernel: [   75.125045] ACPI: Power Button (CM) [PWRB]
Jan  4 12:15:02 molo-laptop kernel: [   75.125910] ACPI: AC Adapter [ACAD] (on-line)
Jan  4 12:15:02 molo-laptop kernel: [   75.150305] ACPI: Battery Slot [BAT0] (battery absent)
Jan  4 12:15:02 molo-laptop kernel: [   75.196708] ACPI: WMI: Mapper loaded
Jan  4 12:15:02 molo-laptop kernel: [   75.911526] acpi device:25: registered as cooling_device2
Jan  4 12:15:02 molo-laptop kernel: [   75.911771] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:23/input/input6
Jan  4 12:15:02 molo-laptop kernel: [   75.940047] ACPI: Video Device [UVGA] (multi-head: yes  rom: no  post: no)
Jan  4 12:15:02 molo-laptop kernel: [   76.185999] ricoh-mmc: Ricoh MMC Controller disabling driver
Jan  4 12:15:02 molo-laptop kernel: [   76.186069] ricoh-mmc: Copyright(c) Philip Langdale
Jan  4 12:15:02 molo-laptop kernel: [   76.186525] ricoh-mmc: Ricoh MMC controller found at 0000:02:05.2 [1180:0843] (rev 12)
Jan  4 12:15:02 molo-laptop kernel: [   76.186614] ricoh-mmc: Controller is now disabled.
Jan  4 12:15:02 molo-laptop kernel: [   76.257072] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Jan  4 12:15:02 molo-laptop kernel: [   76.294068] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Jan  4 12:15:02 molo-laptop kernel: [   76.302249] sdhci: Secure Digital Host Controller Interface driver
Jan  4 12:15:02 molo-laptop kernel: [   76.302316] sdhci: Copyright(c) Pierre Ossman
Jan  4 12:15:02 molo-laptop kernel: [   76.315532] sdhci-pci 0000:02:05.1: SDHCI controller found [1180:0822] (rev 22)
Jan  4 12:15:02 molo-laptop kernel: [   76.316058] ACPI: PCI Interrupt Link [LNK2] enabled at IRQ 7
Jan  4 12:15:02 molo-laptop kernel: [   76.316131] sdhci-pci 0000:02:05.1: PCI INT B -> Link[LNK2] -> GSI 7 (level, low) -> IRQ 7
Jan  4 12:15:02 molo-laptop kernel: [   76.323596] mmc0: SDHCI controller on PCI [0000:02:05.1] using PIO
Jan  4 12:15:02 molo-laptop kernel: [   76.340981] Linux agpgart interface v0.103
Jan  4 12:15:02 molo-laptop kernel: [   76.602438] nvidia: module license 'NVIDIA' taints kernel.
Jan  4 12:15:02 molo-laptop kernel: [   76.858993] ACPI: PCI Interrupt Link [LGPU] enabled at IRQ 16
Jan  4 12:15:02 molo-laptop kernel: [   76.859072] nvidia 0000:00:12.0: PCI INT A -> Link[LGPU] -> GSI 16 (level, low) -> IRQ 16
Jan  4 12:15:02 molo-laptop kernel: [   76.859537] NVRM: loading NVIDIA UNIX x86 Kernel Module  177.80  Wed Oct  1 14:38:10 PDT 2008
Jan  4 12:15:02 molo-laptop kernel: [   76.866870] input: PC Speaker as /devices/platform/pcspkr/input/input7
Jan  4 12:15:02 molo-laptop kernel: [   76.888625] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
Jan  4 12:15:02 molo-laptop kernel: [   77.208913] wlan: 0.9.4
Jan  4 12:15:02 molo-laptop kernel: [   77.215677] ath_pci: 0.9.4
Jan  4 12:15:02 molo-laptop kernel: [   77.216233] ACPI: PCI Interrupt Link [LK4E] enabled at IRQ 19
Jan  4 12:15:02 molo-laptop kernel: [   77.216305] ath_pci 0000:03:00.0: PCI INT A -> Link[LK4E] -> GSI 19 (level, low) -> IRQ 19
Jan  4 12:15:02 molo-laptop kernel: [   77.245252] ath_pci 0000:03:00.0: PCI INT A disabled
Jan  4 12:15:02 molo-laptop kernel: [   77.750697] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 21
Jan  4 12:15:02 molo-laptop kernel: [   77.750775] HDA Intel 0000:00:07.0: PCI INT A -> Link[LAZA] -> GSI 21 (level, low) -> IRQ 21
Jan  4 12:15:02 molo-laptop kernel: [   78.016995] Synaptics Touchpad, model: 1, fw: 6.3, id: 0x1a0b1, caps: 0xa04711/0xa00000
Jan  4 12:15:02 molo-laptop kernel: [   78.094786] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input8
Jan  4 12:15:02 molo-laptop kernel: [   78.493242] lp: driver loaded but no devices found
Jan  4 12:15:02 molo-laptop kernel: [   78.648932] Adding 5084532k swap on /dev/sda6.  Priority:-1 extents:1 across:5084532k
Jan  4 12:15:02 molo-laptop kernel: [   79.216742] EXT3 FS on sda5, internal journal
Jan  4 12:15:02 molo-laptop kernel: [   79.777987] type=1505 audit(1231089300.450:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=4174
Jan  4 12:15:02 molo-laptop kernel: [   79.986140] type=1505 audit(1231089300.658:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4179
Jan  4 12:15:02 molo-laptop kernel: [   79.986389] type=1505 audit(1231089300.658:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4179
Jan  4 12:15:02 molo-laptop kernel: [   80.136532] ip_tables: (C) 2000-2006 Netfilter Core Team
Jan  4 12:15:02 molo-laptop kernel: [   81.066801] powernow-k8: Found 1 AMD Turion(tm) 64 X2 Mobile Technology TL-60 processors (2 cpu cores) (version 2.20.00)
Jan  4 12:15:02 molo-laptop kernel: [   81.067405] powernow-k8:    0 : fid 0xc (2000 MHz), vid 0x12
Jan  4 12:15:02 molo-laptop kernel: [   81.067409] powernow-k8:    1 : fid 0xa (1800 MHz), vid 0x13
Jan  4 12:15:02 molo-laptop kernel: [   81.067412] powernow-k8:    2 : fid 0x8 (1600 MHz), vid 0x14
Jan  4 12:15:02 molo-laptop kernel: [   81.067415] powernow-k8:    3 : fid 0x0 (800 MHz), vid 0x1e
Jan  4 12:15:02 molo-laptop kernel: [   81.745338] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
Jan  4 12:15:02 molo-laptop kernel: [   81.833624] apm: BIOS not found.
Jan  4 12:15:02 molo-laptop kernel: [   82.011412] ppdev: user-space parallel port driver
Jan  4 12:15:05 molo-laptop kernel: [   84.711886] NET: Registered protocol family 10
Jan  4 12:15:05 molo-laptop kernel: [   84.714814] lo: Disabled Privacy Extensions
Jan  4 12:15:06 molo-laptop kernel: [   85.863617] Bluetooth: Core ver 2.13
Jan  4 12:15:06 molo-laptop kernel: [   85.863794] NET: Registered protocol family 31
Jan  4 12:15:06 molo-laptop kernel: [   85.863800] Bluetooth: HCI device and connection manager initialized
Jan  4 12:15:06 molo-laptop kernel: [   85.863811] Bluetooth: HCI socket layer initialized
Jan  4 12:15:06 molo-laptop kernel: [   85.911732] Bluetooth: L2CAP ver 2.11
Jan  4 12:15:06 molo-laptop kernel: [   85.911747] Bluetooth: L2CAP socket layer initialized
Jan  4 12:15:06 molo-laptop kernel: [   85.955710] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Jan  4 12:15:06 molo-laptop kernel: [   85.955732] Bluetooth: BNEP filters: protocol multicast
Jan  4 12:15:06 molo-laptop kernel: [   86.047240] Bridge firewalling registered
Jan  4 12:15:06 molo-laptop kernel: [   86.106933] Bluetooth: RFCOMM socket layer initialized
Jan  4 12:15:06 molo-laptop kernel: [   86.107039] Bluetooth: RFCOMM TTY layer initialized
Jan  4 12:15:06 molo-laptop kernel: [   86.107046] Bluetooth: RFCOMM ver 1.10
Jan  4 12:15:06 molo-laptop kernel: [   86.114259] Bluetooth: SCO (Voice Link) ver 0.6
Jan  4 12:15:06 molo-laptop kernel: [   86.114282] Bluetooth: SCO socket layer initialized
```

---

### Post by walkerk on 2009-01-04
I had to add [ acpi=noirq ] to grub in order to get my HP to boot. Scroll to the bottom and to the right and take not of the highlighted text.

```
gksu gedit /boot/grub/menu.lst
```

```
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=1267e03e-41c4-42e0-8b60-e6cb32b98ba7 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=1267e03e-41c4-42e0-8b60-e6cb32b98ba7

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash quiet

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		1267e03e-41c4-42e0-8b60-e6cb32b98ba7
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=1267e03e-41c4-42e0-8b60-e6cb32b98ba7 ro quiet splash [COLOR="Lime"]**acpi=noirq**[/COLOR]
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		1267e03e-41c4-42e0-8b60-e6cb32b98ba7
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=1267e03e-41c4-42e0-8b60-e6cb32b98ba7 ro single [COLOR="Lime"]**acpi=noirq**[/COLOR]
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		2.6.27-7-generic Backup
uuid		1267e03e-41c4-42e0-8b60-e6cb32b98ba7
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=1267e03e-41c4-42e0-8b60-e6cb32b98ba7 ro single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		1267e03e-41c4-42e0-8b60-e6cb32b98ba7
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```

---

### Post by molo on 2009-01-04
Thanks, that fixed it!  I appreciate the help!

---

