---
title: "xubuntu 6.06 boot-up hangs at &quot;loading hardware drivers&quot;"
date: 2006-06-08
forum: Desktop Environments
---

### Post by Jose Catre-Vandis on 2006-06-08
Its a Dell Latitude CPt 333, with 192mb RAM, which was happily running XP and then Breezy. Decided to install Xubuntu 6.06 to speed things up a bit.

Every two out of three boots it hangs on "Loading Hardware Drivers" and will go no further. Please see the dmesg output from one of these hangs, can anyone see what is going wrong? Or why on the other third of boots it goes through OK??

> [4294667.296000] Linux version 2.6.15-23-386 (buildd@rothera) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Tue May 23 13:49:40 UTC 2006
[4294667.296000] BIOS-provided physical RAM map:
[4294667.296000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[4294667.296000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[4294667.296000]  BIOS-e820: 00000000000c0000 - 00000000000cc000 (reserved)
[4294667.296000]  BIOS-e820: 0000000000100000 - 000000000bfec000 (usable)
[4294667.296000]  BIOS-e820: 000000000bfec000 - 000000000bff0000 (reserved)
[4294667.296000]  BIOS-e820: 00000000100a0000 - 0000000010100000 (reserved)
[4294667.296000]  BIOS-e820: 00000000ffe00000 - 0000000100000000 (reserved)
[4294667.296000] 0MB HIGHMEM available.
[4294667.296000] 191MB LOWMEM available.
[4294667.296000] On node 0 totalpages: 49132
[4294667.296000]   DMA zone: 4096 pages, LIFO batch:0
[4294667.296000]   DMA32 zone: 0 pages, LIFO batch:0
[4294667.296000]   Normal zone: 45036 pages, LIFO batch:7
[4294667.296000]   HighMem zone: 0 pages, LIFO batch:0
[4294667.296000] DMI 2.3 present.
[4294667.296000] ACPI: RSDP (v000 DELL                                  ) @ 0x000f38a0
[4294667.296000] ACPI: RSDT (v001 DELL    CPi R   0x27d10b07 ASL  0x00000061) @ 0x0bff0000
[4294667.296000] ACPI: FADT (v001 DELL    CPi R   0x27d10b07 ASL  0x00000061) @ 0x0bff0400
[4294667.296000] ACPI: DSDT (v001 INT430 SYSFexxx 0x00001001 MSFT 0x0100000c) @ 0x00000000
[4294667.296000] ACPI: PM-Timer IO Port: 0x808
[4294667.296000] Allocating PCI resources starting at 20000000 (gap: 10100000:efd00000)
[4294667.296000] Built 1 zonelists
[4294667.296000] Kernel command line: root=/dev/hda1 ro quiet splash noapic nolapic
[4294667.296000] mapped APIC to ffffd000 (01181000)
[4294667.296000] Initializing CPU#0
[4294667.296000] PID hash table entries: 1024 (order: 10, 16384 bytes)
[4294667.296000] Detected 86.708 MHz processor.
[4294667.296000] Using pmtmr for high-res timesource
[4294667.296000] Console: colour VGA+ 80x25
[4294667.896000] Dentry cache hash table entries: 32768 (order: 5, 131072 bytes)
[4294667.900000] Inode-cache hash table entries: 16384 (order: 4, 65536 bytes)
[4294668.052000] Memory: 184116k/196528k available (1976k kernel code, 11872k reserved, 606k data, 288k init, 0k highmem)
[4294668.052000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[4294668.114000] Calibrating delay using timer specific routine.. 168.58 BogoMIPS (lpj=84293)
[4294668.114000] Security Framework v1.0.0 initialized
[4294668.114000] SELinux:  Disabled at boot.
[4294668.115000] Mount-cache hash table entries: 512
[4294668.116000] CPU: After generic identify, caps: 0183f9ff 00000000 00000000 00000000 00000000 00000000 00000000
[4294668.117000] CPU: After vendor identify, caps: 0183f9ff 00000000 00000000 00000000 00000000 00000000 00000000
[4294668.117000] CPU: L1 I cache: 16K, L1 D cache: 16K
[4294668.117000] CPU: L2 cache: 128K
[4294668.117000] CPU: After all inits, caps: 0183f9ff 00000000 00000000 00000040 00000000 00000000 00000000
[4294668.117000] mtrr: v2.0 (20020519)
[4294668.117000] CPU: Intel Celeron (Mendocino) stepping 0a
[4294668.117000] Enabling fast FPU save and restore... done.
[4294668.118000] Checking 'hlt' instruction... OK.
[4294668.125000] checking if image is initramfs... it is
[4294687.884000] Freeing initrd memory: 6837k freed
[4294688.134000] ACPI: Looking for DSDT ... not found!
[4294688.165000] ACPI: setting ELCR to 0200 (from 0820)
[4294688.170000] NET: Registered protocol family 16
[4294688.170000] EISA bus registered
[4294688.170000] ACPI: bus type pci registered
[4294688.173000] PCI: PCI BIOS revision 2.10 entry at 0xfc0ce, last bus=1
[4294688.173000] PCI: Using configuration type 1
[4294688.175000] ACPI: Subsystem revision 20051216
[4294688.227000] ACPI: Interpreter enabled
[4294688.227000] ACPI: Using PIC for interrupt routing
[4294688.236000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[4294688.236000] PCI: Probing PCI hardware (bus 00)
[4294688.239000] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[4294688.312000] PCI quirk: region 0800-083f claimed by PIIX4 ACPI
[4294688.312000] PCI quirk: region 0840-084f claimed by PIIX4 SMB
[4294688.312000] PIIX4 devres B PIO at 00e0-00e7
[4294688.312000] PIIX4 devres C PIO at 0850-085f
[4294688.312000] PIIX4 devres G PIO at 0300-0307
[4294688.312000] Boot video device is 0000:01:00.0
[4294688.313000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[4294688.526000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[4294688.527000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[4294688.529000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[4294688.531000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[4294688.534000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[4294688.539000] ACPI: Power Resource [PADA] (on)
[4294688.541000] Linux Plug and Play Support v0.97 (c) Adam Belay
[4294688.541000] pnp: PnP ACPI init
[4294688.769000] pnp: PnP ACPI: found 15 devices
[4294688.769000] PnPBIOS: Disabled by ACPI PNP
[4294688.769000] PCI: Using ACPI for IRQ routing
[4294688.769000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[4294688.801000] pnp: 00:01: ioport range 0x4d0-0x4d1 has been reserved
[4294688.801000] pnp: 00:01: ioport range 0x800-0x805 could not be reserved
[4294688.801000] pnp: 00:01: ioport range 0x808-0x80f could not be reserved
[4294688.801000] pnp: 00:02: ioport range 0x806-0x807 has been reserved
[4294688.802000] pnp: 00:02: ioport range 0x850-0x853 has been reserved
[4294688.802000] pnp: 00:02: ioport range 0x856-0x85f has been reserved
[4294688.802000] pnp: 00:02: ioport range 0x810-0x83f has been reserved
[4294688.802000] pnp: 00:02: ioport range 0x840-0x84f has been reserved
[4294688.802000] pnp: 00:03: ioport range 0xf400-0xf4fe has been reserved
[4294688.802000] pnp: 00:08: ioport range 0x3f0-0x3f1 has been reserved
[4294688.803000] PCI: Ignore bogus resource 6 [0:0] of 0000:01:00.0
[4294688.803000] PCI: Bridge: 0000:00:01.0
[4294688.803000]   IO window: c000-cfff
[4294688.803000]   MEM window: fd000000-feffffff
[4294688.803000]   PREFETCH window: f8000000-fbffffff
[4294688.803000] PCI: Bus 2, cardbus bridge: 0000:00:03.0
[4294688.803000]   IO window: 00001000-000010ff
[4294688.803000]   IO window: 00001400-000014ff
[4294688.803000]   PREFETCH window: 20000000-21ffffff
[4294688.803000]   MEM window: 22000000-23ffffff
[4294688.803000] PCI: Bus 6, cardbus bridge: 0000:00:03.1
[4294688.803000]   IO window: 00001800-000018ff
[4294688.803000]   IO window: 00001c00-00001cff
[4294688.803000]   PREFETCH window: 24000000-25ffffff
[4294688.803000]   MEM window: 26000000-27ffffff
[4294688.803000] PCI: Enabling device 0000:00:03.0 (0000 -> 0003)
[4294688.803000] **** SET: Misaligned resource pointer: cb9c94e2 Type 07 Len 0
[4294688.804000] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[4294688.805000] PCI: setting IRQ 11 as level-triggered
[4294688.805000] ACPI: PCI Interrupt 0000:00:03.0[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[4294688.805000] PCI: Enabling device 0000:00:03.1 (0000 -> 0003)
[4294688.805000] ACPI: PCI Interrupt 0000:00:03.1[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[4294688.807000] audit: initializing netlink socket (disabled)
[4294688.807000] audit(1149778409.803:1): initialized
[4294688.808000] VFS: Disk quotas dquot_6.5.1
[4294688.808000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[4294688.808000] Initializing Cryptographic API
[4294688.808000] io scheduler noop registered
[4294688.808000] io scheduler anticipatory registered
[4294688.808000] io scheduler deadline registered
[4294688.809000] io scheduler cfq registered
[4294688.809000] Limiting direct PCI/PCI transfers.
[4294688.810000] isapnp: Scanning for PnP cards...
[4294688.902000] isapnp: No Plug & Play device found
[4294689.005000] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[4294689.014000] serio: i8042 AUX port at 0x60,0x64 irq 12
[4294689.015000] serio: i8042 KBD port at 0x60,0x64 irq 1
[4294689.016000] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
[4294689.017000] serial8250: ttyS3 at I/O 0x2e8 (irq = 3) is a 16550A
[4294689.030000] 00:0c: ttyS3 at I/O 0x2e8 (irq = 3) is a 16550A
[4294689.033000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[4294689.033000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[4294689.033000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[4294689.034000] mice: PS/2 mouse device common for all mice
[4294689.036000] EISA: Probing bus 0 at eisa.0
[4294689.036000] Cannot allocate resource for EISA slot 1
[4294689.036000] EISA: Detected 0 cards.
[4294689.037000] NET: Registered protocol family 2
[4294689.047000] IP route cache hash table entries: 2048 (order: 1, 8192 bytes)
[4294689.047000] TCP established hash table entries: 8192 (order: 3, 32768 bytes)
[4294689.048000] TCP bind hash table entries: 8192 (order: 3, 32768 bytes)
[4294689.048000] TCP: Hash tables configured (established 8192 bind 8192)
[4294689.048000] TCP reno registered
[4294689.048000] TCP bic registered
[4294689.048000] NET: Registered protocol family 1
[4294689.048000] NET: Registered protocol family 8
[4294689.048000] NET: Registered protocol family 20
[4294689.048000] Using IPI Shortcut mode
[4294689.049000] ACPI wakeup devices: 
[4294689.049000]  LID PBTN PCI0 UAR1 MPCI 
[4294689.049000] ACPI: (supports S0 S1 S3 S4 S5)
[4294689.049000] Freeing unused kernel memory: 288k freed
[4294689.053000] input: AT Translated Set 2 keyboard as /class/input/input0
[4294689.363000] vga16fb: initializing
[4294689.363000] vga16fb: mapped to 0xc00a0000
[4294689.474000] Console: switching to colour frame buffer device 80x25
[4294689.474000] fb0: VGA16 VGA frame buffer device
[4294690.674000] Capability LSM initialized
[4294690.886000] ACPI: CPU0 (power states: C1[C1] C2[C2])
[4294690.924000] ACPI: Thermal Zone [THM] (37 C)
[4294693.655000] PIIX4: IDE controller at PCI slot 0000:00:07.1
[4294693.655000] PIIX4: chipset revision 1
[4294693.655000] PIIX4: not 100% native mode: will probe irqs later
[4294693.655000]     ide0: BM-DMA at 0x0860-0x0867, BIOS settings: hda:DMA, hdb:pio
[4294693.655000]     ide1: BM-DMA at 0x0868-0x086f, BIOS settings: hdc:DMA, hdd:pio
[4294693.655000] Probing IDE interface ide0...
[4294693.912000] hda: FUJITSU MHH2048AT, ATA DISK drive
[4294694.528000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[4294694.623000] Probing IDE interface ide1...
[4294695.289000] hdc: TEAC CD-ROM CD-224E, ATAPI CD/DVD-ROM drive
[4294695.901000] ide1 at 0x170-0x177,0x376 on irq 15
[4294695.941000] hda: max request size: 128KiB
[4294695.960000] hda: 9514260 sectors (4871 MB) w/512KiB Cache, CHS=10068/15/63, UDMA(33)
[4294695.960000] hda: cache flushes not supported
[4294695.961000]  hda: hda1 hda2 < hda5 >
[4294696.013000] hdc: ATAPI 24X CD-ROM drive, 128kB Cache, UDMA(33)
[4294696.013000] Uniform CD-ROM driver Revision: 3.20
[4294696.741000] usbcore: registered new driver usbfs
[4294696.744000] usbcore: registered new driver hub
[4294696.757000] USB Universal Host Controller Interface driver v2.3
[4294696.760000] ACPI: PCI Interrupt 0000:00:07.2[D] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[4294696.760000] uhci_hcd 0000:00:07.2: UHCI Host Controller
[4294696.762000] uhci_hcd 0000:00:07.2: new USB bus registered, assigned bus number 1
[4294696.762000] uhci_hcd 0000:00:07.2: irq 11, io base 0x0000ece0
[4294696.763000] hub 1-0:1.0: USB hub found
[4294696.764000] hub 1-0:1.0: 2 ports detected
[4294697.141000] Attempting manual resume
[4294697.276000] EXT3-fs: mounted filesystem with ordered data mode.
[4294697.289000] kjournald starting.  Commit interval 5 seconds
[4294697.473000] usb 1-1: new full speed USB device using uhci_hcd and address 2
[4294725.529000] ACPI: PCI Interrupt 0000:00:03.0[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[4294725.529000] Yenta: CardBus bridge found at 0000:00:03.0 [1028:008b]
[4294725.529000] Yenta: Using CSCINT to route CSC interrupts to PCI
[4294725.529000] Yenta: Routing CardBus interrupts to PCI
[4294725.529000] Yenta TI: socket 0000:00:03.0, mfunc 0x01261222, devctl 0x66
[4294725.551000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[4294725.794000] Yenta: ISA IRQ mask 0x04b8, PCI irq 11
[4294725.794000] Socket status: 30000006
[4294725.813000] ACPI: PCI Interrupt 0000:00:03.1[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[4294725.813000] Yenta: CardBus bridge found at 0000:00:03.1 [1028:008b]
[4294725.813000] Yenta: Using CSCINT to route CSC interrupts to PCI
[4294725.813000] Yenta: Routing CardBus interrupts to PCI
[4294725.813000] Yenta TI: socket 0000:00:03.1, mfunc 0x01261222, devctl 0x66
[4294726.036000] Yenta: ISA IRQ mask 0x04b8, PCI irq 11
[4294726.036000] Socket status: 30000006
[4294726.070000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[4294726.152000] Linux agpgart interface v0.101 (c) Dave Jones
[4294726.169000] agpgart: Detected an Intel 440BX Chipset.
[4294726.177000] agpgart: AGP aperture is 64M @ 0xf4000000
[4294727.225000] piix4_smbus 0000:00:07.3: Found 0000:00:07.3 device
[4294728.059000] input: PS/2 Generic Mouse as /class/input/input1
[4294728.467000] Real Time Clock Driver v1.12
[4294728.534000] prism2usb_init: prism2_usb.o: 0.2.2 Loaded
[4294728.534000] prism2usb_init: dev_info is: prism2_usb
[4294728.535000] usbcore: registered new driver prism2_usb
[4294728.792000] input: PC Speaker as /class/input/input2
[4294729.606000] Floppy drive(s): fd0 is 1.44M
[4294729.619000] FDC 0 is a post-1991 82077
[4294731.014000] parport: PnPBIOS parport detected.
[4294731.014000] parport0: PC-style at 0x378 (0x778), irq 7, dma 1 [PCSPP,COMPAT,ECP,DMA]
[4294731.047000] PCI: Enabling device 0000:01:00.1 (0000 -> 0002)
[4294731.047000] **** SET: Misaligned resource pointer: c80bfca2 Type 07 Len 0
[4294731.049000] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 5
[4294731.049000] PCI: setting IRQ 5 as level-triggered
[4294731.049000] ACPI: PCI Interrupt 0000:01:00.1[B] -> Link [LNKB] -> GSI 5 (level, low) -> IRQ 5
[4294731.049000] nm256: found card signature in video RAM: 0x3fec00
[4294731.049000] nm256: Mapping port 1 from 0x3f09a0 - 0x3fec00
[4294731.171000] ts: Compaq touchscreen protocol output
[4294733.190000] hfa384x_usbctlx_complete_sync: CTLX[3] error: state(Request failed)
[4294733.190000] prism2sta_getcardinfo: Failed to retrieve NICIDENTITY
[4294733.190000] prism2sta_getcardinfo: Failed, result=-5
[4294733.190000] prism2sta_ifstate: prism2sta_getcardinfo() failed,result=-5
[4294733.627000] hfa384x_usbin_rx: Received frame on unsupported port=4
[4294737.712000] lp0: using parport0 (interrupt-driven).
[4294738.027000] Adding 232900k swap on /dev/hda5.  Priority:-1 extents:1 across:232900k
[4294738.286000] EXT3 FS on hda1, internal journal
[4294738.943000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[4294738.943000] md: bitmap version 4.39
[4294740.446000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]
[4294741.817000] hdc: packet command error: status=0x51 { DriveReady SeekComplete Error }
[4294741.817000] hdc: packet command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[4294741.817000] ide: failed opcode was: unknown
[4294741.818000] cdrom: open failed.
[4294745.845000] NET: Registered protocol family 17

---

### Post by Ptero-4 on 2006-06-08
By the five last lines in your dmegs. I can tell one of your drives (hdc) seems to be failing the S.M.A.R.T self-tests. You should check your IDE conections and devices.

---

### Post by Jose Catre-Vandis on 2006-06-08
hdc is the cdrom drive, with this Dell its the cassette swappable type. I'll check the connections....and i have a spare cdrom drive so I'll try that too.

Any way I can workaround the SMART self tests, or are these necessary ?

---

### Post by Ptero-4 on 2006-06-11
They are necesary. If the drive fails them it means that the drive is about to stop functioning at all.

---

### Post by drdrgivemethenews on 2006-06-12
I had something similar on my Dell Latitude with 128mb memory.....I solved(!) the problem by switching out of graphic mode to text mode during boot up...i.e. ctrl-alt f1 as soon as the kernal is unpacked...i.e. just before you see the graphic ubuntu logo come up.... any reasons why this should work I would love to hear

I suspect it is to do with the nm256 stuff

---

### Post by Jose Catre-Vandis on 2006-06-13
OK, so what is the nm256 stuff (is this the neomagic stuff)

And how do you permanently boot in text mode, so that I do not have to do keystrokes each time?

---

### Post by hayalci on 2006-06-17
[QUOTE=Jose Catre-Vandis]

And how do you permanently boot in text mode, so that I do not have to do keystrokes each time?[/QUOTE]

Remove the "splash" options on "kernel" lines in /boot/grub/menu.lst
But if you want the setting to be protected during updates, change the comment lines above the kernel list ( Do not uncomment the line, just remove "splash" option)

```

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet *****splash*****
.......
title           Ubuntu, kernel 2.6.15-23-386
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.15-23-386 root=/dev/hda3 ro quiet *****splash*****
initrd          /boot/initrd.img-2.6.15-23-386
savedefault
boot

```

---

### Post by Jose Catre-Vandis on 2006-06-18
[QUOTE=drdrgivemethenews]I had something similar on my Dell Latitude with 128mb memory.....I solved(!) the problem by switching out of graphic mode to text mode during boot up...i.e. ctrl-alt f1 as soon as the kernal is unpacked...i.e. just before you see the graphic ubuntu logo come up.... any reasons why this should work I would love to hear[/QUOTE]


Well going text mode has certainly improved things, especially on reboot. Still hangs on a cold boot though. I sense it is my USB wlan device that is causing the problem, so I'll have to figure out how to stop xubuntu trying to load the drivers during boot.

Thanks also for the advice on editing to the boot parameters, this works fine

---

### Post by cronholio on 2006-06-18
Might be related to this bug that is still unfixed:

[http://www.ubuntuforums.org/showthread.php?t=167722](http://www.ubuntuforums.org/showthread.php?t=167722)

---

### Post by Jose Catre-Vandis on 2006-06-20
At least I am not alone :-)

---

### Post by DuMu on 2006-06-25
[QUOTE=Jose Catre-Vandis]At least I am not alone :-)[/QUOTE]
Hi, I've been puzzling over this all weekend.  I also have a Dell Latitude CPi notebook PC (A336XT Pentium II 336MHz 256MB mem 20GB HDD).

I am trying to set up a dual boot on it with Windows 2000 (already there) and a fresh install of Xubuntu 6.06 on the other partition.  

It has been a trial reading through pages and pages of posts from people with all kinds of PCs having similar problems.  I finally burnt a CD of the Xubuntu _alternate_ install disk (making this my fourth different CD version of Dapper Drake!).  

I ran a text install, but first pressed F6 and added "ide=nodma" to the end of the options.  (This is mentioned elsewhere in the forums as a possible fix).  I'm currently up to installing the base system, which is a lot further than I got so far - before I only got as far as this with 5.04.  

I'll let you know if it stops working anywhere.  I'm really glad not to be the only person trying to put U/Xu 6.06 on a Dell Latitude CPi!

---

### Post by penvzila on 2007-05-06
I have this problem on my laptop with Edgy.  Basically have to turn it on, wait for it to hang on "loading manual drivers", then off, then on again or it won't boot.

---

