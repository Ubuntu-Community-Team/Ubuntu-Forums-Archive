---
title: "gnome-appearance-properites segfaults"
date: 2008-03-04
forum: Desktop Environments
---

### Post by redgsturbo on 2008-03-04
as the title says, it keeps segfaulting.  Among other things, it seems to cause the appearances applet to fail to load previews of the theme/theme elements, and my desktop icons for cd's seem to be absent.  occasionally, the gnome panels become unresponsive... a ctrl-alt-backspace results in a panel-less desktop, and a hard reboot brings them back.  Note that I am using hardy alpha5 as I needed 2.6.24 flavor kernels so I'm just seeing if someone knows an easy fix.  below is some syslog output upon boot.  While we're at it, what is the message handler not found junk about? Cheers :)

```
Mar  4 15:08:10 hades kernel: [  415.278657] EXT3-fs: dm-1: orphan cleanup on readonly fs
Mar  4 15:08:10 hades kernel: [  415.278684] EXT3-fs: dm-1: 1 orphan inode deleted
Mar  4 15:08:10 hades kernel: [  415.278685] EXT3-fs: recovery complete.
Mar  4 15:08:10 hades kernel: [  415.300585] EXT3-fs: mounted filesystem with ordered data mode.
Mar  4 15:08:10 hades kernel: [  422.297637] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Mar  4 15:08:10 hades kernel: [  422.329719] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Mar  4 15:08:10 hades kernel: [  422.390866] iTCO_vendor_support: vendor-support=0
Mar  4 15:08:10 hades kernel: [  422.412213] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
Mar  4 15:08:10 hades kernel: [  422.517594] agpgart: Detected an Intel 945GM Chipset.
Mar  4 15:08:10 hades kernel: [  422.519352] agpgart: Detected 7932K stolen memory.
Mar  4 15:08:10 hades kernel: [  422.534728] agpgart: AGP aperture is 256M @ 0xd0000000
Mar  4 15:08:10 hades kernel: [  422.610707] ACPI: AC Adapter [AC] (on-line)
Mar  4 15:08:10 hades kernel: [  422.676739] ACPI: Battery Slot [BAT0] (battery present)
Mar  4 15:08:10 hades kernel: [  422.676785] ACPI: Battery Slot [BAT1] (battery absent)
Mar  4 15:08:10 hades kernel: [  422.681014] input: Lid Switch as /devices/virtual/input/input2
Mar  4 15:08:10 hades kernel: [  422.714017] ACPI: Lid Switch [LID]
Mar  4 15:08:10 hades kernel: [  422.714072] input: Power Button (CM) as /devices/virtual/input/input3
Mar  4 15:08:10 hades kernel: [  422.765796] ACPI: Power Button (CM) [PBTN]
Mar  4 15:08:10 hades kernel: [  422.765847] input: Sleep Button (CM) as /devices/virtual/input/input4
Mar  4 15:08:10 hades kernel: [  422.821799] ACPI: Sleep Button (CM) [SBTN]
Mar  4 15:08:10 hades kernel: [  422.821910] ACPI: WMI-Acer: Mapper loaded
Mar  4 15:08:10 hades kernel: [  422.822489] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:01/input/input5
Mar  4 15:08:10 hades kernel: [  422.869700] input: PS/2 Mouse as /devices/virtual/input/input6
Mar  4 15:08:10 hades kernel: [  422.885703] ACPI: Video Device [VID1] (multi-head: yes  rom: no  post: no)
Mar  4 15:08:10 hades kernel: [  422.885837] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:02/input/input7
Mar  4 15:08:10 hades kernel: [  422.908556] Yenta: CardBus bridge found at 0000:03:01.0 [1028:01c2]
Mar  4 15:08:10 hades kernel: [  422.908582] Yenta O2: res at 0x94/0xD4: 00/ea
Mar  4 15:08:10 hades kernel: [  422.908583] Yenta O2: enabling read prefetch/write burst
Mar  4 15:08:10 hades kernel: [  422.949552] ACPI: Video Device [VID2] (multi-head: yes  rom: no  post: no)
Mar  4 15:08:10 hades kernel: [  423.033223] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio1/input/input8
Mar  4 15:08:10 hades kernel: [  423.038465] Yenta: ISA IRQ mask 0x0cb8, PCI irq 18
Mar  4 15:08:10 hades kernel: [  423.038469] Socket status: 30000006
Mar  4 15:08:10 hades kernel: [  423.038471] Yenta: Raising subordinate bus# of parent bus (#03) from #04 to #07
Mar  4 15:08:10 hades kernel: [  423.083194] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
Mar  4 15:08:10 hades kernel: [  423.085489] iTCO_wdt: Found a ICH7-M TCO device (Version=2, TCOBASE=0x1060)
Mar  4 15:08:10 hades kernel: [  423.085527] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
Mar  4 15:08:10 hades kernel: [  423.393679] b43-phy0: Broadcom 4311 WLAN found
Mar  4 15:08:10 hades kernel: [  423.447459] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 21 (level, low) -> IRQ 21
Mar  4 15:08:10 hades kernel: [  428.526377] loop: module loaded
Mar  4 15:08:10 hades kernel: [  428.559864] lp: driver loaded but no devices found
Mar  4 15:08:10 hades kernel: [  428.693457] Adding 2428920k swap on /dev/mapper/hades-swap_1.  Priority:-1 extents:1 across:2428920k
Mar  4 15:08:10 hades kernel: [  426.197259] EXT3 FS on dm-1, internal journal
Mar  4 15:08:10 hades kernel: [  430.149952] kjournald starting.  Commit interval 5 seconds
Mar  4 15:08:10 hades kernel: [  427.068013] EXT3 FS on sda1, internal journal
Mar  4 15:08:10 hades kernel: [  427.068017] EXT3-fs: mounted filesystem with ordered data mode.
Mar  4 15:08:10 hades kernel: [  427.521967] ip_tables: (C) 2000-2006 Netfilter Core Team
Mar  4 15:08:10 hades kernel: [  428.410688] ACPI: ACPI Dock Station Driver 
Mar  4 15:08:10 hades kernel: [  428.416722] ACPI: Bay [\_SB_.PCI0.IDE0.SEC0.MAST] Added
Mar  4 15:08:11 hades kernel: [  429.686720] NET: Registered protocol family 10
Mar  4 15:08:11 hades kernel: [  429.686935] lo: Disabled Privacy Extensions
Mar  4 15:08:11 hades kernel: [  432.869990] ppdev: user-space parallel port driver
Mar  4 15:08:11 hades kernel: [  430.097028] audit(1204661291.721:2): operation="inode_permission" request_mask="a::" denied_mask="a::" name="/dev/tty" pid=5252 profile="/usr/sbin/cupsd" namespace="default"
Mar  4 15:08:11 hades dhcdbd: Started up.
Mar  4 15:08:13 hades kernel: [  431.770087] ADDRCONF(NETDEV_UP): eth0: link is not ready
Mar  4 15:08:13 hades kernel: [  434.947847] Bluetooth: Core ver 2.11
Mar  4 15:08:13 hades kernel: [  434.947985] NET: Registered protocol family 31
Mar  4 15:08:13 hades kernel: [  434.947989] Bluetooth: HCI device and connection manager initialized
Mar  4 15:08:13 hades kernel: [  434.947994] Bluetooth: HCI socket layer initialized
Mar  4 15:08:13 hades kernel: [  431.874426] input: b43-phy0 as /devices/virtual/input/input9
Mar  4 15:08:13 hades kernel: [  434.991124] Bluetooth: L2CAP ver 2.9
Mar  4 15:08:13 hades kernel: [  434.991133] Bluetooth: L2CAP socket layer initialized
Mar  4 15:08:13 hades kernel: [  435.089060] Bluetooth: RFCOMM socket layer initialized
Mar  4 15:08:13 hades kernel: [  435.089075] Bluetooth: RFCOMM TTY layer initialized
Mar  4 15:08:13 hades kernel: [  435.089077] Bluetooth: RFCOMM ver 1.8
Mar  4 15:08:14 hades kernel: [  436.201862] Registered led device: b43-phy0:tx
Mar  4 15:08:14 hades kernel: [  436.201889] Registered led device: b43-phy0:rx
Mar  4 15:08:14 hades kernel: [  436.201910] Registered led device: b43-phy0:radio
Mar  4 15:08:14 hades kernel: [  433.113775] b43-phy0: Radio hardware status changed to DISABLED
Mar  4 15:08:14 hades kernel: [  436.207382] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Mar  4 15:08:14 hades kernel: [  436.377118] b43-phy0: Radio turned on by software
Mar  4 15:08:14 hades kernel: [  436.377127] b43-phy0: The hardware RF-kill button still turns the radio physically off. Press the button to turn it on.
Mar  4 15:08:14 hades kernel: [  433.299709] tg3: eth0: Link is up at 100 Mbps, full duplex.
Mar  4 15:08:14 hades kernel: [  433.299717] tg3: eth0: Flow control is on for TX and on for RX.
Mar  4 15:08:14 hades kernel: [  433.305557] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Mar  4 15:08:14 hades dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Mar  4 15:08:16 hades pcscd: pcscdaemon.c:513:main() pcsc-lite 1.4.99 daemon ready.
Mar  4 15:08:16 hades pcscd: hotplug_libusb.c:478:HPAddHotPluggable() Adding USB device: 005:004
Mar  4 15:08:16 hades pcscd: readerfactory.c:1116:RFInitializeReader() Attempting startup of O2 Micro Oz776 00 00 using /usr/lib/pcsc/drivers/ifd-ccid.bundle/Contents/Linux/libccid.so.1.3.1
Mar  4 15:08:16 hades pcscd: readerfactory.c:983:RFBindFunctions() Loading IFD Handler 3.0
Mar  4 15:08:16 hades pcscd: ifdhandler.c:1239:init_driver() LogLevel: 0x0003
Mar  4 15:08:16 hades pcscd: ifdhandler.c:1249:init_driver() DriverOptions: 0x0000
Mar  4 15:08:16 hades pcscd: ifdhandler.c:77:IFDHCreateChannelByName() lun: 0, device: usb:0b97/7762:libusb:005:004
Mar  4 15:08:16 hades pcscd: ccid_usb.c:233:OpenUSBByName() Manufacturer: Ludovic Rousseau (ludovic.rousseau@free.fr)
Mar  4 15:08:16 hades pcscd: ccid_usb.c:243:OpenUSBByName() ProductString: Generic CCID driver v1.3.1
Mar  4 15:08:16 hades pcscd: ccid_usb.c:249:OpenUSBByName() Copyright: This driver is protected by terms of the GNU Lesser General Public License version 2.1, or (at your option) any later version.
Mar  4 15:08:16 hades pcscd: ccid_usb.c:397:OpenUSBByName() Found Vendor/Product: 0B97/7762 (O2 Micro Oz776)
Mar  4 15:08:16 hades pcscd: ccid_usb.c:399:OpenUSBByName() Using USB bus/device: 005/004
Mar  4 15:08:16 hades pcscd: ccid_usb.c:788:get_data_rates() declared: 9600 bps
Mar  4 15:08:16 hades pcscd: ifdhandler.c:841:IFDHPowerICC() lun: 0, action: PowerUp
Mar  4 15:08:17 hades kernel: [  438.567292] NET: Registered protocol family 17
Mar  4 15:08:17 hades kernel: [  439.227168] [drm] Initialized drm 1.1.0 20060810
Mar  4 15:08:17 hades kernel: [  439.232311] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
Mar  4 15:08:17 hades kernel: [  439.232406] [drm] Initialized i915 1.6.0 20060119 on minor 0
Mar  4 15:08:18 hades pcscd: Card ATR: 3B 95 95 40 FF AE 01 03 00 00 
Mar  4 15:08:18 hades pcscd: ifdhandler.c:271:IFDHGetCapabilities() lun: 0, tag: 0xFAE
Mar  4 15:08:18 hades pcscd: ifdhandler.c:313:IFDHGetCapabilities() Reader supports 1 slot(s)
Mar  4 15:08:19 hades dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.host_name
Mar  4 15:08:19 hades dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
Mar  4 15:08:19 hades dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers
Mar  4 15:09:24 hades kernel: [  506.302949] gnome-appearanc[6262]: segfault at 88 rip 7f5370e35686 rsp 7fff7b2c32b0 error 4

```

---

### Post by glhewett on 2008-03-06
I am having the same issues.  I get a slightly different error, though.

```

Mar  6 16:18:20 greg-laptop kernel: [ 7531.724055] gnome-appearanc[12171]: segfault at 00002b9ded1a86e0 rip 00002b9ded1a86e0 rsp 00007fffca4ec7d8 error 14

```

---

