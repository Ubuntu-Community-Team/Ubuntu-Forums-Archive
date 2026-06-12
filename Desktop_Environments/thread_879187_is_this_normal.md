---
title: "is this normal?"
date: 2008-08-03
forum: Desktop Environments
---

### Post by discostu668 on 2008-08-03
when i boot ubuntu 8.04 and log in, it goes into the desktop, then the screen goes black for a few seconds except for a grey-ish bar that shows up where my top panel is.  i think it might have something to do with my video card (which is the ndivida geforce 7600gt).  i believe i have the latest drivers installed, but i am not entirely sure.

any advice is greatly appreciated.  thanks!

---

### Post by silkstone on 2008-08-03
Not normal.... Check System > Administration > Hardware Drivers and see if the nvidia accelerated graphics driver is installed.

Also go to System > Preferences > Appearance and turn off Desktop Effects. Does that cure the problem?

This is controversial, but Desktop Effects (compiz-fusion) are great for demonstrating that Ubuntu can have more eye-candy than Vista Aero or OS-X, but they slow everything down and don't add much if anything to functionality.

I will now duck. :D

---

### Post by Ingenue on 2008-08-03
> **silkstone said:**
> 
This is controversial, but Desktop Effects (compiz-fusion) are great for demonstrating that Ubuntu can have more eye-candy than Vista Aero or OS-X, but they slow everything down and don't add much if anything to functionality.

I will now duck. :D

I agree, not normal. Being new to all this I don't have much advice though :(. I am interested in seeing how this works out for you though.

Silkstone, I share your feelings on Compiz-fusion. It creates beautiful effects, I just don't need them. 

Quack! Quack!

---

### Post by discostu668 on 2008-08-03
> **silkstone said:**
> Not normal.... Check System > Administration > Hardware Drivers and see if the nvidia accelerated graphics driver is installed.

Also go to System > Preferences > Appearance and turn off Desktop Effects. Does that cure the problem?

This is controversial, but Desktop Effects (compiz-fusion) are great for demonstrating that Ubuntu can have more eye-candy than Vista Aero or OS-X, but they slow everything down and don't add much if anything to functionality.

I will now duck. :D

silkstone,

nvidia accelerated driver is installed.  i turned the desktop effects completely off and it kind of worked, but not really.  the screen didn't go black, but there was still some sort of glitch with the top panel (and my AWN dock does not appear).  if i set the effects to normal, the screen goes black and my AWN dock appears normally (i posted another thread where the AWN dock icons were appearing in the bottom left and slowly sliding towards the dock which was centered on the bottom of the screen).  should i try reinstalling the driver? if so, how do i go about doing that? i'm really new to linux and i'm getting slightly frustrated over the fact that there isn't any kind of .exe or .dmg type of file to just double-click and install the app/driver/etc... though i'm hoping that isn't the case.  

but i'm willing to give linux a shot just to see if i'll warm up to it.  however, i've been on these forums since day one (about a month ago) troubleshooting problem after problem with this OS.

---

### Post by phidia on 2008-08-03
Sorry you're having problems. Maybe attach the results of:
> cat /var/log/Xorg.0.log (from a terminal)
You could also enter > dmesg in a terminal right after this happens/you log in and see what that has for info.

---

### Post by discostu668 on 2008-08-03
this is the output of dmesg:

