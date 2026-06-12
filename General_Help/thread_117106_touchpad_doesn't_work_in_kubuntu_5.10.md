---
title: "touchpad doesn't work in kubuntu 5.10"
date: 2006-01-14
forum: General Help
---

### Post by STiKi on 2006-01-14
Hello I got a big problem. 
I got an ACER Travelmate 2400 with installed Kubuntu 5.10. 
Everything worked fine to the moment when the system stopped responding on any actions and I had to turned it on "manually" (I've just   pressed POWER instead of closing system). After reboot touchpad stopped working. I use an usb mouse when I'm home but I would like also to use touchpad when I'm somewhere else. I've spent hours on google and I didn't find anything. I got touchpad in xorg.conf:```
Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizScrollDelta"      "0"
EndSection

``` and I got also the synaptics package. Could anybody please help me?

I must go to other town today's evening so it'll be nice to now it today ;-)

---

### Post by ikarus9999 on 2006-01-14
Hi

Could you check the X logfile for any error messages regarding the touchpad?

cat /var/log/Xorg.0.log | grep synaptics

You should see something like this:

(II) LoadModule: "synaptics"
(II) Loading /usr/X11R6/lib/modules/input/synaptics_drv.o
(II) Module synaptics: vendor="The XFree86 Project"
(--) Synaptics Touchpad synaptics touchpad found
(--) Synaptics Touchpad synaptics touchpad found
(--) Synaptics Touchpad synaptics touchpad found
(--) Synaptics Touchpad synaptics touchpad found
(--) Synaptics Touchpad synaptics touchpad found


Please post your output if it looks different.

---

### Post by STiKi on 2006-01-14
My output looks like this:
stiki@apofis:~$ cat /var/log/Xorg.0.log | grep synaptics
(II) LoadModule: "synaptics"
(II) Loading /usr/X11R6/lib/modules/input/synaptics_drv.o
(II) Module synaptics: vendor="The XFree86 Project"
Synaptics Touchpad no synaptics event device found (checked 4 nodes)
(EE) Synaptics Touchpad no synaptics touchpad detected and no repeater device
(II) UnloadModule: "synaptics"

---

### Post by ikarus9999 on 2006-01-14
It seems like the event module is not loaded.
Try adding 'evdev' (without the quotes)  into '/etc/modules' and reboot.
This should work.

---

### Post by STiKi on 2006-01-14
I did it and nothing happend :/ Touchpad don't work as it did before.
I did a 'cat /var/log/Xorg.0.log | grep synaptics' and it looks like this:
(II) LoadModule: "synaptics"
(II) Loading /usr/X11R6/lib/modules/input/synaptics_drv.o
(II) Module synaptics: vendor="X.Org Foundation"
Synaptics Touchpad no synaptics event device found (checked 4 nodes)
(EE) Synaptics Touchpad no synaptics touchpad detected and no repeater device
(II) UnloadModule: "synaptics"

---

### Post by ikarus9999 on 2006-01-14
That's strange.

Could you probably post the output of 'dmesg'

---

### Post by STiKi on 2006-01-14
Here it is:
```
94672.038000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[4294672.038000] PCI: Probing PCI hardware (bus 00)
[4294672.038000] ACPI: Assume root bridge [\_SB_.PCI0] segment is 0
[4294672.061000] Boot video device is 0000:00:02.0
[4294672.061000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:1f.1
[4294672.062000] PCI: Transparent bridge - 0000:00:1e.0
[4294672.071000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[4294672.073000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[4294672.074000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[4294672.075000] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5http://www.google.pl/ 6 7 10 12 14 15) *11
[4294672.076000] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 *5 6 7 11 12 14 15)
[4294672.076000] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[4294672.076000] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[4294672.076000] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[4294672.077000] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[4294672.077000] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[4294672.077000] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[4294672.077000] burst-mode-ec-10-Aug
[4294672.077000] ACPI: Embedded Controller [EC0] (gpe 29)
[4294672.126000] Linux Plug and Play Support v0.97 (c) Adam Belay
[4294672.126000] pnp: PnP ACPI init
[4294672.151000] pnp: PnP ACPI: found 9 devices
[4294672.151000] PnPBIOS: Disabled by ACPI PNP
[4294672.151000] PCI: Using ACPI for IRQ routing
[4294672.151000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[4294672.160000] audit: initializing netlink socket (disabled)
[4294672.160000] audit: initialized
[4294672.160000] VFS: Disk quotas dquot_6.5.1
[4294672.160000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[4294672.160000] devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
[4294672.160000] devfs: boot_options: 0x0
[4294672.160000] Initializing Cryptographic API
[4294672.160000] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 5
[4294672.160000] PCI: setting IRQ 5 as level-triggered
[4294672.160000] ACPI: PCI Interrupt 0000:00:1c.0[A] -> Link [LNKB] -> GSI 5 (level, low) -> IRQ 5
[4294672.160000] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[4294672.161000] assign_interrupt_mode Found MSI capability
[4294672.161000] Allocate Port Service[pcie00]
[4294672.161000] Allocate Port Service[pcie02]
[4294672.161000] Allocate Port Service[pcie03]
[4294672.161000] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 10
[4294672.161000] PCI: setting IRQ 10 as level-triggered
[4294672.161000] ACPI: PCI Interrupt 0000:00:1c.1[B] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10
[4294672.161000] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[4294672.161000] assign_interrupt_mode Found MSI capability
[4294672.161000] Allocate Port Service[pcie00]
[4294672.161000] Allocate Port Service[pcie02]
[4294672.161000] Allocate Port Service[pcie03]
[4294672.161000] isapnp: Scanning for PnP cards...
[4294672.514000] isapnp: No Plug & Play device found
[4294672.531000] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2E] at 0x60,0x64 irq 1,12
[4294672.532000] i8042.c: Detected active multiplexing controller, rev 1.1.
[4294672.532000] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[4294672.532000] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[4294672.532000] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[4294672.532000] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[4294672.532000] serio: i8042 KBD port at 0x60,0x64 irq 1
[4294672.532000] Serial: 8250/16550 driver $Revision: 1.90 $ 54 ports, IRQ sharing enabled
[4294672.534000] ACPI: PCI Interrupt Link [LNKE] enabled at IRQ 10
[4294672.534000] ACPI: PCI Interrupt 0000:00:1e.3[B] -> Link [LNKE] -> GSI 10 (level, low) -> IRQ 10
[4294672.534000] ACPI: PCI interrupt for device 0000:00:1e.3 disabled
[4294672.534000] io scheduler noop registered
[4294672.534000] io scheduler anticipatory registered
[4294672.534000] io scheduler deadline registered
[4294672.534000] io scheduler cfq registered
[4294672.534000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[4294672.535000] EISA: Probing bus 0 at eisa.0
[4294672.535000] Cannot allocate resource for EISA slot 1
[4294672.535000] EISA: Detected 0 cards.
[4294672.535000] NET: Registered protocol family 2
[4294672.544000] IP: routing cache hash table of 2048 buckets, 16Kbytes
[4294672.544000] TCP established hash table entries: 8192 (order: 4, 65536 bytes)
[4294672.544000] TCP bind hash table entries: 8192 (order: 3, 32768 bytes)
[4294672.544000] TCP: Hash tables configured (established 8192 bind 8192)
[4294672.544000] NET: Registered protocol family 8
[4294672.544000] NET: Registered protocol family 20
[4294672.544000] ACPI wakeup devices: 
[4294672.544000] AZAL RP02 RP03 RP04 USB1 USB2 USB3 USB4 USB7 ELAN MODM 
[4294672.544000] ACPI: (supports S0 S3 S4 S5)
[4294672.544000] Freeing unused kernel memory: 224k freed
[4294672.556000] vga16fb: initializing
[4294672.556000] vga16fb: mapped to 0xc00a0000
[4294672.696000] Console: switching to colour frame buffer device 80x30
[4294672.696000] fb0: VGA16 VGA frame buffer device
[4294673.140000] input: AT Translated Set 2 keyboard on isa0060/serio0
[4294673.812000] Capability LSM initialized
[4294673.822000] NET: Registered protocol family 1
[4294673.836000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[4294673.836000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[4294673.836000] ACPI: bus type ide registered
[4294673.840000] ICH6: IDE controller at PCI slot 0000:00:1f.1
[4294673.841000] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 10
[4294673.841000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> Link [LNKC] -> GSI 10 (level, low) -> IRQ 10
[4294673.841000] ICH6: chipset revision 4
[4294673.841000] ICH6: not 100% native mode: will probe irqs later
[4294673.841000]     ide0: BM-DMA at 0x1100-0x1107, BIOS settings: hda:DMA, hdb:DMA
[4294673.841000] Probing IDE interface ide0...
[4294674.104000] hda: TOSHIBA MK4025GAS, ATA DISK drive
[4294674.512000] hdb: Slimtype DVDRW SOSW-833S, ATAPI CD/DVD-ROM drive
[4294674.563000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[4294674.563000] Probing IDE interface ide1...
[4294675.076000] Probing IDE interface ide2...
[4294675.588000] Probing IDE interface ide3...
[4294676.100000] Probing IDE interface ide4...
[4294676.612000] Probing IDE interface ide5...
[4294677.127000] hda: max request size: 128KiB
[4294677.176000] hda: 78140160 sectors (40007 MB), CHS=65535/16/63, UDMA(100)
[4294677.176000] hda: cache flushes supported
[4294677.176000]  /dev/ide/host0/bus0/target0/lun0: p1 p2 < p5 >
[4294677.228000] hdb: ATAPI 24X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache
[4294677.228000] Uniform CD-ROM driver Revision: 3.20
[4294677.434000] Attempting manual resume
[4294677.438000] swsusp: Suspend partition has wrong signature?
[4294677.483000] usbcore: registered new driver usbfs
[4294677.483000] usbcore: registered new driver hub
[4294677.484000] USB Universal Host Controller Interface driver v2.2
[4294677.485000] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 11
[4294677.485000] PCI: setting IRQ 11 as level-triggered
[4294677.485000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> Link [LNKH] -> GSI 11 (level, low) -> IRQ 11
[4294677.485000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[4294677.485000] uhci_hcd 0000:00:1d.0: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1
[4294677.547000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[4294677.547000] uhci_hcd 0000:00:1d.0: irq 11, io base 0x00001200
[4294677.547000] hub 1-0:1.0: USB hub found
[4294677.547000] hub 1-0:1.0: 2 ports detected
[4294677.550000] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[4294677.550000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[4294677.550000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[4294677.550000] uhci_hcd 0000:00:1d.1: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2
[4294677.612000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[4294677.612000] uhci_hcd 0000:00:1d.1: irq 11, io base 0x00001220
[4294677.612000] hub 2-0:1.0: USB hub found
[4294677.612000] hub 2-0:1.0: 2 ports detected
[4294677.615000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> Link [LNKC] -> GSI 10 (level, low) -> IRQ 10
[4294677.615000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[4294677.615000] uhci_hcd 0000:00:1d.2: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3
[4294677.677000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[4294677.677000] uhci_hcd 0000:00:1d.2: irq 10, io base 0x00001240
[4294677.677000] hub 3-0:1.0: USB hub found
[4294677.677000] hub 3-0:1.0: 2 ports detected
[4294677.680000] ACPI: PCI Interrupt 0000:00:1d.3[D] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10
[4294677.680000] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[4294677.680000] uhci_hcd 0000:00:1d.3: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4
[4294677.716000] usb 1-1: new low speed USB device using uhci_hcd and address 2
[4294677.742000] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[4294677.742000] uhci_hcd 0000:00:1d.3: irq 10, io base 0x00001260
[4294677.742000] hub 4-0:1.0: USB hub found
[4294677.742000] hub 4-0:1.0: 2 ports detected
[4294677.775000] PCI: Enabling device 0000:00:1d.7 (0000 -> 0002)
[4294677.775000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> Link [LNKH] -> GSI 11 (level, low) -> IRQ 11
[4294677.775000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[4294677.775000] ehci_hcd 0000:00:1d.7: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller
[4294677.775000] ehci_hcd 0000:00:1d.7: debug port 1
[4294677.775000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[4294677.775000] ehci_hcd 0000:00:1d.7: irq 11, io mem 0x0f800000
[4294677.779000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[4294677.779000] ehci_hcd 0000:00:1d.7: USB 2.0 initialized, EHCI 1.00, driver 10 Dec 2004
[4294677.779000] hub 5-0:1.0: USB hub found
[4294677.779000] hub 5-0:1.0: 8 ports detected
[4294677.852000] b44.c:v0.95 (Aug 3, 2004)
[4294677.852000] ACPI: PCI Interrupt Link [LNKF] enabled at IRQ 11
[4294677.852000] ACPI: PCI Interrupt 0000:05:01.0[A] -> Link [LNKF] -> GSI 11 (level, low) -> IRQ 11
[4294677.855000] eth0: Broadcom 4400 10/100BaseT Ethernet 00:0f:b0:7f:5e:35
[4294678.194000] usb 1-1: device not accepting address 2, error -71
[4294678.716000] usb 1-1: new low speed USB device using uhci_hcd and address 4
[4294679.887000] usbcore: registered new driver hiddev
[4294679.907000] input: USB HID v1.10 Mouse [PS/2+USB Mouse] on usb-0000:00:1d.0-1
[4294679.907000] usbcore: registered new driver usbhid
[4294679.907000] drivers/usb/input/hid-core.c: v2.01:USB HID core driver
[4294680.240000] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[4294680.240000] ACPI: Processor [CPU0] (supports 8 throttling states)
[4294680.446000] Attempting manual resume
[4294680.471000] swsusp: Suspend partition has wrong signature?
[4294680.515000] kjournald starting.  Commit interval 5 seconds
[4294680.515000] EXT3-fs: mounted filesystem with ordered data mode.
[4294682.065000] md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
[4294685.472000] Adding 730916k swap on /dev/hda5.  Priority:-1 extents:1
[4294685.747000] EXT3 FS on hda1, internal journal
[4294693.030000] lp: driver loaded but no devices found
[4294693.057000] mice: PS/2 mouse device common for all mice
[4294693.438000] logips2pp: Detected unknown logitech mouse model 99
[4294693.526000] input: ImPS/2 Logitech Wheel Mouse on isa0060/serio4
[4294694.050000] ts: Compaq touchscreen protocol output
[4294696.385000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: dm-devel@redhat.com
[4294697.425000] hdb: packet command error: status=0x51 { DriveReady SeekComplete Error }
[4294697.425000] hdb: packet command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[4294697.425000] ide: failed opcode was: unknown
[4294697.425000] cdrom: open failed.
[4294700.167000] Linux agpgart interface v0.101 (c) Dave Jones
[4294700.175000] agpgart: Detected an Intel 915GM Chipset.
[4294700.176000] agpgart: Detected 7932K stolen memory.
[4294700.208000] agpgart: AGP aperture is 256M @ 0xa0000000
[4294700.311000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[4294700.344000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[4294700.684000] hw_random hardware driver 1.0.0 loaded
[4294700.845000] ACPI: PCI Interrupt 0000:00:1e.2[A] -> Link [LNKB] -> GSI 5 (level, low) -> IRQ 5
[4294700.845000] PCI: Setting latency timer of device 0000:00:1e.2 to 64
[4294701.654000] intel8x0_measure_ac97_clock: measured 49463 usecs
[4294701.654000] intel8x0: clocking to 48000
[4294703.042000] Linux Kernel Card Services
[4294703.042000]   options:  [pci] [cardbus] [pm]
[4294703.054000] ACPI: PCI Interrupt 0000:05:04.0[A] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10
[4294703.054000] Yenta: CardBus bridge found at 0000:05:04.0 [1025:0081]
[4294703.054000] Yenta: Using CSCINT to route CSC interrupts to PCI
[4294703.054000] Yenta: Routing CardBus interrupts to PCI
[4294703.054000] Yenta TI: socket 0000:05:04.0, mfunc 0x00501212, devctl 0x44
[4294703.275000] Yenta: ISA IRQ mask 0x00d8, PCI irq 10
[4294703.275000] Socket status: 30000006
[4294704.757000] Real Time Clock Driver v1.12
[4294706.425000] NET: Registered protocol family 17
[4294707.412000] b44: eth0: Link is down.
[4294709.412000] b44: eth0: Link is up at 100 Mbps, full duplex.
[4294709.412000] b44: eth0: Flow control is on for TX and on for RX.
[4294784.511000] NET: Registered protocol family 10
[4294784.511000] Disabled Privacy Extensions on device c02eb280(lo)
[4294784.513000] IPv6 over IPv4 tunneling driver
[4294786.438000] ACPI: AC Adapter [ACAD] (on-line)
[4294786.616000] ACPI: Battery Slot [BAT1] (battery present)
[4294786.635000] ACPI: Power Button (FF) [PWRF]
[4294786.635000] ACPI: Lid Switch [LID0]
[4294786.635000] ACPI: Power Button (CM) [PWRB]
[4294786.635000] ACPI: Sleep Button (CM) [SLPB]
[4294786.739000] ibm_acpi: ec object not found
[4294786.853000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[4294786.853000] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[4294792.597000] apm: BIOS not found.
[4294793.153000] cs: IO port probe 0x100-0x4ff: excluding 0x4d0-0x4d7
[4294793.156000] cs: IO port probe 0xc00-0xcf7: clean.
[4294793.157000] cs: IO port probe 0xa00-0xaff: clean.
[4294793.839000] Bluetooth: Core ver 2.7
[4294793.839000] NET: Registered protocol family 31
[4294793.839000] Bluetooth: HCI device and connection manager initialized
[4294793.839000] Bluetooth: HCI socket layer initialized
[4294793.985000] Bluetooth: L2CAP ver 2.7
[4294793.985000] Bluetooth: L2CAP socket layer initialized
[4294794.017000] Bluetooth: RFCOMM ver 1.5
[4294794.017000] Bluetooth: RFCOMM socket layer initialized
[4294794.017000] Bluetooth: RFCOMM TTY layer initialized
[4294795.160000] eth0: no IPv6 routers present
[4294795.700000] [drm] Initialized drm 1.0.0 20040925
[4294795.710000] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10
[4294795.717000] [drm] Initialized i915 1.2.0 20040405 on minor 0: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller
[4294795.717000] mtrr: base(0xa0020000) is not aligned on a size(0x640000) boundary

```

---

### Post by ikarus9999 on 2006-01-14
Are you starting your laptop with the usb mouse attached?
Have you tried to unplug the mouse before you start your laptop?

---

### Post by STiKi on 2006-01-14
Yes, I did. 
It does not work even when mouse is unplugged.

---

### Post by ikarus9999 on 2006-01-14
Well then I'm clueless

sorry

---

### Post by STiKi on 2006-01-14
Last question:
I've found somewhere on that forum that I should install xserver-xorg-input-synaptics instead of xorg-driver-synaptics, but when I do that the system has problems:
```
stiki@apofis:~/Desktop$ sudo dpkg -i xserver-xorg-input-synaptics_0.14.3+seriouslythistime-0ubuntu2_i386.deb
Zaznaczenie poprzednio niezaznaczonego pakietu xserver-xorg-input-synaptics.
(Odczytywanie bazy danych ... 82225 plik&#243;w i katalog&#243;w obecnie zainstalowanych.)
Rozpakowanie xserver-xorg-input-synaptics (z xserver-xorg-input-synaptics_0.14.3+seriouslythistime-0ubuntu2_i386.deb) ...
dpkg: problemy z zale&#380;no&#347;ciami uniemo&#380;liwiaj&#261; skonfigurowanie xserver-xorg-input-synaptics:
 xserver-xorg-input-synaptics zale&#380;y od xserver-xorg-core (>= 1:0.99.0-1); jednak&#380;e:
  Wersja xserver-xorg-core w systemie to 6.8.2-77.
dpkg: b&#322;&#261;d przetwarzania xserver-xorg-input-synaptics (--install):
 problemy z zale&#380;no&#347;ciami - pozostawiony nieskonfigurowany
Wyst&#261;pi&#322;y b&#322;&#281;dy podczas przetwarzania:
 xserver-xorg-input-synaptics


```

---