[   22.629761] system 00:07: ioport range 0xa00-0xafe has been reserved
[   22.629764] system 00:07: ioport range 0xb00-0xbfe has been reserved
[   22.629766] system 00:07: ioport range 0xc80-0xcaf has been reserved
[   22.629769] system 00:07: ioport range 0xcb0-0xcbf has been reserved
[   22.629771] system 00:07: ioport range 0xcc0-0xcf7 has been reserved
[   22.629774] system 00:07: ioport range 0xd00-0xdfe has been reserved
[   22.629776] system 00:07: ioport range 0xe00-0xefe has been reserved
[   22.629779] system 00:07: ioport range 0xf00-0xffe has been reserved
[   22.629781] system 00:07: ioport range 0x2000-0x20fe has been reserved
[   22.629784] system 00:07: ioport range 0x2100-0x21fe has been reserved
[   22.629786] system 00:07: ioport range 0x2200-0x22fe has been reserved
[   22.629789] system 00:07: ioport range 0x2300-0x23fe has been reserved
[   22.629791] system 00:07: ioport range 0x2400-0x24fe has been reserved
[   22.629794] system 00:07: ioport range 0x2500-0x25fe has been reserved
[   22.629796] system 00:07: ioport range 0x2600-0x26fe has been reserved
[   22.629799] system 00:07: ioport range 0x2700-0x27fe has been reserved
[   22.629801] system 00:07: ioport range 0x2800-0x28fe has been reserved
[   22.629804] system 00:07: ioport range 0x2900-0x29fe has been reserved
[   22.629807] system 00:07: ioport range 0x2a00-0x2afe has been reserved
[   22.629809] system 00:07: ioport range 0x2b00-0x2bfe has been reserved
[   22.629812] system 00:07: ioport range 0x2c00-0x2cfe has been reserved
[   22.629814] system 00:07: ioport range 0x2d00-0x2dfe has been reserved
[   22.629817] system 00:07: iomem range 0xf0000000-0xf3ffffff could not be reserved
[   22.629820] system 00:07: iomem range 0xfeda0000-0xfedacfff has been reserved
[   22.660303] PCI: Bridge: 0000:00:01.0
[   22.660306]   IO window: d000-dfff
[   22.660310]   MEM window: fc000000-feafffff
[   22.660314]   PREFETCH window: e0000000-efffffff
[   22.660318] PCI: Bridge: 0000:00:1c.0
[   22.660319]   IO window: disabled.
[   22.660324]   MEM window: fbf00000-fbffffff
[   22.660328]   PREFETCH window: disabled.
[   22.660333] PCI: Bridge: 0000:00:1c.4
[   22.660334]   IO window: disabled.
[   22.660339]   MEM window: disabled.
[   22.660342]   PREFETCH window: disabled.
[   22.660347] PCI: Bridge: 0000:00:1c.5
[   22.660350]   IO window: c000-cfff
[   22.660355]   MEM window: fb800000-fbefffff
[   22.660358]   PREFETCH window: disabled.
[   22.660364] PCI: Bridge: 0000:00:1e.0
[   22.660367]   IO window: b000-bfff
[   22.660371]   MEM window: fb700000-fb7fffff
[   22.660375]   PREFETCH window: disabled.
[   22.660396] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 16
[   22.660401] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   22.660421] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 16
[   22.660427] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   22.660446] ACPI: PCI Interrupt 0000:00:1c.4[A] -> GSI 16 (level, low) -> IRQ 16
[   22.660451] PCI: Setting latency timer of device 0000:00:1c.4 to 64
[   22.660471] ACPI: PCI Interrupt 0000:00:1c.5[B] -> GSI 17 (level, low) -> IRQ 17
[   22.660476] PCI: Setting latency timer of device 0000:00:1c.5 to 64
[   22.660488] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   22.660499] NET: Registered protocol family 2
[   22.697651] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   22.697951] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   22.698531] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   22.698818] TCP: Hash tables configured (established 131072 bind 65536)
[   22.698821] TCP reno registered
[   22.709754] checking if image is initramfs... it is
[   23.285461] Freeing initrd memory: 7324k freed
[   23.285594] Simple Boot Flag at 0x7a set to 0x1
[   23.286452] audit: initializing netlink socket (disabled)
[   23.286466] audit(1217816723.080:1): initialized
[   23.286783] highmem bounce pool size: 64 pages
[   23.289380] VFS: Disk quotas dquot_6.5.1
[   23.289478] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   23.289631] io scheduler noop registered
[   23.289634] io scheduler anticipatory registered
[   23.289636] io scheduler deadline registered
[   23.289649] io scheduler cfq registered (default)
[   23.289760] Boot video device is 0000:01:00.0
[   23.289896] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   23.289940] assign_interrupt_mode Found MSI capability
[   23.289977] Allocate Port Service[0000:00:01.0:pcie00]
[   23.290079] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   23.290124] assign_interrupt_mode Found MSI capability
[   23.290160] Allocate Port Service[0000:00:1c.0:pcie00]
[   23.290215] Allocate Port Service[0000:00:1c.0:pcie02]
[   23.290321] PCI: Setting latency timer of device 0000:00:1c.4 to 64
[   23.290375] assign_interrupt_mode Found MSI capability
[   23.290413] Allocate Port Service[0000:00:1c.4:pcie00]
[   23.290458] Allocate Port Service[0000:00:1c.4:pcie02]
[   23.290561] PCI: Setting latency timer of device 0000:00:1c.5 to 64
[   23.290608] assign_interrupt_mode Found MSI capability
[   23.290645] Allocate Port Service[0000:00:1c.5:pcie00]
[   23.290691] Allocate Port Service[0000:00:1c.5:pcie02]
[   23.291024] isapnp: Scanning for PnP cards...
[   23.642492] isapnp: No Plug & Play device found
[   23.682387] Real Time Clock Driver v1.12ac
[   23.682496] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   23.684003] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   23.684099] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   23.684292] PNP: No PS/2 controller found. Probing ports directly.
[   23.686884] serio: i8042 KBD port at 0x60,0x64 irq 1
[   23.686891] serio: i8042 AUX port at 0x60,0x64 irq 12
[   23.697249] mice: PS/2 mouse device common for all mice
[   23.697391] EISA: Probing bus 0 at eisa.0
[   23.697395] EISA: Cannot allocate resource for mainboard
[   23.697401] Cannot allocate resource for EISA slot 2
[   23.697424] EISA: Detected 0 cards.
[   23.697427] cpuidle: using governor ladder
[   23.697429] cpuidle: using governor menu
[   23.697509] NET: Registered protocol family 1
[   23.697540] Using IPI No-Shortcut mode
[   23.697569] registered taskstats version 1
[   23.697667]   Magic number: 4:893:408
[   23.697784] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   23.697786] EDD information not available.
[   23.697993] Freeing unused kernel memory: 368k freed
[   24.929979] fuse init (API version 7.9)
[   24.952988] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
[   24.953005] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
[   25.248506] usbcore: registered new interface driver usbfs
[   25.248532] usbcore: registered new interface driver hub
[   25.248562] usbcore: registered new device driver usb
[   25.249822] USB Universal Host Controller Interface driver v3.0
[   25.249872] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 21 (level, low) -> IRQ 18
[   25.249885] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   25.249888] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   25.250069] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   25.250097] uhci_hcd 0000:00:1d.0: irq 18, io base 0x0000ff80
[   25.250235] usb usb1: configuration #1 chosen from 1 choice
[   25.250262] hub 1-0:1.0: USB hub found
[   25.250268] hub 1-0:1.0: 2 ports detected
[   25.329332] SCSI subsystem initialized
[   25.352336] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 22 (level, low) -> IRQ 19
[   25.352350] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   25.352354] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   25.352382] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   25.352412] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000ff60
[   25.352530] usb usb2: configuration #1 chosen from 1 choice
[   25.352559] hub 2-0:1.0: USB hub found
[   25.352566] hub 2-0:1.0: 2 ports detected
[   25.359370] libata version 3.00 loaded.
[   25.456283] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 20
[   25.456296] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   25.456300] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   25.456326] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   25.456355] uhci_hcd 0000:00:1d.2: irq 20, io base 0x0000ff40
[   25.456477] usb usb3: configuration #1 chosen from 1 choice
[   25.456505] hub 3-0:1.0: USB hub found
[   25.456512] hub 3-0:1.0: 2 ports detected
[   25.560239] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 23 (level, low) -> IRQ 21
[   25.560252] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[   25.560256] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[   25.560285] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[   25.560313] uhci_hcd 0000:00:1d.3: irq 21, io base 0x0000ff20
[   25.560433] usb usb4: configuration #1 chosen from 1 choice
[   25.560462] hub 4-0:1.0: USB hub found
[   25.560468] hub 4-0:1.0: 2 ports detected
[   25.592168] usb 1-1: new full speed USB device using uhci_hcd and address 2
[   25.664319] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 21 (level, low) -> IRQ 18
[   25.664333] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   25.664338] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   25.664365] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[   25.668287] ehci_hcd 0000:00:1d.7: debug port 1
[   25.668293] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
[   25.668301] ehci_hcd 0000:00:1d.7: irq 18, io mem 0xffa80800
[   25.716047] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   25.716180] usb usb5: configuration #1 chosen from 1 choice
[   25.716208] hub 5-0:1.0: USB hub found
[   25.716216] hub 5-0:1.0: 8 ports detected
[   25.820233] ahci 0000:00:1f.2: version 3.0
[   25.820258] ACPI: PCI Interrupt 0000:00:1f.2[C] -> GSI 20 (level, low) -> IRQ 22
[   26.111833] usb 1-1: device not accepting address 2, error -71
[   26.823486] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl RAID mode
[   26.823492] ahci 0000:00:1f.2: flags: 64bit ncq pm led clo pio slum part 
[   26.823497] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   26.823762] scsi0 : ahci
[   26.823824] scsi1 : ahci
[   26.823868] scsi2 : ahci
[   26.823910] scsi3 : ahci
[   26.823945] ata1: SATA max UDMA/133 abar m1024@0xfebffc00 port 0xfebffd00 irq 219
[   26.823949] ata2: SATA max UDMA/133 abar m1024@0xfebffc00 port 0xfebffd80 irq 219
[   26.823954] ata3: SATA max UDMA/133 abar m1024@0xfebffc00 port 0xfebffe00 irq 219
[   26.823957] ata4: SATA max UDMA/133 abar m1024@0xfebffc00 port 0xfebffe80 irq 219
[   26.903426] usb 5-2: new high speed USB device using ehci_hcd and address 3
[   27.035851] usb 5-2: configuration #1 chosen from 1 choice
[   27.036026] hub 5-2:1.0: USB hub found
[   27.036126] hub 5-2:1.0: 4 ports detected
[   27.299224] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   27.300688] ata1.00: ATA-6: ST3160023AS, 8.12, max UDMA/133
[   27.300691] ata1.00: 312500000 sectors, multi 16: LBA48 NCQ (depth 31/32)
[   27.302250] ata1.00: configured for UDMA/133
[   27.379179] usb 5-6: new high speed USB device using ehci_hcd and address 4
[   27.512984] usb 5-6: configuration #1 chosen from 1 choice
[   27.615074] ata2: SATA link down (SStatus 0 SControl 300)
[   27.750988] usb 1-1: new full speed USB device using uhci_hcd and address 4
[   27.921841] usb 1-1: configuration #1 chosen from 1 choice
[   27.927750] hub 1-1:1.0: USB hub found
[   27.928728] hub 1-1:1.0: 3 ports detected
[   28.086816] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   28.088140] ata3.00: ATA-6: ST3160023AS, 8.12, max UDMA/133
[   28.088144] ata3.00: 312500000 sectors, multi 16: LBA48 NCQ (depth 31/32)
[   28.089716] ata3.00: configured for UDMA/133
[   28.234873] usb 5-2.3: new low speed USB device using ehci_hcd and address 5
[   28.331301] usb 5-2.3: configuration #1 chosen from 1 choice
[   28.540405] usb 1-1.1: new full speed USB device using uhci_hcd and address 5
[   28.562567] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   28.564659] ata4.00: ATA-7: Maxtor 6B200M0, BANC1B10, max UDMA/133
[   28.564662] ata4.00: 398297088 sectors, multi 0: LBA48 NCQ (not used)
[   28.567647] ata4.00: configured for UDMA/133
[   28.567776] scsi 0:0:0:0: Direct-Access     ATA      ST3160023AS      8.12 PQ: 0 ANSI: 5
[   28.567934] scsi 2:0:0:0: Direct-Access     ATA      ST3160023AS      8.12 PQ: 0 ANSI: 5
[   28.568065] scsi 3:0:0:0: Direct-Access     ATA      Maxtor 6B200M0   BANC PQ: 0 ANSI: 5
[   28.571281] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 16 (level, low) -> IRQ 16
[   28.571321] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   28.571336] ACPI: PCI interrupt for device 0000:00:1f.1 disabled
[   28.574605] ata_piix 0000:00:1f.1: version 2.12
[   28.574621] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 16 (level, low) -> IRQ 16
[   28.574650] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   28.574710] scsi4 : ata_piix
[   28.574762] scsi5 : ata_piix
[   28.574793] ata5: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[   28.574795] ata6: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[   28.578687] Driver 'sd' needs updating - please use bus_type methods
[   28.582659] sd 0:0:0:0: [sda] 312500000 512-byte hardware sectors (160000 MB)
[   28.582678] sd 0:0:0:0: [sda] Write Protect is off
[   28.582682] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   28.582707] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   28.582769] sd 0:0:0:0: [sda] 312500000 512-byte hardware sectors (160000 MB)
[   28.582783] sd 0:0:0:0: [sda] Write Protect is off
[   28.582786] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   28.582809] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   28.582812]  sda: sda1
[   28.597212]  sda: p1 exceeds device capacity
[   28.597292] sd 0:0:0:0: [sda] Attached SCSI disk
[   28.597722] sd 2:0:0:0: [sdb] 312500000 512-byte hardware sectors (160000 MB)
[   28.597738] sd 2:0:0:0: [sdb] Write Protect is off
[   28.597741] sd 2:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   28.597765] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   28.597814] sd 2:0:0:0: [sdb] 312500000 512-byte hardware sectors (160000 MB)
[   28.597828] sd 2:0:0:0: [sdb] Write Protect is off
[   28.597830] sd 2:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   28.597853] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   28.597857]  sdb: unknown partition table
[   28.612488] sd 2:0:0:0: [sdb] Attached SCSI disk
[   28.612567] sd 3:0:0:0: [sdc] 398297088 512-byte hardware sectors (203928 MB)
[   28.612582] sd 3:0:0:0: [sdc] Write Protect is off
[   28.612585] sd 3:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[   28.612609] sd 3:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   28.612660] sd 3:0:0:0: [sdc] 398297088 512-byte hardware sectors (203928 MB)
[   28.612676] sd 3:0:0:0: [sdc] Write Protect is off
[   28.612679] sd 3:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[   28.612702] sd 3:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   28.612705]  sdc: sdc1 sdc2 < sdc5 >
[   28.652877] sd 3:0:0:0: [sdc] Attached SCSI disk
[   28.657533] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   28.657559] sd 2:0:0:0: Attached scsi generic sg1 type 0
[   28.657581] sd 3:0:0:0: Attached scsi generic sg2 type 0
[   28.677437] usb 1-1.1: configuration #1 chosen from 1 choice
[   28.690338] usbcore: registered new interface driver hiddev
[   28.692203] input: Logitech Optical USB Mouse as /devices/pci0000:00/0000:00:1d.7/usb5/5-2/5-2.3/5-2.3:1.0/input/input1
[   28.710632] input,hidraw0: USB HID v1.10 Mouse [Logitech Optical USB Mouse] on usb-0000:00:1d.7-2.3
[   28.713591] input: Dell Dell USB Keyboard as /devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1.1/1-1.1:1.0/input/input2
[   28.738681] input,hidraw1: USB HID v1.10 Keyboard [Dell Dell USB Keyboard] on usb-0000:00:1d.0-1.1
[   28.744380] input: Dell Dell USB Keyboard as /devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1.1/1-1.1:1.1/input/input3
[   28.762534] input,hidraw2: USB HID v1.10 Device [Dell Dell USB Keyboard] on usb-0000:00:1d.0-1.1
[   28.762560] usbcore: registered new interface driver usbhid
[   28.762564] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   28.773490] attempt to access beyond end of device
[   28.773495] sda: rw=0, want=624988040, limit=312500000
[   28.773498] Buffer I/O error on device sda1, logical block 78123248
[   28.773503] attempt to access beyond end of device
[   28.773505] sda: rw=0, want=624988040, limit=312500000
[   28.773508] Buffer I/O error on device sda1, logical block 78123248
[   28.773519] attempt to access beyond end of device
[   28.773522] sda: rw=0, want=624988152, limit=312500000
[   28.773524] Buffer I/O error on device sda1, logical block 78123262
[   28.773528] attempt to access beyond end of device
[   28.773530] sda: rw=0, want=624988152, limit=312500000
[   28.773533] Buffer I/O error on device sda1, logical block 78123262
[   28.773591] attempt to access beyond end of device
[   28.773594] sda: rw=0, want=624988160, limit=312500000
[   28.773596] Buffer I/O error on device sda1, logical block 78123263
[   28.773600] attempt to access beyond end of device
[   28.773602] sda: rw=0, want=624988160, limit=312500000
[   28.773604] Buffer I/O error on device sda1, logical block 78123263
[   28.773613] attempt to access beyond end of device
[   28.773617] sda: rw=0, want=624988160, limit=312500000
[   28.773620] Buffer I/O error on device sda1, logical block 78123263
[   28.773629] attempt to access beyond end of device
[   28.773631] sda: rw=0, want=624988160, limit=312500000
[   28.773634] Buffer I/O error on device sda1, logical block 78123263
[   28.773641] attempt to access beyond end of device
[   28.773643] sda: rw=0, want=624988160, limit=312500000
[   28.773646] Buffer I/O error on device sda1, logical block 78123263
[   28.773654] attempt to access beyond end of device
[   28.773657] sda: rw=0, want=624988160, limit=312500000
[   28.773660] Buffer I/O error on device sda1, logical block 78123263
[   28.773669] attempt to access beyond end of device
[   28.773671] sda: rw=0, want=624988160, limit=312500000
[   28.773681] attempt to access beyond end of device
[   28.773684] sda: rw=0, want=624988104, limit=312500000
[   28.773692] attempt to access beyond end of device
[   28.773695] sda: rw=0, want=624988152, limit=312500000
[   28.773703] attempt to access beyond end of device
[   28.773706] sda: rw=0, want=624988160, limit=312500000
[   28.773715] attempt to access beyond end of device
[   28.773717] sda: rw=0, want=624988160, limit=312500000
[   28.865142] Attempting manual resume
[   28.865147] swsusp: Resume From Partition 8:37
[   28.865149] PM: Checking swsusp image.
[   28.865244] PM: Resume from disk failed.
[   28.885323] kjournald starting.  Commit interval 5 seconds
[   28.885336] EXT3-fs: mounted filesystem with ordered data mode.
[   29.058765] ata5.00: ATAPI: PIONEER DVD-RW  DVR-112D, 1.21, max UDMA/66
[   29.058793] ata5.01: ATAPI: HL-DT-STDVD-ROM GDR8163B, 0D20, max UDMA/33
[   29.230535] ata5.00: configured for UDMA/66
[   29.402411] ata5.01: configured for UDMA/33
[   29.402457] ata6: port disabled. ignoring.
[   29.408768] scsi 4:0:0:0: CD-ROM            PIONEER  DVD-RW  DVR-112D 1.21 PQ: 0 ANSI: 5
[   29.408858] scsi 4:0:0:0: Attached scsi generic sg3 type 5
[   29.411965] scsi 4:0:1:0: CD-ROM            HL-DT-ST DVD-ROM GDR8163B 0D20 PQ: 0 ANSI: 5
[   29.412055] scsi 4:0:1:0: Attached scsi generic sg4 type 5
[   34.020211] attempt to access beyond end of device
[   34.020218] sda: rw=0, want=624988040, limit=312500000
[   34.020220] printk: 5 messages suppressed.
[   34.020223] Buffer I/O error on device sda1, logical block 78123248
[   34.020228] attempt to access beyond end of device
[   34.020230] sda: rw=0, want=624988040, limit=312500000
[   34.020244] attempt to access beyond end of device
[   34.020247] sda: rw=0, want=624988152, limit=312500000
[   34.020250] attempt to access beyond end of device
[   34.020252] sda: rw=0, want=624988152, limit=312500000
[   34.020300] attempt to access beyond end of device
[   34.020304] sda: rw=0, want=624988160, limit=312500000
[   34.020307] attempt to access beyond end of device
[   34.020309] sda: rw=0, want=624988160, limit=312500000
[   34.020318] attempt to access beyond end of device
[   34.020320] sda: rw=0, want=624988160, limit=312500000
[   34.020328] attempt to access beyond end of device
[   34.020330] sda: rw=0, want=624988160, limit=312500000
[   34.020337] attempt to access beyond end of device
[   34.020340] sda: rw=0, want=624988160, limit=312500000
[   34.020349] attempt to access beyond end of device
[   34.020351] sda: rw=0, want=624988160, limit=312500000
[   34.020358] attempt to access beyond end of device
[   34.020361] sda: rw=0, want=624988160, limit=312500000
[   34.020370] attempt to access beyond end of device
[   34.020372] sda: rw=0, want=624988104, limit=312500000
[   34.020380] attempt to access beyond end of device
[   34.020382] sda: rw=0, want=624988152, limit=312500000
[   34.020389] attempt to access beyond end of device
[   34.020407] sda: rw=0, want=624988160, limit=312500000
[   34.020420] attempt to access beyond end of device
[   34.020423] sda: rw=0, want=624988160, limit=312500000
[   34.316201] input: PC Speaker as /devices/platform/pcspkr/input/input4
[   34.740541] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   34.780514] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   34.820453] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   34.821353] ath_hal: module license 'Proprietary' taints kernel.
[   34.856368] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[   34.956651] Linux agpgart interface v0.102
[   35.001696] input: Power Button (FF) as /devices/virtual/input/input5
[   35.051252] ACPI: Power Button (FF) [PWRF]
[   35.051319] input: Power Button (CM) as /devices/virtual/input/input6
[   35.071310] wlan: 0.9.4
[   35.115224] ACPI: Power Button (CM) [VBTN]
[   35.161682] ath_pci: 0.9.4
[   35.161744] ACPI: PCI Interrupt 0000:05:04.0[A] -> GSI 16 (level, low) -> IRQ 16
[   36.138715] ath_rate_sample: 1.2 (0.9.4)
[   36.139274] wifi0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
[   36.139282] wifi0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[   36.139292] wifi0: H/W encryption support: WEP AES AES_CCM TKIP
[   36.139297] wifi0: mac 7.8 phy 4.5 radio 5.6
[   36.139302] wifi0: Use hw queue 1 for WME_AC_BE traffic
[   36.139304] wifi0: Use hw queue 0 for WME_AC_BK traffic
[   36.139306] wifi0: Use hw queue 2 for WME_AC_VI traffic
[   36.139308] wifi0: Use hw queue 3 for WME_AC_VO traffic
[   36.139310] wifi0: Use hw queue 8 for CAB traffic
[   36.139311] wifi0: Use hw queue 9 for beacons
[   36.161152] Driver 'sr' needs updating - please use bus_type methods
[   36.207806] sr0: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
[   36.207811] Uniform CD-ROM driver Revision: 3.20
[   36.207869] sr 4:0:0:0: Attached scsi CD-ROM sr0
[   36.222046] wifi0: Atheros 5212: mem=0xfb7f0000, irq=16
[   36.255754] sr1: scsi3-mmc drive: 48x/48x cd/rw xa/form2 cdda tray
[   36.255818] sr 4:0:1:0: Attached scsi CD-ROM sr1
[   36.275414] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   36.275425] PCI: Setting latency timer of device 0000:01:00.0 to 64
[   36.275554] NVRM: loading NVIDIA UNIX x86 Kernel Module  169.12  Thu Feb 14 17:53:07 PST 2008
[   36.688730] ACPI: PCI Interrupt 0000:05:02.0[A] -> GSI 18 (level, low) -> IRQ 20
[   36.688751] snd-ca0106: Model 1013 Rev 00000000 Serial 10131102
[   37.728429] lp: driver loaded but no devices found
[   37.834129] Adding 8112784k swap on /dev/sdc5.  Priority:-1 extents:1 across:8112784k
[   38.393014] EXT3 FS on sdc1, internal journal
[   39.539468] ip_tables: (C) 2000-2006 Netfilter Core Team
[   40.025434] No dock devices found.
[   41.184871] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   41.184877] apm: disabled - APM is not SMP safe.
[   41.330610] ppdev: user-space parallel port driver
[   41.441527] audit(1217816741.880:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5080 profile="/usr/sbin/cupsd" namespace="default"
[   42.216491] attempt to access beyond end of device
[   42.216500] sda: rw=0, want=624988040, limit=312500000
[   42.216503] printk: 14 messages suppressed.
[   42.216506] Buffer I/O error on device sda1, logical block 78123248
[   42.217195] attempt to access beyond end of device
[   42.217200] sda: rw=0, want=624988040, limit=312500000
[   42.217529] attempt to access beyond end of device
[   42.217534] sda: rw=0, want=624988152, limit=312500000
[   42.217875] attempt to access beyond end of device
[   42.217879] sda: rw=0, want=624988152, limit=312500000
[   42.218237] attempt to access beyond end of device
[   42.218242] sda: rw=0, want=624988160, limit=312500000
[   42.218590] attempt to access beyond end of device
[   42.218594] sda: rw=0, want=624988160, limit=312500000
[   42.218915] attempt to access beyond end of device
[   42.218920] sda: rw=0, want=624988160, limit=312500000
[   42.219242] attempt to access beyond end of device
[   42.219246] sda: rw=0, want=624988160, limit=312500000
[   42.219587] attempt to access beyond end of device
[   42.219591] sda: rw=0, want=624988160, limit=312500000
[   42.219913] attempt to access beyond end of device
[   42.219918] sda: rw=0, want=624988160, limit=312500000
[   42.220238] attempt to access beyond end of device
[   42.220243] sda: rw=0, want=624988160, limit=312500000
[   42.220586] attempt to access beyond end of device
[   42.220590] sda: rw=0, want=624988104, limit=312500000
[   42.220910] attempt to access beyond end of device
[   42.220915] sda: rw=0, want=624988152, limit=312500000
[   42.221234] attempt to access beyond end of device
[   42.221238] sda: rw=0, want=624988160, limit=312500000
[   42.221558] attempt to access beyond end of device
[   42.221562] sda: rw=0, want=624988160, limit=312500000
[   42.557077] Bluetooth: Core ver 2.11
[   42.558471] NET: Registered protocol family 31
[   42.558493] Bluetooth: HCI device and connection manager initialized
[   42.558497] Bluetooth: HCI socket layer initialized
[   42.615985] Bluetooth: L2CAP ver 2.9
[   42.615991] Bluetooth: L2CAP socket layer initialized
[   42.677872] Bluetooth: RFCOMM socket layer initialized
[   42.678126] Bluetooth: RFCOMM TTY layer initialized
[   42.678131] Bluetooth: RFCOMM ver 1.8
[   59.463307] NET: Registered protocol family 10
[   59.463645] lo: Disabled Privacy Extensions
[   69.446434] NET: Registered protocol family 17
[   69.785178] ath0: no IPv6 routers present

---

### Post by discostu668 on 2008-08-03
i also know now that the nvidia driver installed is not the most recent version.  how do i update the driver? i've downloaded the file (NVIDIA-Linux-x86-173.14.12-pkg1.run), but i do not know how to install it. according to the website, i am supposed to type "sh NVIDIA-Linux-x86-173.14.12-pkg1.run", i am assuming in terminal, but that doesn't do anything.  i get a message saying, "Can't open NVIDIA-Linux-x86-173.14.12-pkg1.run".

---

### Post by rainwalker on 2008-08-03
I'm pretty sure that's just Compiz and your panels starting up; the same sort of thing happens to me and always has with Compiz.
AWN does start up, but it won't be shown if Compiz isn't running

---

### Post by xen-uno on 2008-08-03
[http://ubuntuforums.org/showpost.php?p=5086971&postcount=6](http://ubuntuforums.org/showpost.php?p=5086971&postcount=6)

Run all the commands in 7.b to make sure nvidia is completely cleared out.

---

### Post by discostu668 on 2008-08-12
xen-uno

thanks for the link - i ran all of the steps to install the new nvidia driver.

good news - it worked, thank you!
bad news - i no longer have wireless (it seems to have deleted my network adapter driver).  also, i'm still getting the black screen before the desktop fully loads.

---

### Post by tuxxy on 2008-08-12
I do beleive some of the window management plugins add to functionality but yes it will slow the system down a bit if lower specs

---

### Post by discostu668 on 2008-08-12
tuxxy,

thanks for the reply - i have actually removed AWN and i'm trying cairo dock instead.  doesn't seem to be any different as far as the black screen is concerned, but at least it opens properly when my desktop loads up.

---

### Post by woaibbhemm on 2008-08-12
hello~
      nice    to   meet  you .thank you   for   your  sharing    and  welcome   to  our   website ~










Welcome to usfine for [buy lotro gold](http://www.usfine.com/Lord-of-the-Rings-Online-US-c-93.html)Age Of Conan gold[/url] and 
[buy runescape gold](http://www.usfine.com/runescape-c-68.html)sevise.

---

### Post by Crafty Kisses on 2008-08-12
You can look at your X logs, and also I'd try reconfiguring X.

---

### Post by discostu668 on 2008-08-12
hi codename,

i'm really new when it comes to linux, how would i go about doing those things?

---

