---
title: "Latitude E6500 Built-in Modem Isn't Detected"
date: 2012-01-12
forum: Dell Ubuntu Support (CLOSED)
---

### Post by johnathanamber on 2012-01-12
Hey everyone,

I've recently removed Windows 7 Professional and installed Xubuntu 11.10 64bit.

I did this for several reasons:
-Tired of having to deal with Windows slowness after about 6-9 months of consistent use.
-It is easier to run Windows from within a VM and to replace that VM instead of reinstalling Windows.
-Windows 7 was 32 bit and I wanted to use the rest of my memory.

So that's the background.

When in Windows I was able to use the modem that was built-in. However, I am not able to detect the modem in Xubuntu.

I've already installed gnome-ppp and the modem is not detected.

I've even plugged in a USB 3Com modem, my spare, and that isn't even displayed.

lspci shows the following:
> 00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:19.0 Ethernet controller: Intel Corporation 82567LM Gigabit Network Connection (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M-E LPC Interface Controller (rev 03)
00:1f.2 RAID bus controller: Intel Corporation Mobile 82801 SATA RAID Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
03:01.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ba)
03:01.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 04)
03:01.2 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 21)
0c:00.0 Network controller: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller (rev 01)

Is there a way to setup or detect the modems?

At the very least I need to get these passed through to the VM, either Virtualbox or Vmware Player.

Any ideas?

Thank you and God bless,
Johnathan

---

### Post by johnathanamber on 2012-01-12
Hello again,

I've installed hwinfo and it does see the USB modem, but not the built in. I am still not able to detect it using gnome-ppp. Trying to see if I can get it working in VB or VMware...

I've inserted the modem specific information below:
```
  usb device: name = 6-2:1.0
    path = /devices/pci0000:00/0000:00:1d.0/usb6/6-2/6-2:1.0
    modalias = "usb:v0BAFp00ECd0001dcFFdscFFdpFFicFFiscFFipFF"
    bInterfaceNumber = 0
    bInterfaceClass = 255
    bInterfaceSubClass = 255
    bInterfaceProtocol = 255
    if: 6-2:1.0 @ /devices/pci0000:00/0000:00:1d.0/usb6/6-2
    bDeviceClass = 255
    bDeviceSubClass = 255
    bDeviceProtocol = 255
    idVendor = 0x0baf
    idProduct = 0x00ec
    manufacturer = "U.S. Robotics"
    product = "U.S. Robotics 56K Faxmodem USB"
    serial = "USBHCF00000006"
    bcdDevice = 0001
    speed = "12"

...

  P: /devices/pci0000:00/0000:00:1d.0/usb6/6-2
  N: bus/usb/006/002
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1d.0/usb6/6-2
  E: MAJOR=189
  E: MINOR=641
  E: DEVNAME=/dev/bus/usb/006/002
  E: DEVTYPE=usb_device
  E: DRIVER=usb
  E: PRODUCT=baf/ec/1
  E: TYPE=255/255/255
  E: BUSNUM=006
  E: DEVNUM=002
  E: SUBSYSTEM=usb
  E: ID_VENDOR=U.S._Robotics
  E: ID_VENDOR_ENC=U.S.\x20Robotics
  E: ID_VENDOR_ID=0baf
  E: ID_MODEL=U.S._Robotics_56K_Faxmodem_USB
  E: ID_MODEL_ENC=U.S.\x20Robotics\x2056K\x20Faxmodem\x20USB
  E: ID_MODEL_ID=00ec
  E: ID_REVISION=0001
  E: ID_SERIAL=U.S._Robotics_U.S._Robotics_56K_Faxmodem_USB_USBHCF00000006
  E: ID_SERIAL_SHORT=USBHCF00000006
  E: ID_BUS=usb
  E: ID_USB_INTERFACES=:ffffff:

...

65: USB 00.0: 0000 Unclassified device
  [Created at usb.122]
  Unique ID: +u4I.bBFFBTjAOZ4
  Parent ID: 7eqy.v+N+B0xY+P6
  SysFS ID: /devices/pci0000:00/0000:00:1d.0/usb6/6-2/6-2:1.0
  SysFS BusID: 6-2:1.0
  Hardware Class: unknown
  Model: "U.S. Robotics 56K Faxmodem USB"
  Hotplug: USB
  Vendor: usb 0x0baf "U.S. Robotics"
  Device: usb 0x00ec "U.S. Robotics 56K Faxmodem USB"
  Revision: "0.01"
  Serial ID: "USBHCF00000006"
  Speed: 12 Mbps
  Module Alias: "usb:v0BAFp00ECd0001dcFFdscFFdpFFicFFiscFFipFF"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #55 (Hub)
```

Below is the full hwinfo list:
```
============ start debug info ============
libhd version 16.0u (x86-64)
using /var/lib/hardware
kernel version is 3.0
----- /proc/cmdline -----
  BOOT_IMAGE=/boot/vmlinuz-3.0.0-14-generic root=UUID=2bdc1a9a-8cf1-4e51-8e7a-0717443ce6c8 ro quiet splash vt.handoff=7
----- /proc/cmdline end -----
debug = 0xff7ffff7
probe = 0x00138fc4aa17fcf9fffe (+memory +pci +isapnp +net +floppy +misc +misc.serial +misc.par +misc.floppy +serial +cpu +bios +monitor +mouse +scsi +usb -usb.mods +modem +modem.usb +parallel +parallel.lp +parallel.zip -isa -isa.isdn +isdn +kbd +prom +sbus +int +braille +braille.alva +braille.fhp +braille.ht -ignx11 +sys -bios.vbe -isapnp.old -isapnp.new -isapnp.mod +braille.baum -manual +fb +pppoe -scan +pcmcia -fork -parallel.imm +s390 -cpuemu -sysfs -s390disks +udev +block +block.cdrom +block.part +edd +edd.mod -bios.ddc -bios.fb -bios.mode +input +block.mods +bios.vesa -cpuemu.debug -scsi.noserial +wlan -bios.crc -hal -bios.vram -bios.acpi -bios.ddc.ports -modules.pata -net.eeprom -x86emu -max -lxrc)
shm: attached segment 1146900 at 0x7fabb3c2d000
>> hal.1: read hal data
  hal: connected to: :1.48
  hal: empty device list
>> floppy.1: get nvram
>> floppy.2: klog info
>> bios.1: cmdline
>> bios.1.1: apm
>> bios.2: ram
  bios: 0 disks
>> bios.2: rom
>> bios.3: smp
----- BIOS data 0x00400 - 0x004ff -----
  400  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  410  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  420  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  430  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  440  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  450  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  460  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  470  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  480  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  490  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  4a0  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  4b0  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  4c0  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  4d0  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  4e0  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  4f0  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
----- BIOS data end -----
>> bios.4: vbe
VBE: Could not init Int10
>> bios.5: 32
>> bios.6: acpi
>> sys.1: cpu
  vm check: vm_1 = 0, vm_2 = -1
  is_vmware = 0, has_vmware_mouse = 0
>> misc.9: kernel log
----- kernel log -----
  <6>[   12.480823] pcmcia_socket pcmcia_socket0: cs: memory probe 0xf6500000-0xf65fffff: excluding 0xf6500000-0xf650ffff 0xf65f0000-0xf65fffff
  <6>[   12.503488] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
  <6>[   12.591089] [drm] Initialized drm 1.1.0 20060810
  <6>[   12.628293] parport_pc 00:0a: reported by Plug and Play ACPI
  <6>[   12.628364] parport0: PC-style at 0x378 (0x778), irq 7, dma 1 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
  <6>[   12.724235] lp0: using parport0 (interrupt-driven).
  <6>[   12.835074] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
  <7>[   12.835080] i915 0000:00:02.0: setting latency timer to 64
  <4>[   12.880506] mtrr: type mismatch for e0000000,10000000 old: write-back new: write-combining
  <6>[   12.880509] [drm] MTRR allocation failed.  Graphics performance may suffer.
  <7>[   12.880828] i915 0000:00:02.0: irq 46 for MSI/MSI-X
  <6>[   12.880833] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
  <6>[   12.880834] [drm] Driver supports precise vblank timestamp query.
  <6>[   12.880876] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
  <6>[   12.901693] ppdev: user-space parallel port driver
  <6>[   13.009302] dell_wmi: Received unknown WMI event (0x11)
  <6>[   13.083309] input: DualPoint Stick as /devices/platform/i8042/serio1/input/input8
  <6>[   13.100121] input: AlpsPS/2 ALPS DualPoint TouchPad as /devices/platform/i8042/serio1/input/input9
  <4>[   13.274303] wl: module license 'MIXED/Proprietary' taints kernel.
  <4>[   13.274306] Disabling lock debugging due to kernel taint
  <6>[   13.283972] wl 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
  <7>[   13.283983] wl 0000:0c:00.0: setting latency timer to 64
  <6>[   13.411822] Linux video capture interface: v2.00
  <6>[   13.497506] uvcvideo: Found UVC 1.00 device Integrated_Webcam_2M (0c45:63f1)
  <6>[   13.505740] input: Integrated_Webcam_2M as /devices/pci0000:00/0000:00:1a.7/usb1/1-6/1-6:1.0/input/input10
  <6>[   13.505802] usbcore: registered new interface driver uvcvideo
  <6>[   13.505803] USB Video Class driver (v1.1.0)
  <6>[   13.613285] fbcon: inteldrmfb (fb0) is primary device
  <6>[   13.613409] Console: switching to colour frame buffer device 210x65
  <6>[   13.613438] fb0: inteldrmfb frame buffer device
  <6>[   13.613440] drm: registered panic notifier
  <6>[   13.623229] pcmcia_socket pcmcia_socket0: cs: memory probe 0x0c0000-0x0fffff: excluding 0xc0000-0xd7fff 0xe0000-0xfffff
  <6>[   13.623280] pcmcia_socket pcmcia_socket0: cs: memory probe 0xa0000000-0xa0ffffff: excluding 0xa0000000-0xa0ffffff
  <6>[   13.623328] pcmcia_socket pcmcia_socket0: cs: memory probe 0x60000000-0x60ffffff: excluding 0x60000000-0x60ffffff
  <6>[   13.638204] acpi device:3e: registered as cooling_device2
  <6>[   13.638707] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:01/input/input11
  <6>[   13.638767] ACPI: Video Device [VID1] (multi-head: yes  rom: no  post: no)
  <4>[   13.638787] [Firmware Bug]: Duplicate ACPI video bus devices for the same VGA controller, please try module parameter "video.allow_duplicates=1"if the current driver doesn't work.
  <6>[   13.638848] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
  <7>[   13.728302] lib80211_crypt: registered algorithm 'TKIP'
  <4>[   13.760209] eth1: Broadcom BCM432b 802.11 Hybrid Wireless Controller 5.100.82.38
  <30>[   13.784448] udevd[386]: renamed network interface eth1 to eth2
  <6>[   14.129099] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
  <7>[   14.129165] HDA Intel 0000:00:1b.0: irq 47 for MSI/MSI-X
  <7>[   14.129194] HDA Intel 0000:00:1b.0: setting latency timer to 64
  <5>[   14.303131] type=1400 audit(1326383785.063:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=984 comm="apparmor_parser"
  <5>[   14.303552] type=1400 audit(1326383785.063:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=984 comm="apparmor_parser"
  <5>[   14.303786] type=1400 audit(1326383785.063:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=984 comm="apparmor_parser"
  <5>[   14.304557] type=1400 audit(1326383785.067:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=732 comm="apparmor_parser"
  <5>[   14.304907] type=1400 audit(1326383785.067:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=732 comm="apparmor_parser"
  <5>[   14.305134] type=1400 audit(1326383785.067:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=732 comm="apparmor_parser"
  <5>[   14.305767] type=1400 audit(1326383785.067:8): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=675 comm="apparmor_parser"
  <5>[   14.306107] type=1400 audit(1326383785.067:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=675 comm="apparmor_parser"
  <5>[   14.306319] type=1400 audit(1326383785.067:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=675 comm="apparmor_parser"
  <6>[   14.313265] HDMI status: Pin=3 Presence_Detect=0 ELD_Valid=0
  <6>[   14.313447] input: HDA Intel HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
  <6>[   14.313540] input: HDA Intel Mic at Sep Left Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input13
  <6>[   14.313623] input: HDA Intel Mic at Ext Right Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input14
  <6>[   14.313685] input: HDA Intel Line Out at Sep Left Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input15
  <6>[   14.313760] input: HDA Intel HP Out at Ext Right Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input16
  <6>[   15.901664] EXT3-fs (sda2): using internal journal
  <6>[   16.595870] EXT3-fs: barriers not enabled
  <6>[   16.605224] kjournald starting.  Commit interval 5 seconds
  <6>[   16.606796] EXT3-fs (sda6): using internal journal
  <6>[   16.606801] EXT3-fs (sda6): mounted filesystem with ordered data mode
  <5>[   17.805526] type=1400 audit(1326383788.567:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=1161 comm="apparmor_parser"
  <7>[   19.256271] e1000e 0000:00:19.0: irq 44 for MSI/MSI-X
  <7>[   19.312102] e1000e 0000:00:19.0: irq 44 for MSI/MSI-X
  <6>[   19.312644] ADDRCONF(NETDEV_UP): eth0: link is not ready
  <6>[   20.960915] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: None
  <6>[   20.960919] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
  <6>[   20.961356] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
  <4>[   21.597975] init: failsafe main process (1118) killed by TERM signal
  <4>[   21.674924] init: apport pre-start process (1260) terminated with status 1
  <4>[   21.677220] init: apport post-stop process (1282) terminated with status 1
  <7>[   24.890785] vboxdrv: Found 2 processor cores.
  <4>[   24.891419] vboxdrv: fAsync=0 offMin=0x18f offMax=0x60c
  <6>[   24.893606] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
  <7>[   24.893608] vboxdrv: Successfully loaded version 4.1.2_Ubuntu (interface 0x00190000).
  <6>[   24.939971] vboxpci: IOMMU not found (not registered)
  <6>[   25.157464] Bluetooth: Core ver 2.16
  <6>[   25.157486] NET: Registered protocol family 31
  <6>[   25.157488] Bluetooth: HCI device and connection manager initialized
  <6>[   25.157490] Bluetooth: HCI socket layer initialized
  <6>[   25.157491] Bluetooth: L2CAP socket layer initialized
  <6>[   25.159233] Bluetooth: SCO socket layer initialized
  <6>[   25.170464] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
  <6>[   25.170466] Bluetooth: BNEP filters: protocol multicast
  <6>[   25.257520] Bluetooth: RFCOMM TTY layer initialized
  <6>[   25.257525] Bluetooth: RFCOMM socket layer initialized
  <6>[   25.257527] Bluetooth: RFCOMM ver 1.11
  <4>[   28.206630] init: plymouth-stop pre-start process (1600) terminated with status 1
  <7>[   30.224043] eth2: no IPv6 routers present
  <7>[   31.784039] eth0: no IPv6 routers present
  <7>[   54.544022] eth0: no IPv6 routers present
----- kernel log end -----
>> misc.1: misc data
>> misc.1.1: open serial
>> misc.1.2: open parallel
----- exec: "/sbin/rmmod lp" -----
  ERROR: Removing 'lp': Operation not permitted
----- return code: ? -----
----- exec: "/sbin/rmmod parport_pc" -----
  ERROR: Module parport_pc is in use
----- return code: ? -----
----- exec: "/sbin/rmmod parport" -----
  ERROR: Module parport is in use by ppdev,parport_pc,lp
----- return code: ? -----
>> misc.2.1: io
>> misc.2.2: dma
>> misc.2.3: irq
----- /proc/ioports -----
  0000-0cf7 : PCI Bus 0000:00
    0000-001f : dma1
    0020-0021 : pic1
    0040-0043 : timer0
    0050-0053 : timer1
    0060-0060 : keyboard
    0064-0064 : keyboard
    0070-0071 : rtc0
    0080-008f : dma page reg
    00a0-00a1 : pic2
    00c0-00df : dma2
    00f0-00ff : fpu
    0378-037a : parport0
    03f8-03ff : serial
    04d0-04d1 : pnp 00:0c
    0778-077a : parport0
    0809-0809 : pnp 00:0d
    0900-092f : pnp 00:0c
    0930-0930 : EC data
    0931-0933 : pnp 00:0c
    0934-0934 : EC cmd
    0935-097f : pnp 00:0c
    0c80-0caf : pnp 00:05
    0cb0-0cbb : pnp 00:0b
  0cf8-0cff : PCI conf1
  0d00-ffff : PCI Bus 0000:00
    1000-1005 : pnp 00:0c
      1000-1003 : ACPI PM1a_EVT_BLK
      1004-1005 : ACPI PM1a_CNT_BLK
    1006-1007 : pnp 00:0d
    1008-100f : pnp 00:0c
      1008-100b : ACPI PM_TMR
    1010-102f : pnp 00:0d
      1010-1015 : ACPI CPU throttle
      1020-102f : ACPI GPE0_BLK
    1050-1050 : ACPI PM2_CNT_BLK
    1060-107f : pnp 00:0d
    1080-10bf : pnp 00:0d
    1100-111f : 0000:00:1f.3
      1100-111f : pnp 00:0d
    2000-2fff : PCI Bus 0000:03
      2000-20ff : PCI CardBus 0000:04
      2400-24ff : PCI CardBus 0000:04
    3000-3fff : PCI Bus 0000:0d
    4000-4fff : PCI Bus 0000:0c
    5000-5fff : PCI Bus 0000:0b
    6e70-6e77 : 0000:00:1f.2
      6e70-6e77 : ahci
    6e78-6e7b : 0000:00:1f.2
      6e78-6e7b : ahci
    6e80-6e87 : 0000:00:1f.2
      6e80-6e87 : ahci
    6e88-6e8b : 0000:00:1f.2
      6e88-6e8b : ahci
    6ea0-6ebf : 0000:00:1f.2
      6ea0-6ebf : ahci
    6f00-6f1f : 0000:00:1d.0
      6f00-6f1f : uhci_hcd
    6f20-6f3f : 0000:00:1d.1
      6f20-6f3f : uhci_hcd
    6f40-6f5f : 0000:00:1d.2
      6f40-6f5f : uhci_hcd
    6f60-6f7f : 0000:00:1a.0
      6f60-6f7f : uhci_hcd
    6f80-6f9f : 0000:00:1a.1
      6f80-6f9f : uhci_hcd
    6fa0-6fbf : 0000:00:1a.2
      6fa0-6fbf : uhci_hcd
    d000-dfff : PCI Bus 0000:0e
    ef98-ef9f : 0000:00:02.0
    efe0-efff : 0000:00:19.0
    f400-f4fe : pnp 00:0d
----- /proc/ioports end -----
----- /proc/interrupts -----
    0:      32002      77848   IO-APIC-edge      timer
    1:       1816         13   IO-APIC-edge      i8042
    4:          1          2   IO-APIC-edge      serial
    7:          0          0   IO-APIC-edge      parport0
    8:          1          0   IO-APIC-edge      rtc0
    9:        116        118   IO-APIC-fasteoi   acpi
   12:         57         57   IO-APIC-edge      i8042
   17:       1015         16   IO-APIC-fasteoi   firewire_ohci, eth2
   18:        526        505   IO-APIC-fasteoi   mmc0
   19:          0          0   IO-APIC-fasteoi   yenta
   20:         94         78   IO-APIC-fasteoi   ehci_hcd:usb2, uhci_hcd:usb3, uhci_hcd:usb6
   21:          0          0   IO-APIC-fasteoi   uhci_hcd:usb4, uhci_hcd:usb7
   22:      16856        573   IO-APIC-fasteoi   ehci_hcd:usb1, uhci_hcd:usb5, uhci_hcd:usb8
   44:         18       3269   PCI-MSI-edge      eth0
   45:      71637       2585   PCI-MSI-edge      ahci
   46:      65223        169   PCI-MSI-edge      i915
   47:        165        164   PCI-MSI-edge      hda_intel
  NMI:          0          0   Non-maskable interrupts
  LOC:      84879      47517   Local timer interrupts
  SPU:          0          0   Spurious interrupts
  PMI:          0          0   Performance monitoring interrupts
  IWI:          0          0   IRQ work interrupts
  RES:      58675      80022   Rescheduling interrupts
  CAL:        408        477   Function call interrupts
  TLB:       2235       1669   TLB shootdowns
  TRM:          0          0   Thermal event interrupts
  THR:          0          0   Threshold APIC interrupts
  MCE:          0          0   Machine check exceptions
  MCP:          2          2   Machine check polls
  ERR:          0
  MIS:          0
----- /proc/interrupts end -----
----- /proc/dma -----
   1: parport0
   4: cascade
----- /proc/dma end -----
>> misc.3: FPU
>> misc.3.1: DMA
>> misc.3.2: PIC
>> misc.3.3: timer
>> misc.3.4: RTC
>> cpu.1: cpuinfo
----- /proc/cpuinfo -----
  processor	: 0
  vendor_id	: GenuineIntel
  cpu family	: 6
  model		: 23
  model name	: Intel(R) Core(TM)2 Duo CPU     P8700  @ 2.53GHz
  stepping	: 10
  cpu MHz		: 2535.000
  cache size	: 3072 KB
  physical id	: 0
  siblings	: 2
  core id		: 0
  cpu cores	: 2
  apicid		: 0
  initial apicid	: 0
  fpu		: yes
  fpu_exception	: yes
  cpuid level	: 13
  wp		: yes
  flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good nopl aperfmperf pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 xsave lahf_lm ida dts tpr_shadow vnmi flexpriority
  bogomips	: 5053.30
  clflush size	: 64
  cache_alignment	: 64
  address sizes	: 36 bits physical, 48 bits virtual
  power management:
  
  processor	: 1
  vendor_id	: GenuineIntel
  cpu family	: 6
  model		: 23
  model name	: Intel(R) Core(TM)2 Duo CPU     P8700  @ 2.53GHz
  stepping	: 10
  cpu MHz		: 2535.000
  cache size	: 3072 KB
  physical id	: 0
  siblings	: 2
  core id		: 1
  cpu cores	: 2
  apicid		: 1
  initial apicid	: 1
  fpu		: yes
  fpu_exception	: yes
  cpuid level	: 13
  wp		: yes
  flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good nopl aperfmperf pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 xsave lahf_lm ida dts tpr_shadow vnmi flexpriority
  bogomips	: 5053.95
  clflush size	: 64
  cache_alignment	: 64
  address sizes	: 36 bits physical, 48 bits virtual
  power management:
  
----- /proc/cpuinfo end -----
>> memory.1: main memory size
  kcore mem:  0x7fffffe01000
  klog mem 0: 0x0
  klog mem 1: 0x0
  klog mem:   0x0
  bios mem:   0x0
  meminfo:    0xf4a4a000
>> pci.1: sysfs drivers
----- sysfs driver list (id 0xf0c532985310cd28) -----
      alarmtimer: /devices/platform/alarmtimer
      serial8250: /devices/platform/serial8250
           i8042: /devices/platform/i8042
          dcdbas: module = dcdbas
          dcdbas: /devices/platform/dcdbas
     dell-laptop: module = dell_laptop
     dell-laptop: /devices/platform/dell-laptop
      parport_pc: module = parport_pc
         vboxdrv: /devices/platform/vboxdrv.0
        pcieport: /devices/pci0000:00/0000:00:1c.0
        pcieport: /devices/pci0000:00/0000:00:1c.1
        pcieport: /devices/pci0000:00/0000:00:1c.2
        pcieport: /devices/pci0000:00/0000:00:1c.3
   agpgart-intel: /devices/pci0000:00/0000:00:00.0
        pdc_adma: module = pdc_adma
        ata_piix: module = ata_piix
        pata_sis: module = pata_sis
       pata_acpi: module = pata_acpi
     ata_generic: module = ata_generic
        ehci_hcd: /devices/pci0000:00/0000:00:1a.7
        ehci_hcd: /devices/pci0000:00/0000:00:1d.7
        ehci_hcd: module = ehci_hcd
        uhci_hcd: /devices/pci0000:00/0000:00:1a.0
        uhci_hcd: /devices/pci0000:00/0000:00:1a.1
        uhci_hcd: /devices/pci0000:00/0000:00:1a.2
        uhci_hcd: /devices/pci0000:00/0000:00:1d.0
        uhci_hcd: /devices/pci0000:00/0000:00:1d.1
        uhci_hcd: /devices/pci0000:00/0000:00:1d.2
        uhci_hcd: module = uhci_hcd
          e1000e: /devices/pci0000:00/0000:00:19.0
          e1000e: module = e1000e
            ahci: /devices/pci0000:00/0000:00:1f.2
            ahci: module = ahci
       sdhci-pci: /devices/pci0000:00/0000:00:1e.0/0000:03:01.2
       sdhci-pci: module = sdhci_pci
   firewire_ohci: /devices/pci0000:00/0000:00:1e.0/0000:03:01.1
   firewire_ohci: module = firewire_ohci
              wl: /devices/pci0000:00/0000:00:1c.1/0000:0c:00.0
              wl: module = wl
   yenta_cardbus: /devices/pci0000:00/0000:00:1e.0/0000:03:01.0
   yenta_cardbus: module = yenta_socket
      parport_pc: module = parport_pc
            i915: /devices/pci0000:00/0000:00:02.0
            i915: module = drm
       HDA Intel: /devices/pci0000:00/0000:00:1b.0
       HDA Intel: module = snd_hda_intel
        pci-stub: module = pci_stub
              ec: /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:01/PNP0C09:00
        pci_root: /devices/LNXSYSTM:00/device:00/PNP0A03:00
        pci_link: /devices/LNXSYSTM:00/device:00/PNP0A03:00/PNP0C0F:00
        pci_link: /devices/LNXSYSTM:00/device:00/PNP0A03:00/PNP0C0F:01
        pci_link: /devices/LNXSYSTM:00/device:00/PNP0A03:00/PNP0C0F:02
        pci_link: /devices/LNXSYSTM:00/device:00/PNP0A03:00/PNP0C0F:03
        pci_link: /devices/LNXSYSTM:00/device:00/PNP0A03:00/PNP0C0F:04
        pci_link: /devices/LNXSYSTM:00/device:00/PNP0A03:00/PNP0C0F:05
        pci_link: /devices/LNXSYSTM:00/device:00/PNP0A03:00/PNP0C0F:06
        pci_link: /devices/LNXSYSTM:00/device:00/PNP0A03:00/PNP0C0F:07
              ac: /devices/LNXSYSTM:00/device:00/ACPI0003:00
          button: /devices/LNXSYSTM:00/device:00/PNP0C0D:00
          button: /devices/LNXSYSTM:00/device:00/PNP0C0C:00
          button: /devices/LNXSYSTM:00/device:00/PNP0C0E:00
       processor: /devices/LNXSYSTM:00/LNXCPU:00
       processor: /devices/LNXSYSTM:00/LNXCPU:01
       processor: /devices/LNXSYSTM:00/LNXCPU:02
       processor: /devices/LNXSYSTM:00/LNXCPU:03
         thermal: /devices/LNXSYSTM:00/device:4f/LNXTHERM:00
         battery: /devices/LNXSYSTM:00/device:00/PNP0C0A:00
         battery: /devices/LNXSYSTM:00/device:00/PNP0C0A:01
             wmi: /devices/LNXSYSTM:00/device:00/PNP0C14:00
           video: /devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:01
          system: /devices/pnp0/00:05
          system: /devices/pnp0/00:08
          system: /devices/pnp0/00:0b
          system: /devices/pnp0/00:0c
          system: /devices/pnp0/00:0d
          system: /devices/pnp0/00:0e
          serial: /devices/pnp0/00:09
       i8042 kbd: /devices/pnp0/00:02
       i8042 aux: /devices/pnp0/00:01
        rtc_cmos: /devices/pnp0/00:03
      parport_pc: /devices/pnp0/00:0a
              sd: /devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0
              sd: /devices/pci0000:00/0000:00:1a.7/usb1/1-3/1-3.1/1-3.1.3/1-3.1.3:1.0/host6/target6:0:0/6:0:0:0
              sr: /devices/pci0000:00/0000:00:1f.2/host1/target1:0:0/1:0:0:0
              sr: /devices/pci0000:00/0000:00:1a.7/usb1/1-3/1-3.1/1-3.1.3/1-3.1.3:1.0/host6/target6:0:0/6:0:0:1
             ses: /devices/pci0000:00/0000:00:1a.7/usb1/1-3/1-3.1/1-3.1.3/1-3.1.3:1.0/host6/target6:0:0/6:0:0:2
           usbfs: module = usbcore
             hub: module = usbcore
             hub: /devices/pci0000:00/0000:00:1a.7/usb1/1-0:1.0
             hub: /devices/pci0000:00/0000:00:1d.7/usb2/2-0:1.0
             hub: /devices/pci0000:00/0000:00:1a.0/usb3/3-0:1.0
             hub: /devices/pci0000:00/0000:00:1a.1/usb4/4-0:1.0
             hub: /devices/pci0000:00/0000:00:1a.2/usb5/5-0:1.0
             hub: /devices/pci0000:00/0000:00:1d.0/usb6/6-0:1.0
             hub: /devices/pci0000:00/0000:00:1d.1/usb7/7-0:1.0
             hub: /devices/pci0000:00/0000:00:1d.2/usb8/8-0:1.0
             hub: /devices/pci0000:00/0000:00:1a.7/usb1/1-3/1-3:1.0
             hub: /devices/pci0000:00/0000:00:1a.7/usb1/1-4/1-4:1.0
             hub: /devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1:1.0
             hub: /devices/pci0000:00/0000:00:1a.7/usb1/1-3/1-3.1/1-3.1:1.0
             hub: /devices/pci0000:00/0000:00:1a.7/usb1/1-3/1-3.2/1-3.2:1.0
             usb: /devices/pci0000:00/0000:00:1a.7/usb1
             usb: /devices/pci0000:00/0000:00:1d.7/usb2
             usb: /devices/pci0000:00/0000:00:1a.0/usb3
             usb: /devices/pci0000:00/0000:00:1a.1/usb4
             usb: /devices/pci0000:00/0000:00:1a.2/usb5
             usb: /devices/pci0000:00/0000:00:1d.0/usb6
             usb: /devices/pci0000:00/0000:00:1d.1/usb7
             usb: /devices/pci0000:00/0000:00:1d.2/usb8
             usb: /devices/pci0000:00/0000:00:1a.7/usb1/1-3
             usb: /devices/pci0000:00/0000:00:1a.7/usb1/1-4
             usb: /devices/pci0000:00/0000:00:1a.7/usb1/1-6
             usb: /devices/pci0000:00/0000:00:1a.0/usb3/3-1
             usb: /devices/pci0000:00/0000:00:1a.2/usb5/5-1
             usb: /devices/pci0000:00/0000:00:1d.0/usb6/6-2
             usb: /devices/pci0000:00/0000:00:1a.7/usb1/1-3/1-3.1
             usb: /devices/pci0000:00/0000:00:1a.7/usb1/1-3/1-3.2
             usb: /devices/pci0000:00/0000:00:1a.7/usb1/1-4/1-4.2
             usb: /devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1.1
             usb: /devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1.2
             usb: /devices/pci0000:00/0000:00:1a.7/usb1/1-3/1-3.1/1-3.1.3
          usbhid: /devices/pci0000:00/0000:00:1a.7/usb1/1-4/1-4.2/1-4.2:1.0
          usbhid: module = usbhid
          usbhid: /devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1.1/3-1.1:1.0
             uas: module = uas
     usb-storage: /devices/pci0000:00/0000:00:1a.7/usb1/1-3/1-3.1/1-3.1.3/1-3.1.3:1.0
     usb-storage: module = usb_storage
        uvcvideo: /devices/pci0000:00/0000:00:1a.7/usb1/1-6/1-6:1.0
        uvcvideo: /devices/pci0000:00/0000:00:1a.7/usb1/1-6/1-6:1.1
        uvcvideo: module = uvcvideo
           atkbd: /devices/platform/i8042/serio0
       serio_raw: module = serio_raw
         psmouse: module = psmouse
         psmouse: /devices/platform/i8042/serio1
          mmcblk: /devices/pci0000:00/0000:00:1e.0/0000:03:01.2/mmc_host/mmc0/mmc0:0007
     generic-usb: module = usbhid
     generic-usb: /devices/pci0000:00/0000:00:1a.7/usb1/1-4/1-4.2/1-4.2:1.0/0003:046D:C016.0001
     generic-usb: /devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1.1/3-1.1:1.0/0003:413C:8157.0002
----- sysfs driver list end -----
>> pci.2: get sysfs pci data
  pci device: name = 0000:00:00.0
    path = /devices/pci0000:00/0000:00:00.0
    modalias = "pci:v00008086d00002A40sv00001028sd0000024Fbc06sc00i00"
    class = 0x60000
    vendor = 0x8086
    device = 0x2a40
    subvendor = 0x1028
    subdevice = 0x24f
    irq = 0
    config[64]
  pci device: name = 0000:00:02.0
    path = /devices/pci0000:00/0000:00:02.0
    modalias = "pci:v00008086d00002A42sv00001028sd0000024Fbc03sc00i00"
    class = 0x30000
    vendor = 0x8086
    device = 0x2a42
    subvendor = 0x1028
    subdevice = 0x24f
    irq = 46
    res[0] = 0xf6c00000 0xf6ffffff 0x140204
    res[2] = 0xe0000000 0xefffffff 0x14220c
    res[4] = 0xef98 0xef9f 0x40101
    config[64]
  pci device: name = 0000:00:02.1
    path = /devices/pci0000:00/0000:00:02.1
    modalias = "pci:v00008086d00002A43sv00001028sd0000024Fbc03sc80i00"
    class = 0x38000
    vendor = 0x8086
    device = 0x2a43
    subvendor = 0x1028
    subdevice = 0x24f
    irq = 0
    res[0] = 0xf6b00000 0xf6bfffff 0x140204
    config[64]
  pci device: name = 0000:00:19.0
    path = /devices/pci0000:00/0000:00:19.0
    modalias = "pci:v00008086d000010F5sv00001028sd0000024Fbc02sc00i00"
    class = 0x20000
    vendor = 0x8086
    device = 0x10f5
    subvendor = 0x1028
    subdevice = 0x24f
    irq = 44
    res[0] = 0xf6ae0000 0xf6afffff 0x40200
    res[1] = 0xf6adb000 0xf6adbfff 0x40200
    res[2] = 0xefe0 0xefff 0x40101
    config[64]
  pci device: name = 0000:00:1a.0
    path = /devices/pci0000:00/0000:00:1a.0
    modalias = "pci:v00008086d00002937sv00001028sd0000024Fbc0Csc03i00"
    class = 0xc0300
    vendor = 0x8086
    device = 0x2937
    subvendor = 0x1028
    subdevice = 0x24f
    irq = 20
    res[4] = 0x6f60 0x6f7f 0x40101
    config[64]
  pci device: name = 0000:00:1a.1
    path = /devices/pci0000:00/0000:00:1a.1
    modalias = "pci:v00008086d00002938sv00001028sd0000024Fbc0Csc03i00"
    class = 0xc0300
    vendor = 0x8086
    device = 0x2938
    subvendor = 0x1028
    subdevice = 0x24f
    irq = 21
    res[4] = 0x6f80 0x6f9f 0x40101
    config[64]
  pci device: name = 0000:00:1a.2
    path = /devices/pci0000:00/0000:00:1a.2
    modalias = "pci:v00008086d00002939sv00001028sd0000024Fbc0Csc03i00"
    class = 0xc0300
    vendor = 0x8086
    device = 0x2939
    subvendor = 0x1028
    subdevice = 0x24f
    irq = 22
    res[4] = 0x6fa0 0x6fbf 0x40101
    config[64]
  pci device: name = 0000:00:1a.7
    path = /devices/pci0000:00/0000:00:1a.7
    modalias = "pci:v00008086d0000293Csv00001028sd0000024Fbc0Csc03i20"
    class = 0xc0320
    vendor = 0x8086
    device = 0x293c
    subvendor = 0x1028
    subdevice = 0x24f
    irq = 22
    res[0] = 0xfed1c400 0xfed1c7ff 0x40200
    config[64]
  pci device: name = 0000:00:1b.0
    path = /devices/pci0000:00/0000:00:1b.0
    modalias = "pci:v00008086d0000293Esv00001028sd0000024Fbc04sc03i00"
    class = 0x40300
    vendor = 0x8086
    device = 0x293e
    subvendor = 0x1028
    subdevice = 0x24f
    irq = 47
    res[0] = 0xf6adc000 0xf6adffff 0x140204
    config[64]
  pci device: name = 0000:00:1c.0
    path = /devices/pci0000:00/0000:00:1c.0
    modalias = "pci:v00008086d00002940sv00001028sd0000024Fbc06sc04i00"
    class = 0x60400
    vendor = 0x8086
    device = 0x2940
    subvendor = 0x1028
    subdevice = 0x24f
    irq = 40
    config[64]
  pci device: name = 0000:00:1c.1
    path = /devices/pci0000:00/0000:00:1c.1
    modalias = "pci:v00008086d00002942sv00001028sd0000024Fbc06sc04i00"
    class = 0x60400
    vendor = 0x8086
    device = 0x2942
    subvendor = 0x1028
    subdevice = 0x24f
    irq = 41
    config[64]
  pci device: name = 0000:00:1c.2
    path = /devices/pci0000:00/0000:00:1c.2
    modalias = "pci:v00008086d00002944sv00001028sd0000024Fbc06sc04i00"
    class = 0x60400
    vendor = 0x8086
    device = 0x2944
    subvendor = 0x1028
    subdevice = 0x24f
    irq = 42
    config[64]
  pci device: name = 0000:00:1c.3
    path = /devices/pci0000:00/0000:00:1c.3
    modalias = "pci:v00008086d00002946sv00001028sd0000024Fbc06sc04i00"
    class = 0x60400
    vendor = 0x8086
    device = 0x2946
    subvendor = 0x1028
    subdevice = 0x24f
    irq = 43
    config[64]
  pci device: name = 0000:00:1d.0
    path = /devices/pci0000:00/0000:00:1d.0
    modalias = "pci:v00008086d00002934sv00001028sd0000024Fbc0Csc03i00"
    class = 0xc0300
    vendor = 0x8086
    device = 0x2934
    subvendor = 0x1028
    subdevice = 0x24f
    irq = 20
    res[4] = 0x6f00 0x6f1f 0x40101
    config[64]
  pci device: name = 0000:00:1d.1
    path = /devices/pci0000:00/0000:00:1d.1
    modalias = "pci:v00008086d00002935sv00001028sd0000024Fbc0Csc03i00"
    class = 0xc0300
    vendor = 0x8086
    device = 0x2935
    subvendor = 0x1028
    subdevice = 0x24f
    irq = 21
    res[4] = 0x6f20 0x6f3f 0x40101
    config[64]
  pci device: name = 0000:00:1d.2
    path = /devices/pci0000:00/0000:00:1d.2
    modalias = "pci:v00008086d00002936sv00001028sd0000024Fbc0Csc03i00"
    class = 0xc0300
    vendor = 0x8086
    device = 0x2936
    subvendor = 0x1028
    subdevice = 0x24f
    irq = 22
    res[4] = 0x6f40 0x6f5f 0x40101
    config[64]
  pci device: name = 0000:00:1d.7
    path = /devices/pci0000:00/0000:00:1d.7
    modalias = "pci:v00008086d0000293Asv00001028sd0000024Fbc0Csc03i20"
    class = 0xc0320
    vendor = 0x8086
    device = 0x293a
    subvendor = 0x1028
    subdevice = 0x24f
    irq = 20
    res[0] = 0xfed1c000 0xfed1c3ff 0x40200
    config[64]
  pci device: name = 0000:00:1e.0
    path = /devices/pci0000:00/0000:00:1e.0
    modalias = "pci:v00008086d00002448sv00001028sd0000024Fbc06sc04i01"
    class = 0x60401
    vendor = 0x8086
    device = 0x2448
    subvendor = 0x1028
    subdevice = 0x24f
    irq = 0
    config[64]
  pci device: name = 0000:00:1f.0
    path = /devices/pci0000:00/0000:00:1f.0
    modalias = "pci:v00008086d00002917sv00001028sd0000024Fbc06sc01i00"
    class = 0x60100
    vendor = 0x8086
    device = 0x2917
    subvendor = 0x1028
    subdevice = 0x24f
    irq = 0
    config[64]
  pci device: name = 0000:00:1f.2
    path = /devices/pci0000:00/0000:00:1f.2
    modalias = "pci:v00008086d0000282Asv00001028sd0000024Fbc01sc04i00"
    class = 0x10400
    vendor = 0x8086
    device = 0x282a
    subvendor = 0x1028
    subdevice = 0x24f
    irq = 45
    res[0] = 0x6e70 0x6e77 0x40101
    res[1] = 0x6e78 0x6e7b 0x40101
    res[2] = 0x6e80 0x6e87 0x40101
    res[3] = 0x6e88 0x6e8b 0x40101
    res[4] = 0x6ea0 0x6ebf 0x40101
    res[5] = 0xfed1c800 0xfed1cfff 0x40200
    config[64]
  pci device: name = 0000:00:1f.3
    path = /devices/pci0000:00/0000:00:1f.3
    modalias = "pci:v00008086d00002930sv00001028sd0000024Fbc0Csc05i00"
    class = 0xc0500
    vendor = 0x8086
    device = 0x2930
    subvendor = 0x1028
    subdevice = 0x24f
    irq = 3
    res[0] = 0xf6adaf00 0xf6adafff 0x140204
    res[4] = 0x1100 0x111f 0x40101
    config[64]
  pci device: name = 0000:0c:00.0
    path = /devices/pci0000:00/0000:00:1c.1/0000:0c:00.0
    modalias = "pci:v000014E4d0000432Bsv00001028sd0000000Dbc02sc80i00"
    class = 0x28000
    vendor = 0x14e4
    device = 0x432b
    subvendor = 0x1028
    subdevice = 0xd
    irq = 17
    res[0] = 0xf69fc000 0xf69fffff 0x140204
    config[64]
  pci device: name = 0000:03:01.0
    path = /devices/pci0000:00/0000:00:1e.0/0000:03:01.0
    modalias = "pci:v00001180d00000476sv00001028sd0000024Fbc06sc07i00"
    class = 0x60700
    vendor = 0x1180
    device = 0x476
    subvendor = 0x1028
    subdevice = 0x24f
    irq = 19
    res[0] = 0xf6500000 0xf6500fff 0x40200
    config[64]
  pci device: name = 0000:03:01.1
    path = /devices/pci0000:00/0000:00:1e.0/0000:03:01.1
    modalias = "pci:v00001180d00000832sv00001028sd0000024Fbc0Csc00i10"
    class = 0xc0010
    vendor = 0x1180
    device = 0x832
    subvendor = 0x1028
    subdevice = 0x24f
    irq = 17
    res[0] = 0xf65ff800 0xf65fffff 0x40200
    config[64]
  pci device: name = 0000:03:01.2
    path = /devices/pci0000:00/0000:00:1e.0/0000:03:01.2
    modalias = "pci:v00001180d00000822sv00001028sd0000024Fbc08sc05i01"
    class = 0x80501
    vendor = 0x1180
    device = 0x822
    subvendor = 0x1028
    subdevice = 0x24f
    irq = 18
    res[0] = 0xf65ff700 0xf65ff7ff 0x40200
    config[64]
---------- PCI raw data ----------
bus 00, slot 00, func 0, vend:dev:s_vend:s_dev:rev 8086:2a40:1028:024f:07
class 06, sub_class 00 prog_if 00, hdr 0, flags <>, irq 0
  00: 86 80 40 2a 06 00 90 30 07 00 00 06 00 00 00 00  "..@*...0........"
  10: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  20: 00 00 00 00 00 00 00 00 00 00 00 00 28 10 4f 02  "............(.O."
  30: 00 00 00 00 e0 00 00 00 00 00 00 00 00 00 00 00  "................"

bus 00, slot 02, func 0, vend:dev:s_vend:s_dev:rev 8086:2a42:1028:024f:07
class 03, sub_class 00 prog_if 00, hdr 0, flags <>, irq 46
  addr0 f6c00000, size 00400000
  addr2 e0000000, size 10000000
  addr4 0000ef98, size 00000008
  00: 86 80 42 2a 07 04 90 00 07 00 00 03 00 00 80 00  "..B*............"
  10: 04 00 c0 f6 00 00 00 00 0c 00 00 e0 00 00 00 00  "................"
  20: 99 ef 00 00 00 00 00 00 00 00 00 00 28 10 4f 02  "............(.O."
  30: 00 00 00 00 90 00 00 00 00 00 00 00 0b 01 00 00  "................"

bus 00, slot 02, func 1, vend:dev:s_vend:s_dev:rev 8086:2a43:1028:024f:07
class 03, sub_class 80 prog_if 00, hdr 0, flags <>, irq 0
  addr0 f6b00000, size 00100000
  00: 86 80 43 2a 07 00 90 00 07 00 80 03 00 00 80 00  "..C*............"
  10: 04 00 b0 f6 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  20: 00 00 00 00 00 00 00 00 00 00 00 00 28 10 4f 02  "............(.O."
  30: 00 00 00 00 d0 00 00 00 00 00 00 00 00 00 00 00  "................"

bus 00, slot 19, func 0, vend:dev:s_vend:s_dev:rev 8086:10f5:1028:024f:03
class 02, sub_class 00 prog_if 00, hdr 0, flags <>, irq 44
  addr0 f6ae0000, size 00020000
  addr1 f6adb000, size 00001000
  addr2 0000efe0, size 00000020
  00: 86 80 f5 10 07 05 10 00 03 00 00 02 00 00 00 00  "................"
  10: 00 00 ae f6 00 b0 ad f6 e1 ef 00 00 00 00 00 00  "................"
  20: 00 00 00 00 00 00 00 00 00 00 00 00 28 10 4f 02  "............(.O."
  30: 00 00 00 00 c8 00 00 00 00 00 00 00 0a 01 00 00  "................"

bus 00, slot 1a, func 0, vend:dev:s_vend:s_dev:rev 8086:2937:1028:024f:03
class 0c, sub_class 03 prog_if 00, hdr 0, flags <>, irq 20
  addr4 00006f60, size 00000020
  00: 86 80 37 29 05 00 90 02 03 00 03 0c 00 00 80 00  "..7)............"
  10: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  20: 61 6f 00 00 00 00 00 00 00 00 00 00 28 10 4f 02  "ao..........(.O."
  30: 00 00 00 00 50 00 00 00 00 00 00 00 03 01 00 00  "....P..........."

bus 00, slot 1a, func 1, vend:dev:s_vend:s_dev:rev 8086:2938:1028:024f:03
class 0c, sub_class 03 prog_if 00, hdr 0, flags <>, irq 21
  addr4 00006f80, size 00000020
  00: 86 80 38 29 05 00 90 02 03 00 03 0c 00 00 00 00  "..8)............"
  10: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  20: 81 6f 00 00 00 00 00 00 00 00 00 00 28 10 4f 02  ".o..........(.O."
  30: 00 00 00 00 50 00 00 00 00 00 00 00 0b 02 00 00  "....P..........."

bus 00, slot 1a, func 2, vend:dev:s_vend:s_dev:rev 8086:2939:1028:024f:03
class 0c, sub_class 03 prog_if 00, hdr 0, flags <>, irq 22
  addr4 00006fa0, size 00000020
  00: 86 80 39 29 05 00 90 02 03 00 03 0c 00 00 00 00  "..9)............"
  10: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  20: a1 6f 00 00 00 00 00 00 00 00 00 00 28 10 4f 02  ".o..........(.O."
  30: 00 00 00 00 50 00 00 00 00 00 00 00 0a 03 00 00  "....P..........."

bus 00, slot 1a, func 7, vend:dev:s_vend:s_dev:rev 8086:293c:1028:024f:03
class 0c, sub_class 03 prog_if 20, hdr 0, flags <>, irq 22
  addr0 fed1c400, size 00000400
  00: 86 80 3c 29 06 01 90 02 03 20 03 0c 00 00 00 00  "..<)..... ......"
  10: 00 c4 d1 fe 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  20: 00 00 00 00 00 00 00 00 00 00 00 00 28 10 4f 02  "............(.O."
  30: 00 00 00 00 50 00 00 00 00 00 00 00 0a 03 00 00  "....P..........."

bus 00, slot 1b, func 0, vend:dev:s_vend:s_dev:rev 8086:293e:1028:024f:03
class 04, sub_class 03 prog_if 00, hdr 0, flags <>, irq 47
  addr0 f6adc000, size 00004000
  00: 86 80 3e 29 06 05 10 00 03 00 03 04 10 00 00 00  "..>)............"
  10: 04 c0 ad f6 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  20: 00 00 00 00 00 00 00 00 00 00 00 00 28 10 4f 02  "............(.O."
  30: 00 00 00 00 50 00 00 00 00 00 00 00 0b 01 00 00  "....P..........."

bus 00->0b, slot 1c, func 0, vend:dev:s_vend:s_dev:rev 8086:2940:1028:024f:03
class 06, sub_class 04 prog_if 00, hdr 1, flags <>, irq 40
  00: 86 80 40 29 07 05 10 00 03 00 04 06 10 00 81 00  "..@)............"
  10: 00 00 00 00 00 00 00 00 00 0b 0b 00 50 50 00 20  "............PP. "
  20: 80 f0 90 f0 a1 f0 b1 f0 00 00 00 00 00 00 00 00  "................"
  30: 00 00 00 00 40 00 00 00 00 00 00 00 00 01 02 00  "....@..........."

bus 00->0c, slot 1c, func 1, vend:dev:s_vend:s_dev:rev 8086:2942:1028:024f:03
class 06, sub_class 04 prog_if 00, hdr 1, flags <>, irq 41
  00: 86 80 42 29 07 05 10 48 03 00 04 06 10 00 81 00  "..B)...H........"
  10: 00 00 00 00 00 00 00 00 00 0c 0c 00 40 40 00 10  "............@@.."
  20: 90 f6 90 f6 61 f0 71 f0 00 00 00 00 00 00 00 00  "....a.q........."
  30: 00 00 00 00 40 00 00 00 00 00 00 00 00 02 02 00  "....@..........."

bus 00->0d, slot 1c, func 2, vend:dev:s_vend:s_dev:rev 8086:2944:1028:024f:03
class 06, sub_class 04 prog_if 00, hdr 1, flags <>, irq 42
  00: 86 80 44 29 07 05 10 00 03 00 04 06 10 00 81 00  "..D)............"
  10: 00 00 00 00 00 00 00 00 00 0d 0d 00 30 30 00 00  "............00.."
  20: 20 f0 30 f0 41 f0 51 f0 00 00 00 00 00 00 00 00  " .0.A.Q........."
  30: 00 00 00 00 40 00 00 00 00 00 00 00 00 03 02 00  "....@..........."

bus 00->0e, slot 1c, func 3, vend:dev:s_vend:s_dev:rev 8086:2946:1028:024f:03
class 06, sub_class 04 prog_if 00, hdr 1, flags <>, irq 43
  00: 86 80 46 29 07 04 10 00 03 00 04 06 10 00 81 00  "..F)............"
  10: 00 00 00 00 00 00 00 00 00 0e 0f 00 d0 d0 00 00  "................"
  20: 60 f6 80 f6 01 f0 11 f0 00 00 00 00 00 00 00 00  "`..............."
  30: 00 00 00 00 40 00 00 00 00 00 00 00 00 04 02 00  "....@..........."

bus 00, slot 1d, func 0, vend:dev:s_vend:s_dev:rev 8086:2934:1028:024f:03
class 0c, sub_class 03 prog_if 00, hdr 0, flags <>, irq 20
  addr4 00006f00, size 00000020
  00: 86 80 34 29 05 00 90 02 03 00 03 0c 00 00 80 00  "..4)............"
  10: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  20: 01 6f 00 00 00 00 00 00 00 00 00 00 28 10 4f 02  ".o..........(.O."
  30: 00 00 00 00 50 00 00 00 00 00 00 00 03 01 00 00  "....P..........."

bus 00, slot 1d, func 1, vend:dev:s_vend:s_dev:rev 8086:2935:1028:024f:03
class 0c, sub_class 03 prog_if 00, hdr 0, flags <>, irq 21
  addr4 00006f20, size 00000020
  00: 86 80 35 29 05 00 90 02 03 00 03 0c 00 00 00 00  "..5)............"
  10: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  20: 21 6f 00 00 00 00 00 00 00 00 00 00 28 10 4f 02  "!o..........(.O."
  30: 00 00 00 00 50 00 00 00 00 00 00 00 0b 02 00 00  "....P..........."

bus 00, slot 1d, func 2, vend:dev:s_vend:s_dev:rev 8086:2936:1028:024f:03
class 0c, sub_class 03 prog_if 00, hdr 0, flags <>, irq 22
  addr4 00006f40, size 00000020
  00: 86 80 36 29 05 00 90 02 03 00 03 0c 00 00 00 00  "..6)............"
  10: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  20: 41 6f 00 00 00 00 00 00 00 00 00 00 28 10 4f 02  "Ao..........(.O."
  30: 00 00 00 00 50 00 00 00 00 00 00 00 0a 03 00 00  "....P..........."

bus 00, slot 1d, func 7, vend:dev:s_vend:s_dev:rev 8086:293a:1028:024f:03
class 0c, sub_class 03 prog_if 20, hdr 0, flags <>, irq 20
  addr0 fed1c000, size 00000400
  00: 86 80 3a 29 06 01 90 02 03 20 03 0c 00 00 00 00  "..:)..... ......"
  10: 00 c0 d1 fe 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  20: 00 00 00 00 00 00 00 00 00 00 00 00 28 10 4f 02  "............(.O."
  30: 00 00 00 00 50 00 00 00 00 00 00 00 03 01 00 00  "....P..........."

bus 00->03, slot 1e, func 0, vend:dev:s_vend:s_dev:rev 8086:2448:1028:024f:93
class 06, sub_class 04 prog_if 01, hdr 1, flags <>, irq 0
  00: 86 80 48 24 07 01 10 00 93 01 04 06 00 00 01 00  "..H$............"
  10: 00 00 00 00 00 00 00 00 00 03 07 20 20 20 80 22  "...........   .""
  20: 50 f6 50 f6 f1 ff 01 00 00 00 00 00 00 00 00 00  "P.P............."
  30: 00 00 00 00 50 00 00 00 00 00 00 00 ff 00 02 00  "....P..........."

bus 00, slot 1f, func 0, vend:dev:s_vend:s_dev:rev 8086:2917:1028:024f:03
class 06, sub_class 01 prog_if 00, hdr 0, flags <>, irq 0
  00: 86 80 17 29 07 01 10 02 03 00 01 06 00 00 80 00  "...)............"
  10: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  20: 00 00 00 00 00 00 00 00 00 00 00 00 28 10 4f 02  "............(.O."
  30: 00 00 00 00 e0 00 00 00 00 00 00 00 00 00 00 00  "................"

bus 00, slot 1f, func 2, vend:dev:s_vend:s_dev:rev 8086:282a:1028:024f:03
class 01, sub_class 04 prog_if 00, hdr 0, flags <>, irq 45
  addr0 00006e70, size 00000008
  addr1 00006e78, size 00000004
  addr2 00006e80, size 00000008
  addr3 00006e88, size 00000004
  addr4 00006ea0, size 00000020
  addr5 fed1c800, size 00000800
  00: 86 80 2a 28 07 04 b0 02 03 00 04 01 00 00 00 00  "..*(............"
  10: 71 6e 00 00 79 6e 00 00 81 6e 00 00 89 6e 00 00  "qn..yn...n...n.."
  20: a1 6e 00 00 00 c8 d1 fe 00 00 00 00 28 10 4f 02  ".n..........(.O."
  30: 00 00 00 00 80 00 00 00 00 00 00 00 0a 04 00 00  "................"

bus 00, slot 1f, func 3, vend:dev:s_vend:s_dev:rev 8086:2930:1028:024f:03
class 0c, sub_class 05 prog_if 00, hdr 0, flags <>, irq 3
  addr0 f6adaf00, size 00000100
  addr4 00001100, size 00000020
  00: 86 80 30 29 03 01 80 02 03 00 05 0c 00 00 00 00  "..0)............"
  10: 04 af ad f6 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  20: 01 11 00 00 00 00 00 00 00 00 00 00 28 10 4f 02  "............(.O."
  30: 00 00 00 00 00 00 00 00 00 00 00 00 03 02 00 00  "................"

bus 0c, slot 00, func 0, vend:dev:s_vend:s_dev:rev 14e4:432b:1028:000d:01
class 02, sub_class 80 prog_if 00, hdr 0, flags <>, irq 17
  addr0 f69fc000, size 00004000
  00: e4 14 2b 43 06 01 10 08 01 00 80 02 10 00 00 00  "..+C............"
  10: 04 c0 9f f6 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  20: 00 00 00 00 00 00 00 00 00 00 00 00 28 10 0d 00  "............(..."
  30: 00 00 00 00 40 00 00 00 00 00 00 00 03 01 00 00  "....@..........."

bus 03->04, slot 01, func 0, vend:dev:s_vend:s_dev:rev 1180:0476:1028:024f:ba
class 06, sub_class 07 prog_if 00, hdr 2, flags <>, irq 19
  addr0 f6500000, size 00001000
  00: 80 11 76 04 07 00 10 02 ba 00 07 06 10 a8 82 00  "..v............."
  10: 00 00 50 f6 dc 00 00 02 03 04 07 b0 00 00 00 f1  "..P............."
  20: 00 f0 3f f1 00 00 40 f1 00 f0 7f f1 00 20 00 00  "..?...@...... .."
  30: fc 20 00 00 00 24 00 00 fc 24 00 00 0a 01 80 05  ". ...$...$......"

bus 03, slot 01, func 1, vend:dev:s_vend:s_dev:rev 1180:0832:1028:024f:04
class 0c, sub_class 00 prog_if 10, hdr 0, flags <>, irq 17
  addr0 f65ff800, size 00000800
  00: 80 11 32 08 06 01 10 02 04 10 00 0c 10 40 80 00  "..2..........@.."
  10: 00 f8 5f f6 00 00 00 00 00 00 00 00 00 00 00 00  ".._............."
  20: 00 00 00 00 00 00 00 00 00 00 00 00 28 10 4f 02  "............(.O."
  30: 00 00 00 00 dc 00 00 00 00 00 00 00 03 02 02 04  "................"

bus 03, slot 01, func 2, vend:dev:s_vend:s_dev:rev 1180:0822:1028:024f:21
class 08, sub_class 05 prog_if 01, hdr 0, flags <>, irq 18
  addr0 f65ff700, size 00000100
  00: 80 11 22 08 06 01 10 02 21 01 05 08 10 40 80 00  "..".....!....@.."
  10: 00 f7 5f f6 00 00 00 00 00 00 00 00 00 00 00 00  ".._............."
  20: 00 00 00 00 00 00 00 00 00 00 00 00 28 10 4f 02  "............(.O."
  30: 00 00 00 00 80 00 00 00 00 00 00 00 0b 03 00 00  "................"
---------- PCI raw data end ----------
>> pci.4: build list
>> pci.3: macio
sysfs: no such bus: macio
>> pci.4: vio
sysfs: no such bus: vio
>> pci.5: xen
sysfs: no such bus: xen
>> pci.6: ps3
sysfs: no such bus: ps3_system_bus
>> pci.7: platform
  platform device: name = reg-dummy
    path = /devices/platform/reg-dummy
    type = "platform:reg-dummy"
  platform device: sf_eth_net = (null) sf_eth_dev = (nil)
  platform device: name = pcspkr
    path = /devices/platform/pcspkr
    type = "platform:pcspkr"
  platform device: sf_eth_net = (null) sf_eth_dev = (nil)
  platform device: name = alarmtimer
    path = /devices/platform/alarmtimer
    type = "platform:alarmtimer"
  platform device: sf_eth_net = (null) sf_eth_dev = (nil)
  platform device: name = serial8250
    path = /devices/platform/serial8250
    type = "platform:serial8250"
  platform device: sf_eth_net = (null) sf_eth_dev = (nil)
  platform device: name = Fixed MDIO bus.0
    path = /devices/platform/Fixed MDIO bus.0
    type = "platform:Fixed MDIO bus"
  platform device: sf_eth_net = (null) sf_eth_dev = (nil)
  platform device: name = i8042
    path = /devices/platform/i8042
    type = "platform:i8042"
  platform device: sf_eth_net = (null) sf_eth_dev = (nil)
  platform device: name = dcdbas
    path = /devices/platform/dcdbas
    type = "platform:dcdbas"
  platform device: sf_eth_net = (null) sf_eth_dev = (nil)
  platform device: name = dell-laptop
    path = /devices/platform/dell-laptop
    type = "platform:dell-laptop"
  platform device: sf_eth_net = (null) sf_eth_dev = (nil)
  platform device: name = vboxdrv.0
    path = /devices/platform/vboxdrv.0
    type = "platform:vboxdrv"
  platform device: sf_eth_net = (null) sf_eth_dev = (nil)
>> pci.8: of_platform
sysfs: no such bus: of_platform
>> pci.9: vm
sysfs: no such bus: vm
>> pci.10: virtio
sysfs: no such bus: virtio
>> pci.11: ibmebus
sysfs: no such bus: ibmebus
>> monitor.1: ddc
>> monitor.2: bios
>> monitor.3: pci
>> monitor.4: internal db
>> monitor.5: prom
>> pcmcia.1: sysfs drivers
>> pcmcia.2: pcmcia
sysfs: no such bus: pcmcia
>> pcmcia.3: pcmcia ctrl
sysfs: no such class: pcmcia_socket
>> serial.1: read info
----- serial info -----
----- serial info end -----
>> serial.2: build list
>> misc.5: misc data
----- misc resources -----
i/o:0 0x0000 - 0x0cf7 (0xcf8) "PCI Bus 0000:00"
i/o:1 0x0000 - 0x001f (0x20) "dma1"
i/o:1 0x0020 - 0x0021 (0x02) "pic1"
i/o:0 0x0040 - 0x0043 (0x04) "timer0"
i/o:0 0x0050 - 0x0053 (0x04) "timer1"
i/o:1 0x0060 - 0x0060 (0x01) "keyboard"
i/o:1 0x0064 - 0x0064 (0x01) "keyboard"
i/o:0 0x0070 - 0x0071 (0x02) "rtc0"
i/o:1 0x0080 - 0x008f (0x10) "dma page reg"
i/o:1 0x00a0 - 0x00a1 (0x02) "pic2"
i/o:1 0x00c0 - 0x00df (0x20) "dma2"
i/o:1 0x00f0 - 0x00ff (0x10) "fpu"
i/o:1 0x0378 - 0x037a (0x03) "parport0"
i/o:1 0x03f8 - 0x03ff (0x08) "serial"
i/o:0 0x04d0 - 0x04d1 (0x02) "pnp 00:0c"
i/o:1 0x0778 - 0x077a (0x03) "parport0"
i/o:0 0x0809 - 0x0809 (0x01) "pnp 00:0d"
i/o:0 0x0900 - 0x092f (0x30) "pnp 00:0c"
i/o:0 0x0930 - 0x0930 (0x01) "EC data"
i/o:0 0x0931 - 0x0933 (0x03) "pnp 00:0c"
i/o:0 0x0934 - 0x0934 (0x01) "EC cmd"
i/o:0 0x0935 - 0x097f (0x4b) "pnp 00:0c"
i/o:0 0x0c80 - 0x0caf (0x30) "pnp 00:05"
i/o:0 0x0cb0 - 0x0cbb (0x0c) "pnp 00:0b"
i/o:0 0x0cf8 - 0x0cff (0x08) "PCI conf1"
i/o:0 0x0d00 - 0xffff (0xf300) "PCI Bus 0000:00"
i/o:0 0x1000 - 0x1005 (0x06) "pnp 00:0c"
i/o:0 0x1000 - 0x1003 (0x04) "ACPI PM1a_EVT_BLK"
i/o:0 0x1004 - 0x1005 (0x02) "ACPI PM1a_CNT_BLK"
i/o:0 0x1006 - 0x1007 (0x02) "pnp 00:0d"
i/o:0 0x1008 - 0x100f (0x08) "pnp 00:0c"
i/o:0 0x1008 - 0x100b (0x04) "ACPI PM_TMR"
i/o:0 0x1010 - 0x102f (0x20) "pnp 00:0d"
i/o:0 0x1010 - 0x1015 (0x06) "ACPI CPU throttle"
i/o:0 0x1020 - 0x102f (0x10) "ACPI GPE0_BLK"
i/o:0 0x1050 - 0x1050 (0x01) "ACPI PM2_CNT_BLK"
i/o:0 0x1060 - 0x107f (0x20) "pnp 00:0d"
i/o:0 0x1080 - 0x10bf (0x40) "pnp 00:0d"
i/o:0 0x1100 - 0x111f (0x20) "0000:00:1f.3"
i/o:0 0x1100 - 0x111f (0x20) "pnp 00:0d"
i/o:0 0x2000 - 0x2fff (0x1000) "PCI Bus 0000:03"
i/o:0 0x2000 - 0x20ff (0x100) "PCI CardBus 0000:04"
i/o:0 0x2400 - 0x24ff (0x100) "PCI CardBus 0000:04"
i/o:0 0x3000 - 0x3fff (0x1000) "PCI Bus 0000:0d"
i/o:0 0x4000 - 0x4fff (0x1000) "PCI Bus 0000:0c"
i/o:0 0x5000 - 0x5fff (0x1000) "PCI Bus 0000:0b"
i/o:0 0x6e70 - 0x6e77 (0x08) "0000:00:1f.2"
i/o:0 0x6e70 - 0x6e77 (0x08) "ahci"
i/o:0 0x6e78 - 0x6e7b (0x04) "0000:00:1f.2"
i/o:0 0x6e78 - 0x6e7b (0x04) "ahci"
i/o:0 0x6e80 - 0x6e87 (0x08) "0000:00:1f.2"
i/o:0 0x6e80 - 0x6e87 (0x08) "ahci"
i/o:0 0x6e88 - 0x6e8b (0x04) "0000:00:1f.2"
i/o:0 0x6e88 - 0x6e8b (0x04) "ahci"
i/o:0 0x6ea0 - 0x6ebf (0x20) "0000:00:1f.2"
i/o:0 0x6ea0 - 0x6ebf (0x20) "ahci"
i/o:0 0x6f00 - 0x6f1f (0x20) "0000:00:1d.0"
i/o:0 0x6f00 - 0x6f1f (0x20) "uhci_hcd"
i/o:0 0x6f20 - 0x6f3f (0x20) "0000:00:1d.1"
i/o:0 0x6f20 - 0x6f3f (0x20) "uhci_hcd"
i/o:0 0x6f40 - 0x6f5f (0x20) "0000:00:1d.2"
i/o:0 0x6f40 - 0x6f5f (0x20) "uhci_hcd"
i/o:0 0x6f60 - 0x6f7f (0x20) "0000:00:1a.0"
i/o:0 0x6f60 - 0x6f7f (0x20) "uhci_hcd"
i/o:0 0x6f80 - 0x6f9f (0x20) "0000:00:1a.1"
i/o:0 0x6f80 - 0x6f9f (0x20) "uhci_hcd"
i/o:0 0x6fa0 - 0x6fbf (0x20) "0000:00:1a.2"
i/o:0 0x6fa0 - 0x6fbf (0x20) "uhci_hcd"
i/o:0 0xd000 - 0xdfff (0x1000) "PCI Bus 0000:0e"
i/o:0 0xef98 - 0xef9f (0x08) "0000:00:02.0"
i/o:0 0xefe0 - 0xefff (0x20) "0000:00:19.0"
i/o:0 0xf400 - 0xf4fe (0xff) "pnp 00:0d"
irq:1  0 (   109850) "timer"
irq:0  1 (     1829) "i8042"
irq:1  4 (        3) "serial"
irq:1  7 (        0) "parport0"
irq:0  8 (        1) "rtc0"
irq:0  9 (      234) "acpi"
irq:0 12 (      114) "i8042"
irq:0 17 (     1031) "firewire_ohci" "eth2"
irq:0 18 (     1031) "mmc0"
irq:0 19 (        0) "yenta"
irq:0 20 (      172) "ehci_hcd:usb2" "uhci_hcd:usb3" "uhci_hcd:usb6"
irq:0 21 (        0) "uhci_hcd:usb4" "uhci_hcd:usb7"
irq:0 22 (    17429) "ehci_hcd:usb1" "uhci_hcd:usb5" "uhci_hcd:usb8"
irq:0 44 (     3287) "eth0"
irq:0 45 (    74222) "ahci"
irq:0 46 (    65392) "i915"
irq:0 47 (      329) "hda_intel"
dma:1 1 "parport0"
dma:1 4 "cascade"
----- misc resources end -----
>> parallel.1: pp mod
----- exec: "/sbin/rmmod lp" -----
  ERROR: Removing 'lp': Operation not permitted
----- return code: ? -----
----- exec: "/sbin/rmmod parport_pc" -----
  ERROR: Module parport_pc is in use
----- return code: ? -----
>> parallel.2.1: lp read info
>> parallel.2.2: lp read info
>> parallel.2.3: lp read info
----- parallel info -----
/proc/sys/dev/parport/parport0/base-addr
  888	1912
/proc/sys/dev/parport/parport0/autoprobe
----- parallel info end -----
>> parallel.5: ppa mod
----- exec: "/sbin/modprobe ppa " -----
  FATAL: Error inserting ppa (/lib/modules/3.0.0-14-generic/kernel/drivers/scsi/ppa.ko): Operation not permitted
----- return code: ? -----
>> block.1: block modules
----- exec: "/sbin/modprobe ide-cd_mod " -----
  FATAL: Module ide_cd_mod not found.
----- return code: ? -----
----- exec: "/sbin/modprobe ide-disk " -----
  FATAL: Module ide_disk not found.
----- return code: ? -----
----- exec: "/sbin/modprobe sr_mod " -----
----- return code: ? -----
----- exec: "/sbin/modprobe sd_mod " -----
----- return code: ? -----
----- exec: "/sbin/modprobe st " -----
  FATAL: Error inserting st (/lib/modules/3.0.0-14-generic/kernel/drivers/scsi/st.ko): Operation not permitted
----- return code: ? -----
>> block.2: sysfs drivers
>> block.3: cdrom
----- /proc/sys/dev/cdrom/info -----
drive name:		sr1	sr0
drive speed:		51	24
drive # of slots:	1	1
Can close tray:		0	1
Can open tray:		1	1
Can lock tray:		1	1
Can change speed:	1	1
Can select disk:	0	0
Can read multisession:	1	1
Can read MCN:		1	1
Reports media changed:	1	1
Can play audio:		1	1
Can write CD-R:		0	1
Can write CD-RW:	0	1
Can read DVD:		0	1
Can write DVD-R:	0	1
Can write DVD-RAM:	0	1
Can read MRW:		1	1
Can write MRW:		1	1
Can write RAM:		1	1
----- /proc/sys/dev/cdrom/info end -----
>> block.4: partition
----- /proc/partitions -----
   179        0    3993600 mmcblk0
   179        1    3989504 mmcblk0p1
     8        0  244198584 sda
     8        1     102400 sda1
     8        2   40960000 sda2
     8        4          1 sda4
     8        5    4352000 sda5
     8        6  198779904 sda6
     8       16  487700480 sdb
     8       17  487699456 sdb1
----- /proc/partitions end -----
disks:
  mmcblk0
  sda
  sdb
partitions:
  mmcblk0p1
  sda1
  sda2
  sda4
  sda5
  sda6
  sdb1
>> block.5: get sysfs block dev data
-----  lsscsi -----
-----  lsscsi end -----
  block: name = ram0, path = /class/block/ram0
    dev = 1:0
    range = 1
  block: name = ram1, path = /class/block/ram1
    dev = 1:1
    range = 1
  block: name = ram2, path = /class/block/ram2
    dev = 1:2
    range = 1
  block: name = ram3, path = /class/block/ram3
    dev = 1:3
    range = 1
  block: name = ram4, path = /class/block/ram4
    dev = 1:4
    range = 1
  block: name = ram5, path = /class/block/ram5
    dev = 1:5
    range = 1
  block: name = ram6, path = /class/block/ram6
    dev = 1:6
    range = 1
  block: name = ram7, path = /class/block/ram7
    dev = 1:7
    range = 1
  block: name = ram8, path = /class/block/ram8
    dev = 1:8
    range = 1
  block: name = ram9, path = /class/block/ram9
    dev = 1:9
    range = 1
  block: name = ram10, path = /class/block/ram10
    dev = 1:10
    range = 1
  block: name = ram11, path = /class/block/ram11
    dev = 1:11
    range = 1
  block: name = ram12, path = /class/block/ram12
    dev = 1:12
    range = 1
  block: name = ram13, path = /class/block/ram13
    dev = 1:13
    range = 1
  block: name = ram14, path = /class/block/ram14
    dev = 1:14
    range = 1
  block: name = ram15, path = /class/block/ram15
    dev = 1:15
    range = 1
  block: name = loop0, path = /class/block/loop0
    dev = 7:0
    range = 1
  block: name = loop1, path = /class/block/loop1
    dev = 7:1
    range = 1
  block: name = loop2, path = /class/block/loop2
    dev = 7:2
    range = 1
  block: name = loop3, path = /class/block/loop3
    dev = 7:3
    range = 1
  block: name = loop4, path = /class/block/loop4
    dev = 7:4
    range = 1
  block: name = loop5, path = /class/block/loop5
    dev = 7:5
    range = 1
  block: name = loop6, path = /class/block/loop6
    dev = 7:6
    range = 1
  block: name = loop7, path = /class/block/loop7
    dev = 7:7
    range = 1
  block: name = mmcblk0, path = /class/block/mmcblk0
    dev = 179:0
    range = 8
    block device: bus = mmc, bus_id = mmc0:0007 driver = mmcblk
      path = /devices/pci0000:00/0000:00:1e.0/0000:03:01.2/mmc_host/mmc0/mmc0:0007
>> block.5: /dev/mmcblk0
  block: name = mmcblk0p1, path = /class/block/mmcblk0p1
    dev = 179:1
  block: name = sda, path = /class/block/sda
    dev = 8:0
    range = 16
    block device: bus = scsi, bus_id = 0:0:0:0 driver = sd
      path = /devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0
    vendor = ATA
    model = ST9250410ASG
    rev = 0002
    type = 0
>> block.5: /dev/sda
  block: name = sda1, path = /class/block/sda1
    dev = 8:1
  block: name = sda2, path = /class/block/sda2
    dev = 8:2
  block: name = sda4, path = /class/block/sda4
    dev = 8:4
  block: name = sda5, path = /class/block/sda5
    dev = 8:5
  block: name = sda6, path = /class/block/sda6
    dev = 8:6
  block: name = sr0, path = /class/block/sr0
    dev = 11:0
    range = 1
    block device: bus = scsi, bus_id = 1:0:0:0 driver = sr
      path = /devices/pci0000:00/0000:00:1f.2/host1/target1:0:0/1:0:0:0
    vendor = HL-DT-ST
    model = DVD+-RW GU10N
    rev = A102
    type = 5
>> block.5: /dev/sr0
>> block.5.1: /dev/sr0 cache
  scsi cache: 0x00
  block: name = sr1, path = /class/block/sr1
    dev = 11:1
    range = 1
    block device: bus = scsi, bus_id = 6:0:0:1 driver = sr
      path = /devices/pci0000:00/0000:00:1a.7/usb1/1-3/1-3.1/1-3.1.3/1-3.1.3:1.0/host6/target6:0:0/6:0:0:1
    vendor = WD
    model = Virtual CD 070A
    rev = 1030
    type = 5
>> block.5: /dev/sr1
>> block.5.1: /dev/sr1 cache
  scsi cache: 0x00
  block: name = sdb, path = /class/block/sdb
    dev = 8:16
    range = 16
    block device: bus = scsi, bus_id = 6:0:0:0 driver = sd
      path = /devices/pci0000:00/0000:00:1a.7/usb1/1-3/1-3.1/1-3.1.3/1-3.1.3:1.0/host6/target6:0:0/6:0:0:0
    vendor = WD
    model = My Passport 070A
    rev = 1030
    type = 0
>> block.5: /dev/sdb
  block: name = sdb1, path = /class/block/sdb1
    dev = 8:17
>> scsi.1: scsi modules
----- exec: "/sbin/modprobe sg " -----
----- return code: ? -----
>> scsi.2: scsi tape
sysfs: no such class: scsi_tape
>> scsi.3: scsi generic
  scsi: name = sg0, path = /class/scsi_generic/sg0
    dev = 21:0
    scsi device: bus_id = 0:0:0:0 driver = sd
      path = /devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0
  scsi: name = sg1, path = /class/scsi_generic/sg1
    dev = 21:1
    scsi device: bus_id = 1:0:0:0 driver = sr
      path = /devices/pci0000:00/0000:00:1f.2/host1/target1:0:0/1:0:0:0
  scsi: name = sg2, path = /class/scsi_generic/sg2
    dev = 21:2
    scsi device: bus_id = 6:0:0:0 driver = sd
      path = /devices/pci0000:00/0000:00:1a.7/usb1/1-3/1-3.1/1-3.1.3/1-3.1.3:1.0/host6/target6:0:0/6:0:0:0
  scsi: name = sg3, path = /class/scsi_generic/sg3
    dev = 21:3
    scsi device: bus_id = 6:0:0:1 driver = sr
      path = /devices/pci0000:00/0000:00:1a.7/usb1/1-3/1-3.1/1-3.1.3/1-3.1.3:1.0/host6/target6:0:0/6:0:0:1
  scsi: name = sg4, path = /class/scsi_generic/sg4
    dev = 21:4
    scsi device: bus_id = 6:0:0:2 driver = ses
      path = /devices/pci0000:00/0000:00:1a.7/usb1/1-3/1-3.1/1-3.1.3/1-3.1.3:1.0/host6/target6:0:0/6:0:0:2
>> usb.1: sysfs drivers
>> usb.2: usb
  usb dev: /devices/pci0000:00/0000:00:1a.7/usb1
  usb dev: /devices/pci0000:00/0000:00:1d.7/usb2
  usb dev: /devices/pci0000:00/0000:00:1a.0/usb3
  usb dev: /devices/pci0000:00/0000:00:1a.1/usb4
  usb dev: /devices/pci0000:00/0000:00:1a.2/usb5
  usb dev: /devices/pci0000:00/0000:00:1d.0/usb6
  usb dev: /devices/pci0000:00/0000:00:1d.1/usb7
  usb dev: /devices/pci0000:00/0000:00:1d.2/usb8
  usb dev: /devices/pci0000:00/0000:00:1a.7/usb1/1-3
  usb dev: /devices/pci0000:00/0000:00:1a.7/usb1/1-4
  usb dev: /devices/pci0000:00/0000:00:1a.7/usb1/1-6
  usb dev: /devices/pci0000:00/0000:00:1a.0/usb3/3-1
  usb dev: /devices/pci0000:00/0000:00:1a.2/usb5/5-1
  usb dev: /devices/pci0000:00/0000:00:1d.0/usb6/6-2
  usb dev: /devices/pci0000:00/0000:00:1a.7/usb1/1-3/1-3.1
  usb dev: /devices/pci0000:00/0000:00:1a.7/usb1/1-3/1-3.2
  usb dev: /devices/pci0000:00/0000:00:1a.7/usb1/1-4/1-4.2
  usb dev: /devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1.1
  usb dev: /devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1.2
  usb dev: /devices/pci0000:00/0000:00:1a.7/usb1/1-3/1-3.1/1-3.1.3
  usb device: name = usb1
    path = /devices/pci0000:00/0000:00:1a.7/usb1
  usb device: name = 1-0:1.0
    path = /devices/pci0000:00/0000:00:1a.7/usb1/1-0:1.0
    modalias = "usb:v1D6Bp0002d0300dc09dsc00dp00ic09isc00ip00"
    bInterfaceNumber = 0
    bInterfaceClass = 9
    bInterfaceSubClass = 0
    bInterfaceProtocol = 0
    if: 1-0:1.0 @ /devices/pci0000:00/0000:00:1a.7/usb1
    bDeviceClass = 9
    bDeviceSubClass = 0
    bDeviceProtocol = 0
    idVendor = 0x1d6b
    idProduct = 0x0002
    manufacturer = "Linux 3.0.0-14-generic ehci_hcd"
    product = "EHCI Host Controller"
    serial = "0000:00:1a.7"
    bcdDevice = 0300
    speed = "480"
  usb device: name = usb2
    path = /devices/pci0000:00/0000:00:1d.7/usb2
  usb device: name = 2-0:1.0
    path = /devices/pci0000:00/0000:00:1d.7/usb2/2-0:1.0
    modalias = "usb:v1D6Bp0002d0300dc09dsc00dp00ic09isc00ip00"
    bInterfaceNumber = 0
    bInterfaceClass = 9
    bInterfaceSubClass = 0
    bInterfaceProtocol = 0
    if: 2-0:1.0 @ /devices/pci0000:00/0000:00:1d.7/usb2
    bDeviceClass = 9
    bDeviceSubClass = 0
    bDeviceProtocol = 0
    idVendor = 0x1d6b
    idProduct = 0x0002
    manufacturer = "Linux 3.0.0-14-generic ehci_hcd"
    product = "EHCI Host Controller"
    serial = "0000:00:1d.7"
    bcdDevice = 0300
    speed = "480"
  usb device: name = usb3
    path = /devices/pci0000:00/0000:00:1a.0/usb3
  usb device: name = 3-0:1.0
    path = /devices/pci0000:00/0000:00:1a.0/usb3/3-0:1.0
    modalias = "usb:v1D6Bp0001d0300dc09dsc00dp00ic09isc00ip00"
    bInterfaceNumber = 0
    bInterfaceClass = 9
    bInterfaceSubClass = 0
    bInterfaceProtocol = 0
    if: 3-0:1.0 @ /devices/pci0000:00/0000:00:1a.0/usb3
    bDeviceClass = 9
    bDeviceSubClass = 0
    bDeviceProtocol = 0
    idVendor = 0x1d6b
    idProduct = 0x0001
    manufacturer = "Linux 3.0.0-14-generic uhci_hcd"
    product = "UHCI Host Controller"
    serial = "0000:00:1a.0"
    bcdDevice = 0300
    speed = "12"
  usb device: name = usb4
    path = /devices/pci0000:00/0000:00:1a.1/usb4
  usb device: name = 4-0:1.0
    path = /devices/pci0000:00/0000:00:1a.1/usb4/4-0:1.0
    modalias = "usb:v1D6Bp0001d0300dc09dsc00dp00ic09isc00ip00"
    bInterfaceNumber = 0
    bInterfaceClass = 9
    bInterfaceSubClass = 0
    bInterfaceProtocol = 0
    if: 4-0:1.0 @ /devices/pci0000:00/0000:00:1a.1/usb4
    bDeviceClass = 9
    bDeviceSubClass = 0
    bDeviceProtocol = 0
    idVendor = 0x1d6b
    idProduct = 0x0001
    manufacturer = "Linux 3.0.0-14-generic uhci_hcd"
    product = "UHCI Host Controller"
    serial = "0000:00:1a.1"
    bcdDevice = 0300
    speed = "12"
  usb device: name = usb5
    path = /devices/pci0000:00/0000:00:1a.2/usb5
  usb device: name = 5-0:1.0
    path = /devices/pci0000:00/0000:00:1a.2/usb5/5-0:1.0
    modalias = "usb:v1D6Bp0001d0300dc09dsc00dp00ic09isc00ip00"
    bInterfaceNumber = 0
    bInterfaceClass = 9
    bInterfaceSubClass = 0
    bInterfaceProtocol = 0
    if: 5-0:1.0 @ /devices/pci0000:00/0000:00:1a.2/usb5
    bDeviceClass = 9
    bDeviceSubClass = 0
    bDeviceProtocol = 0
    idVendor = 0x1d6b
    idProduct = 0x0001
    manufacturer = "Linux 3.0.0-14-generic uhci_hcd"
    product = "UHCI Host Controller"
    serial = "0000:00:1a.2"
    bcdDevice = 0300
    speed = "12"
  usb device: name = usb6
    path = /devices/pci0000:00/0000:00:1d.0/usb6
  usb device: name = 6-0:1.0
    path = /devices/pci0000:00/0000:00:1d.0/usb6/6-0:1.0
    modalias = "usb:v1D6Bp0001d0300dc09dsc00dp00ic09isc00ip00"
    bInterfaceNumber = 0
    bInterfaceClass = 9
    bInterfaceSubClass = 0
    bInterfaceProtocol = 0
    if: 6-0:1.0 @ /devices/pci0000:00/0000:00:1d.0/usb6
    bDeviceClass = 9
    bDeviceSubClass = 0
    bDeviceProtocol = 0
    idVendor = 0x1d6b
    idProduct = 0x0001
    manufacturer = "Linux 3.0.0-14-generic uhci_hcd"
    product = "UHCI Host Controller"
    serial = "0000:00:1d.0"
    bcdDevice = 0300
    speed = "12"
  usb device: name = usb7
    path = /devices/pci0000:00/0000:00:1d.1/usb7
  usb device: name = 7-0:1.0
    path = /devices/pci0000:00/0000:00:1d.1/usb7/7-0:1.0
    modalias = "usb:v1D6Bp0001d0300dc09dsc00dp00ic09isc00ip00"
    bInterfaceNumber = 0
    bInterfaceClass = 9
    bInterfaceSubClass = 0
    bInterfaceProtocol = 0
    if: 7-0:1.0 @ /devices/pci0000:00/0000:00:1d.1/usb7
    bDeviceClass = 9
    bDeviceSubClass = 0
    bDeviceProtocol = 0
    idVendor = 0x1d6b
    idProduct = 0x0001
    manufacturer = "Linux 3.0.0-14-generic uhci_hcd"
    product = "UHCI Host Controller"
    serial = "0000:00:1d.1"
    bcdDevice = 0300
    speed = "12"
  usb device: name = usb8
    path = /devices/pci0000:00/0000:00:1d.2/usb8
  usb device: name = 8-0:1.0
    path = /devices/pci0000:00/0000:00:1d.2/usb8/8-0:1.0
    modalias = "usb:v1D6Bp0001d0300dc09dsc00dp00ic09isc00ip00"
    bInterfaceNumber = 0
    bInterfaceClass = 9
    bInterfaceSubClass = 0
    bInterfaceProtocol = 0
    if: 8-0:1.0 @ /devices/pci0000:00/0000:00:1d.2/usb8
    bDeviceClass = 9
    bDeviceSubClass = 0
    bDeviceProtocol = 0
    idVendor = 0x1d6b
    idProduct = 0x0001
    manufacturer = "Linux 3.0.0-14-generic uhci_hcd"
    product = "UHCI Host Controller"
    serial = "0000:00:1d.2"
    bcdDevice = 0300
    speed = "12"
  usb device: name = 1-3
    path = /devices/pci0000:00/0000:00:1a.7/usb1/1-3
  usb device: name = 1-3:1.0
    path = /devices/pci0000:00/0000:00:1a.7/usb1/1-3/1-3:1.0
    modalias = "usb:v413Cp2513dA005dc09dsc00dp02ic09isc00ip02"
    bInterfaceNumber = 0
    bInterfaceClass = 9
    bInterfaceSubClass = 0
    bInterfaceProtocol = 2
    if: 1-3:1.0 @ /devices/pci0000:00/0000:00:1a.7/usb1/1-3
    bDeviceClass = 9
    bDeviceSubClass = 0
    bDeviceProtocol = 2
    idVendor = 0x413c
    idProduct = 0x2513
    bcdDevice = a005
    speed = "480"
  usb device: name = 1-4
    path = /devices/pci0000:00/0000:00:1a.7/usb1/1-4
  usb device: name = 1-4:1.0
    path = /devices/pci0000:00/0000:00:1a.7/usb1/1-4/1-4:1.0
    modalias = "usb:v413Cp2513dA005dc09dsc00dp02ic09isc00ip02"
    bInterfaceNumber = 0
    bInterfaceClass = 9
    bInterfaceSubClass = 0
    bInterfaceProtocol = 2
    if: 1-4:1.0 @ /devices/pci0000:00/0000:00:1a.7/usb1/1-4
    bDeviceClass = 9
    bDeviceSubClass = 0
    bDeviceProtocol = 2
    idVendor = 0x413c
    idProduct = 0x2513
    bcdDevice = a005
    speed = "480"
  usb device: name = 1-6
    path = /devices/pci0000:00/0000:00:1a.7/usb1/1-6
  usb device: name = 1-6:1.0
    path = /devices/pci0000:00/0000:00:1a.7/usb1/1-6/1-6:1.0
    modalias = "usb:v0C45p63F1d9416dcEFdsc02dp01ic0Eisc01ip00"
    bInterfaceNumber = 0
    bInterfaceClass = 14
    bInterfaceSubClass = 1
    bInterfaceProtocol = 0
    if: 1-6:1.0 @ /devices/pci0000:00/0000:00:1a.7/usb1/1-6
    bDeviceClass = 239
    bDeviceSubClass = 2
    bDeviceProtocol = 1
    idVendor = 0x0c45
    idProduct = 0x63f1
    manufacturer = "CN0K113P7248703G05EC"
    product = "Integrated_Webcam_2M"
    bcdDevice = 9416
    speed = "480"
  usb device: name = 1-6:1.1
    path = /devices/pci0000:00/0000:00:1a.7/usb1/1-6/1-6:1.1
    modalias = "usb:v0C45p63F1d9416dcEFdsc02dp01ic0Eisc02ip00"
    bInterfaceNumber = 1
    bInterfaceClass = 14
    bInterfaceSubClass = 2
    bInterfaceProtocol = 0
    if: 1-6:1.1 @ /devices/pci0000:00/0000:00:1a.7/usb1/1-6
    bDeviceClass = 239
    bDeviceSubClass = 2
    bDeviceProtocol = 1
    idVendor = 0x0c45
    idProduct = 0x63f1
    manufacturer = "CN0K113P7248703G05EC"
    product = "Integrated_Webcam_2M"
    bcdDevice = 9416
    speed = "480"
  usb device: name = 3-1
    path = /devices/pci0000:00/0000:00:1a.0/usb3/3-1
  usb device: name = 3-1:1.0
    path = /devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1:1.0
    modalias = "usb:v0A5Cp4500d0100dc09dsc00dp00ic09isc00ip00"
    bInterfaceNumber = 0
    bInterfaceClass = 9
    bInterfaceSubClass = 0
    bInterfaceProtocol = 0
    if: 3-1:1.0 @ /devices/pci0000:00/0000:00:1a.0/usb3/3-1
    bDeviceClass = 9
    bDeviceSubClass = 0
    bDeviceProtocol = 0
    idVendor = 0x0a5c
    idProduct = 0x4500
    manufacturer = "Broadcom"
    product = "BCM2046B1"
    bcdDevice = 0100
    speed = "12"
  usb device: name = 5-1
    path = /devices/pci0000:00/0000:00:1a.2/usb5/5-1
  usb device: name = 5-1:0.0
    path = /devices/pci0000:00/0000:00:1a.2/usb5/5-1/5-1:0.0
    modalias = "usb:v0A5Cp5800d0101dc00dsc00dp00icFEisc00ip00"
    bInterfaceNumber = 0
    bInterfaceClass = 254
    bInterfaceSubClass = 0
    bInterfaceProtocol = 0
    if: 5-1:0.0 @ /devices/pci0000:00/0000:00:1a.2/usb5/5-1
    bDeviceClass = 0
    bDeviceSubClass = 0
    bDeviceProtocol = 0
    idVendor = 0x0a5c
    idProduct = 0x5800
    manufacturer = "Broadcom Corp"
    product = "5880"
    serial = "0123456789ABCD"
    bcdDevice = 0101
    speed = "12"
  usb device: name = 5-1:0.1
    path = /devices/pci0000:00/0000:00:1a.2/usb5/5-1/5-1:0.1
    modalias = "usb:v0A5Cp5800d0101dc00dsc00dp00ic0Bisc00ip00"
    bInterfaceNumber = 1
    bInterfaceClass = 11
    bInterfaceSubClass = 0
    bInterfaceProtocol = 0
    if: 5-1:0.1 @ /devices/pci0000:00/0000:00:1a.2/usb5/5-1
    bDeviceClass = 0
    bDeviceSubClass = 0
    bDeviceProtocol = 0
    idVendor = 0x0a5c
    idProduct = 0x5800
    manufacturer = "Broadcom Corp"
    product = "5880"
    serial = "0123456789ABCD"
    bcdDevice = 0101
    speed = "12"
  usb device: name = 6-2
    path = /devices/pci0000:00/0000:00:1d.0/usb6/6-2
  usb device: name = 6-2:1.0
    path = /devices/pci0000:00/0000:00:1d.0/usb6/6-2/6-2:1.0
    modalias = "usb:v0BAFp00ECd0001dcFFdscFFdpFFicFFiscFFipFF"
    bInterfaceNumber = 0
    bInterfaceClass = 255
    bInterfaceSubClass = 255
    bInterfaceProtocol = 255
    if: 6-2:1.0 @ /devices/pci0000:00/0000:00:1d.0/usb6/6-2
    bDeviceClass = 255
    bDeviceSubClass = 255
    bDeviceProtocol = 255
    idVendor = 0x0baf
    idProduct = 0x00ec
    manufacturer = "U.S. Robotics"
    product = "U.S. Robotics 56K Faxmodem USB"
    serial = "USBHCF00000006"
    bcdDevice = 0001
    speed = "12"
  usb device: name = 1-3.1
    path = /devices/pci0000:00/0000:00:1a.7/usb1/1-3/1-3.1
  usb device: name = 1-3.1:1.0
    path = /devices/pci0000:00/0000:00:1a.7/usb1/1-3/1-3.1/1-3.1:1.0
    modalias = "usb:v0424p2514d0000dc09dsc00dp02ic09isc00ip02"
    bInterfaceNumber = 0
    bInterfaceClass = 9
    bInterfaceSubClass = 0
    bInterfaceProtocol = 2
    if: 1-3.1:1.0 @ /devices/pci0000:00/0000:00:1a.7/usb1/1-3/1-3.1
    bDeviceClass = 9
    bDeviceSubClass = 0
    bDeviceProtocol = 2
    idVendor = 0x0424
    idProduct = 0x2514
    bcdDevice = 0000
    speed = "480"
  usb device: name = 1-3.2
    path = /devices/pci0000:00/0000:00:1a.7/usb1/1-3/1-3.2
  usb device: name = 1-3.2:1.0
    path = /devices/pci0000:00/0000:00:1a.7/usb1/1-3/1-3.2/1-3.2:1.0
    modalias = "usb:v0424p2514d0BB3dc09dsc00dp02ic09isc00ip02"
    bInterfaceNumber = 0
    bInterfaceClass = 9
    bInterfaceSubClass = 0
    bInterfaceProtocol = 2
    if: 1-3.2:1.0 @ /devices/pci0000:00/0000:00:1a.7/usb1/1-3/1-3.2
    bDeviceClass = 9
    bDeviceSubClass = 0
    bDeviceProtocol = 2
    idVendor = 0x0424
    idProduct = 0x2514
    bcdDevice = 0bb3
    speed = "480"
  usb device: name = 1-4.2
    path = /devices/pci0000:00/0000:00:1a.7/usb1/1-4/1-4.2
  usb device: name = 1-4.2:1.0
    path = /devices/pci0000:00/0000:00:1a.7/usb1/1-4/1-4.2/1-4.2:1.0
    modalias = "usb:v046DpC016d0340dc00dsc00dp00ic03isc01ip02"
    bInterfaceNumber = 0
    bInterfaceClass = 3
    bInterfaceSubClass = 1
    bInterfaceProtocol = 2
    if: 1-4.2:1.0 @ /devices/pci0000:00/0000:00:1a.7/usb1/1-4/1-4.2
    bDeviceClass = 0
    bDeviceSubClass = 0
    bDeviceProtocol = 0
    idVendor = 0x046d
    idProduct = 0xc016
    manufacturer = "Logitech"
    product = "Optical USB Mouse"
    bcdDevice = 0340
    speed = "1.5"
  usb device: name = 3-1.1
    path = /devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1.1
  usb device: name = 3-1.1:1.0
    path = /devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1.1/3-1.1:1.0
    modalias = "usb:v413Cp8157d0100dc00dsc00dp00ic03isc01ip01"
    bInterfaceNumber = 0
    bInterfaceClass = 3
    bInterfaceSubClass = 1
    bInterfaceProtocol = 1
    if: 3-1.1:1.0 @ /devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1.1
    bDeviceClass = 0
    bDeviceSubClass = 0
    bDeviceProtocol = 0
    idVendor = 0x413c
    idProduct = 0x8157
    bcdDevice = 0100
    speed = "12"
  usb device: name = 3-1.2
    path = /devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1.2
  usb device: name = 3-1.2:1.0
    path = /devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1.2/3-1.2:1.0
    modalias = "usb:v413Cp8158d0100dc00dsc00dp00ic03isc01ip02"
    bInterfaceNumber = 0
    bInterfaceClass = 3
    bInterfaceSubClass = 1
    bInterfaceProtocol = 2
    if: 3-1.2:1.0 @ /devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1.2
    bDeviceClass = 0
    bDeviceSubClass = 0
    bDeviceProtocol = 0
    idVendor = 0x413c
    idProduct = 0x8158
    bcdDevice = 0100
    speed = "12"
  usb device: name = 1-3.1.3
    path = /devices/pci0000:00/0000:00:1a.7/usb1/1-3/1-3.1/1-3.1.3
  usb device: name = 1-3.1.3:1.0
    path = /devices/pci0000:00/0000:00:1a.7/usb1/1-3/1-3.1/1-3.1.3/1-3.1.3:1.0
    modalias = "usb:v1058p070Ad1030dc00dsc00dp00ic08isc06ip50"
    bInterfaceNumber = 0
    bInterfaceClass = 8
    bInterfaceSubClass = 6
    bInterfaceProtocol = 80
    if: 1-3.1.3:1.0 @ /devices/pci0000:00/0000:00:1a.7/usb1/1-3/1-3.1/1-3.1.3
    bDeviceClass = 0
    bDeviceSubClass = 0
    bDeviceProtocol = 0
    idVendor = 0x1058
    idProduct = 0x070a
    manufacturer = "Western Digital"
    product = "My Passport 070A"
    serial = "57584D304139395330373331"
    bcdDevice = 1030
    speed = "480"
removed: /devices/pci0000:00/0000:00:1a.7/usb1/1-6/1-6:1.1
removed: /devices/pci0000:00/0000:00:1a.2/usb5/5-1/5-1:0.1
>> usb.3.1: joydev mod
>> usb.3.2: evdev mod
----- exec: "/sbin/modprobe evdev " -----
----- return code: ? -----
>> usb.3.3: input
  input: name = input0, path = /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
    no dev - ignored
  input: name = input1, path = /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
    no dev - ignored
  input: name = input2, path = /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
    no dev - ignored
  input: name = mice, path = /devices/virtual/input/mice
    dev = 13:63
  input: name = event0, path = /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0/event0
    dev = 13:64
    input device: bus = acpi, bus_id = PNP0C0D:00 driver = button
      path = /devices/LNXSYSTM:00/device:00/PNP0C0D:00
  input: name = event1, path = /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1/event1
    dev = 13:65
    input device: bus = acpi, bus_id = PNP0C0C:00 driver = button
      path = /devices/LNXSYSTM:00/device:00/PNP0C0C:00
  input: name = event2, path = /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2/event2
    dev = 13:66
    input device: bus = acpi, bus_id = PNP0C0E:00 driver = button
      path = /devices/LNXSYSTM:00/device:00/PNP0C0E:00
  input: name = input3, path = /devices/platform/i8042/serio0/input/input3
    no dev - ignored
  input: name = event3, path = /devices/platform/i8042/serio0/input/input3/event3
    dev = 13:67
    input device: bus = serio, bus_id = serio0 driver = atkbd
      path = /devices/platform/i8042/serio0
  input: name = input4, path = /devices/pci0000:00/0000:00:1a.7/usb1/1-4/1-4.2/1-4.2:1.0/input/input4
    no dev - ignored
  input: name = mouse0, path = /devices/pci0000:00/0000:00:1a.7/usb1/1-4/1-4.2/1-4.2:1.0/input/input4/mouse0
    dev = 13:32
    input device: bus = usb, bus_id = 1-4.2:1.0 driver = usbhid
      path = /devices/pci0000:00/0000:00:1a.7/usb1/1-4/1-4.2/1-4.2:1.0
  input: name = event4, path = /devices/pci0000:00/0000:00:1a.7/usb1/1-4/1-4.2/1-4.2:1.0/input/input4/event4
    dev = 13:68
    input device: bus = usb, bus_id = 1-4.2:1.0 driver = usbhid
      path = /devices/pci0000:00/0000:00:1a.7/usb1/1-4/1-4.2/1-4.2:1.0
  input: name = input5, path = /devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1.1/3-1.1:1.0/input/input5
    no dev - ignored
  input: name = event5, path = /devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1.1/3-1.1:1.0/input/input5/event5
    dev = 13:69
    input device: bus = usb, bus_id = 3-1.1:1.0 driver = usbhid
      path = /devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1.1/3-1.1:1.0
  input: name = input7, path = /devices/virtual/input/input7
    no dev - ignored
  input: name = event7, path = /devices/virtual/input/input7/event7
    dev = 13:71
    input device: bus = input, bus_id = input7 driver = (null)
      path = /devices/virtual/input/input7
  input: name = input8, path = /devices/platform/i8042/serio1/input/input8
    no dev - ignored
  input: name = mouse2, path = /devices/platform/i8042/serio1/input/input8/mouse2
    dev = 13:34
    input device: bus = serio, bus_id = serio1 driver = psmouse
      path = /devices/platform/i8042/serio1
  input: name = event8, path = /devices/platform/i8042/serio1/input/input8/event8
    dev = 13:72
    input device: bus = serio, bus_id = serio1 driver = psmouse
      path = /devices/platform/i8042/serio1
  input: name = input9, path = /devices/platform/i8042/serio1/input/input9
    no dev - ignored
  input: name = mouse3, path = /devices/platform/i8042/serio1/input/input9/mouse3
    dev = 13:35
    input device: bus = serio, bus_id = serio1 driver = psmouse
      path = /devices/platform/i8042/serio1
  input: name = event9, path = /devices/platform/i8042/serio1/input/input9/event9
    dev = 13:73
    input device: bus = serio, bus_id = serio1 driver = psmouse
      path = /devices/platform/i8042/serio1
  input: name = input10, path = /devices/pci0000:00/0000:00:1a.7/usb1/1-6/1-6:1.0/input/input10
    no dev - ignored
  input: name = event6, path = /devices/pci0000:00/0000:00:1a.7/usb1/1-6/1-6:1.0/input/input10/event6
    dev = 13:70
    input device: bus = usb, bus_id = 1-6:1.0 driver = uvcvideo
      path = /devices/pci0000:00/0000:00:1a.7/usb1/1-6/1-6:1.0
  input: name = input11, path = /devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:01/input/input11
    no dev - ignored
  input: name = event10, path = /devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:01/input/input11/event10
    dev = 13:74
    input device: bus = acpi, bus_id = LNXVIDEO:01 driver = video
      path = /devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:01
  input: name = input12, path = /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
    no dev - ignored
  input: name = event11, path = /devices/pci0000:00/0000:00:1b.0/sound/card0/input12/event11
    dev = 13:75
    input device: bus = sound, bus_id = card0 driver = (null)
      path = /devices/pci0000:00/0000:00:1b.0/sound/card0
  input: name = input13, path = /devices/pci0000:00/0000:00:1b.0/sound/card0/input13
    no dev - ignored
  input: name = event12, path = /devices/pci0000:00/0000:00:1b.0/sound/card0/input13/event12
    dev = 13:76
    input device: bus = sound, bus_id = card0 driver = (null)
      path = /devices/pci0000:00/0000:00:1b.0/sound/card0
  input: name = input14, path = /devices/pci0000:00/0000:00:1b.0/sound/card0/input14
    no dev - ignored
  input: name = event13, path = /devices/pci0000:00/0000:00:1b.0/sound/card0/input14/event13
    dev = 13:77
    input device: bus = sound, bus_id = card0 driver = (null)
      path = /devices/pci0000:00/0000:00:1b.0/sound/card0
  input: name = input15, path = /devices/pci0000:00/0000:00:1b.0/sound/card0/input15
    no dev - ignored
  input: name = event14, path = /devices/pci0000:00/0000:00:1b.0/sound/card0/input15/event14
    dev = 13:78
    input device: bus = sound, bus_id = card0 driver = (null)
      path = /devices/pci0000:00/0000:00:1b.0/sound/card0
  input: name = input16, path = /devices/pci0000:00/0000:00:1b.0/sound/card0/input16
    no dev - ignored
  input: name = event15, path = /devices/pci0000:00/0000:00:1b.0/sound/card0/input16/event15
    dev = 13:79
    input device: bus = sound, bus_id = card0 driver = (null)
      path = /devices/pci0000:00/0000:00:1b.0/sound/card0
>> usb.3.4: lp
sysfs: no such class: usb
>> usb.3.5: serial
>> edd.1: edd mod
----- exec: "/sbin/modprobe edd " -----
----- return code: ? -----
>> edd.2: edd info
>> modem.1: serial
******  started child process 2741 (15s/120s)  ******
******  stopped child process 2741 (120s)  ******
>> mouse.2: serial
******  started child process 2742 (20s/20s)  ******
******  stopped child process 2742 (20s)  ******
>> input.1: joydev mod
>> input.1.1: evdev mod
----- exec: "/sbin/modprobe evdev " -----
----- return code: ? -----
>> input.2: input
----- /proc/bus/input/devices -----
  I: Bus=0019 Vendor=0000 Product=0005 Version=0000
  N: Name="Lid Switch"
  P: Phys=PNP0C0D/button/input0
  S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
  U: Uniq=
  H: Handlers=event0 
  B: PROP=0
  B: EV=21
  B: SW=1
  
  I: Bus=0019 Vendor=0000 Product=0001 Version=0000
  N: Name="Power Button"
  P: Phys=PNP0C0C/button/input0
  S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
  U: Uniq=
  H: Handlers=kbd event1 
  B: PROP=0
  B: EV=3
  B: KEY=10000000000000 0
  
  I: Bus=0019 Vendor=0000 Product=0003 Version=0000
  N: Name="Sleep Button"
  P: Phys=PNP0C0E/button/input0
  S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
  U: Uniq=
  H: Handlers=kbd event2 
  B: PROP=0
  B: EV=3
  B: KEY=4000 0 0
  
  I: Bus=0011 Vendor=0001 Product=0001 Version=ab41
  N: Name="AT Translated Set 2 keyboard"
  P: Phys=isa0060/serio0/input0
  S: Sysfs=/devices/platform/i8042/serio0/input/input3
  U: Uniq=
  H: Handlers=sysrq kbd event3 
  B: PROP=0
  B: EV=120013
  B: KEY=1100f02902002 8380307cf910f001 feffffdfffefffff fffffffffffffffe
  B: MSC=10
  B: LED=7
  
  I: Bus=0003 Vendor=046d Product=c016 Version=0110
  N: Name="Logitech Optical USB Mouse"
  P: Phys=usb-0000:00:1a.7-4.2/input0
  S: Sysfs=/devices/pci0000:00/0000:00:1a.7/usb1/1-4/1-4.2/1-4.2:1.0/input/input4
  U: Uniq=
  H: Handlers=mouse0 event4 
  B: PROP=0
  B: EV=17
  B: KEY=70000 0 0 0 0
  B: REL=103
  B: MSC=10
  
  I: Bus=0003 Vendor=413c Product=8157 Version=0111
  N: Name="HID 413c:8157"
  P: Phys=usb-0000:00:1a.0-1.1/input0
  S: Sysfs=/devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1.1/3-1.1:1.0/input/input5
  U: Uniq=
  H: Handlers=sysrq kbd event5 
  B: PROP=0
  B: EV=120013
  B: KEY=1000000000007 ff800000000007ff febeffdff3cfffff fffffffffffffffe
  B: MSC=10
  B: LED=7
  
  I: Bus=0019 Vendor=0000 Product=0000 Version=0000
  N: Name="Dell WMI hotkeys"
  P: Phys=wmi/input0
  S: Sysfs=/devices/virtual/input/input7
  U: Uniq=
  H: Handlers=kbd event7 
  B: PROP=0
  B: EV=13
  B: KEY=1101b00000400 100000 e000000000000 0
  B: MSC=10
  
  I: Bus=0011 Vendor=0002 Product=0008 Version=0000
  N: Name="DualPoint Stick"
  P: Phys=isa0060/serio1/input1
  S: Sysfs=/devices/platform/i8042/serio1/input/input8
  U: Uniq=
  H: Handlers=mouse2 event8 
  B: PROP=0
  B: EV=7
  B: KEY=70000 0 0 0 0
  B: REL=3
  
  I: Bus=0011 Vendor=0002 Product=0008 Version=6222
  N: Name="AlpsPS/2 ALPS DualPoint TouchPad"
  P: Phys=isa0060/serio1/input0
  S: Sysfs=/devices/platform/i8042/serio1/input/input9
  U: Uniq=
  H: Handlers=mouse3 event9 
  B: PROP=0
  B: EV=b
  B: KEY=420 70000 0 0 0 0
  B: ABS=1000003
  
  I: Bus=0003 Vendor=0c45 Product=63f1 Version=9416
  N: Name="Integrated_Webcam_2M"
  P: Phys=usb-0000:00:1a.7-6/button
  S: Sysfs=/devices/pci0000:00/0000:00:1a.7/usb1/1-6/1-6:1.0/input/input10
  U: Uniq=
  H: Handlers=kbd event6 
  B: PROP=0
  B: EV=3
  B: KEY=100000 0 0 0
  
  I: Bus=0019 Vendor=0000 Product=0006 Version=0000
  N: Name="Video Bus"
  P: Phys=LNXVIDEO/video/input0
  S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:01/input/input11
  U: Uniq=
  H: Handlers=kbd event10 
  B: PROP=0
  B: EV=3
  B: KEY=3e000b00000000 0 0 0
  
  I: Bus=0000 Vendor=0000 Product=0000 Version=0000
  N: Name="HDA Intel HDMI/DP,pcm=3"
  P: Phys=ALSA
  S: Sysfs=/devices/pci0000:00/0000:00:1b.0/sound/card0/input12
  U: Uniq=
  H: Handlers=event11 
  B: PROP=0
  B: EV=21
  B: SW=100
  
  I: Bus=0000 Vendor=0000 Product=0000 Version=0000
  N: Name="HDA Intel Mic at Sep Left Jack"
  P: Phys=ALSA
  S: Sysfs=/devices/pci0000:00/0000:00:1b.0/sound/card0/input13
  U: Uniq=
  H: Handlers=event12 
  B: PROP=0
  B: EV=21
  B: SW=10
  
  I: Bus=0000 Vendor=0000 Product=0000 Version=0000
  N: Name="HDA Intel Mic at Ext Right Jack"
  P: Phys=ALSA
  S: Sysfs=/devices/pci0000:00/0000:00:1b.0/sound/card0/input14
  U: Uniq=
  H: Handlers=event13 
  B: PROP=0
  B: EV=21
  B: SW=10
  
  I: Bus=0000 Vendor=0000 Product=0000 Version=0000
  N: Name="HDA Intel Line Out at Sep Left Jack"
  P: Phys=ALSA
  S: Sysfs=/devices/pci0000:00/0000:00:1b.0/sound/card0/input15
  U: Uniq=
  H: Handlers=event14 
  B: PROP=0
  B: EV=21
  B: SW=40
  
  I: Bus=0000 Vendor=0000 Product=0000 Version=0000
  N: Name="HDA Intel HP Out at Ext Right Jack"
  P: Phys=ALSA
  S: Sysfs=/devices/pci0000:00/0000:00:1b.0/sound/card0/input16
  U: Uniq=
  H: Handlers=event15 
  B: PROP=0
  B: EV=21
  B: SW=4
  
----- /proc/bus/input/devices end -----
bus = 25, name = Lid Switch
  handlers = event0
  mouse buttons = 0
  mouse wheels = 0
bus = 25, name = Power Button
  handlers = kbd event1
  key = 00100000000000000000000000000000
  mouse buttons = 0
  mouse wheels = 0
bus = 25, name = Sleep Button
  handlers = kbd event2
  key = 000000000000400000000000000000000000000000000000
  mouse buttons = 0
  mouse wheels = 0
bus = 17, name = AT Translated Set 2 keyboard
  handlers = sysrq kbd event3
  key = 0001100f029020028380307cf910f001feffffdfffeffffffffffffffffffffe
  mouse buttons = 0
  mouse wheels = 0
bus = 3, name = Logitech Optical USB Mouse
  handlers = mouse0 event4
  key = 00000000000700000000000000000000000000000000000000000000000000000000000000000000
  rel = 0000000000000103
  mouse buttons = 3
  mouse wheels = 1
bus = 3, name = HID 413c:8157
  handlers = sysrq kbd event5
  key = 0001000000000007ff800000000007fffebeffdff3cffffffffffffffffffffe
  mouse buttons = 0
  mouse wheels = 0
bus = 25, name = Dell WMI hotkeys
  handlers = kbd event7
  key = 0001101b000004000000000000100000000e0000000000000000000000000000
  mouse buttons = 0
  mouse wheels = 0
bus = 17, name = DualPoint Stick
  handlers = mouse2 event8
  key = 00000000000700000000000000000000000000000000000000000000000000000000000000000000
  rel = 0000000000000003
  mouse buttons = 3
  mouse wheels = 0
bus = 17, name = AlpsPS/2 ALPS DualPoint TouchPad
  handlers = mouse3 event9
  key = 000000000000042000000000000700000000000000000000000000000000000000000000000000000000000000000000
  abs = 0000000001000003
  mouse buttons = 3
  mouse wheels = 0
bus = 3, name = Integrated_Webcam_2M
  handlers = kbd event6
  key = 0000000000100000000000000000000000000000000000000000000000000000
  mouse buttons = 0
  mouse wheels = 0
bus = 25, name = Video Bus
  handlers = kbd event10
  key = 003e000b00000000000000000000000000000000000000000000000000000000
  mouse buttons = 0
  mouse wheels = 0
bus = 0, name = HDA Intel HDMI/DP,pcm=3
  handlers = event11
  mouse buttons = 0
  mouse wheels = 0
bus = 0, name = HDA Intel Mic at Sep Left Jack
  handlers = event12
  mouse buttons = 0
  mouse wheels = 0
bus = 0, name = HDA Intel Mic at Ext Right Jack
  handlers = event13
  mouse buttons = 0
  mouse wheels = 0
bus = 0, name = HDA Intel Line Out at Sep Left Jack
  handlers = event14
  mouse buttons = 0
  mouse wheels = 0
bus = 0, name = HDA Intel HP Out at Ext Right Jack
  handlers = event15
  mouse buttons = 0
  mouse wheels = 0
>> kbd.2: uml
>> cpu.1: cpuinfo
----- /proc/cpuinfo -----
  processor	: 0
  vendor_id	: GenuineIntel
  cpu family	: 6
  model		: 23
  model name	: Intel(R) Core(TM)2 Duo CPU     P8700  @ 2.53GHz
  stepping	: 10
  cpu MHz		: 2535.000
  cache size	: 3072 KB
  physical id	: 0
  siblings	: 2
  core id		: 0
  cpu cores	: 2
  apicid		: 0
  initial apicid	: 0
  fpu		: yes
  fpu_exception	: yes
  cpuid level	: 13
  wp		: yes
  flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good nopl aperfmperf pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 xsave lahf_lm ida dts tpr_shadow vnmi flexpriority
  bogomips	: 5053.30
  clflush size	: 64
  cache_alignment	: 64
  address sizes	: 36 bits physical, 48 bits virtual
  power management:
  
  processor	: 1
  vendor_id	: GenuineIntel
  cpu family	: 6
  model		: 23
  model name	: Intel(R) Core(TM)2 Duo CPU     P8700  @ 2.53GHz
  stepping	: 10
  cpu MHz		: 2535.000
  cache size	: 3072 KB
  physical id	: 0
  siblings	: 2
  core id		: 1
  cpu cores	: 2
  apicid		: 1
  initial apicid	: 1
  fpu		: yes
  fpu_exception	: yes
  cpuid level	: 13
  wp		: yes
  flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good nopl aperfmperf pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 xsave lahf_lm ida dts tpr_shadow vnmi flexpriority
  bogomips	: 5053.95
  clflush size	: 64
  cache_alignment	: 64
  address sizes	: 36 bits physical, 48 bits virtual
  power management:
  
----- /proc/cpuinfo end -----
>> kbd.3: serial console
>> fb.1: read info
>> net.1: get network data
  net interface: name = lo, path = /class/net/lo
    type = 772
    carrier = 1
    hw_addr = 00:00:00:00:00:00
    GDRVINFO ethtool error: Operation not supported
  net interface: name = eth0, path = /class/net/eth0
    type = 1
    carrier = 1
    hw_addr = 00:26:b9:c1:c5:00
    net device: path = /devices/pci0000:00/0000:00:19.0
    net driver: name = e1000e, path = /bus/pci/drivers/e1000e
  net interface: name = eth2, path = /class/net/eth2
    type = 1
    carrier = 1
    hw_addr = f0:7b:cb:73:88:8d
    net device: path = /devices/pci0000:00/0000:00:1c.1/0000:0c:00.0
    net driver: name = wl, path = /bus/pci/drivers/wl
>> net.2: eeprom dump
>> net.2: eeprom dump
>> net.2: eeprom dump
>> pppoe.1: looking for pppoe
>> pppoe.2: discovery
eth0: socket failed: Operation not permitted
eth2: socket failed: Operation not permitted
>> wlan.1: detecting wlan features
>> isdn.1: list
>> dsl.1: list
>> int.2: cdrom
>> int.3: media
>> int.4.1: /dev/mmcblk0
  read_block0: open(/dev/mmcblk0) failed
>> int.4.2: /dev/sda
  read_block0: open(/dev/sda) failed
>> int.4.3: /dev/sdb
  read_block0: open(/dev/sdb) failed
>> int.4: floppy
>> int.5: edd
>> int.5.1: bios
  bios ctrl 0: 36
  bios ctrl 1: 31
  bios ctrl 2: 19
  bios ctrl 3: 66
>> int.6: mouse
>> int.15: system info
  system type:
  acpi: 1
>> int.7: hdb
>> int.7.1: modules
>> int.8: usbscsi
>> int.9: hotplug
>> int.10: modem
>> int.11: wlan
>> int.12: udev
-----  udevinfo -----
  P: /devices/LNXSYSTM:00
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00
  E: MODALIAS=acpi:LNXSYSTM:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/LNXCPU:00
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXCPU:00
  E: DRIVER=processor
  E: MODALIAS=acpi:LNXCPU:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/LNXCPU:01
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXCPU:01
  E: DRIVER=processor
  E: MODALIAS=acpi:LNXCPU:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/LNXCPU:02
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXCPU:02
  E: DRIVER=processor
  E: MODALIAS=acpi:LNXCPU:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/LNXCPU:03
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXCPU:03
  E: DRIVER=processor
  E: MODALIAS=acpi:LNXCPU:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/ACPI0003:00
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/ACPI0003:00
  E: DRIVER=ac
  E: MODALIAS=acpi:ACPI0003:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/ACPI0003:00/power_supply/AC
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/ACPI0003:00/power_supply/AC
  E: POWER_SUPPLY_NAME=AC
  E: POWER_SUPPLY_ONLINE=1
  E: SUBSYSTEM=power_supply
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A03:00
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A03:00
  E: DRIVER=pci_root
  E: MODALIAS=acpi:PNP0A03:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:01
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:01
  E: DRIVER=video
  E: MODALIAS=acpi:LNXVIDEO:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:01/device:3d
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:01/device:3d
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:01/device:3e
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:01/device:3e
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:01/device:3f
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:01/device:3f
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:01/device:40
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:01/device:40
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:01/device:41
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:01/device:41
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:01/device:42
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:01/device:42
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:01/input/input11
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:01/input/input11
  E: PRODUCT=19/0/6/0
  E: NAME="Video Bus"
  E: PHYS="LNXVIDEO/video/input0"
  E: PROP=0
  E: EV=3
  E: KEY=3e000b00000000 0 0 0
  E: MODALIAS=input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw
  E: SUBSYSTEM=input
  E: ID_INPUT=1
  E: ID_INPUT_KEY=1
  E: ID_PATH=acpi-LNXVIDEO:01
  E: ID_PATH_TAG=acpi-LNXVIDEO_01
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:01/input/input11/event10
  N: input/event10
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:01/input/input11/event10
  E: MAJOR=13
  E: MINOR=74
  E: DEVNAME=/dev/input/event10
  E: SUBSYSTEM=input
  E: ID_INPUT=1
  E: ID_INPUT_KEY=1
  E: ID_PATH=acpi-LNXVIDEO:01
  E: ID_PATH_TAG=acpi-LNXVIDEO_01
  E: XKBMODEL=pc105
  E: XKBLAYOUT=us
  E: DMI_VENDOR=Dell Inc.
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:02
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:02
  E: MODALIAS=acpi:LNXVIDEO:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A03:00/PNP0C01:02
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A03:00/PNP0C01:02
  E: MODALIAS=acpi:PNP0C01:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A03:00/PNP0C01:03
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A03:00/PNP0C01:03
  E: MODALIAS=acpi:PNP0C01:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A03:00/PNP0C0F:00
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A03:00/PNP0C0F:00
  E: DRIVER=pci_link
  E: MODALIAS=acpi:PNP0C0F:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A03:00/PNP0C0F:01
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A03:00/PNP0C0F:01
  E: DRIVER=pci_link
  E: MODALIAS=acpi:PNP0C0F:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A03:00/PNP0C0F:02
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A03:00/PNP0C0F:02
  E: DRIVER=pci_link
  E: MODALIAS=acpi:PNP0C0F:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A03:00/PNP0C0F:03
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A03:00/PNP0C0F:03
  E: DRIVER=pci_link
  E: MODALIAS=acpi:PNP0C0F:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A03:00/PNP0C0F:04
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A03:00/PNP0C0F:04
  E: DRIVER=pci_link
  E: MODALIAS=acpi:PNP0C0F:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A03:00/PNP0C0F:05
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A03:00/PNP0C0F:05
  E: DRIVER=pci_link
  E: MODALIAS=acpi:PNP0C0F:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A03:00/PNP0C0F:06
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A03:00/PNP0C0F:06
  E: DRIVER=pci_link
  E: MODALIAS=acpi:PNP0C0F:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A03:00/PNP0C0F:07
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A03:00/PNP0C0F:07
  E: DRIVER=pci_link
  E: MODALIAS=acpi:PNP0C0F:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:01
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:01
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:01/PNP0000:00
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:01/PNP0000:00
  E: MODALIAS=acpi:PNP0000:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:01/PNP0100:00
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:01/PNP0100:00
  E: MODALIAS=acpi:PNP0100:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:01/PNP0103:00
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:01/PNP0103:00
  E: MODALIAS=acpi:PNP0103:PNP0C01:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:01/PNP0200:00
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:01/PNP0200:00
  E: MODALIAS=acpi:PNP0200:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:01/PNP0303:00
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:01/PNP0303:00
  E: MODALIAS=acpi:PNP0303:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:01/PNP0401:00
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:01/PNP0401:00
  E: MODALIAS=acpi:PNP0401:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:01/PNP0501:00
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:01/PNP0501:00
  E: MODALIAS=acpi:PNP0501:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:01/PNP0800:00
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:01/PNP0800:00
  E: MODALIAS=acpi:PNP0800:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:01/PNP0B00:00
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:01/PNP0B00:00
  E: MODALIAS=acpi:PNP0B00:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:01/PNP0C01:00
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:01/PNP0C01:00
  E: MODALIAS=acpi:PNP0C01:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:01/PNP0C01:01
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:01/PNP0C01:01
  E: MODALIAS=acpi:PNP0C01:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:01/PNP0C04:00
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:01/PNP0C04:00
  E: MODALIAS=acpi:PNP0C04:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:01/PNP0C09:00
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:01/PNP0C09:00
  E: DRIVER=ec
  E: MODALIAS=acpi:PNP0C09:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:01/PNP0F13:00
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:01/PNP0F13:00
  E: MODALIAS=acpi:PNP0F13:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:02
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:02
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:02/device:03
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:02/device:03
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:02/device:04
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:02/device:04
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:05
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:05
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:05/device:06
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:05/device:06
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:05/device:06/device:07
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:05/device:06/device:07
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:05/device:06/device:08
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:05/device:06/device:08
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:09
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:09
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:09/device:0a
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:09/device:0a
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:09/device:0a/device:0b
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:09/device:0a/device:0b
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:09/device:0a/device:0c
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:09/device:0a/device:0c
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:0d
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:0d
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:0d/device:0e
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:0d/device:0e
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:0d/device:0e/device:0f
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:0d/device:0e/device:0f
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:0d/device:0e/device:10
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:0d/device:0e/device:10
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:11
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:11
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:11/device:12
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:11/device:12
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:11/device:12/device:13
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:11/device:12/device:13
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:11/device:12/device:14
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:11/device:12/device:14
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:15
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:15
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:15/device:16
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:15/device:16
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:15/device:16/device:17
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:15/device:16/device:17
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:15/device:16/device:18
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:15/device:16/device:18
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:19
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:19
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:19/device:1a
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:19/device:1a
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:19/device:1a/device:1b
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:19/device:1a/device:1b
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:19/device:1a/device:1c
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:19/device:1a/device:1c
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:1d
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:1d
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:1d/device:1e
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:1d/device:1e
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:1d/device:1e/device:1f
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:1d/device:1e/device:1f
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:1d/device:1e/device:20
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:1d/device:1e/device:20
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:1d/device:1e/device:21
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:1d/device:1e/device:21
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:1d/device:1e/device:22
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:1d/device:1e/device:22
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:1d/device:1e/device:23
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:1d/device:1e/device:23
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:1d/device:1e/device:24
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:1d/device:1e/device:24
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:25
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:25
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:25/device:26
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:25/device:26
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:25/device:26/device:27
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:25/device:26/device:27
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:25/device:26/device:28
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:25/device:26/device:28
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:25/device:26/device:29
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:25/device:26/device:29
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:25/device:26/device:2a
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:25/device:26/device:2a
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:25/device:26/device:2b
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:25/device:26/device:2b
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:25/device:26/device:2c
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:25/device:26/device:2c
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:2d
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:2d
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:2d/device:2e
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:2d/device:2e
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:2d/device:2f
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:2d/device:2f
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:2d/device:2f/device:30
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:2d/device:2f/device:30
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:31
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:31
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:31/device:32
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:31/device:32
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:31/device:32/device:33
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:31/device:32/device:33
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:31/device:34
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:31/device:34
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:35
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:35
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:36
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:36
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:36/LNXVIDEO:00
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:36/LNXVIDEO:00
  E: MODALIAS=acpi:LNXVIDEO:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:36/LNXVIDEO:00/device:37
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:36/LNXVIDEO:00/device:37
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:36/LNXVIDEO:00/device:38
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:36/LNXVIDEO:00/device:38
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:36/LNXVIDEO:00/device:39
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:36/LNXVIDEO:00/device:39
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:36/LNXVIDEO:00/device:3a
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:36/LNXVIDEO:00/device:3a
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:36/LNXVIDEO:00/device:3b
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:36/LNXVIDEO:00/device:3b
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:36/LNXVIDEO:00/device:3c
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:36/LNXVIDEO:00/device:3c
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:43
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:43
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:43/device:44
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:43/device:44
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:45
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:45
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:45/device:46
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:45/device:46
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:47
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:47
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:47/device:48
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:47/device:48
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:49
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:49
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:49/device:4a
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:49/device:4a
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:4b
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:4b
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:4b/device:4c
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:4b/device:4c
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:4d
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:4d
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:4d/device:4e
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:4d/device:4e
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0C01:04
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0C01:04
  E: MODALIAS=acpi:PNP0C01:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0C0A:00
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0C0A:00
  E: DRIVER=battery
  E: MODALIAS=acpi:PNP0C0A:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0C0A:00/power_supply/BAT0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0C0A:00/power_supply/BAT0
  E: POWER_SUPPLY_NAME=BAT0
  E: POWER_SUPPLY_STATUS=Full
  E: POWER_SUPPLY_PRESENT=1
  E: POWER_SUPPLY_TECHNOLOGY=Li-ion
  E: POWER_SUPPLY_CYCLE_COUNT=0
  E: POWER_SUPPLY_VOLTAGE_MIN_DESIGN=11100000
  E: POWER_SUPPLY_VOLTAGE_NOW=12508000
  E: POWER_SUPPLY_CURRENT_NOW=1000
  E: POWER_SUPPLY_CHARGE_FULL_DESIGN=5200000
  E: POWER_SUPPLY_CHARGE_FULL=4680000
  E: POWER_SUPPLY_CHARGE_NOW=5200000
  E: POWER_SUPPLY_MODEL_NAME=DELL KY26603
  E: POWER_SUPPLY_MANUFACTURER=Sanyo
  E: POWER_SUPPLY_SERIAL_NUMBER=2679
  E: SUBSYSTEM=power_supply
  
  P: /devices/LNXSYSTM:00/device:00/PNP0C0A:01
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0C0A:01
  E: DRIVER=battery
  E: MODALIAS=acpi:PNP0C0A:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0C0C:00
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0C0C:00
  E: DRIVER=button
  E: MODALIAS=acpi:PNP0C0C:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
  E: PRODUCT=19/0/1/0
  E: NAME="Power Button"
  E: PHYS="PNP0C0C/button/input0"
  E: PROP=0
  E: EV=3
  E: KEY=10000000000000 0
  E: MODALIAS=input:b0019v0000p0001e0000-e0,1,k74,ramlsfw
  E: SUBSYSTEM=input
  E: ID_INPUT=1
  E: ID_INPUT_KEY=1
  E: ID_PATH=acpi-PNP0C0C:00
  E: ID_PATH_TAG=acpi-PNP0C0C_00
  
  P: /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1/event1
  N: input/event1
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1/event1
  E: MAJOR=13
  E: MINOR=65
  E: DEVNAME=/dev/input/event1
  E: SUBSYSTEM=input
  E: ID_INPUT=1
  E: ID_INPUT_KEY=1
  E: ID_PATH=acpi-PNP0C0C:00
  E: ID_PATH_TAG=acpi-PNP0C0C_00
  E: XKBMODEL=pc105
  E: XKBLAYOUT=us
  E: DMI_VENDOR=Dell Inc.
  
  P: /devices/LNXSYSTM:00/device:00/PNP0C0D:00
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0C0D:00
  E: DRIVER=button
  E: MODALIAS=acpi:PNP0C0D:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
  E: PRODUCT=19/0/5/0
  E: NAME="Lid Switch"
  E: PHYS="PNP0C0D/button/input0"
  E: PROP=0
  E: EV=21
  E: SW=1
  E: MODALIAS=input:b0019v0000p0005e0000-e0,5,kramlsfw0,
  E: SUBSYSTEM=input
  E: ID_INPUT=1
  E: ID_PATH=acpi-PNP0C0D:00
  E: ID_PATH_TAG=acpi-PNP0C0D_00
  
  P: /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0/event0
  N: input/event0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0/event0
  E: MAJOR=13
  E: MINOR=64
  E: DEVNAME=/dev/input/event0
  E: SUBSYSTEM=input
  E: ID_INPUT=1
  E: ID_PATH=acpi-PNP0C0D:00
  E: ID_PATH_TAG=acpi-PNP0C0D_00
  
  P: /devices/LNXSYSTM:00/device:00/PNP0C0E:00
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0C0E:00
  E: DRIVER=button
  E: MODALIAS=acpi:PNP0C0E:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
  E: PRODUCT=19/0/3/0
  E: NAME="Sleep Button"
  E: PHYS="PNP0C0E/button/input0"
  E: PROP=0
  E: EV=3
  E: KEY=4000 0 0
  E: MODALIAS=input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw
  E: SUBSYSTEM=input
  E: ID_INPUT=1
  E: ID_INPUT_KEY=1
  E: ID_PATH=acpi-PNP0C0E:00
  E: ID_PATH_TAG=acpi-PNP0C0E_00
  
  P: /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2/event2
  N: input/event2
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2/event2
  E: MAJOR=13
  E: MINOR=66
  E: DEVNAME=/dev/input/event2
  E: SUBSYSTEM=input
  E: ID_INPUT=1
  E: ID_INPUT_KEY=1
  E: ID_PATH=acpi-PNP0C0E:00
  E: ID_PATH_TAG=acpi-PNP0C0E_00
  E: XKBMODEL=pc105
  E: XKBLAYOUT=us
  E: DMI_VENDOR=Dell Inc.
  
  P: /devices/LNXSYSTM:00/device:00/PNP0C14:00
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0C14:00
  E: DRIVER=wmi
  E: MODALIAS=acpi:PNP0C14:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:4f
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:4f
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:4f/LNXTHERM:00
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:4f/LNXTHERM:00
  E: DRIVER=thermal
  E: MODALIAS=acpi:LNXTHERM:
  E: SUBSYSTEM=acpi
  
  P: /devices/breakpoint
  E: UDEV_LOG=3
  E: DEVPATH=/devices/breakpoint
  E: SUBSYSTEM=event_source
  
  P: /devices/cpu
  E: UDEV_LOG=3
  E: DEVPATH=/devices/cpu
  E: SUBSYSTEM=event_source
  
  P: /devices/pci0000:00/0000:00:00.0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:00.0
  E: DRIVER=agpgart-intel
  E: PCI_CLASS=60000
  E: PCI_ID=8086:2A40
  E: PCI_SUBSYS_ID=1028:024F
  E: PCI_SLOT_NAME=0000:00:00.0
  E: MODALIAS=pci:v00008086d00002A40sv00001028sd0000024Fbc06sc00i00
  E: SUBSYSTEM=pci
  
  P: /devices/pci0000:00/0000:00:02.0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:02.0
  E: DRIVER=i915
  E: PCI_CLASS=30000
  E: PCI_ID=8086:2A42
  E: PCI_SUBSYS_ID=1028:024F
  E: PCI_SLOT_NAME=0000:00:02.0
  E: MODALIAS=pci:v00008086d00002A42sv00001028sd0000024Fbc03sc00i00
  E: SUBSYSTEM=pci
  
  P: /devices/pci0000:00/0000:00:02.0/backlight/acpi_video0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:02.0/backlight/acpi_video0
  E: SUBSYSTEM=backlight
  
  P: /devices/pci0000:00/0000:00:02.0/drm/card0
  N: dri/card0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:02.0/drm/card0
  E: MAJOR=226
  E: MINOR=0
  E: DEVNAME=/dev/dri/card0
  E: DEVTYPE=drm_minor
  E: SUBSYSTEM=drm
  E: TAGS=:udev-acl:
  
  P: /devices/pci0000:00/0000:00:02.0/drm/card0/card0-DP-1
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:02.0/drm/card0/card0-DP-1
  E: SUBSYSTEM=drm
  
  P: /devices/pci0000:00/0000:00:02.0/drm/card0/card0-DP-1/i2c-14
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:02.0/drm/card0/card0-DP-1/i2c-14
  E: SUBSYSTEM=i2c
  
  P: /devices/pci0000:00/0000:00:02.0/drm/card0/card0-DP-2
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:02.0/drm/card0/card0-DP-2
  E: SUBSYSTEM=drm
  
  P: /devices/pci0000:00/0000:00:02.0/drm/card0/card0-DP-2/i2c-15
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:02.0/drm/card0/card0-DP-2/i2c-15
  E: SUBSYSTEM=i2c
  
  P: /devices/pci0000:00/0000:00:02.0/drm/card0/card0-DP-3
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:02.0/drm/card0/card0-DP-3
  E: SUBSYSTEM=drm
  
  P: /devices/pci0000:00/0000:00:02.0/drm/card0/card0-DP-3/i2c-16
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:02.0/drm/card0/card0-DP-3/i2c-16
  E: SUBSYSTEM=i2c
  
  P: /devices/pci0000:00/0000:00:02.0/drm/card0/card0-HDMI-A-1
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:02.0/drm/card0/card0-HDMI-A-1
  E: SUBSYSTEM=drm
  
  P: /devices/pci0000:00/0000:00:02.0/drm/card0/card0-HDMI-A-2
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:02.0/drm/card0/card0-HDMI-A-2
  E: SUBSYSTEM=drm
  
  P: /devices/pci0000:00/0000:00:02.0/drm/card0/card0-LVDS-1
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:02.0/drm/card0/card0-LVDS-1
  E: SUBSYSTEM=drm
  
  P: /devices/pci0000:00/0000:00:02.0/drm/card0/card0-LVDS-1/intel_backlight
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:02.0/drm/card0/card0-LVDS-1/intel_backlight
  E: SUBSYSTEM=backlight
  
  P: /devices/pci0000:00/0000:00:02.0/drm/card0/card0-SVIDEO-1
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:02.0/drm/card0/card0-SVIDEO-1
  E: SUBSYSTEM=drm
  
  P: /devices/pci0000:00/0000:00:02.0/drm/card0/card0-VGA-1
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:02.0/drm/card0/card0-VGA-1
  E: SUBSYSTEM=drm
  
  P: /devices/pci0000:00/0000:00:02.0/drm/controlD64
  N: dri/controlD64
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:02.0/drm/controlD64
  E: MAJOR=226
  E: MINOR=64
  E: DEVNAME=/dev/dri/controlD64
  E: DEVTYPE=drm_minor
  E: SUBSYSTEM=drm
  
  P: /devices/pci0000:00/0000:00:02.0/graphics/fb0
  N: fb0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:02.0/graphics/fb0
  E: MAJOR=29
  E: MINOR=0
  E: DEVNAME=/dev/fb0
  E: SUBSYSTEM=graphics
  
  P: /devices/pci0000:00/0000:00:02.0/i2c-0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:02.0/i2c-0
  E: SUBSYSTEM=i2c
  
  P: /devices/pci0000:00/0000:00:02.0/i2c-1
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:02.0/i2c-1
  E: SUBSYSTEM=i2c
  
  P: /devices/pci0000:00/0000:00:02.0/i2c-10
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:02.0/i2c-10
  E: SUBSYSTEM=i2c
  
  P: /devices/pci0000:00/0000:00:02.0/i2c-11
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:02.0/i2c-11
  E: SUBSYSTEM=i2c
  
  P: /devices/pci0000:00/0000:00:02.0/i2c-12
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:02.0/i2c-12
  E: SUBSYSTEM=i2c
  
  P: /devices/pci0000:00/0000:00:02.0/i2c-13
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:02.0/i2c-13
  E: SUBSYSTEM=i2c
  
  P: /devices/pci0000:00/0000:00:02.0/i2c-2
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:02.0/i2c-2
  E: SUBSYSTEM=i2c
  
  P: /devices/pci0000:00/0000:00:02.0/i2c-3
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:02.0/i2c-3
  E: SUBSYSTEM=i2c
  
  P: /devices/pci0000:00/0000:00:02.0/i2c-4
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:02.0/i2c-4
  E: SUBSYSTEM=i2c
  
  P: /devices/pci0000:00/0000:00:02.0/i2c-5
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:02.0/i2c-5
  E: SUBSYSTEM=i2c
  
  P: /devices/pci0000:00/0000:00:02.0/i2c-6
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:02.0/i2c-6
  E: SUBSYSTEM=i2c
  
  P: /devices/pci0000:00/0000:00:02.0/i2c-7
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:02.0/i2c-7
  E: SUBSYSTEM=i2c
  
  P: /devices/pci0000:00/0000:00:02.0/i2c-8
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:02.0/i2c-8
  E: SUBSYSTEM=i2c
  
  P: /devices/pci0000:00/0000:00:02.0/i2c-9
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:02.0/i2c-9
  E: SUBSYSTEM=i2c
  
  P: /devices/pci0000:00/0000:00:02.1
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:02.1
  E: PCI_CLASS=38000
  E: PCI_ID=8086:2A43
  E: PCI_SUBSYS_ID=1028:024F
  E: PCI_SLOT_NAME=0000:00:02.1
  E: MODALIAS=pci:v00008086d00002A43sv00001028sd0000024Fbc03sc80i00
  E: SUBSYSTEM=pci
  
  P: /devices/pci0000:00/0000:00:19.0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:19.0
  E: DRIVER=e1000e
  E: PCI_CLASS=20000
  E: PCI_ID=8086:10F5
  E: PCI_SUBSYS_ID=1028:024F
  E: PCI_SLOT_NAME=0000:00:19.0
  E: MODALIAS=pci:v00008086d000010F5sv00001028sd0000024Fbc02sc00i00
  E: SUBSYSTEM=pci
  
  P: /devices/pci0000:00/0000:00:19.0/net/eth0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:19.0/net/eth0
  E: INTERFACE=eth0
  E: IFINDEX=2
  E: SUBSYSTEM=net
  E: ID_VENDOR_FROM_DATABASE=Intel Corporation
  E: ID_MODEL_FROM_DATABASE=82567LM Gigabit Network Connection
  E: ID_BUS=pci
  E: ID_VENDOR_ID=0x8086
  E: ID_MODEL_ID=0x10f5
  E: ID_MM_CANDIDATE=1
  
  P: /devices/pci0000:00/0000:00:1a.0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1a.0
  E: DRIVER=uhci_hcd
  E: PCI_CLASS=C0300
  E: PCI_ID=8086:2937
  E: PCI_SUBSYS_ID=1028:024F
  E: PCI_SLOT_NAME=0000:00:1a.0
  E: MODALIAS=pci:v00008086d00002937sv00001028sd0000024Fbc0Csc03i00
  E: SUBSYSTEM=pci
  
  P: /devices/pci0000:00/0000:00:1a.0/usb3
  N: bus/usb/003/001
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1a.0/usb3
  E: MAJOR=189
  E: MINOR=256
  E: DEVNAME=/dev/bus/usb/003/001
  E: DEVTYPE=usb_device
  E: DRIVER=usb
  E: PRODUCT=1d6b/1/300
  E: TYPE=9/0/0
  E: BUSNUM=003
  E: DEVNUM=001
  E: SUBSYSTEM=usb
  E: ID_VENDOR=Linux_3.0.0-14-generic_uhci_hcd
  E: ID_VENDOR_ENC=Linux\x203.0.0-14-generic\x20uhci_hcd
  E: ID_VENDOR_ID=1d6b
  E: ID_MODEL=UHCI_Host_Controller
  E: ID_MODEL_ENC=UHCI\x20Host\x20Controller
  E: ID_MODEL_ID=0001
  E: ID_REVISION=0300
  E: ID_SERIAL=Linux_3.0.0-14-generic_uhci_hcd_UHCI_Host_Controller_0000:00:1a.0
  E: ID_SERIAL_SHORT=0000:00:1a.0
  E: ID_BUS=usb
  E: ID_USB_INTERFACES=:090000:
  
  P: /devices/pci0000:00/0000:00:1a.0/usb3/3-0:1.0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1a.0/usb3/3-0:1.0
  E: DEVTYPE=usb_interface
  E: DRIVER=hub
  E: PRODUCT=1d6b/1/300
  E: TYPE=9/0/0
  E: INTERFACE=9/0/0
  E: MODALIAS=usb:v1D6Bp0001d0300dc09dsc00dp00ic09isc00ip00
  E: SUBSYSTEM=usb
  
  P: /devices/pci0000:00/0000:00:1a.0/usb3/3-1
  N: bus/usb/003/002
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1a.0/usb3/3-1
  E: MAJOR=189
  E: MINOR=257
  E: DEVNAME=/dev/bus/usb/003/002
  E: DEVTYPE=usb_device
  E: DRIVER=usb
  E: PRODUCT=a5c/4500/100
  E: TYPE=9/0/0
  E: BUSNUM=003
  E: DEVNUM=002
  E: SUBSYSTEM=usb
  E: ID_VENDOR=Broadcom
  E: ID_VENDOR_ENC=Broadcom
  E: ID_VENDOR_ID=0a5c
  E: ID_MODEL=BCM2046B1
  E: ID_MODEL_ENC=BCM2046B1
  E: ID_MODEL_ID=4500
  E: ID_REVISION=0100
  E: ID_SERIAL=Broadcom_BCM2046B1
  E: ID_BUS=usb
  E: ID_USB_INTERFACES=:090000:
  
  P: /devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1.1
  N: bus/usb/003/003
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1.1
  E: MAJOR=189
  E: MINOR=258
  E: DEVNAME=/dev/bus/usb/003/003
  E: DEVTYPE=usb_device
  E: DRIVER=usb
  E: PRODUCT=413c/8157/100
  E: TYPE=0/0/0
  E: BUSNUM=003
  E: DEVNUM=003
  E: SUBSYSTEM=usb
  E: ID_VENDOR=413c
  E: ID_VENDOR_ENC=413c
  E: ID_VENDOR_ID=413c
  E: ID_MODEL=8157
  E: ID_MODEL_ENC=8157
  E: ID_MODEL_ID=8157
  E: ID_REVISION=0100
  E: ID_SERIAL=413c_8157
  E: ID_BUS=usb
  E: ID_USB_INTERFACES=:030101:
  
  P: /devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1.1/3-1.1:1.0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1.1/3-1.1:1.0
  E: DEVTYPE=usb_interface
  E: DRIVER=usbhid
  E: PRODUCT=413c/8157/100
  E: TYPE=0/0/0
  E: INTERFACE=3/1/1
  E: MODALIAS=usb:v413Cp8157d0100dc00dsc00dp00ic03isc01ip01
  E: SUBSYSTEM=usb
  
  P: /devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1.1/3-1.1:1.0/0003:413C:8157.0002
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1.1/3-1.1:1.0/0003:413C:8157.0002
  E: DRIVER=generic-usb
  E: HID_ID=0003:0000413C:00008157
  E: HID_NAME=HID 413c:8157
  E: HID_PHYS=usb-0000:00:1a.0-1.1/input0
  E: SUBSYSTEM=hid
  E: MODALIAS=hid:b0003v0000413Cp00008157
  
  P: /devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1.1/3-1.1:1.0/0003:413C:8157.0002/hidraw/hidraw1
  N: hidraw1
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1.1/3-1.1:1.0/0003:413C:8157.0002/hidraw/hidraw1
  E: MAJOR=250
  E: MINOR=1
  E: DEVNAME=/dev/hidraw1
  E: SUBSYSTEM=hidraw
  
  P: /devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1.1/3-1.1:1.0/input/input5
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1.1/3-1.1:1.0/input/input5
  E: PRODUCT=3/413c/8157/111
  E: NAME="HID 413c:8157"
  E: PHYS="usb-0000:00:1a.0-1.1/input0"
  E: UNIQ=""
  E: PROP=0
  E: EV=120013
  E: KEY=1000000000007 ff800000000007ff febeffdff3cfffff fffffffffffffffe
  E: MSC=10
  E: LED=7
  E: MODALIAS=input:b0003v413Cp8157e0111-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,sfw
  E: SUBSYSTEM=input
  E: ID_INPUT=1
  E: ID_INPUT_KEY=1
  E: ID_INPUT_KEYBOARD=1
  E: ID_VENDOR=413c
  E: ID_VENDOR_ENC=413c
  E: ID_VENDOR_ID=413c
  E: ID_MODEL=8157
  E: ID_MODEL_ENC=8157
  E: ID_MODEL_ID=8157
  E: ID_REVISION=0100
  E: ID_SERIAL=413c_8157
  E: ID_TYPE=hid
  E: ID_BUS=usb
  E: ID_USB_INTERFACES=:030101:
  E: ID_USB_INTERFACE_NUM=00
  E: ID_USB_DRIVER=usbhid
  E: ID_PATH=pci-0000:00:1a.0-usb-0:1.1:1.0
  E: ID_PATH_TAG=pci-0000_00_1a_0-usb-0_1_1_1_0
  
  P: /devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1.1/3-1.1:1.0/input/input5/event5
  N: input/event5
  S: input/by-id/usb-413c_8157-event-kbd
  S: input/by-path/pci-0000:00:1a.0-usb-0:1.1:1.0-event-kbd
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1.1/3-1.1:1.0/input/input5/event5
  E: MAJOR=13
  E: MINOR=69
  E: DEVNAME=/dev/input/event5
  E: SUBSYSTEM=input
  E: ID_INPUT=1
  E: ID_INPUT_KEY=1
  E: ID_INPUT_KEYBOARD=1
  E: ID_VENDOR=413c
  E: ID_VENDOR_ENC=413c
  E: ID_VENDOR_ID=413c
  E: ID_MODEL=8157
  E: ID_MODEL_ENC=8157
  E: ID_MODEL_ID=8157
  E: ID_REVISION=0100
  E: ID_SERIAL=413c_8157
  E: ID_TYPE=hid
  E: ID_BUS=usb
  E: ID_USB_INTERFACES=:030101:
  E: ID_USB_INTERFACE_NUM=00
  E: ID_USB_DRIVER=usbhid
  E: ID_PATH=pci-0000:00:1a.0-usb-0:1.1:1.0
  E: ID_PATH_TAG=pci-0000_00_1a_0-usb-0_1_1_1_0
  E: XKBMODEL=pc105
  E: XKBLAYOUT=us
  E: DEVLINKS=/dev/input/by-id/usb-413c_8157-event-kbd /dev/input/by-path/pci-0000:00:1a.0-usb-0:1.1:1.0-event-kbd
  
  P: /devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1.2
  N: bus/usb/003/004
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1.2
  E: MAJOR=189
  E: MINOR=259
  E: DEVNAME=/dev/bus/usb/003/004
  E: DEVTYPE=usb_device
  E: DRIVER=usb
  E: PRODUCT=413c/8158/100
  E: TYPE=0/0/0
  E: BUSNUM=003
  E: DEVNUM=004
  E: SUBSYSTEM=usb
  E: ID_VENDOR=413c
  E: ID_VENDOR_ENC=413c
  E: ID_VENDOR_ID=413c
  E: ID_MODEL=8158
  E: ID_MODEL_ENC=8158
  E: ID_MODEL_ID=8158
  E: ID_REVISION=0100
  E: ID_SERIAL=413c_8158
  E: ID_BUS=usb
  E: ID_USB_INTERFACES=:030102:
  
  P: /devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1.2/3-1.2:1.0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1.2/3-1.2:1.0
  E: DEVTYPE=usb_interface
  E: PRODUCT=413c/8158/100
  E: TYPE=0/0/0
  E: INTERFACE=3/1/2
  E: MODALIAS=usb:v413Cp8158d0100dc00dsc00dp00ic03isc01ip02
  E: SUBSYSTEM=usb
  E: HID2HCI_SWITCH=1
  
  P: /devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1:1.0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1:1.0
  E: DEVTYPE=usb_interface
  E: DRIVER=hub
  E: PRODUCT=a5c/4500/100
  E: TYPE=9/0/0
  E: INTERFACE=9/0/0
  E: MODALIAS=usb:v0A5Cp4500d0100dc09dsc00dp00ic09isc00ip00
  E: SUBSYSTEM=usb
  
  P: /devices/pci0000:00/0000:00:1a.0/usbmon/usbmon3
  N: usbmon3
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1a.0/usbmon/usbmon3
  E: MAJOR=252
  E: MINOR=3
  E: DEVNAME=/dev/usbmon3
  E: SUBSYSTEM=usbmon
  
  P: /devices/pci0000:00/0000:00:1a.1
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1a.1
  E: DRIVER=uhci_hcd
  E: PCI_CLASS=C0300
  E: PCI_ID=8086:2938
  E: PCI_SUBSYS_ID=1028:024F
  E: PCI_SLOT_NAME=0000:00:1a.1
  E: MODALIAS=pci:v00008086d00002938sv00001028sd0000024Fbc0Csc03i00
  E: SUBSYSTEM=pci
  
  P: /devices/pci0000:00/0000:00:1a.1/usb4
  N: bus/usb/004/001
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1a.1/usb4
  E: MAJOR=189
  E: MINOR=384
  E: DEVNAME=/dev/bus/usb/004/001
  E: DEVTYPE=usb_device
  E: DRIVER=usb
  E: PRODUCT=1d6b/1/300
  E: TYPE=9/0/0
  E: BUSNUM=004
  E: DEVNUM=001
  E: SUBSYSTEM=usb
  E: ID_VENDOR=Linux_3.0.0-14-generic_uhci_hcd
  E: ID_VENDOR_ENC=Linux\x203.0.0-14-generic\x20uhci_hcd
  E: ID_VENDOR_ID=1d6b
  E: ID_MODEL=UHCI_Host_Controller
  E: ID_MODEL_ENC=UHCI\x20Host\x20Controller
  E: ID_MODEL_ID=0001
  E: ID_REVISION=0300
  E: ID_SERIAL=Linux_3.0.0-14-generic_uhci_hcd_UHCI_Host_Controller_0000:00:1a.1
  E: ID_SERIAL_SHORT=0000:00:1a.1
  E: ID_BUS=usb
  E: ID_USB_INTERFACES=:090000:
  
  P: /devices/pci0000:00/0000:00:1a.1/usb4/4-0:1.0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1a.1/usb4/4-0:1.0
  E: DEVTYPE=usb_interface
  E: DRIVER=hub
  E: PRODUCT=1d6b/1/300
  E: TYPE=9/0/0
  E: INTERFACE=9/0/0
  E: MODALIAS=usb:v1D6Bp0001d0300dc09dsc00dp00ic09isc00ip00
  E: SUBSYSTEM=usb
  
  P: /devices/pci0000:00/0000:00:1a.1/usbmon/usbmon4
  N: usbmon4
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1a.1/usbmon/usbmon4
  E: MAJOR=252
  E: MINOR=4
  E: DEVNAME=/dev/usbmon4
  E: SUBSYSTEM=usbmon
  
  P: /devices/pci0000:00/0000:00:1a.2
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1a.2
  E: DRIVER=uhci_hcd
  E: PCI_CLASS=C0300
  E: PCI_ID=8086:2939
  E: PCI_SUBSYS_ID=1028:024F
  E: PCI_SLOT_NAME=0000:00:1a.2
  E: MODALIAS=pci:v00008086d00002939sv00001028sd0000024Fbc0Csc03i00
  E: SUBSYSTEM=pci
  
  P: /devices/pci0000:00/0000:00:1a.2/usb5
  N: bus/usb/005/001
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1a.2/usb5
  E: MAJOR=189
  E: MINOR=512
  E: DEVNAME=/dev/bus/usb/005/001
  E: DEVTYPE=usb_device
  E: DRIVER=usb
  E: PRODUCT=1d6b/1/300
  E: TYPE=9/0/0
  E: BUSNUM=005
  E: DEVNUM=001
  E: SUBSYSTEM=usb
  E: ID_VENDOR=Linux_3.0.0-14-generic_uhci_hcd
  E: ID_VENDOR_ENC=Linux\x203.0.0-14-generic\x20uhci_hcd
  E: ID_VENDOR_ID=1d6b
  E: ID_MODEL=UHCI_Host_Controller
  E: ID_MODEL_ENC=UHCI\x20Host\x20Controller
  E: ID_MODEL_ID=0001
  E: ID_REVISION=0300
  E: ID_SERIAL=Linux_3.0.0-14-generic_uhci_hcd_UHCI_Host_Controller_0000:00:1a.2
  E: ID_SERIAL_SHORT=0000:00:1a.2
  E: ID_BUS=usb
  E: ID_USB_INTERFACES=:090000:
  
  P: /devices/pci0000:00/0000:00:1a.2/usb5/5-0:1.0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1a.2/usb5/5-0:1.0
  E: DEVTYPE=usb_interface
  E: DRIVER=hub
  E: PRODUCT=1d6b/1/300
  E: TYPE=9/0/0
  E: INTERFACE=9/0/0
  E: MODALIAS=usb:v1D6Bp0001d0300dc09dsc00dp00ic09isc00ip00
  E: SUBSYSTEM=usb
  
  P: /devices/pci0000:00/0000:00:1a.2/usb5/5-1
  N: bus/usb/005/002
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1a.2/usb5/5-1
  E: MAJOR=189
  E: MINOR=513
  E: DEVNAME=/dev/bus/usb/005/002
  E: DEVTYPE=usb_device
  E: DRIVER=usb
  E: PRODUCT=a5c/5800/101
  E: TYPE=0/0/0
  E: BUSNUM=005
  E: DEVNUM=002
  E: SUBSYSTEM=usb
  E: ID_VENDOR=Broadcom_Corp
  E: ID_VENDOR_ENC=Broadcom\x20Corp
  E: ID_VENDOR_ID=0a5c
  E: ID_MODEL=5880
  E: ID_MODEL_ENC=5880
  E: ID_MODEL_ID=5800
  E: ID_REVISION=0101
  E: ID_SERIAL=Broadcom_Corp_5880_0123456789ABCD
  E: ID_SERIAL_SHORT=0123456789ABCD
  E: ID_BUS=usb
  E: ID_USB_INTERFACES=:fe0000:0b0000:
  
  P: /devices/pci0000:00/0000:00:1a.2/usb5/5-1/5-1:0.0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1a.2/usb5/5-1/5-1:0.0
  E: DEVTYPE=usb_interface
  E: PRODUCT=a5c/5800/101
  E: TYPE=0/0/0
  E: INTERFACE=254/0/0
  E: MODALIAS=usb:v0A5Cp5800d0101dc00dsc00dp00icFEisc00ip00
  E: SUBSYSTEM=usb
  
  P: /devices/pci0000:00/0000:00:1a.2/usb5/5-1/5-1:0.1
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1a.2/usb5/5-1/5-1:0.1
  E: DEVTYPE=usb_interface
  E: PRODUCT=a5c/5800/101
  E: TYPE=0/0/0
  E: INTERFACE=11/0/0
  E: MODALIAS=usb:v0A5Cp5800d0101dc00dsc00dp00ic0Bisc00ip00
  E: SUBSYSTEM=usb
  
  P: /devices/pci0000:00/0000:00:1a.2/usbmon/usbmon5
  N: usbmon5
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1a.2/usbmon/usbmon5
  E: MAJOR=252
  E: MINOR=5
  E: DEVNAME=/dev/usbmon5
  E: SUBSYSTEM=usbmon
  
  P: /devices/pci0000:00/0000:00:1a.7
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1a.7
  E: DRIVER=ehci_hcd
  E: PCI_CLASS=C0320
  E: PCI_ID=8086:293C
  E: PCI_SUBSYS_ID=1028:024F
  E: PCI_SLOT_NAME=0000:00:1a.7
  E: MODALIAS=pci:v00008086d0000293Csv00001028sd0000024Fbc0Csc03i20
  E: SUBSYSTEM=pci
  
  P: /devices/pci0000:00/0000:00:1a.7/usb1
  N: bus/usb/001/001
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1a.7/usb1
  E: MAJOR=189
  E: MINOR=0
  E: DEVNAME=/dev/bus/usb/001/001
  E: DEVTYPE=usb_device
  E: DRIVER=usb
  E: PRODUCT=1d6b/2/300
  E: TYPE=9/0/0
  E: BUSNUM=001
  E: DEVNUM=001
  E: SUBSYSTEM=usb
  E: ID_VENDOR=Linux_3.0.0-14-generic_ehci_hcd
  E: ID_VENDOR_ENC=Linux\x203.0.0-14-generic\x20ehci_hcd
  E: ID_VENDOR_ID=1d6b
  E: ID_MODEL=EHCI_Host_Controller
  E: ID_MODEL_ENC=EHCI\x20Host\x20Controller
  E: ID_MODEL_ID=0002
  E: ID_REVISION=0300
  E: ID_SERIAL=Linux_3.0.0-14-generic_ehci_hcd_EHCI_Host_Controller_0000:00:1a.7
  E: ID_SERIAL_SHORT=0000:00:1a.7
  E: ID_BUS=usb
  E: ID_USB_INTERFACES=:090000:
  
  P: /devices/pci0000:00/0000:00:1a.7/usb1/1-0:1.0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1a.7/usb1/1-0:1.0
  E: DEVTYPE=usb_interface
  E: DRIVER=hub
  E: PRODUCT=1d6b/2/300
  E: TYPE=9/0/0
  E: INTERFACE=9/0/0
  E: MODALIAS=usb:v1D6Bp0002d0300dc09dsc00dp00ic09isc00ip00
  E: SUBSYSTEM=usb
  
  P: /devices/pci0000:00/0000:00:1a.7/usb1/1-3
  N: bus/usb/001/003
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1a.7/usb1/1-3
  E: MAJOR=189
  E: MINOR=2
  E: DEVNAME=/dev/bus/usb/001/003
  E: DEVTYPE=usb_device
  E: DRIVER=usb
  E: PRODUCT=413c/2513/a005
  E: TYPE=9/0/2
  E: BUSNUM=001
  E: DEVNUM=003
  E: SUBSYSTEM=usb
  E: ID_VENDOR=413c
  E: ID_VENDOR_ENC=413c
  E: ID_VENDOR_ID=413c
  E: ID_MODEL=2513
  E: ID_MODEL_ENC=2513
  E: ID_MODEL_ID=2513
  E: ID_REVISION=a005
  E: ID_SERIAL=413c_2513
  E: ID_BUS=usb
  E: ID_USB_INTERFACES=:090001:090002:
  
  P: /devices/pci0000:00/0000:00:1a.7/usb1/1-3/1-3.1
  N: bus/usb/001/007
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1a.7/usb1/1-3/1-3.1
  E: MAJOR=189
  E: MINOR=6
  E: DEVNAME=/dev/bus/usb/001/007
  E: DEVTYPE=usb_device
  E: DRIVER=usb
  E: PRODUCT=424/2514/0
  E: TYPE=9/0/2
  E: BUSNUM=001
  E: DEVNUM=007
  E: SUBSYSTEM=usb
  E: ID_VENDOR=0424
  E: ID_VENDOR_ENC=0424
  E: ID_VENDOR_ID=0424
  E: ID_MODEL=2514
  E: ID_MODEL_ENC=2514
  E: ID_MODEL_ID=2514
  E: ID_REVISION=0000
  E: ID_SERIAL=0424_2514
  E: ID_BUS=usb
  E: ID_USB_INTERFACES=:090001:090002:
  
  P: /devices/pci0000:00/0000:00:1a.7/usb1/1-3/1-3.1/1-3.1.3
  N: bus/usb/001/010
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1a.7/usb1/1-3/1-3.1/1-3.1.3
  E: MAJOR=189
  E: MINOR=9
  E: DEVNAME=/dev/bus/usb/001/010
  E: DEVTYPE=usb_device
  E: DRIVER=usb
  E: PRODUCT=1058/70a/1030
  E: TYPE=0/0/0
  E: BUSNUM=001
  E: DEVNUM=010
  E: SUBSYSTEM=usb
  E: ID_VENDOR=Western_Digital
  E: ID_VENDOR_ENC=Western\x20Digital
  E: ID_VENDOR_ID=1058
  E: ID_MODEL=My_Passport_070A
  E: ID_MODEL_ENC=My\x20Passport\x20070A
  E: ID_MODEL_ID=070a
  E: ID_REVISION=1030
  E: ID_SERIAL=Western_Digital_My_Passport_070A_57584D304139395330373331
  E: ID_SERIAL_SHORT=57584D304139395330373331
  E: ID_BUS=usb
  E: ID_USB_INTERFACES=:080650:
  
  P: /devices/pci0000:00/0000:00:1a.7/usb1/1-3/1-3.1/1-3.1.3/1-3.1.3:1.0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1a.7/usb1/1-3/1-3.1/1-3.1.3/1-3.1.3:1.0
  E: DEVTYPE=usb_interface
  E: DRIVER=usb-storage
  E: PRODUCT=1058/70a/1030
  E: TYPE=0/0/0
  E: INTERFACE=8/6/80
  E: MODALIAS=usb:v1058p070Ad1030dc00dsc00dp00ic08isc06ip50
  E: SUBSYSTEM=usb
  
  P: /devices/pci0000:00/0000:00:1a.7/usb1/1-3/1-3.1/1-3.1.3/1-3.1.3:1.0/host6
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1a.7/usb1/1-3/1-3.1/1-3.1.3/1-3.1.3:1.0/host6
  E: DEVTYPE=scsi_host
  E: SUBSYSTEM=scsi
  
  P: /devices/pci0000:00/0000:00:1a.7/usb1/1-3/1-3.1/1-3.1.3/1-3.1.3:1.0/host6/scsi_host/host6
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1a.7/usb1/1-3/1-3.1/1-3.1.3/1-3.1.3:1.0/host6/scsi_host/host6
  E: SUBSYSTEM=scsi_host
  
  P: /devices/pci0000:00/0000:00:1a.7/usb1/1-3/1-3.1/1-3.1.3/1-3.1.3:1.0/host6/target6:0:0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1a.7/usb1/1-3/1-3.1/1-3.1.3/1-3.1.3:1.0/host6/target6:0:0
  E: DEVTYPE=scsi_target
  E: SUBSYSTEM=scsi
  
  P: /devices/pci0000:00/0000:00:1a.7/usb1/1-3/1-3.1/1-3.1.3/1-3.1.3:1.0/host6/target6:0:0/6:0:0:0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1a.7/usb1/1-3/1-3.1/1-3.1.3/1-3.1.3:1.0/host6/target6:0:0/6:0:0:0
  E: DEVTYPE=scsi_device
  E: DRIVER=sd
  E: MODALIAS=scsi:t-0x00
  E: SUBSYSTEM=scsi
  
  P: /devices/pci0000:00/0000:00:1a.7/usb1/1-3/1-3.1/1-3.1.3/1-3.1.3:1.0/host6/target6:0:0/6:0:0:0/block/sdb
  N: sdb
  S: disk/by-id/ata-WDC_WD5000BMVV-11A1CS0_WD-WXM0A99S0731
  S: disk/by-id/scsi-SWD_My_Passport_070WXM0A99S0731
  S: disk/by-path/pci-0000:00:1a.7-usb-0:3.1.3:1.0-scsi-0:0:0:0
  S: disk/by-id/wwn-0x50014ee2ae2b6104
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1a.7/usb1/1-3/1-3.1/1-3.1.3/1-3.1.3:1.0/host6/target6:0:0/6:0:0:0/block/sdb
  E: MAJOR=8
  E: MINOR=16
  E: DEVNAME=/dev/sdb
  E: DEVTYPE=disk
  E: SUBSYSTEM=block
  E: ID_ATA=1
  E: ID_TYPE=disk
  E: ID_BUS=ata
  E: ID_MODEL=WDC_WD5000BMVV-11A1CS0
  E: ID_MODEL_ENC=WDC\x20WD5000BMVV-11A1CS0\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20
  E: ID_REVISION=01.01A10
  E: ID_SERIAL=WDC_WD5000BMVV-11A1CS0_WD-WXM0A99S0731
  E: ID_SERIAL_SHORT=WD-WXM0A99S0731
  E: ID_ATA_WRITE_CACHE=1
  E: ID_ATA_WRITE_CACHE_ENABLED=1
  E: ID_ATA_FEATURE_SET_HPA=1
  E: ID_ATA_FEATURE_SET_HPA_ENABLED=1
  E: ID_ATA_FEATURE_SET_PM=1
  E: ID_ATA_FEATURE_SET_PM_ENABLED=1
  E: ID_ATA_FEATURE_SET_SECURITY=1
  E: ID_ATA_FEATURE_SET_SECURITY_ENABLED=0
  E: ID_ATA_FEATURE_SET_SECURITY_ERASE_UNIT_MIN=134
  E: ID_ATA_FEATURE_SET_SECURITY_ENHANCED_ERASE_UNIT_MIN=134
  E: ID_ATA_FEATURE_SET_SMART=1
  E: ID_ATA_FEATURE_SET_SMART_ENABLED=1
  E: ID_ATA_FEATURE_SET_AAM=1
  E: ID_ATA_FEATURE_SET_AAM_ENABLED=1
  E: ID_ATA_FEATURE_SET_AAM_VENDOR_RECOMMENDED_VALUE=128
  E: ID_ATA_FEATURE_SET_AAM_CURRENT_VALUE=254
  E: ID_ATA_FEATURE_SET_APM=1
  E: ID_ATA_FEATURE_SET_APM_ENABLED=1
  E: ID_ATA_FEATURE_SET_APM_CURRENT_VALUE=96
  E: ID_ATA_DOWNLOAD_MICROCODE=1
  E: ID_ATA_SATA=1
  E: ID_ATA_SATA_SIGNAL_RATE_GEN2=1
  E: ID_ATA_SATA_SIGNAL_RATE_GEN1=1
  E: ID_ATA_ROTATION_RATE_RPM=5400
  E: ID_WWN=0x50014ee2ae2b6104
  E: ID_WWN_WITH_EXTENSION=0x50014ee2ae2b6104
  E: ID_SCSI_COMPAT=SWD_My_Passport_070WXM0A99S0731
  E: ID_PATH=pci-0000:00:1a.7-usb-0:3.1.3:1.0-scsi-0:0:0:0
  E: ID_PATH_TAG=pci-0000_00_1a_7-usb-0_3_1_3_1_0-scsi-0_0_0_0
  E: ID_PART_TABLE_TYPE=dos
  E: UDISKS_PRESENTATION_NOPOLICY=0
  E: UDISKS_PARTITION_TABLE=1
  E: UDISKS_PARTITION_TABLE_SCHEME=mbr
  E: UDISKS_PARTITION_TABLE_COUNT=1
  E: UDISKS_ATA_SMART_IS_AVAILABLE=1
  E: DEVLINKS=/dev/disk/by-id/ata-WDC_WD5000BMVV-11A1CS0_WD-WXM0A99S0731 /dev/disk/by-id/scsi-SWD_My_Passport_070WXM0A99S0731 /dev/disk/by-path/pci-0000:00:1a.7-usb-0:3.1.3:1.0-scsi-0:0:0:0 /dev/disk/by-id/wwn-0x50014ee2ae2b6104
  
  P: /devices/pci0000:00/0000:00:1a.7/usb1/1-3/1-3.1/1-3.1.3/1-3.1.3:1.0/host6/target6:0:0/6:0:0:0/block/sdb/sdb1
  N: sdb1
  S: disk/by-id/ata-WDC_WD5000BMVV-11A1CS0_WD-WXM0A99S0731-part1
  S: disk/by-id/scsi-SWD_My_Passport_070WXM0A99S0731-part1
  S: disk/by-path/pci-0000:00:1a.7-usb-0:3.1.3:1.0-scsi-0:0:0:0-part1
  S: disk/by-uuid/325220A852207331
  S: disk/by-label/My\x20Passport
  S: disk/by-id/wwn-0x50014ee2ae2b6104-part1
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1a.7/usb1/1-3/1-3.1/1-3.1.3/1-3.1.3:1.0/host6/target6:0:0/6:0:0:0/block/sdb/sdb1
  E: MAJOR=8
  E: MINOR=17
  E: DEVNAME=/dev/sdb1
  E: DEVTYPE=partition
  E: SUBSYSTEM=block
  E: ID_ATA=1
  E: ID_TYPE=disk
  E: ID_BUS=ata
  E: ID_MODEL=WDC_WD5000BMVV-11A1CS0
  E: ID_MODEL_ENC=WDC\x20WD5000BMVV-11A1CS0\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20
  E: ID_REVISION=01.01A10
  E: ID_SERIAL=WDC_WD5000BMVV-11A1CS0_WD-WXM0A99S0731
  E: ID_SERIAL_SHORT=WD-WXM0A99S0731
  E: ID_ATA_WRITE_CACHE=1
  E: ID_ATA_WRITE_CACHE_ENABLED=1
  E: ID_ATA_FEATURE_SET_HPA=1
  E: ID_ATA_FEATURE_SET_HPA_ENABLED=1
  E: ID_ATA_FEATURE_SET_PM=1
  E: ID_ATA_FEATURE_SET_PM_ENABLED=1
  E: ID_ATA_FEATURE_SET_SECURITY=1
  E: ID_ATA_FEATURE_SET_SECURITY_ENABLED=0
  E: ID_ATA_FEATURE_SET_SECURITY_ERASE_UNIT_MIN=134
  E: ID_ATA_FEATURE_SET_SECURITY_ENHANCED_ERASE_UNIT_MIN=134
  E: ID_ATA_FEATURE_SET_SMART=1
  E: ID_ATA_FEATURE_SET_SMART_ENABLED=1
  E: ID_ATA_FEATURE_SET_AAM=1
  E: ID_ATA_FEATURE_SET_AAM_ENABLED=1
  E: ID_ATA_FEATURE_SET_AAM_VENDOR_RECOMMENDED_VALUE=128
  E: ID_ATA_FEATURE_SET_AAM_CURRENT_VALUE=254
  E: ID_ATA_FEATURE_SET_APM=1
  E: ID_ATA_FEATURE_SET_APM_ENABLED=1
  E: ID_ATA_FEATURE_SET_APM_CURRENT_VALUE=96
  E: ID_ATA_DOWNLOAD_MICROCODE=1
  E: ID_ATA_SATA=1
  E: ID_ATA_SATA_SIGNAL_RATE_GEN2=1
  E: ID_ATA_SATA_SIGNAL_RATE_GEN1=1
  E: ID_ATA_ROTATION_RATE_RPM=5400
  E: ID_WWN=0x50014ee2ae2b6104
  E: ID_WWN_WITH_EXTENSION=0x50014ee2ae2b6104
  E: ID_SCSI_COMPAT=SWD_My_Passport_070WXM0A99S0731
  E: ID_PATH=pci-0000:00:1a.7-usb-0:3.1.3:1.0-scsi-0:0:0:0
  E: ID_PATH_TAG=pci-0000_00_1a_7-usb-0_3_1_3_1_0-scsi-0_0_0_0
  E: ID_PART_TABLE_TYPE=dos
  E: ID_FS_LABEL=My_Passport
  E: ID_FS_LABEL_ENC=My\x20Passport
  E: ID_FS_UUID=325220A852207331
  E: ID_FS_UUID_ENC=325220A852207331
  E: ID_FS_TYPE=ntfs
  E: ID_FS_USAGE=filesystem
  E: ID_PART_ENTRY_SCHEME=dos
  E: ID_PART_ENTRY_TYPE=0x7
  E: ID_PART_ENTRY_NUMBER=1
  E: UDISKS_PRESENTATION_NOPOLICY=0
  E: UDISKS_PARTITION=1
  E: UDISKS_PARTITION_SCHEME=mbr
  E: UDISKS_PARTITION_NUMBER=1
  E: UDISKS_PARTITION_TYPE=0x07
  E: UDISKS_PARTITION_SIZE=499404242944
  E: UDISKS_PARTITION_SLAVE=/sys/devices/pci0000:00/0000:00:1a.7/usb1/1-3/1-3.1/1-3.1.3/1-3.1.3:1.0/host6/target6:0:0/6:0:0:0/block/sdb
  E: UDISKS_PARTITION_OFFSET=1048576
  E: UDISKS_PARTITION_ALIGNMENT_OFFSET=0
  E: DEVLINKS=/dev/disk/by-id/ata-WDC_WD5000BMVV-11A1CS0_WD-WXM0A99S0731-part1 /dev/disk/by-id/scsi-SWD_My_Passport_070WXM0A99S0731-part1 /dev/disk/by-path/pci-0000:00:1a.7-usb-0:3.1.3:1.0-scsi-0:0:0:0-part1 /dev/disk/by-uuid/325220A852207331 /dev/disk/by-label/My\x20Passport /dev/disk/by-id/wwn-0x50014ee2ae2b6104-part1
  
  P: /devices/pci0000:00/0000:00:1a.7/usb1/1-3/1-3.1/1-3.1.3/1-3.1.3:1.0/host6/target6:0:0/6:0:0:0/bsg/6:0:0:0
  N: bsg/6:0:0:0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1a.7/usb1/1-3/1-3.1/1-3.1.3/1-3.1.3:1.0/host6/target6:0:0/6:0:0:0/bsg/6:0:0:0
  E: MAJOR=253
  E: MINOR=2
  E: DEVNAME=/dev/bsg/6:0:0:0
  E: SUBSYSTEM=bsg
  
  P: /devices/pci0000:00/0000:00:1a.7/usb1/1-3/1-3.1/1-3.1.3/1-3.1.3:1.0/host6/target6:0:0/6:0:0:0/scsi_device/6:0:0:0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1a.7/usb1/1-3/1-3.1/1-3.1.3/1-3.1.3:1.0/host6/target6:0:0/6:0:0:0/scsi_device/6:0:0:0
  E: SUBSYSTEM=scsi_device
  
  P: /devices/pci0000:00/0000:00:1a.7/usb1/1-3/1-3.1/1-3.1.3/1-3.1.3:1.0/host6/target6:0:0/6:0:0:0/scsi_disk/6:0:0:0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1a.7/usb1/1-3/1-3.1/1-3.1.3/1-3.1.3:1.0/host6/target6:0:0/6:0:0:0/scsi_disk/6:0:0:0
  E: SUBSYSTEM=scsi_disk
  
  P: /devices/pci0000:00/0000:00:1a.7/usb1/1-3/1-3.1/1-3.1.3/1-3.1.3:1.0/host6/target6:0:0/6:0:0:0/scsi_generic/sg2
  N: sg2
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1a.7/usb1/1-3/1-3.1/1-3.1.3/1-3.1.3:1.0/host6/target6:0:0/6:0:0:0/scsi_generic/sg2
  E: MAJOR=21
  E: MINOR=2
  E: DEVNAME=/dev/sg2
  E: SUBSYSTEM=scsi_generic
  
  P: /devices/pci0000:00/0000:00:1a.7/usb1/1-3/1-3.1/1-3.1.3/1-3.1.3:1.0/host6/target6:0:0/6:0:0:1
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1a.7/usb1/1-3/1-3.1/1-3.1.3/1-3.1.3:1.0/host6/target6:0:0/6:0:0:1
  E: DEVTYPE=scsi_device
  E: DRIVER=sr
  E: MODALIAS=scsi:t-0x05
  E: SUBSYSTEM=scsi
  
  P: /devices/pci0000:00/0000:00:1a.7/usb1/1-3/1-3.1/1-3.1.3/1-3.1.3:1.0/host6/target6:0:0/6:0:0:1/block/sr1
  N: sr1
  S: scd1
  S: disk/by-id/usb-WD_Virtual_CD_070A_57584D304139395330373331-0:1
  S: disk/by-path/pci-0000:00:1a.7-usb-0:3.1.3:1.0-scsi-0:0:0:1
  S: disk/by-label/WD\x20SmartWare
  S: cdrom
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1a.7/usb1/1-3/1-3.1/1-3.1.3/1-3.1.3:1.0/host6/target6:0:0/6:0:0:1/block/sr1
  E: MAJOR=11
  E: MINOR=1
  E: DEVNAME=/dev/sr1
  E: DEVTYPE=disk
  E: SUBSYSTEM=block
  E: ID_CDROM=1
  E: ID_CDROM_MRW=1
  E: ID_CDROM_MRW_W=1
  E: ID_CDROM_MEDIA=1
  E: ID_CDROM_MEDIA_CD=1
  E: ID_CDROM_MEDIA_TRACK_COUNT_DATA=1
  E: ID_VENDOR=WD
  E: ID_VENDOR_ENC=WD\x20\x20\x20\x20\x20\x20
  E: ID_VENDOR_ID=1058
  E: ID_MODEL=Virtual_CD_070A
  E: ID_MODEL_ENC=Virtual\x20CD\x20070A\x20
  E: ID_MODEL_ID=070a
  E: ID_REVISION=1030
  E: ID_SERIAL=WD_Virtual_CD_070A_57584D304139395330373331-0:1
  E: ID_SERIAL_SHORT=57584D304139395330373331
  E: ID_TYPE=cd
  E: ID_INSTANCE=0:1
  E: ID_BUS=usb
  E: ID_USB_INTERFACES=:080650:
  E: ID_USB_INTERFACE_NUM=00
  E: ID_USB_DRIVER=usb-storage
  E: ID_PATH=pci-0000:00:1a.7-usb-0:3.1.3:1.0-scsi-0:0:0:1
  E: ID_PATH_TAG=pci-0000_00_1a_7-usb-0_3_1_3_1_0-scsi-0_0_0_1
  E: ID_FS_LABEL=WD_SmartWare
  E: ID_FS_LABEL_ENC=WD\x20SmartWare
  E: ID_FS_TYPE=udf
  E: ID_FS_USAGE=filesystem
  E: GENERATED=1
  E: UDISKS_PRESENTATION_NOPOLICY=0
  E: DEVLINKS=/dev/scd1 /dev/disk/by-id/usb-WD_Virtual_CD_070A_57584D304139395330373331-0:1 /dev/disk/by-path/pci-0000:00:1a.7-usb-0:3.1.3:1.0-scsi-0:0:0:1 /dev/disk/by-label/WD\x20SmartWare /dev/cdrom
  E: TAGS=:udev-acl:
  
  P: /devices/pci0000:00/0000:00:1a.7/usb1/1-3/1-3.1/1-3.1.3/1-3.1.3:1.0/host6/target6:0:0/6:0:0:1/bsg/6:0:0:1
  N: bsg/6:0:0:1
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1a.7/usb1/1-3/1-3.1/1-3.1.3/1-3.1.3:1.0/host6/target6:0:0/6:0:0:1/bsg/6:0:0:1
  E: MAJOR=253
  E: MINOR=3
  E: DEVNAME=/dev/bsg/6:0:0:1
  E: SUBSYSTEM=bsg
  
  P: /devices/pci0000:00/0000:00:1a.7/usb1/1-3/1-3.1/1-3.1.3/1-3.1.3:1.0/host6/target6:0:0/6:0:0:1/scsi_device/6:0:0:1
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1a.7/usb1/1-3/1-3.1/1-3.1.3/1-3.1.3:1.0/host6/target6:0:0/6:0:0:1/scsi_device/6:0:0:1
  E: SUBSYSTEM=scsi_device
  
  P: /devices/pci0000:00/0000:00:1a.7/usb1/1-3/1-3.1/1-3.1.3/1-3.1.3:1.0/host6/target6:0:0/6:0:0:1/scsi_generic/sg3
  N: sg3
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1a.7/usb1/1-3/1-3.1/1-3.1.3/1-3.1.3:1.0/host6/target6:0:0/6:0:0:1/scsi_generic/sg3
  E: MAJOR=21
  E: MINOR=3
  E: DEVNAME=/dev/sg3
  E: SUBSYSTEM=scsi_generic
  E: TAGS=:udev-acl:
  
  P: /devices/pci0000:00/0000:00:1a.7/usb1/1-3/1-3.1/1-3.1.3/1-3.1.3:1.0/host6/target6:0:0/6:0:0:2
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1a.7/usb1/1-3/1-3.1/1-3.1.3/1-3.1.3:1.0/host6/target6:0:0/6:0:0:2
  E: DEVTYPE=scsi_device
  E: DRIVER=ses
  E: MODALIAS=scsi:t-0x0d
  E: SUBSYSTEM=scsi
  
  P: /devices/pci0000:00/0000:00:1a.7/usb1/1-3/1-3.1/1-3.1.3/1-3.1.3:1.0/host6/target6:0:0/6:0:0:2/bsg/6:0:0:2
  N: bsg/6:0:0:2
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1a.7/usb1/1-3/1-3.1/1-3.1.3/1-3.1.3:1.0/host6/target6:0:0/6:0:0:2/bsg/6:0:0:2
  E: MAJOR=253
  E: MINOR=4
  E: DEVNAME=/dev/bsg/6:0:0:2
  E: SUBSYSTEM=bsg
  
  P: /devices/pci0000:00/0000:00:1a.7/usb1/1-3/1-3.1/1-3.1.3/1-3.1.3:1.0/host6/target6:0:0/6:0:0:2/scsi_device/6:0:0:2
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1a.7/usb1/1-3/1-3.1/1-3.1.3/1-3.1.3:1.0/host6/target6:0:0/6:0:0:2/scsi_device/6:0:0:2
  E: SUBSYSTEM=scsi_device
  
  P: /devices/pci0000:00/0000:00:1a.7/usb1/1-3/1-3.1/1-3.1.3/1-3.1.3:1.0/host6/target6:0:0/6:0:0:2/scsi_generic/sg4
  N: sg4
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1a.7/usb1/1-3/1-3.1/1-3.1.3/1-3.1.3:1.0/host6/target6:0:0/6:0:0:2/scsi_generic/sg4
  E: MAJOR=21
  E: MINOR=4
  E: DEVNAME=/dev/sg4
  E: SUBSYSTEM=scsi_generic
  
  P: /devices/pci0000:00/0000:00:1a.7/usb1/1-3/1-3.1/1-3.1:1.0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1a.7/usb1/1-3/1-3.1/1-3.1:1.0
  E: DEVTYPE=usb_interface
  E: DRIVER=hub
  E: PRODUCT=424/2514/0
  E: TYPE=9/0/2
  E: INTERFACE=9/0/2
  E: MODALIAS=usb:v0424p2514d0000dc09dsc00dp02ic09isc00ip02
  E: SUBSYSTEM=usb
  
  P: /devices/pci0000:00/0000:00:1a.7/usb1/1-3/1-3.2
  N: bus/usb/001/008
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1a.7/usb1/1-3/1-3.2
  E: MAJOR=189
  E: MINOR=7
  E: DEVNAME=/dev/bus/usb/001/008
  E: DEVTYPE=usb_device
  E: DRIVER=usb
  E: PRODUCT=424/2514/bb3
  E: TYPE=9/0/2
  E: BUSNUM=001
  E: DEVNUM=008
  E: SUBSYSTEM=usb
  E: ID_VENDOR=0424
  E: ID_VENDOR_ENC=0424
  E: ID_VENDOR_ID=0424
  E: ID_MODEL=2514
  E: ID_MODEL_ENC=2514
  E: ID_MODEL_ID=2514
  E: ID_REVISION=0bb3
  E: ID_SERIAL=0424_2514
  E: ID_BUS=usb
  E: ID_USB_INTERFACES=:090001:090002:
  
  P: /devices/pci0000:00/0000:00:1a.7/usb1/1-3/1-3.2/1-3.2:1.0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1a.7/usb1/1-3/1-3.2/1-3.2:1.0
  E: DEVTYPE=usb_interface
  E: DRIVER=hub
  E: PRODUCT=424/2514/bb3
  E: TYPE=9/0/2
  E: INTERFACE=9/0/2
  E: MODALIAS=usb:v0424p2514d0BB3dc09dsc00dp02ic09isc00ip02
  E: SUBSYSTEM=usb
  
  P: /devices/pci0000:00/0000:00:1a.7/usb1/1-3/1-3:1.0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1a.7/usb1/1-3/1-3:1.0
  E: DEVTYPE=usb_interface
  E: DRIVER=hub
  E: PRODUCT=413c/2513/a005
  E: TYPE=9/0/2
  E: INTERFACE=9/0/2
  E: MODALIAS=usb:v413Cp2513dA005dc09dsc00dp02ic09isc00ip02
  E: SUBSYSTEM=usb
  
  P: /devices/pci0000:00/0000:00:1a.7/usb1/1-4
  N: bus/usb/001/004
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1a.7/usb1/1-4
  E: MAJOR=189
  E: MINOR=3
  E: DEVNAME=/dev/bus/usb/001/004
  E: DEVTYPE=usb_device
  E: DRIVER=usb
  E: PRODUCT=413c/2513/a005
  E: TYPE=9/0/2
  E: BUSNUM=001
  E: DEVNUM=004
  E: SUBSYSTEM=usb
  E: ID_VENDOR=413c
  E: ID_VENDOR_ENC=413c
  E: ID_VENDOR_ID=413c
  E: ID_MODEL=2513
  E: ID_MODEL_ENC=2513
  E: ID_MODEL_ID=2513
  E: ID_REVISION=a005
  E: ID_SERIAL=413c_2513
  E: ID_BUS=usb
  E: ID_USB_INTERFACES=:090001:090002:
  
  P: /devices/pci0000:00/0000:00:1a.7/usb1/1-4/1-4.2
  N: bus/usb/001/009
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1a.7/usb1/1-4/1-4.2
  E: MAJOR=189
  E: MINOR=8
  E: DEVNAME=/dev/bus/usb/001/009
  E: DEVTYPE=usb_device
  E: DRIVER=usb
  E: PRODUCT=46d/c016/340
  E: TYPE=0/0/0
  E: BUSNUM=001
  E: DEVNUM=009
  E: SUBSYSTEM=usb
  E: ID_VENDOR=Logitech
  E: ID_VENDOR_ENC=Logitech
  E: ID_VENDOR_ID=046d
  E: ID_MODEL=Optical_USB_Mouse
  E: ID_MODEL_ENC=Optical\x20USB\x20Mouse
  E: ID_MODEL_ID=c016
  E: ID_REVISION=0340
  E: ID_SERIAL=Logitech_Optical_USB_Mouse
  E: ID_BUS=usb
  E: ID_USB_INTERFACES=:030102:
  E: UPOWER_VENDOR=Logitech, Inc.
  
  P: /devices/pci0000:00/0000:00:1a.7/usb1/1-4/1-4.2/1-4.2:1.0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1a.7/usb1/1-4/1-4.2/1-4.2:1.0
  E: DEVTYPE=usb_interface
  E: DRIVER=usbhid
  E: PRODUCT=46d/c016/340
  E: TYPE=0/0/0
  E: INTERFACE=3/1/2
  E: MODALIAS=usb:v046DpC016d0340dc00dsc00dp00ic03isc01ip02
  E: SUBSYSTEM=usb
  
  P: /devices/pci0000:00/0000:00:1a.7/usb1/1-4/1-4.2/1-4.2:1.0/0003:046D:C016.0001
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1a.7/usb1/1-4/1-4.2/1-4.2:1.0/0003:046D:C016.0001
  E: DRIVER=generic-usb
  E: HID_ID=0003:0000046D:0000C016
  E: HID_NAME=Logitech Optical USB Mouse
  E: HID_PHYS=usb-0000:00:1a.7-4.2/input0
  E: SUBSYSTEM=hid
  E: MODALIAS=hid:b0003v0000046Dp0000C016
  
  P: /devices/pci0000:00/0000:00:1a.7/usb1/1-4/1-4.2/1-4.2:1.0/0003:046D:C016.0001/hidraw/hidraw0
  N: hidraw0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1a.7/usb1/1-4/1-4.2/1-4.2:1.0/0003:046D:C016.0001/hidraw/hidraw0
  E: MAJOR=250
  E: MINOR=0
  E: DEVNAME=/dev/hidraw0
  E: SUBSYSTEM=hidraw
  
  P: /devices/pci0000:00/0000:00:1a.7/usb1/1-4/1-4.2/1-4.2:1.0/input/input4
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1a.7/usb1/1-4/1-4.2/1-4.2:1.0/input/input4
  E: PRODUCT=3/46d/c016/110
  E: NAME="Logitech Optical USB Mouse"
  E: PHYS="usb-0000:00:1a.7-4.2/input0"
  E: UNIQ=""
  E: PROP=0
  E: EV=17
  E: KEY=70000 0 0 0 0
  E: REL=103
  E: MSC=10
  E: MODALIAS=input:b0003v046DpC016e0110-e0,1,2,4,k110,111,112,r0,1,8,am4,lsfw
  E: SUBSYSTEM=input
  E: ID_INPUT=1
  E: ID_INPUT_MOUSE=1
  E: ID_VENDOR=Logitech
  E: ID_VENDOR_ENC=Logitech
  E: ID_VENDOR_ID=046d
  E: ID_MODEL=Optical_USB_Mouse
  E: ID_MODEL_ENC=Optical\x20USB\x20Mouse
  E: ID_MODEL_ID=c016
  E: ID_REVISION=0340
  E: ID_SERIAL=Logitech_Optical_USB_Mouse
  E: ID_TYPE=hid
  E: ID_BUS=usb
  E: ID_USB_INTERFACES=:030102:
  E: ID_USB_INTERFACE_NUM=00
  E: ID_USB_DRIVER=usbhid
  E: ID_PATH=pci-0000:00:1a.7-usb-0:4.2:1.0
  E: ID_PATH_TAG=pci-0000_00_1a_7-usb-0_4_2_1_0
  
  P: /devices/pci0000:00/0000:00:1a.7/usb1/1-4/1-4.2/1-4.2:1.0/input/input4/event4
  N: input/event4
  S: input/by-id/usb-Logitech_Optical_USB_Mouse-event-mouse
  S: input/by-path/pci-0000:00:1a.7-usb-0:4.2:1.0-event-mouse
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1a.7/usb1/1-4/1-4.2/1-4.2:1.0/input/input4/event4
  E: MAJOR=13
  E: MINOR=68
  E: DEVNAME=/dev/input/event4
  E: SUBSYSTEM=input
  E: ID_INPUT=1
  E: ID_INPUT_MOUSE=1
  E: ID_VENDOR=Logitech
  E: ID_VENDOR_ENC=Logitech
  E: ID_VENDOR_ID=046d
  E: ID_MODEL=Optical_USB_Mouse
  E: ID_MODEL_ENC=Optical\x20USB\x20Mouse
  E: ID_MODEL_ID=c016
  E: ID_REVISION=0340
  E: ID_SERIAL=Logitech_Optical_USB_Mouse
  E: ID_TYPE=hid
  E: ID_BUS=usb
  E: ID_USB_INTERFACES=:030102:
  E: ID_USB_INTERFACE_NUM=00
  E: ID_USB_DRIVER=usbhid
  E: ID_PATH=pci-0000:00:1a.7-usb-0:4.2:1.0
  E: ID_PATH_TAG=pci-0000_00_1a_7-usb-0_4_2_1_0
  E: DEVLINKS=/dev/input/by-id/usb-Logitech_Optical_USB_Mouse-event-mouse /dev/input/by-path/pci-0000:00:1a.7-usb-0:4.2:1.0-event-mouse
  
  P: /devices/pci0000:00/0000:00:1a.7/usb1/1-4/1-4.2/1-4.2:1.0/input/input4/mouse0
  N: input/mouse0
  S: input/by-id/usb-Logitech_Optical_USB_Mouse-mouse
  S: input/by-path/pci-0000:00:1a.7-usb-0:4.2:1.0-mouse
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1a.7/usb1/1-4/1-4.2/1-4.2:1.0/input/input4/mouse0
  E: MAJOR=13
  E: MINOR=32
  E: DEVNAME=/dev/input/mouse0
  E: SUBSYSTEM=input
  E: ID_INPUT=1
  E: ID_INPUT_MOUSE=1
  E: ID_VENDOR=Logitech
  E: ID_VENDOR_ENC=Logitech
  E: ID_VENDOR_ID=046d
  E: ID_MODEL=Optical_USB_Mouse
  E: ID_MODEL_ENC=Optical\x20USB\x20Mouse
  E: ID_MODEL_ID=c016
  E: ID_REVISION=0340
  E: ID_SERIAL=Logitech_Optical_USB_Mouse
  E: ID_TYPE=hid
  E: ID_BUS=usb
  E: ID_USB_INTERFACES=:030102:
  E: ID_USB_INTERFACE_NUM=00
  E: ID_USB_DRIVER=usbhid
  E: ID_PATH=pci-0000:00:1a.7-usb-0:4.2:1.0
  E: ID_PATH_TAG=pci-0000_00_1a_7-usb-0_4_2_1_0
  E: DEVLINKS=/dev/input/by-id/usb-Logitech_Optical_USB_Mouse-mouse /dev/input/by-path/pci-0000:00:1a.7-usb-0:4.2:1.0-mouse
  
  P: /devices/pci0000:00/0000:00:1a.7/usb1/1-4/1-4:1.0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1a.7/usb1/1-4/1-4:1.0
  E: DEVTYPE=usb_interface
  E: DRIVER=hub
  E: PRODUCT=413c/2513/a005
  E: TYPE=9/0/2
  E: INTERFACE=9/0/2
  E: MODALIAS=usb:v413Cp2513dA005dc09dsc00dp02ic09isc00ip02
  E: SUBSYSTEM=usb
  
  P: /devices/pci0000:00/0000:00:1a.7/usb1/1-6
  N: bus/usb/001/006
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1a.7/usb1/1-6
  E: MAJOR=189
  E: MINOR=5
  E: DEVNAME=/dev/bus/usb/001/006
  E: DEVTYPE=usb_device
  E: DRIVER=usb
  E: PRODUCT=c45/63f1/9416
  E: TYPE=239/2/1
  E: BUSNUM=001
  E: DEVNUM=006
  E: SUBSYSTEM=usb
  E: ID_VENDOR=CN0K113P7248703G05EC
  E: ID_VENDOR_ENC=CN0K113P7248703G05EC
  E: ID_VENDOR_ID=0c45
  E: ID_MODEL=Integrated_Webcam_2M
  E: ID_MODEL_ENC=Integrated_Webcam_2M
  E: ID_MODEL_ID=63f1
  E: ID_REVISION=9416
  E: ID_SERIAL=CN0K113P7248703G05EC_Integrated_Webcam_2M
  E: ID_BUS=usb
  E: ID_USB_INTERFACES=:0e0100:0e0200:
  
  P: /devices/pci0000:00/0000:00:1a.7/usb1/1-6/1-6:1.0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1a.7/usb1/1-6/1-6:1.0
  E: DEVTYPE=usb_interface
  E: DRIVER=uvcvideo
  E: PRODUCT=c45/63f1/9416
  E: TYPE=239/2/1
  E: INTERFACE=14/1/0
  E: MODALIAS=usb:v0C45p63F1d9416dcEFdsc02dp01ic0Eisc01ip00
  E: SUBSYSTEM=usb
  
  P: /devices/pci0000:00/0000:00:1a.7/usb1/1-6/1-6:1.0/input/input10
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1a.7/usb1/1-6/1-6:1.0/input/input10
  E: PRODUCT=3/c45/63f1/9416
  E: NAME="Integrated_Webcam_2M"
  E: PHYS="usb-0000:00:1a.7-6/button"
  E: PROP=0
  E: EV=3
  E: KEY=100000 0 0 0
  E: MODALIAS=input:b0003v0C45p63F1e9416-e0,1,kD4,ramlsfw
  E: SUBSYSTEM=input
  E: ID_INPUT=1
  E: ID_INPUT_KEY=1
  E: ID_VENDOR=CN0K113P7248703G05EC
  E: ID_VENDOR_ENC=CN0K113P7248703G05EC
  E: ID_VENDOR_ID=0c45
  E: ID_MODEL=Integrated_Webcam_2M
  E: ID_MODEL_ENC=Integrated_Webcam_2M
  E: ID_MODEL_ID=63f1
  E: ID_REVISION=9416
  E: ID_SERIAL=CN0K113P7248703G05EC_Integrated_Webcam_2M
  E: ID_TYPE=video
  E: ID_BUS=usb
  E: ID_USB_INTERFACES=:0e0100:0e0200:
  E: ID_USB_INTERFACE_NUM=00
  E: ID_USB_DRIVER=uvcvideo
  E: ID_PATH=pci-0000:00:1a.7-usb-0:6:1.0
  E: ID_PATH_TAG=pci-0000_00_1a_7-usb-0_6_1_0
  
  P: /devices/pci0000:00/0000:00:1a.7/usb1/1-6/1-6:1.0/input/input10/event6
  N: input/event6
  S: input/by-id/usb-CN0K113P7248703G05EC_Integrated_Webcam_2M-event-if00
  S: input/by-path/pci-0000:00:1a.7-usb-0:6:1.0-event
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1a.7/usb1/1-6/1-6:1.0/input/input10/event6
  E: MAJOR=13
  E: MINOR=70
  E: DEVNAME=/dev/input/event6
  E: SUBSYSTEM=input
  E: ID_INPUT=1
  E: ID_INPUT_KEY=1
  E: ID_VENDOR=CN0K113P7248703G05EC
  E: ID_VENDOR_ENC=CN0K113P7248703G05EC
  E: ID_VENDOR_ID=0c45
  E: ID_MODEL=Integrated_Webcam_2M
  E: ID_MODEL_ENC=Integrated_Webcam_2M
  E: ID_MODEL_ID=63f1
  E: ID_REVISION=9416
  E: ID_SERIAL=CN0K113P7248703G05EC_Integrated_Webcam_2M
  E: ID_TYPE=video
  E: ID_BUS=usb
  E: ID_USB_INTERFACES=:0e0100:0e0200:
  E: ID_USB_INTERFACE_NUM=00
  E: ID_USB_DRIVER=uvcvideo
  E: ID_PATH=pci-0000:00:1a.7-usb-0:6:1.0
  E: ID_PATH_TAG=pci-0000_00_1a_7-usb-0_6_1_0
  E: XKBMODEL=pc105
  E: XKBLAYOUT=us
  E: DEVLINKS=/dev/input/by-id/usb-CN0K113P7248703G05EC_Integrated_Webcam_2M-event-if00 /dev/input/by-path/pci-0000:00:1a.7-usb-0:6:1.0-event
  
  P: /devices/pci0000:00/0000:00:1a.7/usb1/1-6/1-6:1.0/video4linux/video0
  N: video0
  S: v4l/by-id/usb-CN0K113P7248703G05EC_Integrated_Webcam_2M-video-index0
  S: v4l/by-path/pci-0000:00:1a.7-usb-0:6:1.0-video-index0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1a.7/usb1/1-6/1-6:1.0/video4linux/video0
  E: MAJOR=81
  E: MINOR=0
  E: DEVNAME=/dev/video0
  E: SUBSYSTEM=video4linux
  E: ID_V4L_VERSION=2
  E: ID_V4L_PRODUCT=Integrated_Webcam_2M
  E: ID_V4L_CAPABILITIES=:capture:
  E: ID_VENDOR=CN0K113P7248703G05EC
  E: ID_VENDOR_ENC=CN0K113P7248703G05EC
  E: ID_VENDOR_ID=0c45
  E: ID_MODEL=Integrated_Webcam_2M
  E: ID_MODEL_ENC=Integrated_Webcam_2M
  E: ID_MODEL_ID=63f1
  E: ID_REVISION=9416
  E: ID_SERIAL=CN0K113P7248703G05EC_Integrated_Webcam_2M
  E: ID_TYPE=video
  E: ID_BUS=usb
  E: ID_USB_INTERFACES=:0e0100:0e0200:
  E: ID_USB_INTERFACE_NUM=00
  E: ID_USB_DRIVER=uvcvideo
  E: ID_PATH=pci-0000:00:1a.7-usb-0:6:1.0
  E: ID_PATH_TAG=pci-0000_00_1a_7-usb-0_6_1_0
  E: COLORD_DEVICE=1
  E: COLORD_KIND=camera
  E: DEVLINKS=/dev/v4l/by-id/usb-CN0K113P7248703G05EC_Integrated_Webcam_2M-video-index0 /dev/v4l/by-path/pci-0000:00:1a.7-usb-0:6:1.0-video-index0
  E: TAGS=:udev-acl:
  
  P: /devices/pci0000:00/0000:00:1a.7/usb1/1-6/1-6:1.1
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1a.7/usb1/1-6/1-6:1.1
  E: DEVTYPE=usb_interface
  E: DRIVER=uvcvideo
  E: PRODUCT=c45/63f1/9416
  E: TYPE=239/2/1
  E: INTERFACE=14/2/0
  E: MODALIAS=usb:v0C45p63F1d9416dcEFdsc02dp01ic0Eisc02ip00
  E: SUBSYSTEM=usb
  
  P: /devices/pci0000:00/0000:00:1a.7/usbmon/usbmon1
  N: usbmon1
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1a.7/usbmon/usbmon1
  E: MAJOR=252
  E: MINOR=1
  E: DEVNAME=/dev/usbmon1
  E: SUBSYSTEM=usbmon
  
  P: /devices/pci0000:00/0000:00:1b.0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1b.0
  E: DRIVER=HDA Intel
  E: PCI_CLASS=40300
  E: PCI_ID=8086:293E
  E: PCI_SUBSYS_ID=1028:024F
  E: PCI_SLOT_NAME=0000:00:1b.0
  E: MODALIAS=pci:v00008086d0000293Esv00001028sd0000024Fbc04sc03i00
  E: SUBSYSTEM=pci
  
  P: /devices/pci0000:00/0000:00:1b.0/sound/card0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1b.0/sound/card0
  E: SUBSYSTEM=sound
  E: SOUND_INITIALIZED=1
  E: ID_VENDOR_FROM_DATABASE=Intel Corporation
  E: ID_MODEL_FROM_DATABASE=82801I (ICH9 Family) HD Audio Controller
  E: ID_BUS=pci
  E: ID_VENDOR_ID=0x8086
  E: ID_MODEL_ID=0x293e
  E: ID_PATH=pci-0000:00:1b.0
  E: ID_PATH_TAG=pci-0000_00_1b_0
  E: SOUND_FORM_FACTOR=internal
  E: PULSE_PROFILE_SET=extra-hdmi.conf
  
  P: /devices/pci0000:00/0000:00:1b.0/sound/card0/hwC0D0
  N: snd/hwC0D0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1b.0/sound/card0/hwC0D0
  E: MAJOR=116
  E: MINOR=7
  E: DEVNAME=/dev/snd/hwC0D0
  E: SUBSYSTEM=sound
  E: TAGS=:udev-acl:
  
  P: /devices/pci0000:00/0000:00:1b.0/sound/card0/hwC0D1
  N: snd/hwC0D1
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1b.0/sound/card0/hwC0D1
  E: MAJOR=116
  E: MINOR=6
  E: DEVNAME=/dev/snd/hwC0D1
  E: SUBSYSTEM=sound
  E: TAGS=:udev-acl:
  
  P: /devices/pci0000:00/0000:00:1b.0/sound/card0/hwC0D2
  N: snd/hwC0D2
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1b.0/sound/card0/hwC0D2
  E: MAJOR=116
  E: MINOR=5
  E: DEVNAME=/dev/snd/hwC0D2
  E: SUBSYSTEM=sound
  E: TAGS=:udev-acl:
  
  P: /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1b.0/sound/card0/input12
  E: PRODUCT=0/0/0/0
  E: NAME="HDA Intel HDMI/DP,pcm=3"
  E: PHYS="ALSA"
  E: PROP=0
  E: EV=21
  E: SW=100
  E: MODALIAS=input:b0000v0000p0000e0000-e0,5,kramlsfw8,
  E: SUBSYSTEM=input
  E: ID_INPUT=1
  E: ID_INPUT_SNDJACK=1
  E: ID_PATH=pci-0000:00:1b.0
  E: ID_PATH_TAG=pci-0000_00_1b_0
  
  P: /devices/pci0000:00/0000:00:1b.0/sound/card0/input12/event11
  N: input/event11
  S: input/by-path/pci-0000:00:1b.0-event-sndjack
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1b.0/sound/card0/input12/event11
  E: MAJOR=13
  E: MINOR=75
  E: DEVNAME=/dev/input/event11
  E: SUBSYSTEM=input
  E: ID_INPUT=1
  E: ID_INPUT_SNDJACK=1
  E: ID_SERIAL=noserial
  E: ID_PATH=pci-0000:00:1b.0
  E: ID_PATH_TAG=pci-0000_00_1b_0
  E: DEVLINKS=/dev/input/by-path/pci-0000:00:1b.0-event-sndjack
  
  P: /devices/pci0000:00/0000:00:1b.0/sound/card0/input13
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1b.0/sound/card0/input13
  E: PRODUCT=0/0/0/0
  E: NAME="HDA Intel Mic at Sep Left Jack"
  E: PHYS="ALSA"
  E: PROP=0
  E: EV=21
  E: SW=10
  E: MODALIAS=input:b0000v0000p0000e0000-e0,5,kramlsfw4,
  E: SUBSYSTEM=input
  E: ID_INPUT=1
  E: ID_INPUT_SNDJACK=1
  E: ID_PATH=pci-0000:00:1b.0
  E: ID_PATH_TAG=pci-0000_00_1b_0
  
  P: /devices/pci0000:00/0000:00:1b.0/sound/card0/input13/event12
  N: input/event12
  S: input/by-path/pci-0000:00:1b.0-event-sndjack
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1b.0/sound/card0/input13/event12
  E: MAJOR=13
  E: MINOR=76
  E: DEVNAME=/dev/input/event12
  E: SUBSYSTEM=input
  E: ID_INPUT=1
  E: ID_INPUT_SNDJACK=1
  E: ID_SERIAL=noserial
  E: ID_PATH=pci-0000:00:1b.0
  E: ID_PATH_TAG=pci-0000_00_1b_0
  E: DEVLINKS=/dev/input/by-path/pci-0000:00:1b.0-event-sndjack
  
  P: /devices/pci0000:00/0000:00:1b.0/sound/card0/input14
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1b.0/sound/card0/input14
  E: PRODUCT=0/0/0/0
  E: NAME="HDA Intel Mic at Ext Right Jack"
  E: PHYS="ALSA"
  E: PROP=0
  E: EV=21
  E: SW=10
  E: MODALIAS=input:b0000v0000p0000e0000-e0,5,kramlsfw4,
  E: SUBSYSTEM=input
  E: ID_INPUT=1
  E: ID_INPUT_SNDJACK=1
  E: ID_PATH=pci-0000:00:1b.0
  E: ID_PATH_TAG=pci-0000_00_1b_0
  
  P: /devices/pci0000:00/0000:00:1b.0/sound/card0/input14/event13
  N: input/event13
  S: input/by-path/pci-0000:00:1b.0-event-sndjack
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1b.0/sound/card0/input14/event13
  E: MAJOR=13
  E: MINOR=77
  E: DEVNAME=/dev/input/event13
  E: SUBSYSTEM=input
  E: ID_INPUT=1
  E: ID_INPUT_SNDJACK=1
  E: ID_SERIAL=noserial
  E: ID_PATH=pci-0000:00:1b.0
  E: ID_PATH_TAG=pci-0000_00_1b_0
  E: DEVLINKS=/dev/input/by-path/pci-0000:00:1b.0-event-sndjack
  
  P: /devices/pci0000:00/0000:00:1b.0/sound/card0/input15
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1b.0/sound/card0/input15
  E: PRODUCT=0/0/0/0
  E: NAME="HDA Intel Line Out at Sep Left Jack"
  E: PHYS="ALSA"
  E: PROP=0
  E: EV=21
  E: SW=40
  E: MODALIAS=input:b0000v0000p0000e0000-e0,5,kramlsfw6,
  E: SUBSYSTEM=input
  E: ID_INPUT=1
  E: ID_INPUT_SNDJACK=1
  E: ID_PATH=pci-0000:00:1b.0
  E: ID_PATH_TAG=pci-0000_00_1b_0
  
  P: /devices/pci0000:00/0000:00:1b.0/sound/card0/input15/event14
  N: input/event14
  S: input/by-path/pci-0000:00:1b.0-event-sndjack
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1b.0/sound/card0/input15/event14
  E: MAJOR=13
  E: MINOR=78
  E: DEVNAME=/dev/input/event14
  E: SUBSYSTEM=input
  E: ID_INPUT=1
  E: ID_INPUT_SNDJACK=1
  E: ID_SERIAL=noserial
  E: ID_PATH=pci-0000:00:1b.0
  E: ID_PATH_TAG=pci-0000_00_1b_0
  E: DEVLINKS=/dev/input/by-path/pci-0000:00:1b.0-event-sndjack
  
  P: /devices/pci0000:00/0000:00:1b.0/sound/card0/input16
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1b.0/sound/card0/input16
  E: PRODUCT=0/0/0/0
  E: NAME="HDA Intel HP Out at Ext Right Jack"
  E: PHYS="ALSA"
  E: PROP=0
  E: EV=21
  E: SW=4
  E: MODALIAS=input:b0000v0000p0000e0000-e0,5,kramlsfw2,
  E: SUBSYSTEM=input
  E: ID_INPUT=1
  E: ID_INPUT_SNDJACK=1
  E: ID_PATH=pci-0000:00:1b.0
  E: ID_PATH_TAG=pci-0000_00_1b_0
  
  P: /devices/pci0000:00/0000:00:1b.0/sound/card0/input16/event15
  N: input/event15
  S: input/by-path/pci-0000:00:1b.0-event-sndjack
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1b.0/sound/card0/input16/event15
  E: MAJOR=13
  E: MINOR=79
  E: DEVNAME=/dev/input/event15
  E: SUBSYSTEM=input
  E: ID_INPUT=1
  E: ID_INPUT_SNDJACK=1
  E: ID_SERIAL=noserial
  E: ID_PATH=pci-0000:00:1b.0
  E: ID_PATH_TAG=pci-0000_00_1b_0
  E: DEVLINKS=/dev/input/by-path/pci-0000:00:1b.0-event-sndjack
  
  P: /devices/pci0000:00/0000:00:1b.0/sound/card0/pcmC0D0c
  N: snd/pcmC0D0c
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1b.0/sound/card0/pcmC0D0c
  E: MAJOR=116
  E: MINOR=4
  E: DEVNAME=/dev/snd/pcmC0D0c
  E: SUBSYSTEM=sound
  E: TAGS=:udev-acl:
  
  P: /devices/pci0000:00/0000:00:1b.0/sound/card0/pcmC0D0p
  N: snd/pcmC0D0p
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1b.0/sound/card0/pcmC0D0p
  E: MAJOR=116
  E: MINOR=3
  E: DEVNAME=/dev/snd/pcmC0D0p
  E: SUBSYSTEM=sound
  E: TAGS=:udev-acl:
  
  P: /devices/pci0000:00/0000:00:1b.0/sound/card0/pcmC0D3p
  N: snd/pcmC0D3p
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1b.0/sound/card0/pcmC0D3p
  E: MAJOR=116
  E: MINOR=2
  E: DEVNAME=/dev/snd/pcmC0D3p
  E: SUBSYSTEM=sound
  E: TAGS=:udev-acl:
  
  P: /devices/pci0000:00/0000:00:1b.0/sound/card0/controlC0
  N: snd/controlC0
  S: snd/by-path/pci-0000:00:1b.0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1b.0/sound/card0/controlC0
  E: MAJOR=116
  E: MINOR=8
  E: DEVNAME=/dev/snd/controlC0
  E: SUBSYSTEM=sound
  E: ID_PATH=pci-0000:00:1b.0
  E: ID_PATH_TAG=pci-0000_00_1b_0
  E: DEVLINKS=/dev/snd/by-path/pci-0000:00:1b.0
  E: TAGS=:udev-acl:
  
  P: /devices/pci0000:00/0000:00:1c.0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1c.0
  E: DRIVER=pcieport
  E: PCI_CLASS=60400
  E: PCI_ID=8086:2940
  E: PCI_SUBSYS_ID=1028:024F
  E: PCI_SLOT_NAME=0000:00:1c.0
  E: MODALIAS=pci:v00008086d00002940sv00001028sd0000024Fbc06sc04i00
  E: SUBSYSTEM=pci
  
  P: /devices/pci0000:00/0000:00:1c.0/0000:00:1c.0:pcie08
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1c.0/0000:00:1c.0:pcie08
  E: SUBSYSTEM=pci_express
  
  P: /devices/pci0000:00/0000:00:1c.0/pci_bus/0000:0b
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1c.0/pci_bus/0000:0b
  E: SUBSYSTEM=pci_bus
  
  P: /devices/pci0000:00/0000:00:1c.1
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1c.1
  E: DRIVER=pcieport
  E: PCI_CLASS=60400
  E: PCI_ID=8086:2942
  E: PCI_SUBSYS_ID=1028:024F
  E: PCI_SLOT_NAME=0000:00:1c.1
  E: MODALIAS=pci:v00008086d00002942sv00001028sd0000024Fbc06sc04i00
  E: SUBSYSTEM=pci
  
  P: /devices/pci0000:00/0000:00:1c.1/0000:00:1c.1:pcie08
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1c.1/0000:00:1c.1:pcie08
  E: SUBSYSTEM=pci_express
  
  P: /devices/pci0000:00/0000:00:1c.1/0000:0c:00.0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1c.1/0000:0c:00.0
  E: DRIVER=wl
  E: PCI_CLASS=28000
  E: PCI_ID=14E4:432B
  E: PCI_SUBSYS_ID=1028:000D
  E: PCI_SLOT_NAME=0000:0c:00.0
  E: MODALIAS=pci:v000014E4d0000432Bsv00001028sd0000000Dbc02sc80i00
  E: SUBSYSTEM=pci
  
  P: /devices/pci0000:00/0000:00:1c.1/0000:0c:00.0/net/eth2
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1c.1/0000:0c:00.0/net/eth2
  E: INTERFACE=eth2
  E: IFINDEX=3
  E: SUBSYSTEM=net
  E: ID_VENDOR_FROM_DATABASE=Broadcom Corporation
  E: ID_MODEL_FROM_DATABASE=BCM4322 802.11a/b/g/n Wireless LAN Controller
  E: ID_BUS=pci
  E: ID_VENDOR_ID=0x14e4
  E: ID_MODEL_ID=0x432b
  E: ID_MM_CANDIDATE=1
  
  P: /devices/pci0000:00/0000:00:1c.1/0000:0c:00.0/net/eth2/rfkill2
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1c.1/0000:0c:00.0/net/eth2/rfkill2
  E: RFKILL_NAME=brcmwl-0
  E: RFKILL_TYPE=wlan
  E: RFKILL_STATE=1
  E: SUBSYSTEM=rfkill
  
  P: /devices/pci0000:00/0000:00:1c.1/pci_bus/0000:0c
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1c.1/pci_bus/0000:0c
  E: SUBSYSTEM=pci_bus
  
  P: /devices/pci0000:00/0000:00:1c.2
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1c.2
  E: DRIVER=pcieport
  E: PCI_CLASS=60400
  E: PCI_ID=8086:2944
  E: PCI_SUBSYS_ID=1028:024F
  E: PCI_SLOT_NAME=0000:00:1c.2
  E: MODALIAS=pci:v00008086d00002944sv00001028sd0000024Fbc06sc04i00
  E: SUBSYSTEM=pci
  
  P: /devices/pci0000:00/0000:00:1c.2/0000:00:1c.2:pcie08
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1c.2/0000:00:1c.2:pcie08
  E: SUBSYSTEM=pci_express
  
  P: /devices/pci0000:00/0000:00:1c.2/pci_bus/0000:0d
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1c.2/pci_bus/0000:0d
  E: SUBSYSTEM=pci_bus
  
  P: /devices/pci0000:00/0000:00:1c.3
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1c.3
  E: DRIVER=pcieport
  E: PCI_CLASS=60400
  E: PCI_ID=8086:2946
  E: PCI_SUBSYS_ID=1028:024F
  E: PCI_SLOT_NAME=0000:00:1c.3
  E: MODALIAS=pci:v00008086d00002946sv00001028sd0000024Fbc06sc04i00
  E: SUBSYSTEM=pci
  
  P: /devices/pci0000:00/0000:00:1c.3/0000:00:1c.3:pcie08
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1c.3/0000:00:1c.3:pcie08
  E: SUBSYSTEM=pci_express
  
  P: /devices/pci0000:00/0000:00:1c.3/pci_bus/0000:0e
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1c.3/pci_bus/0000:0e
  E: SUBSYSTEM=pci_bus
  
  P: /devices/pci0000:00/0000:00:1d.0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1d.0
  E: DRIVER=uhci_hcd
  E: PCI_CLASS=C0300
  E: PCI_ID=8086:2934
  E: PCI_SUBSYS_ID=1028:024F
  E: PCI_SLOT_NAME=0000:00:1d.0
  E: MODALIAS=pci:v00008086d00002934sv00001028sd0000024Fbc0Csc03i00
  E: SUBSYSTEM=pci
  
  P: /devices/pci0000:00/0000:00:1d.0/usb6
  N: bus/usb/006/001
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1d.0/usb6
  E: MAJOR=189
  E: MINOR=640
  E: DEVNAME=/dev/bus/usb/006/001
  E: DEVTYPE=usb_device
  E: DRIVER=usb
  E: PRODUCT=1d6b/1/300
  E: TYPE=9/0/0
  E: BUSNUM=006
  E: DEVNUM=001
  E: SUBSYSTEM=usb
  E: ID_VENDOR=Linux_3.0.0-14-generic_uhci_hcd
  E: ID_VENDOR_ENC=Linux\x203.0.0-14-generic\x20uhci_hcd
  E: ID_VENDOR_ID=1d6b
  E: ID_MODEL=UHCI_Host_Controller
  E: ID_MODEL_ENC=UHCI\x20Host\x20Controller
  E: ID_MODEL_ID=0001
  E: ID_REVISION=0300
  E: ID_SERIAL=Linux_3.0.0-14-generic_uhci_hcd_UHCI_Host_Controller_0000:00:1d.0
  E: ID_SERIAL_SHORT=0000:00:1d.0
  E: ID_BUS=usb
  E: ID_USB_INTERFACES=:090000:
  
  P: /devices/pci0000:00/0000:00:1d.0/usb6/6-0:1.0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1d.0/usb6/6-0:1.0
  E: DEVTYPE=usb_interface
  E: DRIVER=hub
  E: PRODUCT=1d6b/1/300
  E: TYPE=9/0/0
  E: INTERFACE=9/0/0
  E: MODALIAS=usb:v1D6Bp0001d0300dc09dsc00dp00ic09isc00ip00
  E: SUBSYSTEM=usb
  
  P: /devices/pci0000:00/0000:00:1d.0/usb6/6-2
  N: bus/usb/006/002
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1d.0/usb6/6-2
  E: MAJOR=189
  E: MINOR=641
  E: DEVNAME=/dev/bus/usb/006/002
  E: DEVTYPE=usb_device
  E: DRIVER=usb
  E: PRODUCT=baf/ec/1
  E: TYPE=255/255/255
  E: BUSNUM=006
  E: DEVNUM=002
  E: SUBSYSTEM=usb
  E: ID_VENDOR=U.S._Robotics
  E: ID_VENDOR_ENC=U.S.\x20Robotics
  E: ID_VENDOR_ID=0baf
  E: ID_MODEL=U.S._Robotics_56K_Faxmodem_USB
  E: ID_MODEL_ENC=U.S.\x20Robotics\x2056K\x20Faxmodem\x20USB
  E: ID_MODEL_ID=00ec
  E: ID_REVISION=0001
  E: ID_SERIAL=U.S._Robotics_U.S._Robotics_56K_Faxmodem_USB_USBHCF00000006
  E: ID_SERIAL_SHORT=USBHCF00000006
  E: ID_BUS=usb
  E: ID_USB_INTERFACES=:ffffff:
  
  P: /devices/pci0000:00/0000:00:1d.0/usb6/6-2/6-2:1.0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1d.0/usb6/6-2/6-2:1.0
  E: DEVTYPE=usb_interface
  E: PRODUCT=baf/ec/1
  E: TYPE=255/255/255
  E: INTERFACE=255/255/255
  E: MODALIAS=usb:v0BAFp00ECd0001dcFFdscFFdpFFicFFiscFFipFF
  E: SUBSYSTEM=usb
  
  P: /devices/pci0000:00/0000:00:1d.0/usbmon/usbmon6
  N: usbmon6
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1d.0/usbmon/usbmon6
  E: MAJOR=252
  E: MINOR=6
  E: DEVNAME=/dev/usbmon6
  E: SUBSYSTEM=usbmon
  
  P: /devices/pci0000:00/0000:00:1d.1
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1d.1
  E: DRIVER=uhci_hcd
  E: PCI_CLASS=C0300
  E: PCI_ID=8086:2935
  E: PCI_SUBSYS_ID=1028:024F
  E: PCI_SLOT_NAME=0000:00:1d.1
  E: MODALIAS=pci:v00008086d00002935sv00001028sd0000024Fbc0Csc03i00
  E: SUBSYSTEM=pci
  
  P: /devices/pci0000:00/0000:00:1d.1/usb7
  N: bus/usb/007/001
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1d.1/usb7
  E: MAJOR=189
  E: MINOR=768
  E: DEVNAME=/dev/bus/usb/007/001
  E: DEVTYPE=usb_device
  E: DRIVER=usb
  E: PRODUCT=1d6b/1/300
  E: TYPE=9/0/0
  E: BUSNUM=007
  E: DEVNUM=001
  E: SUBSYSTEM=usb
  E: ID_VENDOR=Linux_3.0.0-14-generic_uhci_hcd
  E: ID_VENDOR_ENC=Linux\x203.0.0-14-generic\x20uhci_hcd
  E: ID_VENDOR_ID=1d6b
  E: ID_MODEL=UHCI_Host_Controller
  E: ID_MODEL_ENC=UHCI\x20Host\x20Controller
  E: ID_MODEL_ID=0001
  E: ID_REVISION=0300
  E: ID_SERIAL=Linux_3.0.0-14-generic_uhci_hcd_UHCI_Host_Controller_0000:00:1d.1
  E: ID_SERIAL_SHORT=0000:00:1d.1
  E: ID_BUS=usb
  E: ID_USB_INTERFACES=:090000:
  
  P: /devices/pci0000:00/0000:00:1d.1/usb7/7-0:1.0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1d.1/usb7/7-0:1.0
  E: DEVTYPE=usb_interface
  E: DRIVER=hub
  E: PRODUCT=1d6b/1/300
  E: TYPE=9/0/0
  E: INTERFACE=9/0/0
  E: MODALIAS=usb:v1D6Bp0001d0300dc09dsc00dp00ic09isc00ip00
  E: SUBSYSTEM=usb
  
  P: /devices/pci0000:00/0000:00:1d.1/usbmon/usbmon7
  N: usbmon7
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1d.1/usbmon/usbmon7
  E: MAJOR=252
  E: MINOR=7
  E: DEVNAME=/dev/usbmon7
  E: SUBSYSTEM=usbmon
  
  P: /devices/pci0000:00/0000:00:1d.2
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1d.2
  E: DRIVER=uhci_hcd
  E: PCI_CLASS=C0300
  E: PCI_ID=8086:2936
  E: PCI_SUBSYS_ID=1028:024F
  E: PCI_SLOT_NAME=0000:00:1d.2
  E: MODALIAS=pci:v00008086d00002936sv00001028sd0000024Fbc0Csc03i00
  E: SUBSYSTEM=pci
  
  P: /devices/pci0000:00/0000:00:1d.2/usb8
  N: bus/usb/008/001
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1d.2/usb8
  E: MAJOR=189
  E: MINOR=896
  E: DEVNAME=/dev/bus/usb/008/001
  E: DEVTYPE=usb_device
  E: DRIVER=usb
  E: PRODUCT=1d6b/1/300
  E: TYPE=9/0/0
  E: BUSNUM=008
  E: DEVNUM=001
  E: SUBSYSTEM=usb
  E: ID_VENDOR=Linux_3.0.0-14-generic_uhci_hcd
  E: ID_VENDOR_ENC=Linux\x203.0.0-14-generic\x20uhci_hcd
  E: ID_VENDOR_ID=1d6b
  E: ID_MODEL=UHCI_Host_Controller
  E: ID_MODEL_ENC=UHCI\x20Host\x20Controller
  E: ID_MODEL_ID=0001
  E: ID_REVISION=0300
  E: ID_SERIAL=Linux_3.0.0-14-generic_uhci_hcd_UHCI_Host_Controller_0000:00:1d.2
  E: ID_SERIAL_SHORT=0000:00:1d.2
  E: ID_BUS=usb
  E: ID_USB_INTERFACES=:090000:
  
  P: /devices/pci0000:00/0000:00:1d.2/usb8/8-0:1.0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1d.2/usb8/8-0:1.0
  E: DEVTYPE=usb_interface
  E: DRIVER=hub
  E: PRODUCT=1d6b/1/300
  E: TYPE=9/0/0
  E: INTERFACE=9/0/0
  E: MODALIAS=usb:v1D6Bp0001d0300dc09dsc00dp00ic09isc00ip00
  E: SUBSYSTEM=usb
  
  P: /devices/pci0000:00/0000:00:1d.2/usbmon/usbmon8
  N: usbmon8
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1d.2/usbmon/usbmon8
  E: MAJOR=252
  E: MINOR=8
  E: DEVNAME=/dev/usbmon8
  E: SUBSYSTEM=usbmon
  
  P: /devices/pci0000:00/0000:00:1d.7
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1d.7
  E: DRIVER=ehci_hcd
  E: PCI_CLASS=C0320
  E: PCI_ID=8086:293A
  E: PCI_SUBSYS_ID=1028:024F
  E: PCI_SLOT_NAME=0000:00:1d.7
  E: MODALIAS=pci:v00008086d0000293Asv00001028sd0000024Fbc0Csc03i20
  E: SUBSYSTEM=pci
  
  P: /devices/pci0000:00/0000:00:1d.7/usb2
  N: bus/usb/002/001
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1d.7/usb2
  E: MAJOR=189
  E: MINOR=128
  E: DEVNAME=/dev/bus/usb/002/001
  E: DEVTYPE=usb_device
  E: DRIVER=usb
  E: PRODUCT=1d6b/2/300
  E: TYPE=9/0/0
  E: BUSNUM=002
  E: DEVNUM=001
  E: SUBSYSTEM=usb
  E: ID_VENDOR=Linux_3.0.0-14-generic_ehci_hcd
  E: ID_VENDOR_ENC=Linux\x203.0.0-14-generic\x20ehci_hcd
  E: ID_VENDOR_ID=1d6b
  E: ID_MODEL=EHCI_Host_Controller
  E: ID_MODEL_ENC=EHCI\x20Host\x20Controller
  E: ID_MODEL_ID=0002
  E: ID_REVISION=0300
  E: ID_SERIAL=Linux_3.0.0-14-generic_ehci_hcd_EHCI_Host_Controller_0000:00:1d.7
  E: ID_SERIAL_SHORT=0000:00:1d.7
  E: ID_BUS=usb
  E: ID_USB_INTERFACES=:090000:
  
  P: /devices/pci0000:00/0000:00:1d.7/usb2/2-0:1.0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1d.7/usb2/2-0:1.0
  E: DEVTYPE=usb_interface
  E: DRIVER=hub
  E: PRODUCT=1d6b/2/300
  E: TYPE=9/0/0
  E: INTERFACE=9/0/0
  E: MODALIAS=usb:v1D6Bp0002d0300dc09dsc00dp00ic09isc00ip00
  E: SUBSYSTEM=usb
  
  P: /devices/pci0000:00/0000:00:1d.7/usbmon/usbmon2
  N: usbmon2
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1d.7/usbmon/usbmon2
  E: MAJOR=252
  E: MINOR=2
  E: DEVNAME=/dev/usbmon2
  E: SUBSYSTEM=usbmon
  
  P: /devices/pci0000:00/0000:00:1e.0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1e.0
  E: PCI_CLASS=60401
  E: PCI_ID=8086:2448
  E: PCI_SUBSYS_ID=1028:024F
  E: PCI_SLOT_NAME=0000:00:1e.0
  E: MODALIAS=pci:v00008086d00002448sv00001028sd0000024Fbc06sc04i01
  E: SUBSYSTEM=pci
  
  P: /devices/pci0000:00/0000:00:1e.0/0000:03:01.0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1e.0/0000:03:01.0
  E: DRIVER=yenta_cardbus
  E: PCI_CLASS=60700
  E: PCI_ID=1180:0476
  E: PCI_SUBSYS_ID=1028:024F
  E: PCI_SLOT_NAME=0000:03:01.0
  E: MODALIAS=pci:v00001180d00000476sv00001028sd0000024Fbc06sc07i00
  E: SUBSYSTEM=pci
  
  P: /devices/pci0000:00/0000:00:1e.0/0000:03:01.0/pci_bus/0000:04
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1e.0/0000:03:01.0/pci_bus/0000:04
  E: SUBSYSTEM=pci_bus
  
  P: /devices/pci0000:00/0000:00:1e.0/0000:03:01.0/pcmcia_socket/pcmcia_socket0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1e.0/0000:03:01.0/pcmcia_socket/pcmcia_socket0
  E: SOCKET_NO=0
  E: SUBSYSTEM=pcmcia_socket
  
  P: /devices/pci0000:00/0000:00:1e.0/0000:03:01.1
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1e.0/0000:03:01.1
  E: DRIVER=firewire_ohci
  E: PCI_CLASS=C0010
  E: PCI_ID=1180:0832
  E: PCI_SUBSYS_ID=1028:024F
  E: PCI_SLOT_NAME=0000:03:01.1
  E: MODALIAS=pci:v00001180d00000832sv00001028sd0000024Fbc0Csc00i10
  E: SUBSYSTEM=pci
  
  P: /devices/pci0000:00/0000:00:1e.0/0000:03:01.1/fw0
  N: fw0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1e.0/0000:03:01.1/fw0
  E: MAJOR=251
  E: MINOR=0
  E: DEVNAME=/dev/fw0
  E: SUBSYSTEM=firewire
  
  P: /devices/pci0000:00/0000:00:1e.0/0000:03:01.2
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1e.0/0000:03:01.2
  E: DRIVER=sdhci-pci
  E: PCI_CLASS=80501
  E: PCI_ID=1180:0822
  E: PCI_SUBSYS_ID=1028:024F
  E: PCI_SLOT_NAME=0000:03:01.2
  E: MODALIAS=pci:v00001180d00000822sv00001028sd0000024Fbc08sc05i01
  E: SUBSYSTEM=pci
  
  P: /devices/pci0000:00/0000:00:1e.0/0000:03:01.2/leds/mmc0::
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1e.0/0000:03:01.2/leds/mmc0::
  E: SUBSYSTEM=leds
  
  P: /devices/pci0000:00/0000:00:1e.0/0000:03:01.2/mmc_host/mmc0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1e.0/0000:03:01.2/mmc_host/mmc0
  E: SUBSYSTEM=mmc_host
  
  P: /devices/pci0000:00/0000:00:1e.0/0000:03:01.2/mmc_host/mmc0/mmc0:0007
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1e.0/0000:03:01.2/mmc_host/mmc0/mmc0:0007
  E: DRIVER=mmcblk
  E: MMC_TYPE=SD
  E: MMC_NAME=SD04G
  E: MODALIAS=mmc:block
  E: SUBSYSTEM=mmc
  
  P: /devices/pci0000:00/0000:00:1e.0/0000:03:01.2/mmc_host/mmc0/mmc0:0007/block/mmcblk0
  N: mmcblk0
  S: disk/by-id/mmc-SD04G_0xb000631b
  S: disk/by-path/pci-0000:03:01.2
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1e.0/0000:03:01.2/mmc_host/mmc0/mmc0:0007/block/mmcblk0
  E: MAJOR=179
  E: MINOR=0
  E: DEVNAME=/dev/mmcblk0
  E: DEVTYPE=disk
  E: SUBSYSTEM=block
  E: ID_NAME=SD04G
  E: ID_SERIAL=0xb000631b
  E: ID_PATH=pci-0000:03:01.2
  E: ID_PATH_TAG=pci-0000_03_01_2
  E: ID_PART_TABLE_TYPE=dos
  E: UDISKS_PRESENTATION_NOPOLICY=0
  E: UDISKS_PARTITION_TABLE=1
  E: UDISKS_PARTITION_TABLE_SCHEME=mbr
  E: UDISKS_PARTITION_TABLE_COUNT=1
  E: DEVLINKS=/dev/disk/by-id/mmc-SD04G_0xb000631b /dev/disk/by-path/pci-0000:03:01.2
  
  P: /devices/pci0000:00/0000:00:1e.0/0000:03:01.2/mmc_host/mmc0/mmc0:0007/block/mmcblk0/mmcblk0p1
  N: mmcblk0p1
  S: disk/by-id/mmc-SD04G_0xb000631b-part1
  S: disk/by-path/pci-0000:03:01.2-part1
  S: disk/by-uuid/3B2B-5097
  S: disk/by-label/DATA
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1e.0/0000:03:01.2/mmc_host/mmc0/mmc0:0007/block/mmcblk0/mmcblk0p1
  E: MAJOR=179
  E: MINOR=1
  E: DEVNAME=/dev/mmcblk0p1
  E: DEVTYPE=partition
  E: SUBSYSTEM=block
  E: ID_NAME=SD04G
  E: ID_SERIAL=0xb000631b
  E: ID_PATH=pci-0000:03:01.2
  E: ID_PATH_TAG=pci-0000_03_01_2
  E: ID_PART_TABLE_TYPE=dos
  E: ID_FS_LABEL=DATA
  E: ID_FS_LABEL_ENC=DATA
  E: ID_FS_UUID=3B2B-5097
  E: ID_FS_UUID_ENC=3B2B-5097
  E: ID_FS_VERSION=FAT32
  E: ID_FS_TYPE=vfat
  E: ID_FS_USAGE=filesystem
  E: ID_PART_ENTRY_SCHEME=dos
  E: ID_PART_ENTRY_TYPE=0xb
  E: ID_PART_ENTRY_NUMBER=1
  E: UDISKS_PRESENTATION_NOPOLICY=0
  E: UDISKS_PARTITION=1
  E: UDISKS_PARTITION_SCHEME=mbr
  E: UDISKS_PARTITION_NUMBER=1
  E: UDISKS_PARTITION_TYPE=0x0b
  E: UDISKS_PARTITION_SIZE=4085252096
  E: UDISKS_PARTITION_SLAVE=/sys/devices/pci0000:00/0000:00:1e.0/0000:03:01.2/mmc_host/mmc0/mmc0:0007/block/mmcblk0
  E: UDISKS_PARTITION_OFFSET=4194304
  E: UDISKS_PARTITION_ALIGNMENT_OFFSET=0
  E: DEVLINKS=/dev/disk/by-id/mmc-SD04G_0xb000631b-part1 /dev/disk/by-path/pci-0000:03:01.2-part1 /dev/disk/by-uuid/3B2B-5097 /dev/disk/by-label/DATA
  
  P: /devices/pci0000:00/0000:00:1e.0/pci_bus/0000:03
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1e.0/pci_bus/0000:03
  E: SUBSYSTEM=pci_bus
  
  P: /devices/pci0000:00/0000:00:1f.0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1f.0
  E: PCI_CLASS=60100
  E: PCI_ID=8086:2917
  E: PCI_SUBSYS_ID=1028:024F
  E: PCI_SLOT_NAME=0000:00:1f.0
  E: MODALIAS=pci:v00008086d00002917sv00001028sd0000024Fbc06sc01i00
  E: SUBSYSTEM=pci
  
  P: /devices/pci0000:00/0000:00:1f.2
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1f.2
  E: DRIVER=ahci
  E: PCI_CLASS=10400
  E: PCI_ID=8086:282A
  E: PCI_SUBSYS_ID=1028:024F
  E: PCI_SLOT_NAME=0000:00:1f.2
  E: MODALIAS=pci:v00008086d0000282Asv00001028sd0000024Fbc01sc04i00
  E: SUBSYSTEM=pci
  E: ID_VENDOR_FROM_DATABASE=Intel Corporation
  E: ID_MODEL_FROM_DATABASE=Mobile 82801 SATA RAID Controller
  
  P: /devices/pci0000:00/0000:00:1f.2/ata1/ata_port/ata1
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/ata1/ata_port/ata1
  E: SUBSYSTEM=ata_port
  
  P: /devices/pci0000:00/0000:00:1f.2/ata1/link1/ata_link/link1
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/ata1/link1/ata_link/link1
  E: SUBSYSTEM=ata_link
  
  P: /devices/pci0000:00/0000:00:1f.2/ata1/link1/dev1.0/ata_device/dev1.0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/ata1/link1/dev1.0/ata_device/dev1.0
  E: SUBSYSTEM=ata_device
  
  P: /devices/pci0000:00/0000:00:1f.2/ata2/ata_port/ata2
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/ata2/ata_port/ata2
  E: SUBSYSTEM=ata_port
  
  P: /devices/pci0000:00/0000:00:1f.2/ata2/link2/ata_link/link2
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/ata2/link2/ata_link/link2
  E: SUBSYSTEM=ata_link
  
  P: /devices/pci0000:00/0000:00:1f.2/ata2/link2/dev2.0/ata_device/dev2.0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/ata2/link2/dev2.0/ata_device/dev2.0
  E: SUBSYSTEM=ata_device
  
  P: /devices/pci0000:00/0000:00:1f.2/ata3/ata_port/ata3
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/ata3/ata_port/ata3
  E: SUBSYSTEM=ata_port
  
  P: /devices/pci0000:00/0000:00:1f.2/ata3/link3/ata_link/link3
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/ata3/link3/ata_link/link3
  E: SUBSYSTEM=ata_link
  
  P: /devices/pci0000:00/0000:00:1f.2/ata3/link3/dev3.0/ata_device/dev3.0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/ata3/link3/dev3.0/ata_device/dev3.0
  E: SUBSYSTEM=ata_device
  
  P: /devices/pci0000:00/0000:00:1f.2/ata4/ata_port/ata4
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/ata4/ata_port/ata4
  E: SUBSYSTEM=ata_port
  
  P: /devices/pci0000:00/0000:00:1f.2/ata4/link4/ata_link/link4
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/ata4/link4/ata_link/link4
  E: SUBSYSTEM=ata_link
  
  P: /devices/pci0000:00/0000:00:1f.2/ata4/link4/dev4.0/ata_device/dev4.0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/ata4/link4/dev4.0/ata_device/dev4.0
  E: SUBSYSTEM=ata_device
  
  P: /devices/pci0000:00/0000:00:1f.2/ata5/ata_port/ata5
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/ata5/ata_port/ata5
  E: SUBSYSTEM=ata_port
  
  P: /devices/pci0000:00/0000:00:1f.2/ata5/link5/ata_link/link5
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/ata5/link5/ata_link/link5
  E: SUBSYSTEM=ata_link
  
  P: /devices/pci0000:00/0000:00:1f.2/ata5/link5/dev5.0/ata_device/dev5.0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/ata5/link5/dev5.0/ata_device/dev5.0
  E: SUBSYSTEM=ata_device
  
  P: /devices/pci0000:00/0000:00:1f.2/ata6/ata_port/ata6
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/ata6/ata_port/ata6
  E: SUBSYSTEM=ata_port
  
  P: /devices/pci0000:00/0000:00:1f.2/ata6/link6/ata_link/link6
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/ata6/link6/ata_link/link6
  E: SUBSYSTEM=ata_link
  
  P: /devices/pci0000:00/0000:00:1f.2/ata6/link6/dev6.0/ata_device/dev6.0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/ata6/link6/dev6.0/ata_device/dev6.0
  E: SUBSYSTEM=ata_device
  
  P: /devices/pci0000:00/0000:00:1f.2/host0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/host0
  E: DEVTYPE=scsi_host
  E: SUBSYSTEM=scsi
  
  P: /devices/pci0000:00/0000:00:1f.2/host0/scsi_host/host0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/host0/scsi_host/host0
  E: SUBSYSTEM=scsi_host
  
  P: /devices/pci0000:00/0000:00:1f.2/host0/target0:0:0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/host0/target0:0:0
  E: DEVTYPE=scsi_target
  E: SUBSYSTEM=scsi
  
  P: /devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0
  E: DEVTYPE=scsi_device
  E: DRIVER=sd
  E: MODALIAS=scsi:t-0x00
  E: SUBSYSTEM=scsi
  
  P: /devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0/block/sda
  N: sda
  S: disk/by-id/ata-ST9250410ASG_5VG5AW0Z
  S: disk/by-id/scsi-SATA_ST9250410ASG_5VG5AW0Z
  S: disk/by-path/pci-0000:00:1f.2-scsi-0:0:0:0
  S: disk/by-id/wwn-0x5000c500251025f4
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0/block/sda
  E: MAJOR=8
  E: MINOR=0
  E: DEVNAME=/dev/sda
  E: DEVTYPE=disk
  E: SUBSYSTEM=block
  E: ID_ATA=1
  E: ID_TYPE=disk
  E: ID_BUS=ata
  E: ID_MODEL=ST9250410ASG
  E: ID_MODEL_ENC=ST9250410ASG\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20
  E: ID_REVISION=0002SD1M
  E: ID_SERIAL=ST9250410ASG_5VG5AW0Z
  E: ID_SERIAL_SHORT=5VG5AW0Z
  E: ID_ATA_WRITE_CACHE=1
  E: ID_ATA_WRITE_CACHE_ENABLED=1
  E: ID_ATA_FEATURE_SET_HPA=1
  E: ID_ATA_FEATURE_SET_HPA_ENABLED=1
  E: ID_ATA_FEATURE_SET_PM=1
  E: ID_ATA_FEATURE_SET_PM_ENABLED=1
  E: ID_ATA_FEATURE_SET_SECURITY=1
  E: ID_ATA_FEATURE_SET_SECURITY_ENABLED=0
  E: ID_ATA_FEATURE_SET_SECURITY_ERASE_UNIT_MIN=54
  E: ID_ATA_FEATURE_SET_SECURITY_ENHANCED_ERASE_UNIT_MIN=54
  E: ID_ATA_FEATURE_SET_SECURITY_FROZEN=1
  E: ID_ATA_FEATURE_SET_SMART=1
  E: ID_ATA_FEATURE_SET_SMART_ENABLED=1
  E: ID_ATA_FEATURE_SET_AAM=1
  E: ID_ATA_FEATURE_SET_AAM_ENABLED=1
  E: ID_ATA_FEATURE_SET_AAM_VENDOR_RECOMMENDED_VALUE=208
  E: ID_ATA_FEATURE_SET_AAM_CURRENT_VALUE=208
  E: ID_ATA_FEATURE_SET_APM=1
  E: ID_ATA_FEATURE_SET_APM_ENABLED=1
  E: ID_ATA_FEATURE_SET_APM_CURRENT_VALUE=254
  E: ID_ATA_DOWNLOAD_MICROCODE=1
  E: ID_ATA_SATA=1
  E: ID_ATA_SATA_SIGNAL_RATE_GEN2=1
  E: ID_ATA_SATA_SIGNAL_RATE_GEN1=1
  E: ID_ATA_ROTATION_RATE_RPM=7200
  E: ID_WWN=0x5000c500251025f4
  E: ID_WWN_WITH_EXTENSION=0x5000c500251025f4
  E: ID_SCSI_COMPAT=SATA_ST9250410ASG_5VG5AW0Z
  E: ID_PATH=pci-0000:00:1f.2-scsi-0:0:0:0
  E: ID_PATH_TAG=pci-0000_00_1f_2-scsi-0_0_0_0
  E: ID_PART_TABLE_TYPE=dos
  E: UDISKS_PRESENTATION_NOPOLICY=0
  E: UDISKS_PARTITION_TABLE=1
  E: UDISKS_PARTITION_TABLE_SCHEME=mbr
  E: UDISKS_PARTITION_TABLE_COUNT=5
  E: UDISKS_ATA_SMART_IS_AVAILABLE=1
  E: DEVLINKS=/dev/disk/by-id/ata-ST9250410ASG_5VG5AW0Z /dev/disk/by-id/scsi-SATA_ST9250410ASG_5VG5AW0Z /dev/disk/by-path/pci-0000:00:1f.2-scsi-0:0:0:0 /dev/disk/by-id/wwn-0x5000c500251025f4
  
  P: /devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0/block/sda/sda1
  N: sda1
  S: disk/by-id/ata-ST9250410ASG_5VG5AW0Z-part1
  S: disk/by-id/scsi-SATA_ST9250410ASG_5VG5AW0Z-part1
  S: disk/by-path/pci-0000:00:1f.2-scsi-0:0:0:0-part1
  S: disk/by-uuid/A8EE7F75EE7F3B20
  S: disk/by-label/System\x20Reserved
  S: disk/by-id/wwn-0x5000c500251025f4-part1
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0/block/sda/sda1
  E: MAJOR=8
  E: MINOR=1
  E: DEVNAME=/dev/sda1
  E: DEVTYPE=partition
  E: SUBSYSTEM=block
  E: ID_ATA=1
  E: ID_TYPE=disk
  E: ID_BUS=ata
  E: ID_MODEL=ST9250410ASG
  E: ID_MODEL_ENC=ST9250410ASG\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20
  E: ID_REVISION=0002SD1M
  E: ID_SERIAL=ST9250410ASG_5VG5AW0Z
  E: ID_SERIAL_SHORT=5VG5AW0Z
  E: ID_ATA_WRITE_CACHE=1
  E: ID_ATA_WRITE_CACHE_ENABLED=1
  E: ID_ATA_FEATURE_SET_HPA=1
  E: ID_ATA_FEATURE_SET_HPA_ENABLED=1
  E: ID_ATA_FEATURE_SET_PM=1
  E: ID_ATA_FEATURE_SET_PM_ENABLED=1
  E: ID_ATA_FEATURE_SET_SECURITY=1
  E: ID_ATA_FEATURE_SET_SECURITY_ENABLED=0
  E: ID_ATA_FEATURE_SET_SECURITY_ERASE_UNIT_MIN=54
  E: ID_ATA_FEATURE_SET_SECURITY_ENHANCED_ERASE_UNIT_MIN=54
  E: ID_ATA_FEATURE_SET_SECURITY_FROZEN=1
  E: ID_ATA_FEATURE_SET_SMART=1
  E: ID_ATA_FEATURE_SET_SMART_ENABLED=1
  E: ID_ATA_FEATURE_SET_AAM=1
  E: ID_ATA_FEATURE_SET_AAM_ENABLED=1
  E: ID_ATA_FEATURE_SET_AAM_VENDOR_RECOMMENDED_VALUE=208
  E: ID_ATA_FEATURE_SET_AAM_CURRENT_VALUE=208
  E: ID_ATA_FEATURE_SET_APM=1
  E: ID_ATA_FEATURE_SET_APM_ENABLED=1
  E: ID_ATA_FEATURE_SET_APM_CURRENT_VALUE=254
  E: ID_ATA_DOWNLOAD_MICROCODE=1
  E: ID_ATA_SATA=1
  E: ID_ATA_SATA_SIGNAL_RATE_GEN2=1
  E: ID_ATA_SATA_SIGNAL_RATE_GEN1=1
  E: ID_ATA_ROTATION_RATE_RPM=7200
  E: ID_WWN=0x5000c500251025f4
  E: ID_WWN_WITH_EXTENSION=0x5000c500251025f4
  E: ID_SCSI_COMPAT=SATA_ST9250410ASG_5VG5AW0Z
  E: ID_PATH=pci-0000:00:1f.2-scsi-0:0:0:0
  E: ID_PATH_TAG=pci-0000_00_1f_2-scsi-0_0_0_0
  E: ID_PART_TABLE_TYPE=dos
  E: ID_FS_LABEL=System_Reserved
  E: ID_FS_LABEL_ENC=System\x20Reserved
  E: ID_FS_UUID=A8EE7F75EE7F3B20
  E: ID_FS_UUID_ENC=A8EE7F75EE7F3B20
  E: ID_FS_TYPE=ntfs
  E: ID_FS_USAGE=filesystem
  E: ID_PART_ENTRY_SCHEME=dos
  E: ID_PART_ENTRY_TYPE=0x7
  E: ID_PART_ENTRY_FLAGS=0x80
  E: ID_PART_ENTRY_NUMBER=1
  E: UDISKS_PRESENTATION_NOPOLICY=0
  E: UDISKS_PARTITION=1
  E: UDISKS_PARTITION_SCHEME=mbr
  E: UDISKS_PARTITION_NUMBER=1
  E: UDISKS_PARTITION_TYPE=0x07
  E: UDISKS_PARTITION_SIZE=104857600
  E: UDISKS_PARTITION_FLAGS=boot
  E: UDISKS_PARTITION_SLAVE=/sys/devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0/block/sda
  E: UDISKS_PARTITION_OFFSET=1048576
  E: UDISKS_PARTITION_ALIGNMENT_OFFSET=0
  E: DEVLINKS=/dev/disk/by-id/ata-ST9250410ASG_5VG5AW0Z-part1 /dev/disk/by-id/scsi-SATA_ST9250410ASG_5VG5AW0Z-part1 /dev/disk/by-path/pci-0000:00:1f.2-scsi-0:0:0:0-part1 /dev/disk/by-uuid/A8EE7F75EE7F3B20 /dev/disk/by-label/System\x20Reserved /dev/disk/by-id/wwn-0x5000c500251025f4-part1
  
  P: /devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0/block/sda/sda2
  N: sda2
  S: disk/by-id/ata-ST9250410ASG_5VG5AW0Z-part2
  S: disk/by-id/scsi-SATA_ST9250410ASG_5VG5AW0Z-part2
  S: disk/by-path/pci-0000:00:1f.2-scsi-0:0:0:0-part2
  S: disk/by-uuid/2bdc1a9a-8cf1-4e51-8e7a-0717443ce6c8
  S: disk/by-id/wwn-0x5000c500251025f4-part2
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0/block/sda/sda2
  E: MAJOR=8
  E: MINOR=2
  E: DEVNAME=/dev/sda2
  E: DEVTYPE=partition
  E: SUBSYSTEM=block
  E: ID_ATA=1
  E: ID_TYPE=disk
  E: ID_BUS=ata
  E: ID_MODEL=ST9250410ASG
  E: ID_MODEL_ENC=ST9250410ASG\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20
  E: ID_REVISION=0002SD1M
  E: ID_SERIAL=ST9250410ASG_5VG5AW0Z
  E: ID_SERIAL_SHORT=5VG5AW0Z
  E: ID_ATA_WRITE_CACHE=1
  E: ID_ATA_WRITE_CACHE_ENABLED=1
  E: ID_ATA_FEATURE_SET_HPA=1
  E: ID_ATA_FEATURE_SET_HPA_ENABLED=1
  E: ID_ATA_FEATURE_SET_PM=1
  E: ID_ATA_FEATURE_SET_PM_ENABLED=1
  E: ID_ATA_FEATURE_SET_SECURITY=1
  E: ID_ATA_FEATURE_SET_SECURITY_ENABLED=0
  E: ID_ATA_FEATURE_SET_SECURITY_ERASE_UNIT_MIN=54
  E: ID_ATA_FEATURE_SET_SECURITY_ENHANCED_ERASE_UNIT_MIN=54
  E: ID_ATA_FEATURE_SET_SECURITY_FROZEN=1
  E: ID_ATA_FEATURE_SET_SMART=1
  E: ID_ATA_FEATURE_SET_SMART_ENABLED=1
  E: ID_ATA_FEATURE_SET_AAM=1
  E: ID_ATA_FEATURE_SET_AAM_ENABLED=1
  E: ID_ATA_FEATURE_SET_AAM_VENDOR_RECOMMENDED_VALUE=208
  E: ID_ATA_FEATURE_SET_AAM_CURRENT_VALUE=208
  E: ID_ATA_FEATURE_SET_APM=1
  E: ID_ATA_FEATURE_SET_APM_ENABLED=1
  E: ID_ATA_FEATURE_SET_APM_CURRENT_VALUE=254
  E: ID_ATA_DOWNLOAD_MICROCODE=1
  E: ID_ATA_SATA=1
  E: ID_ATA_SATA_SIGNAL_RATE_GEN2=1
  E: ID_ATA_SATA_SIGNAL_RATE_GEN1=1
  E: ID_ATA_ROTATION_RATE_RPM=7200
  E: ID_WWN=0x5000c500251025f4
  E: ID_WWN_WITH_EXTENSION=0x5000c500251025f4
  E: ID_SCSI_COMPAT=SATA_ST9250410ASG_5VG5AW0Z
  E: ID_PATH=pci-0000:00:1f.2-scsi-0:0:0:0
  E: ID_PATH_TAG=pci-0000_00_1f_2-scsi-0_0_0_0
  E: ID_PART_TABLE_TYPE=dos
  E: ID_FS_UUID=2bdc1a9a-8cf1-4e51-8e7a-0717443ce6c8
  E: ID_FS_UUID_ENC=2bdc1a9a-8cf1-4e51-8e7a-0717443ce6c8
  E: ID_FS_VERSION=1.0
  E: ID_FS_TYPE=ext3
  E: ID_FS_USAGE=filesystem
  E: ID_PART_ENTRY_SCHEME=dos
  E: ID_PART_ENTRY_TYPE=0x83
  E: ID_PART_ENTRY_NUMBER=2
  E: UDISKS_PRESENTATION_NOPOLICY=0
  E: UDISKS_PARTITION=1
  E: UDISKS_PARTITION_SCHEME=mbr
  E: UDISKS_PARTITION_NUMBER=2
  E: UDISKS_PARTITION_TYPE=0x83
  E: UDISKS_PARTITION_SIZE=41943040000
  E: UDISKS_PARTITION_SLAVE=/sys/devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0/block/sda
  E: UDISKS_PARTITION_OFFSET=105906176
  E: UDISKS_PARTITION_ALIGNMENT_OFFSET=0
  E: DEVLINKS=/dev/disk/by-id/ata-ST9250410ASG_5VG5AW0Z-part2 /dev/disk/by-id/scsi-SATA_ST9250410ASG_5VG5AW0Z-part2 /dev/disk/by-path/pci-0000:00:1f.2-scsi-0:0:0:0-part2 /dev/disk/by-uuid/2bdc1a9a-8cf1-4e51-8e7a-0717443ce6c8 /dev/disk/by-id/wwn-0x5000c500251025f4-part2
  
  P: /devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0/block/sda/sda4
  N: sda4
  S: disk/by-id/ata-ST9250410ASG_5VG5AW0Z-part4
  S: disk/by-id/scsi-SATA_ST9250410ASG_5VG5AW0Z-part4
  S: disk/by-path/pci-0000:00:1f.2-scsi-0:0:0:0-part4
  S: disk/by-id/wwn-0x5000c500251025f4-part4
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0/block/sda/sda4
  E: MAJOR=8
  E: MINOR=4
  E: DEVNAME=/dev/sda4
  E: DEVTYPE=partition
  E: SUBSYSTEM=block
  E: ID_ATA=1
  E: ID_TYPE=disk
  E: ID_BUS=ata
  E: ID_MODEL=ST9250410ASG
  E: ID_MODEL_ENC=ST9250410ASG\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20
  E: ID_REVISION=0002SD1M
  E: ID_SERIAL=ST9250410ASG_5VG5AW0Z
  E: ID_SERIAL_SHORT=5VG5AW0Z
  E: ID_ATA_WRITE_CACHE=1
  E: ID_ATA_WRITE_CACHE_ENABLED=1
  E: ID_ATA_FEATURE_SET_HPA=1
  E: ID_ATA_FEATURE_SET_HPA_ENABLED=1
  E: ID_ATA_FEATURE_SET_PM=1
  E: ID_ATA_FEATURE_SET_PM_ENABLED=1
  E: ID_ATA_FEATURE_SET_SECURITY=1
  E: ID_ATA_FEATURE_SET_SECURITY_ENABLED=0
  E: ID_ATA_FEATURE_SET_SECURITY_ERASE_UNIT_MIN=54
  E: ID_ATA_FEATURE_SET_SECURITY_ENHANCED_ERASE_UNIT_MIN=54
  E: ID_ATA_FEATURE_SET_SECURITY_FROZEN=1
  E: ID_ATA_FEATURE_SET_SMART=1
  E: ID_ATA_FEATURE_SET_SMART_ENABLED=1
  E: ID_ATA_FEATURE_SET_AAM=1
  E: ID_ATA_FEATURE_SET_AAM_ENABLED=1
  E: ID_ATA_FEATURE_SET_AAM_VENDOR_RECOMMENDED_VALUE=208
  E: ID_ATA_FEATURE_SET_AAM_CURRENT_VALUE=208
  E: ID_ATA_FEATURE_SET_APM=1
  E: ID_ATA_FEATURE_SET_APM_ENABLED=1
  E: ID_ATA_FEATURE_SET_APM_CURRENT_VALUE=254
  E: ID_ATA_DOWNLOAD_MICROCODE=1
  E: ID_ATA_SATA=1
  E: ID_ATA_SATA_SIGNAL_RATE_GEN2=1
  E: ID_ATA_SATA_SIGNAL_RATE_GEN1=1
  E: ID_ATA_ROTATION_RATE_RPM=7200
  E: ID_WWN=0x5000c500251025f4
  E: ID_WWN_WITH_EXTENSION=0x5000c500251025f4
  E: ID_SCSI_COMPAT=SATA_ST9250410ASG_5VG5AW0Z
  E: ID_PATH=pci-0000:00:1f.2-scsi-0:0:0:0
  E: ID_PATH_TAG=pci-0000_00_1f_2-scsi-0_0_0_0
  E: ID_PART_TABLE_TYPE=dos
  E: ID_PART_ENTRY_SCHEME=dos
  E: ID_PART_ENTRY_TYPE=0x5
  E: ID_PART_ENTRY_NUMBER=4
  E: UDISKS_PRESENTATION_NOPOLICY=0
  E: UDISKS_PARTITION=1
  E: UDISKS_PARTITION_SCHEME=mbr
  E: UDISKS_PARTITION_NUMBER=4
  E: UDISKS_PARTITION_TYPE=0x05
  E: UDISKS_PARTITION_SIZE=208009167872
  E: UDISKS_PARTITION_SLAVE=/sys/devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0/block/sda
  E: UDISKS_PARTITION_OFFSET=42049993728
  E: UDISKS_PARTITION_ALIGNMENT_OFFSET=0
  E: DEVLINKS=/dev/disk/by-id/ata-ST9250410ASG_5VG5AW0Z-part4 /dev/disk/by-id/scsi-SATA_ST9250410ASG_5VG5AW0Z-part4 /dev/disk/by-path/pci-0000:00:1f.2-scsi-0:0:0:0-part4 /dev/disk/by-id/wwn-0x5000c500251025f4-part4
  
  P: /devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0/block/sda/sda5
  N: sda5
  S: disk/by-id/ata-ST9250410ASG_5VG5AW0Z-part5
  S: disk/by-id/scsi-SATA_ST9250410ASG_5VG5AW0Z-part5
  S: disk/by-path/pci-0000:00:1f.2-scsi-0:0:0:0-part5
  S: disk/by-uuid/b2d1e233-8260-43f6-b0a0-be7c7d903301
  S: disk/by-label/swap
  S: disk/by-id/wwn-0x5000c500251025f4-part5
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0/block/sda/sda5
  E: MAJOR=8
  E: MINOR=5
  E: DEVNAME=/dev/sda5
  E: DEVTYPE=partition
  E: SUBSYSTEM=block
  E: ID_ATA=1
  E: ID_TYPE=disk
  E: ID_BUS=ata
  E: ID_MODEL=ST9250410ASG
  E: ID_MODEL_ENC=ST9250410ASG\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20
  E: ID_REVISION=0002SD1M
  E: ID_SERIAL=ST9250410ASG_5VG5AW0Z
  E: ID_SERIAL_SHORT=5VG5AW0Z
  E: ID_ATA_WRITE_CACHE=1
  E: ID_ATA_WRITE_CACHE_ENABLED=1
  E: ID_ATA_FEATURE_SET_HPA=1
  E: ID_ATA_FEATURE_SET_HPA_ENABLED=1
  E: ID_ATA_FEATURE_SET_PM=1
  E: ID_ATA_FEATURE_SET_PM_ENABLED=1
  E: ID_ATA_FEATURE_SET_SECURITY=1
  E: ID_ATA_FEATURE_SET_SECURITY_ENABLED=0
  E: ID_ATA_FEATURE_SET_SECURITY_ERASE_UNIT_MIN=54
  E: ID_ATA_FEATURE_SET_SECURITY_ENHANCED_ERASE_UNIT_MIN=54
  E: ID_ATA_FEATURE_SET_SECURITY_FROZEN=1
  E: ID_ATA_FEATURE_SET_SMART=1
  E: ID_ATA_FEATURE_SET_SMART_ENABLED=1
  E: ID_ATA_FEATURE_SET_AAM=1
  E: ID_ATA_FEATURE_SET_AAM_ENABLED=1
  E: ID_ATA_FEATURE_SET_AAM_VENDOR_RECOMMENDED_VALUE=208
  E: ID_ATA_FEATURE_SET_AAM_CURRENT_VALUE=208
  E: ID_ATA_FEATURE_SET_APM=1
  E: ID_ATA_FEATURE_SET_APM_ENABLED=1
  E: ID_ATA_FEATURE_SET_APM_CURRENT_VALUE=254
  E: ID_ATA_DOWNLOAD_MICROCODE=1
  E: ID_ATA_SATA=1
  E: ID_ATA_SATA_SIGNAL_RATE_GEN2=1
  E: ID_ATA_SATA_SIGNAL_RATE_GEN1=1
  E: ID_ATA_ROTATION_RATE_RPM=7200
  E: ID_WWN=0x5000c500251025f4
  E: ID_WWN_WITH_EXTENSION=0x5000c500251025f4
  E: ID_SCSI_COMPAT=SATA_ST9250410ASG_5VG5AW0Z
  E: ID_PATH=pci-0000:00:1f.2-scsi-0:0:0:0
  E: ID_PATH_TAG=pci-0000_00_1f_2-scsi-0_0_0_0
  E: ID_PART_TABLE_TYPE=dos
  E: ID_FS_LABEL=swap
  E: ID_FS_LABEL_ENC=swap
  E: ID_FS_UUID=b2d1e233-8260-43f6-b0a0-be7c7d903301
  E: ID_FS_UUID_ENC=b2d1e233-8260-43f6-b0a0-be7c7d903301
  E: ID_FS_VERSION=2
  E: ID_FS_TYPE=swap
  E: ID_FS_USAGE=other
  E: ID_PART_ENTRY_SCHEME=dos
  E: ID_PART_ENTRY_TYPE=0x82
  E: ID_PART_ENTRY_NUMBER=5
  E: UDISKS_PRESENTATION_NOPOLICY=0
  E: UDISKS_PARTITION=1
  E: UDISKS_PARTITION_SCHEME=mbr
  E: UDISKS_PARTITION_NUMBER=5
  E: UDISKS_PARTITION_TYPE=0x82
  E: UDISKS_PARTITION_SIZE=4456448000
  E: UDISKS_PARTITION_SLAVE=/sys/devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0/block/sda
  E: UDISKS_PARTITION_OFFSET=42051043328
  E: UDISKS_PARTITION_ALIGNMENT_OFFSET=0
  E: DEVLINKS=/dev/disk/by-id/ata-ST9250410ASG_5VG5AW0Z-part5 /dev/disk/by-id/scsi-SATA_ST9250410ASG_5VG5AW0Z-part5 /dev/disk/by-path/pci-0000:00:1f.2-scsi-0:0:0:0-part5 /dev/disk/by-uuid/b2d1e233-8260-43f6-b0a0-be7c7d903301 /dev/disk/by-label/swap /dev/disk/by-id/wwn-0x5000c500251025f4-part5
  
  P: /devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0/block/sda/sda6
  N: sda6
  S: disk/by-id/ata-ST9250410ASG_5VG5AW0Z-part6
  S: disk/by-id/scsi-SATA_ST9250410ASG_5VG5AW0Z-part6
  S: disk/by-path/pci-0000:00:1f.2-scsi-0:0:0:0-part6
  S: disk/by-uuid/25bdc29e-9e7c-467b-b63b-a6456e2c667b
  S: disk/by-label/\x2fhome
  S: disk/by-id/wwn-0x5000c500251025f4-part6
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0/block/sda/sda6
  E: MAJOR=8
  E: MINOR=6
  E: DEVNAME=/dev/sda6
  E: DEVTYPE=partition
  E: SUBSYSTEM=block
  E: ID_ATA=1
  E: ID_TYPE=disk
  E: ID_BUS=ata
  E: ID_MODEL=ST9250410ASG
  E: ID_MODEL_ENC=ST9250410ASG\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20
  E: ID_REVISION=0002SD1M
  E: ID_SERIAL=ST9250410ASG_5VG5AW0Z
  E: ID_SERIAL_SHORT=5VG5AW0Z
  E: ID_ATA_WRITE_CACHE=1
  E: ID_ATA_WRITE_CACHE_ENABLED=1
  E: ID_ATA_FEATURE_SET_HPA=1
  E: ID_ATA_FEATURE_SET_HPA_ENABLED=1
  E: ID_ATA_FEATURE_SET_PM=1
  E: ID_ATA_FEATURE_SET_PM_ENABLED=1
  E: ID_ATA_FEATURE_SET_SECURITY=1
  E: ID_ATA_FEATURE_SET_SECURITY_ENABLED=0
  E: ID_ATA_FEATURE_SET_SECURITY_ERASE_UNIT_MIN=54
  E: ID_ATA_FEATURE_SET_SECURITY_ENHANCED_ERASE_UNIT_MIN=54
  E: ID_ATA_FEATURE_SET_SECURITY_FROZEN=1
  E: ID_ATA_FEATURE_SET_SMART=1
  E: ID_ATA_FEATURE_SET_SMART_ENABLED=1
  E: ID_ATA_FEATURE_SET_AAM=1
  E: ID_ATA_FEATURE_SET_AAM_ENABLED=1
  E: ID_ATA_FEATURE_SET_AAM_VENDOR_RECOMMENDED_VALUE=208
  E: ID_ATA_FEATURE_SET_AAM_CURRENT_VALUE=208
  E: ID_ATA_FEATURE_SET_APM=1
  E: ID_ATA_FEATURE_SET_APM_ENABLED=1
  E: ID_ATA_FEATURE_SET_APM_CURRENT_VALUE=254
  E: ID_ATA_DOWNLOAD_MICROCODE=1
  E: ID_ATA_SATA=1
  E: ID_ATA_SATA_SIGNAL_RATE_GEN2=1
  E: ID_ATA_SATA_SIGNAL_RATE_GEN1=1
  E: ID_ATA_ROTATION_RATE_RPM=7200
  E: ID_WWN=0x5000c500251025f4
  E: ID_WWN_WITH_EXTENSION=0x5000c500251025f4
  E: ID_SCSI_COMPAT=SATA_ST9250410ASG_5VG5AW0Z
  E: ID_PATH=pci-0000:00:1f.2-scsi-0:0:0:0
  E: ID_PATH_TAG=pci-0000_00_1f_2-scsi-0_0_0_0
  E: ID_PART_TABLE_TYPE=dos
  E: ID_FS_LABEL=/home
  E: ID_FS_LABEL_ENC=\x2fhome
  E: ID_FS_UUID=25bdc29e-9e7c-467b-b63b-a6456e2c667b
  E: ID_FS_UUID_ENC=25bdc29e-9e7c-467b-b63b-a6456e2c667b
  E: ID_FS_SEC_TYPE=ext2
  E: ID_FS_VERSION=1.0
  E: ID_FS_TYPE=ext3
  E: ID_FS_USAGE=filesystem
  E: ID_PART_ENTRY_SCHEME=dos
  E: ID_PART_ENTRY_TYPE=0x83
  E: ID_PART_ENTRY_NUMBER=6
  E: UDISKS_PRESENTATION_NOPOLICY=0
  E: UDISKS_PARTITION=1
  E: UDISKS_PARTITION_SCHEME=mbr
  E: UDISKS_PARTITION_NUMBER=6
  E: UDISKS_PARTITION_TYPE=0x83
  E: UDISKS_PARTITION_SIZE=203550621696
  E: UDISKS_PARTITION_SLAVE=/sys/devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0/block/sda
  E: UDISKS_PARTITION_OFFSET=46508539904
  E: UDISKS_PARTITION_ALIGNMENT_OFFSET=0
  E: DEVLINKS=/dev/disk/by-id/ata-ST9250410ASG_5VG5AW0Z-part6 /dev/disk/by-id/scsi-SATA_ST9250410ASG_5VG5AW0Z-part6 /dev/disk/by-path/pci-0000:00:1f.2-scsi-0:0:0:0-part6 /dev/disk/by-uuid/25bdc29e-9e7c-467b-b63b-a6456e2c667b /dev/disk/by-label/\x2fhome /dev/disk/by-id/wwn-0x5000c500251025f4-part6
  
  P: /devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0/bsg/0:0:0:0
  N: bsg/0:0:0:0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0/bsg/0:0:0:0
  E: MAJOR=253
  E: MINOR=0
  E: DEVNAME=/dev/bsg/0:0:0:0
  E: SUBSYSTEM=bsg
  
  P: /devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0/scsi_device/0:0:0:0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0/scsi_device/0:0:0:0
  E: SUBSYSTEM=scsi_device
  
  P: /devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0/scsi_disk/0:0:0:0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0/scsi_disk/0:0:0:0
  E: SUBSYSTEM=scsi_disk
  
  P: /devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0/scsi_generic/sg0
  N: sg0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0/scsi_generic/sg0
  E: MAJOR=21
  E: MINOR=0
  E: DEVNAME=/dev/sg0
  E: SUBSYSTEM=scsi_generic
  
  P: /devices/pci0000:00/0000:00:1f.2/host1
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/host1
  E: DEVTYPE=scsi_host
  E: SUBSYSTEM=scsi
  
  P: /devices/pci0000:00/0000:00:1f.2/host1/scsi_host/host1
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/host1/scsi_host/host1
  E: SUBSYSTEM=scsi_host
  
  P: /devices/pci0000:00/0000:00:1f.2/host1/target1:0:0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/host1/target1:0:0
  E: DEVTYPE=scsi_target
  E: SUBSYSTEM=scsi
  
  P: /devices/pci0000:00/0000:00:1f.2/host1/target1:0:0/1:0:0:0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/host1/target1:0:0/1:0:0:0
  E: DEVTYPE=scsi_device
  E: DRIVER=sr
  E: MODALIAS=scsi:t-0x05
  E: SUBSYSTEM=scsi
  
  P: /devices/pci0000:00/0000:00:1f.2/host1/target1:0:0/1:0:0:0/block/sr0
  N: sr0
  S: scd0
  S: disk/by-id/ata-HL-DT-ST_DVD+_-RW_GU10N_KVEA3B93937
  S: disk/by-path/pci-0000:00:1f.2-scsi-1:0:0:0
  S: cdrom1
  S: cdrw1
  S: dvd1
  S: dvdrw1
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/host1/target1:0:0/1:0:0:0/block/sr0
  E: MAJOR=11
  E: MINOR=0
  E: DEVNAME=/dev/sr0
  E: DEVTYPE=disk
  E: SUBSYSTEM=block
  E: ID_CDROM=1
  E: ID_CDROM_CD=1
  E: ID_CDROM_CD_R=1
  E: ID_CDROM_CD_RW=1
  E: ID_CDROM_DVD=1
  E: ID_CDROM_DVD_R=1
  E: ID_CDROM_DVD_RW=1
  E: ID_CDROM_DVD_RAM=1
  E: ID_CDROM_DVD_PLUS_R=1
  E: ID_CDROM_DVD_PLUS_RW=1
  E: ID_CDROM_DVD_PLUS_R_DL=1
  E: ID_CDROM_MRW=1
  E: ID_CDROM_MRW_W=1
  E: ID_ATA=1
  E: ID_TYPE=cd
  E: ID_BUS=ata
  E: ID_MODEL=HL-DT-ST_DVD+_-RW_GU10N
  E: ID_MODEL_ENC=HL-DT-ST\x20DVD+\x2f-RW\x20GU10N\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20
  E: ID_REVISION=A102
  E: ID_SERIAL=HL-DT-ST_DVD+_-RW_GU10N_KVEA3B93937
  E: ID_SERIAL_SHORT=KVEA3B93937
  E: ID_ATA_FEATURE_SET_PM=1
  E: ID_ATA_FEATURE_SET_PM_ENABLED=1
  E: ID_ATA_SATA=1
  E: ID_ATA_SATA_SIGNAL_RATE_GEN1=1
  E: ID_PATH=pci-0000:00:1f.2-scsi-1:0:0:0
  E: ID_PATH_TAG=pci-0000_00_1f_2-scsi-1_0_0_0
  E: GENERATED=1
  E: UDISKS_PRESENTATION_NOPOLICY=0
  E: DEVLINKS=/dev/scd0 /dev/disk/by-id/ata-HL-DT-ST_DVD+_-RW_GU10N_KVEA3B93937 /dev/disk/by-path/pci-0000:00:1f.2-scsi-1:0:0:0 /dev/cdrom1 /dev/cdrw1 /dev/dvd1 /dev/dvdrw1
  E: TAGS=:udev-acl:
  
  P: /devices/pci0000:00/0000:00:1f.2/host1/target1:0:0/1:0:0:0/bsg/1:0:0:0
  N: bsg/1:0:0:0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/host1/target1:0:0/1:0:0:0/bsg/1:0:0:0
  E: MAJOR=253
  E: MINOR=1
  E: DEVNAME=/dev/bsg/1:0:0:0
  E: SUBSYSTEM=bsg
  
  P: /devices/pci0000:00/0000:00:1f.2/host1/target1:0:0/1:0:0:0/scsi_device/1:0:0:0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/host1/target1:0:0/1:0:0:0/scsi_device/1:0:0:0
  E: SUBSYSTEM=scsi_device
  
  P: /devices/pci0000:00/0000:00:1f.2/host1/target1:0:0/1:0:0:0/scsi_generic/sg1
  N: sg1
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/host1/target1:0:0/1:0:0:0/scsi_generic/sg1
  E: MAJOR=21
  E: MINOR=1
  E: DEVNAME=/dev/sg1
  E: SUBSYSTEM=scsi_generic
  E: TAGS=:udev-acl:
  
  P: /devices/pci0000:00/0000:00:1f.2/host2
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/host2
  E: DEVTYPE=scsi_host
  E: SUBSYSTEM=scsi
  
  P: /devices/pci0000:00/0000:00:1f.2/host2/scsi_host/host2
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/host2/scsi_host/host2
  E: SUBSYSTEM=scsi_host
  
  P: /devices/pci0000:00/0000:00:1f.2/host3
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/host3
  E: DEVTYPE=scsi_host
  E: SUBSYSTEM=scsi
  
  P: /devices/pci0000:00/0000:00:1f.2/host3/scsi_host/host3
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/host3/scsi_host/host3
  E: SUBSYSTEM=scsi_host
  
  P: /devices/pci0000:00/0000:00:1f.2/host4
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/host4
  E: DEVTYPE=scsi_host
  E: SUBSYSTEM=scsi
  
  P: /devices/pci0000:00/0000:00:1f.2/host4/scsi_host/host4
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/host4/scsi_host/host4
  E: SUBSYSTEM=scsi_host
  
  P: /devices/pci0000:00/0000:00:1f.2/host5
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/host5
  E: DEVTYPE=scsi_host
  E: SUBSYSTEM=scsi
  
  P: /devices/pci0000:00/0000:00:1f.2/host5/scsi_host/host5
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/host5/scsi_host/host5
  E: SUBSYSTEM=scsi_host
  
  P: /devices/pci0000:00/0000:00:1f.3
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1f.3
  E: PCI_CLASS=C0500
  E: PCI_ID=8086:2930
  E: PCI_SUBSYS_ID=1028:024F
  E: PCI_SLOT_NAME=0000:00:1f.3
  E: MODALIAS=pci:v00008086d00002930sv00001028sd0000024Fbc0Csc05i00
  E: SUBSYSTEM=pci
  
  P: /devices/pci0000:00/pci_bus/0000:00
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/pci_bus/0000:00
  E: SUBSYSTEM=pci_bus
  
  P: /devices/platform/Fixed MDIO bus.0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/platform/Fixed MDIO bus.0
  E: MODALIAS=platform:Fixed MDIO bus
  E: SUBSYSTEM=platform
  
  P: /devices/platform/Fixed MDIO bus.0/mdio_bus/0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/platform/Fixed MDIO bus.0/mdio_bus/0
  E: SUBSYSTEM=mdio_bus
  
  P: /devices/platform/alarmtimer
  E: UDEV_LOG=3
  E: DEVPATH=/devices/platform/alarmtimer
  E: DRIVER=alarmtimer
  E: MODALIAS=platform:alarmtimer
  E: SUBSYSTEM=platform
  
  P: /devices/platform/dcdbas
  E: UDEV_LOG=3
  E: DEVPATH=/devices/platform/dcdbas
  E: DRIVER=dcdbas
  E: MODALIAS=platform:dcdbas
  E: SUBSYSTEM=platform
  
  P: /devices/platform/dell-laptop
  E: UDEV_LOG=3
  E: DEVPATH=/devices/platform/dell-laptop
  E: DRIVER=dell-laptop
  E: MODALIAS=platform:dell-laptop
  E: SUBSYSTEM=platform
  
  P: /devices/platform/dell-laptop/rfkill/rfkill0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/platform/dell-laptop/rfkill/rfkill0
  E: RFKILL_NAME=dell-wifi
  E: RFKILL_TYPE=wlan
  E: RFKILL_STATE=1
  E: SUBSYSTEM=rfkill
  
  P: /devices/platform/dell-laptop/rfkill/rfkill1
  E: UDEV_LOG=3
  E: DEVPATH=/devices/platform/dell-laptop/rfkill/rfkill1
  E: RFKILL_NAME=dell-bluetooth
  E: RFKILL_TYPE=bluetooth
  E: RFKILL_STATE=1
  E: SUBSYSTEM=rfkill
  
  P: /devices/platform/i8042
  E: UDEV_LOG=3
  E: DEVPATH=/devices/platform/i8042
  E: DRIVER=i8042
  E: MODALIAS=platform:i8042
  E: SUBSYSTEM=platform
  
  P: /devices/platform/i8042/serio0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/platform/i8042/serio0
  E: DRIVER=atkbd
  E: SERIO_TYPE=06
  E: SERIO_PROTO=00
  E: SERIO_ID=00
  E: SERIO_EXTRA=00
  E: MODALIAS=serio:ty06pr00id00ex00
  E: SUBSYSTEM=serio
  E: DMI_VENDOR=Dell Inc.
  
  P: /devices/platform/i8042/serio0/input/input3
  E: UDEV_LOG=3
  E: DEVPATH=/devices/platform/i8042/serio0/input/input3
  E: PRODUCT=11/1/1/ab41
  E: NAME="AT Translated Set 2 keyboard"
  E: PHYS="isa0060/serio0/input0"
  E: PROP=0
  E: EV=120013
  E: KEY=1100f02902002 8380307cf910f001 feffffdfffefffff fffffffffffffffe
  E: MSC=10
  E: LED=7
  E: MODALIAS=input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8D,8E,8F,94,98,9B,9C,9D,9E,9F,A2,A3,A4,A5,A6,AC,AD,B7,B8,B9,BF,C1,CD,D4,D7,D9,E0,E1,E2,E3,EC,F0,ram4,l0,1,2,sfw
  E: SUBSYSTEM=input
  E: ID_INPUT=1
  E: ID_INPUT_KEY=1
  E: ID_INPUT_KEYBOARD=1
  E: ID_SERIAL=noserial
  E: ID_PATH=platform-i8042-serio-0
  E: ID_PATH_TAG=platform-i8042-serio-0
  
  P: /devices/platform/i8042/serio0/input/input3/event3
  N: input/event3
  S: input/by-path/platform-i8042-serio-0-event-kbd
  E: UDEV_LOG=3
  E: DEVPATH=/devices/platform/i8042/serio0/input/input3/event3
  E: MAJOR=13
  E: MINOR=67
  E: DEVNAME=/dev/input/event3
  E: SUBSYSTEM=input
  E: ID_INPUT=1
  E: ID_INPUT_KEY=1
  E: ID_INPUT_KEYBOARD=1
  E: ID_SERIAL=noserial
  E: ID_PATH=platform-i8042-serio-0
  E: ID_PATH_TAG=platform-i8042-serio-0
  E: XKBMODEL=pc105
  E: XKBLAYOUT=us
  E: DEVLINKS=/dev/input/by-path/platform-i8042-serio-0-event-kbd
  E: DMI_VENDOR=Dell Inc.
  
  P: /devices/platform/i8042/serio1
  E: UDEV_LOG=3
  E: DEVPATH=/devices/platform/i8042/serio1
  E: DRIVER=psmouse
  E: SERIO_TYPE=01
  E: SERIO_PROTO=00
  E: SERIO_ID=00
  E: SERIO_EXTRA=00
  E: MODALIAS=serio:ty01pr00id00ex00
  E: SUBSYSTEM=serio
  
  P: /devices/platform/i8042/serio1/input/input8
  E: UDEV_LOG=3
  E: DEVPATH=/devices/platform/i8042/serio1/input/input8
  E: PRODUCT=11/2/8/0
  E: NAME="DualPoint Stick"
  E: PHYS="isa0060/serio1/input1"
  E: PROP=0
  E: EV=7
  E: KEY=70000 0 0 0 0
  E: REL=3
  E: MODALIAS=input:b0011v0002p0008e0000-e0,1,2,k110,111,112,r0,1,amlsfw
  E: SUBSYSTEM=input
  E: ID_INPUT=1
  E: ID_INPUT_MOUSE=1
  E: ID_SERIAL=noserial
  E: ID_PATH=platform-i8042-serio-1
  E: ID_PATH_TAG=platform-i8042-serio-1
  
  P: /devices/platform/i8042/serio1/input/input8/event8
  N: input/event8
  S: input/by-path/platform-i8042-serio-1-event-mouse
  E: UDEV_LOG=3
  E: DEVPATH=/devices/platform/i8042/serio1/input/input8/event8
  E: MAJOR=13
  E: MINOR=72
  E: DEVNAME=/dev/input/event8
  E: SUBSYSTEM=input
  E: ID_INPUT=1
  E: ID_INPUT_MOUSE=1
  E: ID_SERIAL=noserial
  E: ID_PATH=platform-i8042-serio-1
  E: ID_PATH_TAG=platform-i8042-serio-1
  E: DEVLINKS=/dev/input/by-path/platform-i8042-serio-1-event-mouse
  
  P: /devices/platform/i8042/serio1/input/input8/mouse2
  N: input/mouse2
  S: input/by-path/platform-i8042-serio-1-mouse
  E: UDEV_LOG=3
  E: DEVPATH=/devices/platform/i8042/serio1/input/input8/mouse2
  E: MAJOR=13
  E: MINOR=34
  E: DEVNAME=/dev/input/mouse2
  E: SUBSYSTEM=input
  E: ID_INPUT=1
  E: ID_INPUT_MOUSE=1
  E: ID_SERIAL=noserial
  E: ID_PATH=platform-i8042-serio-1
  E: ID_PATH_TAG=platform-i8042-serio-1
  E: DEVLINKS=/dev/input/by-path/platform-i8042-serio-1-mouse
  
  P: /devices/platform/i8042/serio1/input/input9
  E: UDEV_LOG=3
  E: DEVPATH=/devices/platform/i8042/serio1/input/input9
  E: PRODUCT=11/2/8/6222
  E: NAME="AlpsPS/2 ALPS DualPoint TouchPad"
  E: PHYS="isa0060/serio1/input0"
  E: PROP=0
  E: EV=b
  E: KEY=420 70000 0 0 0 0
  E: ABS=1000003
  E: MODALIAS=input:b0011v0002p0008e6222-e0,1,3,k110,111,112,145,14A,ra0,1,18,mlsfw
  E: SUBSYSTEM=input
  E: ID_INPUT=1
  E: ID_INPUT_TOUCHPAD=1
  E: ID_SERIAL=noserial
  E: ID_PATH=platform-i8042-serio-1
  E: ID_PATH_TAG=platform-i8042-serio-1
  
  P: /devices/platform/i8042/serio1/input/input9/event9
  N: input/event9
  S: input/by-path/platform-i8042-serio-1-event-mouse
  E: UDEV_LOG=3
  E: DEVPATH=/devices/platform/i8042/serio1/input/input9/event9
  E: MAJOR=13
  E: MINOR=73
  E: DEVNAME=/dev/input/event9
  E: SUBSYSTEM=input
  E: ID_INPUT=1
  E: ID_INPUT_TOUCHPAD=1
  E: ID_SERIAL=noserial
  E: ID_PATH=platform-i8042-serio-1
  E: ID_PATH_TAG=platform-i8042-serio-1
  E: DEVLINKS=/dev/input/by-path/platform-i8042-serio-1-event-mouse
  
  P: /devices/platform/i8042/serio1/input/input9/mouse3
  N: input/mouse3
  S: input/by-path/platform-i8042-serio-1-mouse
  E: UDEV_LOG=3
  E: DEVPATH=/devices/platform/i8042/serio1/input/input9/mouse3
  E: MAJOR=13
  E: MINOR=35
  E: DEVNAME=/dev/input/mouse3
  E: SUBSYSTEM=input
  E: ID_INPUT=1
  E: ID_INPUT_TOUCHPAD=1
  E: ID_SERIAL=noserial
  E: ID_PATH=platform-i8042-serio-1
  E: ID_PATH_TAG=platform-i8042-serio-1
  E: DEVLINKS=/dev/input/by-path/platform-i8042-serio-1-mouse
  
  P: /devices/platform/pcspkr
  E: UDEV_LOG=3
  E: DEVPATH=/devices/platform/pcspkr
  E: MODALIAS=platform:pcspkr
  E: SUBSYSTEM=platform
  
  P: /devices/platform/reg-dummy
  E: UDEV_LOG=3
  E: DEVPATH=/devices/platform/reg-dummy
  E: MODALIAS=platform:reg-dummy
  E: SUBSYSTEM=platform
  
  P: /devices/platform/serial8250
  E: UDEV_LOG=3
  E: DEVPATH=/devices/platform/serial8250
  E: DRIVER=serial8250
  E: MODALIAS=platform:serial8250
  E: SUBSYSTEM=platform
  
  P: /devices/platform/serial8250/tty/ttyS1
  N: ttyS1
  E: UDEV_LOG=3
  E: DEVPATH=/devices/platform/serial8250/tty/ttyS1
  E: MAJOR=4
  E: MINOR=65
  E: DEVNAME=/dev/ttyS1
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/platform/serial8250/tty/ttyS10
  N: ttyS10
  E: UDEV_LOG=3
  E: DEVPATH=/devices/platform/serial8250/tty/ttyS10
  E: MAJOR=4
  E: MINOR=74
  E: DEVNAME=/dev/ttyS10
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/platform/serial8250/tty/ttyS11
  N: ttyS11
  E: UDEV_LOG=3
  E: DEVPATH=/devices/platform/serial8250/tty/ttyS11
  E: MAJOR=4
  E: MINOR=75
  E: DEVNAME=/dev/ttyS11
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/platform/serial8250/tty/ttyS12
  N: ttyS12
  E: UDEV_LOG=3
  E: DEVPATH=/devices/platform/serial8250/tty/ttyS12
  E: MAJOR=4
  E: MINOR=76
  E: DEVNAME=/dev/ttyS12
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/platform/serial8250/tty/ttyS13
  N: ttyS13
  E: UDEV_LOG=3
  E: DEVPATH=/devices/platform/serial8250/tty/ttyS13
  E: MAJOR=4
  E: MINOR=77
  E: DEVNAME=/dev/ttyS13
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/platform/serial8250/tty/ttyS14
  N: ttyS14
  E: UDEV_LOG=3
  E: DEVPATH=/devices/platform/serial8250/tty/ttyS14
  E: MAJOR=4
  E: MINOR=78
  E: DEVNAME=/dev/ttyS14
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/platform/serial8250/tty/ttyS15
  N: ttyS15
  E: UDEV_LOG=3
  E: DEVPATH=/devices/platform/serial8250/tty/ttyS15
  E: MAJOR=4
  E: MINOR=79
  E: DEVNAME=/dev/ttyS15
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/platform/serial8250/tty/ttyS16
  N: ttyS16
  E: UDEV_LOG=3
  E: DEVPATH=/devices/platform/serial8250/tty/ttyS16
  E: MAJOR=4
  E: MINOR=80
  E: DEVNAME=/dev/ttyS16
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/platform/serial8250/tty/ttyS17
  N: ttyS17
  E: UDEV_LOG=3
  E: DEVPATH=/devices/platform/serial8250/tty/ttyS17
  E: MAJOR=4
  E: MINOR=81
  E: DEVNAME=/dev/ttyS17
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/platform/serial8250/tty/ttyS18
  N: ttyS18
  E: UDEV_LOG=3
  E: DEVPATH=/devices/platform/serial8250/tty/ttyS18
  E: MAJOR=4
  E: MINOR=82
  E: DEVNAME=/dev/ttyS18
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/platform/serial8250/tty/ttyS19
  N: ttyS19
  E: UDEV_LOG=3
  E: DEVPATH=/devices/platform/serial8250/tty/ttyS19
  E: MAJOR=4
  E: MINOR=83
  E: DEVNAME=/dev/ttyS19
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/platform/serial8250/tty/ttyS2
  N: ttyS2
  E: UDEV_LOG=3
  E: DEVPATH=/devices/platform/serial8250/tty/ttyS2
  E: MAJOR=4
  E: MINOR=66
  E: DEVNAME=/dev/ttyS2
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/platform/serial8250/tty/ttyS20
  N: ttyS20
  E: UDEV_LOG=3
  E: DEVPATH=/devices/platform/serial8250/tty/ttyS20
  E: MAJOR=4
  E: MINOR=84
  E: DEVNAME=/dev/ttyS20
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/platform/serial8250/tty/ttyS21
  N: ttyS21
  E: UDEV_LOG=3
  E: DEVPATH=/devices/platform/serial8250/tty/ttyS21
  E: MAJOR=4
  E: MINOR=85
  E: DEVNAME=/dev/ttyS21
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/platform/serial8250/tty/ttyS22
  N: ttyS22
  E: UDEV_LOG=3
  E: DEVPATH=/devices/platform/serial8250/tty/ttyS22
  E: MAJOR=4
  E: MINOR=86
  E: DEVNAME=/dev/ttyS22
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/platform/serial8250/tty/ttyS23
  N: ttyS23
  E: UDEV_LOG=3
  E: DEVPATH=/devices/platform/serial8250/tty/ttyS23
  E: MAJOR=4
  E: MINOR=87
  E: DEVNAME=/dev/ttyS23
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/platform/serial8250/tty/ttyS24
  N: ttyS24
  E: UDEV_LOG=3
  E: DEVPATH=/devices/platform/serial8250/tty/ttyS24
  E: MAJOR=4
  E: MINOR=88
  E: DEVNAME=/dev/ttyS24
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/platform/serial8250/tty/ttyS25
  N: ttyS25
  E: UDEV_LOG=3
  E: DEVPATH=/devices/platform/serial8250/tty/ttyS25
  E: MAJOR=4
  E: MINOR=89
  E: DEVNAME=/dev/ttyS25
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/platform/serial8250/tty/ttyS26
  N: ttyS26
  E: UDEV_LOG=3
  E: DEVPATH=/devices/platform/serial8250/tty/ttyS26
  E: MAJOR=4
  E: MINOR=90
  E: DEVNAME=/dev/ttyS26
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/platform/serial8250/tty/ttyS27
  N: ttyS27
  E: UDEV_LOG=3
  E: DEVPATH=/devices/platform/serial8250/tty/ttyS27
  E: MAJOR=4
  E: MINOR=91
  E: DEVNAME=/dev/ttyS27
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/platform/serial8250/tty/ttyS28
  N: ttyS28
  E: UDEV_LOG=3
  E: DEVPATH=/devices/platform/serial8250/tty/ttyS28
  E: MAJOR=4
  E: MINOR=92
  E: DEVNAME=/dev/ttyS28
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/platform/serial8250/tty/ttyS29
  N: ttyS29
  E: UDEV_LOG=3
  E: DEVPATH=/devices/platform/serial8250/tty/ttyS29
  E: MAJOR=4
  E: MINOR=93
  E: DEVNAME=/dev/ttyS29
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/platform/serial8250/tty/ttyS3
  N: ttyS3
  E: UDEV_LOG=3
  E: DEVPATH=/devices/platform/serial8250/tty/ttyS3
  E: MAJOR=4
  E: MINOR=67
  E: DEVNAME=/dev/ttyS3
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/platform/serial8250/tty/ttyS30
  N: ttyS30
  E: UDEV_LOG=3
  E: DEVPATH=/devices/platform/serial8250/tty/ttyS30
  E: MAJOR=4
  E: MINOR=94
  E: DEVNAME=/dev/ttyS30
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/platform/serial8250/tty/ttyS31
  N: ttyS31
  E: UDEV_LOG=3
  E: DEVPATH=/devices/platform/serial8250/tty/ttyS31
  E: MAJOR=4
  E: MINOR=95
  E: DEVNAME=/dev/ttyS31
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/platform/serial8250/tty/ttyS4
  N: ttyS4
  E: UDEV_LOG=3
  E: DEVPATH=/devices/platform/serial8250/tty/ttyS4
  E: MAJOR=4
  E: MINOR=68
  E: DEVNAME=/dev/ttyS4
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/platform/serial8250/tty/ttyS5
  N: ttyS5
  E: UDEV_LOG=3
  E: DEVPATH=/devices/platform/serial8250/tty/ttyS5
  E: MAJOR=4
  E: MINOR=69
  E: DEVNAME=/dev/ttyS5
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/platform/serial8250/tty/ttyS6
  N: ttyS6
  E: UDEV_LOG=3
  E: DEVPATH=/devices/platform/serial8250/tty/ttyS6
  E: MAJOR=4
  E: MINOR=70
  E: DEVNAME=/dev/ttyS6
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/platform/serial8250/tty/ttyS7
  N: ttyS7
  E: UDEV_LOG=3
  E: DEVPATH=/devices/platform/serial8250/tty/ttyS7
  E: MAJOR=4
  E: MINOR=71
  E: DEVNAME=/dev/ttyS7
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/platform/serial8250/tty/ttyS8
  N: ttyS8
  E: UDEV_LOG=3
  E: DEVPATH=/devices/platform/serial8250/tty/ttyS8
  E: MAJOR=4
  E: MINOR=72
  E: DEVNAME=/dev/ttyS8
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/platform/serial8250/tty/ttyS9
  N: ttyS9
  E: UDEV_LOG=3
  E: DEVPATH=/devices/platform/serial8250/tty/ttyS9
  E: MAJOR=4
  E: MINOR=73
  E: DEVNAME=/dev/ttyS9
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/platform/vboxdrv.0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/platform/vboxdrv.0
  E: DRIVER=vboxdrv
  E: MODALIAS=platform:vboxdrv
  E: SUBSYSTEM=platform
  
  P: /devices/pnp0/00:00
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pnp0/00:00
  E: SUBSYSTEM=pnp
  
  P: /devices/pnp0/00:01
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pnp0/00:01
  E: DRIVER=i8042 aux
  E: SUBSYSTEM=pnp
  
  P: /devices/pnp0/00:02
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pnp0/00:02
  E: DRIVER=i8042 kbd
  E: SUBSYSTEM=pnp
  
  P: /devices/pnp0/00:03
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pnp0/00:03
  E: DRIVER=rtc_cmos
  E: SUBSYSTEM=pnp
  
  P: /devices/pnp0/00:03/rtc/rtc0
  N: rtc0
  S: rtc
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pnp0/00:03/rtc/rtc0
  E: MAJOR=254
  E: MINOR=0
  E: DEVNAME=/dev/rtc0
  E: SUBSYSTEM=rtc
  E: DEVLINKS=/dev/rtc
  
  P: /devices/pnp0/00:04
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pnp0/00:04
  E: SUBSYSTEM=pnp
  
  P: /devices/pnp0/00:05
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pnp0/00:05
  E: DRIVER=system
  E: SUBSYSTEM=pnp
  
  P: /devices/pnp0/00:06
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pnp0/00:06
  E: SUBSYSTEM=pnp
  
  P: /devices/pnp0/00:07
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pnp0/00:07
  E: SUBSYSTEM=pnp
  
  P: /devices/pnp0/00:08
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pnp0/00:08
  E: DRIVER=system
  E: SUBSYSTEM=pnp
  
  P: /devices/pnp0/00:09
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pnp0/00:09
  E: DRIVER=serial
  E: SUBSYSTEM=pnp
  
  P: /devices/pnp0/00:09/tty/ttyS0
  N: ttyS0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pnp0/00:09/tty/ttyS0
  E: MAJOR=4
  E: MINOR=64
  E: DEVNAME=/dev/ttyS0
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/pnp0/00:0a
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pnp0/00:0a
  E: DRIVER=parport_pc
  E: SUBSYSTEM=pnp
  
  P: /devices/pnp0/00:0a/ppdev/parport0
  N: parport0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pnp0/00:0a/ppdev/parport0
  E: MAJOR=99
  E: MINOR=0
  E: DEVNAME=/dev/parport0
  E: SUBSYSTEM=ppdev
  
  P: /devices/pnp0/00:0a/printer/lp0
  N: lp0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pnp0/00:0a/printer/lp0
  E: MAJOR=6
  E: MINOR=0
  E: DEVNAME=/dev/lp0
  E: SUBSYSTEM=printer
  E: TAGS=:udev-configure-printer:
  
  P: /devices/pnp0/00:0b
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pnp0/00:0b
  E: DRIVER=system
  E: SUBSYSTEM=pnp
  
  P: /devices/pnp0/00:0c
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pnp0/00:0c
  E: DRIVER=system
  E: SUBSYSTEM=pnp
  
  P: /devices/pnp0/00:0d
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pnp0/00:0d
  E: DRIVER=system
  E: SUBSYSTEM=pnp
  
  P: /devices/pnp0/00:0e
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pnp0/00:0e
  E: DRIVER=system
  E: SUBSYSTEM=pnp
  
  P: /devices/software
  E: UDEV_LOG=3
  E: DEVPATH=/devices/software
  E: SUBSYSTEM=event_source
  
  P: /devices/tracepoint
  E: UDEV_LOG=3
  E: DEVPATH=/devices/tracepoint
  E: SUBSYSTEM=event_source
  
  P: /devices/virtual/bdi/0:19
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/bdi/0:19
  E: SUBSYSTEM=bdi
  
  P: /devices/virtual/bdi/0:20
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/bdi/0:20
  E: SUBSYSTEM=bdi
  
  P: /devices/virtual/bdi/0:21
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/bdi/0:21
  E: SUBSYSTEM=bdi
  
  P: /devices/virtual/bdi/0:22
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/bdi/0:22
  E: SUBSYSTEM=bdi
  
  P: /devices/virtual/bdi/11:0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/bdi/11:0
  E: SUBSYSTEM=bdi
  
  P: /devices/virtual/bdi/11:1
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/bdi/11:1
  E: SUBSYSTEM=bdi
  
  P: /devices/virtual/bdi/179:0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/bdi/179:0
  E: SUBSYSTEM=bdi
  
  P: /devices/virtual/bdi/1:0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/bdi/1:0
  E: SUBSYSTEM=bdi
  
  P: /devices/virtual/bdi/1:1
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/bdi/1:1
  E: SUBSYSTEM=bdi
  
  P: /devices/virtual/bdi/1:10
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/bdi/1:10
  E: SUBSYSTEM=bdi
  
  P: /devices/virtual/bdi/1:11
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/bdi/1:11
  E: SUBSYSTEM=bdi
  
  P: /devices/virtual/bdi/1:12
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/bdi/1:12
  E: SUBSYSTEM=bdi
  
  P: /devices/virtual/bdi/1:13
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/bdi/1:13
  E: SUBSYSTEM=bdi
  
  P: /devices/virtual/bdi/1:14
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/bdi/1:14
  E: SUBSYSTEM=bdi
  
  P: /devices/virtual/bdi/1:15
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/bdi/1:15
  E: SUBSYSTEM=bdi
  
  P: /devices/virtual/bdi/1:2
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/bdi/1:2
  E: SUBSYSTEM=bdi
  
  P: /devices/virtual/bdi/1:3
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/bdi/1:3
  E: SUBSYSTEM=bdi
  
  P: /devices/virtual/bdi/1:4
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/bdi/1:4
  E: SUBSYSTEM=bdi
  
  P: /devices/virtual/bdi/1:5
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/bdi/1:5
  E: SUBSYSTEM=bdi
  
  P: /devices/virtual/bdi/1:6
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/bdi/1:6
  E: SUBSYSTEM=bdi
  
  P: /devices/virtual/bdi/1:7
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/bdi/1:7
  E: SUBSYSTEM=bdi
  
  P: /devices/virtual/bdi/1:8
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/bdi/1:8
  E: SUBSYSTEM=bdi
  
  P: /devices/virtual/bdi/1:9
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/bdi/1:9
  E: SUBSYSTEM=bdi
  
  P: /devices/virtual/bdi/7:0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/bdi/7:0
  E: SUBSYSTEM=bdi
  
  P: /devices/virtual/bdi/7:1
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/bdi/7:1
  E: SUBSYSTEM=bdi
  
  P: /devices/virtual/bdi/7:2
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/bdi/7:2
  E: SUBSYSTEM=bdi
  
  P: /devices/virtual/bdi/7:3
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/bdi/7:3
  E: SUBSYSTEM=bdi
  
  P: /devices/virtual/bdi/7:4
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/bdi/7:4
  E: SUBSYSTEM=bdi
  
  P: /devices/virtual/bdi/7:5
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/bdi/7:5
  E: SUBSYSTEM=bdi
  
  P: /devices/virtual/bdi/7:6
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/bdi/7:6
  E: SUBSYSTEM=bdi
  
  P: /devices/virtual/bdi/7:7
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/bdi/7:7
  E: SUBSYSTEM=bdi
  
  P: /devices/virtual/bdi/8:0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/bdi/8:0
  E: SUBSYSTEM=bdi
  
  P: /devices/virtual/bdi/8:16
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/bdi/8:16
  E: SUBSYSTEM=bdi
  
  P: /devices/virtual/bdi/default
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/bdi/default
  E: SUBSYSTEM=bdi
  
  P: /devices/virtual/block/loop0
  N: loop0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/block/loop0
  E: MAJOR=7
  E: MINOR=0
  E: DEVNAME=/dev/loop0
  E: DEVTYPE=disk
  E: SUBSYSTEM=block
  E: UDISKS_PRESENTATION_NOPOLICY=1
  
  P: /devices/virtual/block/loop1
  N: loop1
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/block/loop1
  E: MAJOR=7
  E: MINOR=1
  E: DEVNAME=/dev/loop1
  E: DEVTYPE=disk
  E: SUBSYSTEM=block
  E: UDISKS_PRESENTATION_NOPOLICY=1
  
  P: /devices/virtual/block/loop2
  N: loop2
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/block/loop2
  E: MAJOR=7
  E: MINOR=2
  E: DEVNAME=/dev/loop2
  E: DEVTYPE=disk
  E: SUBSYSTEM=block
  E: UDISKS_PRESENTATION_NOPOLICY=1
  
  P: /devices/virtual/block/loop3
  N: loop3
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/block/loop3
  E: MAJOR=7
  E: MINOR=3
  E: DEVNAME=/dev/loop3
  E: DEVTYPE=disk
  E: SUBSYSTEM=block
  E: UDISKS_PRESENTATION_NOPOLICY=1
  
  P: /devices/virtual/block/loop4
  N: loop4
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/block/loop4
  E: MAJOR=7
  E: MINOR=4
  E: DEVNAME=/dev/loop4
  E: DEVTYPE=disk
  E: SUBSYSTEM=block
  E: UDISKS_PRESENTATION_NOPOLICY=1
  
  P: /devices/virtual/block/loop5
  N: loop5
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/block/loop5
  E: MAJOR=7
  E: MINOR=5
  E: DEVNAME=/dev/loop5
  E: DEVTYPE=disk
  E: SUBSYSTEM=block
  E: UDISKS_PRESENTATION_NOPOLICY=1
  
  P: /devices/virtual/block/loop6
  N: loop6
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/block/loop6
  E: MAJOR=7
  E: MINOR=6
  E: DEVNAME=/dev/loop6
  E: DEVTYPE=disk
  E: SUBSYSTEM=block
  E: UDISKS_PRESENTATION_NOPOLICY=1
  
  P: /devices/virtual/block/loop7
  N: loop7
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/block/loop7
  E: MAJOR=7
  E: MINOR=7
  E: DEVNAME=/dev/loop7
  E: DEVTYPE=disk
  E: SUBSYSTEM=block
  E: UDISKS_PRESENTATION_NOPOLICY=1
  
  P: /devices/virtual/block/ram0
  N: ram0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/block/ram0
  E: MAJOR=1
  E: MINOR=0
  E: DEVNAME=/dev/ram0
  E: DEVTYPE=disk
  E: SUBSYSTEM=block
  
  P: /devices/virtual/block/ram1
  N: ram1
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/block/ram1
  E: MAJOR=1
  E: MINOR=1
  E: DEVNAME=/dev/ram1
  E: DEVTYPE=disk
  E: SUBSYSTEM=block
  
  P: /devices/virtual/block/ram10
  N: ram10
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/block/ram10
  E: MAJOR=1
  E: MINOR=10
  E: DEVNAME=/dev/ram10
  E: DEVTYPE=disk
  E: SUBSYSTEM=block
  
  P: /devices/virtual/block/ram11
  N: ram11
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/block/ram11
  E: MAJOR=1
  E: MINOR=11
  E: DEVNAME=/dev/ram11
  E: DEVTYPE=disk
  E: SUBSYSTEM=block
  
  P: /devices/virtual/block/ram12
  N: ram12
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/block/ram12
  E: MAJOR=1
  E: MINOR=12
  E: DEVNAME=/dev/ram12
  E: DEVTYPE=disk
  E: SUBSYSTEM=block
  
  P: /devices/virtual/block/ram13
  N: ram13
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/block/ram13
  E: MAJOR=1
  E: MINOR=13
  E: DEVNAME=/dev/ram13
  E: DEVTYPE=disk
  E: SUBSYSTEM=block
  
  P: /devices/virtual/block/ram14
  N: ram14
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/block/ram14
  E: MAJOR=1
  E: MINOR=14
  E: DEVNAME=/dev/ram14
  E: DEVTYPE=disk
  E: SUBSYSTEM=block
  
  P: /devices/virtual/block/ram15
  N: ram15
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/block/ram15
  E: MAJOR=1
  E: MINOR=15
  E: DEVNAME=/dev/ram15
  E: DEVTYPE=disk
  E: SUBSYSTEM=block
  
  P: /devices/virtual/block/ram2
  N: ram2
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/block/ram2
  E: MAJOR=1
  E: MINOR=2
  E: DEVNAME=/dev/ram2
  E: DEVTYPE=disk
  E: SUBSYSTEM=block
  
  P: /devices/virtual/block/ram3
  N: ram3
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/block/ram3
  E: MAJOR=1
  E: MINOR=3
  E: DEVNAME=/dev/ram3
  E: DEVTYPE=disk
  E: SUBSYSTEM=block
  
  P: /devices/virtual/block/ram4
  N: ram4
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/block/ram4
  E: MAJOR=1
  E: MINOR=4
  E: DEVNAME=/dev/ram4
  E: DEVTYPE=disk
  E: SUBSYSTEM=block
  
  P: /devices/virtual/block/ram5
  N: ram5
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/block/ram5
  E: MAJOR=1
  E: MINOR=5
  E: DEVNAME=/dev/ram5
  E: DEVTYPE=disk
  E: SUBSYSTEM=block
  
  P: /devices/virtual/block/ram6
  N: ram6
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/block/ram6
  E: MAJOR=1
  E: MINOR=6
  E: DEVNAME=/dev/ram6
  E: DEVTYPE=disk
  E: SUBSYSTEM=block
  
  P: /devices/virtual/block/ram7
  N: ram7
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/block/ram7
  E: MAJOR=1
  E: MINOR=7
  E: DEVNAME=/dev/ram7
  E: DEVTYPE=disk
  E: SUBSYSTEM=block
  
  P: /devices/virtual/block/ram8
  N: ram8
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/block/ram8
  E: MAJOR=1
  E: MINOR=8
  E: DEVNAME=/dev/ram8
  E: DEVTYPE=disk
  E: SUBSYSTEM=block
  
  P: /devices/virtual/block/ram9
  N: ram9
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/block/ram9
  E: MAJOR=1
  E: MINOR=9
  E: DEVNAME=/dev/ram9
  E: DEVTYPE=disk
  E: SUBSYSTEM=block
  
  P: /devices/virtual/dmi/id
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/dmi/id
  E: MODALIAS=dmi:bvnDellInc.:bvrA19:bd12/21/2009:svnDellInc.:pnLatitudeE6500:pvr:rvnDellInc.:rn0F328M:rvr:cvnDellInc.:ct8:cvr:
  E: SUBSYSTEM=dmi
  
  P: /devices/virtual/graphics/fbcon
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/graphics/fbcon
  E: SUBSYSTEM=graphics
  
  P: /devices/virtual/hwmon/hwmon0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/hwmon/hwmon0
  E: SUBSYSTEM=hwmon
  
  P: /devices/virtual/input/input7
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/input/input7
  E: PRODUCT=19/0/0/0
  E: NAME="Dell WMI hotkeys"
  E: PHYS="wmi/input0"
  E: PROP=0
  E: EV=13
  E: KEY=1101b00000400 100000 e000000000000 0
  E: MSC=10
  E: MODALIAS=input:b0019v0000p0000e0000-e0,1,4,k71,72,73,94,CA,E0,E1,E3,E4,EC,F0,ram4,lsfw
  E: SUBSYSTEM=input
  E: ID_INPUT=1
  E: ID_INPUT_KEY=1
  
  P: /devices/virtual/input/input7/event7
  N: input/event7
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/input/input7/event7
  E: MAJOR=13
  E: MINOR=71
  E: DEVNAME=/dev/input/event7
  E: SUBSYSTEM=input
  E: ID_INPUT=1
  E: ID_INPUT_KEY=1
  E: XKBMODEL=pc105
  E: XKBLAYOUT=us
  E: DMI_VENDOR=Dell Inc.
  
  P: /devices/virtual/input/mice
  N: input/mice
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/input/mice
  E: MAJOR=13
  E: MINOR=63
  E: DEVNAME=/dev/input/mice
  E: SUBSYSTEM=input
  
  P: /devices/virtual/mem/full
  N: full
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/mem/full
  E: MAJOR=1
  E: MINOR=7
  E: DEVNAME=/dev/full
  E: DEVMODE=0666
  E: SUBSYSTEM=mem
  
  P: /devices/virtual/mem/kmsg
  N: kmsg
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/mem/kmsg
  E: MAJOR=1
  E: MINOR=11
  E: DEVNAME=/dev/kmsg
  E: SUBSYSTEM=mem
  
  P: /devices/virtual/mem/mem
  N: mem
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/mem/mem
  E: MAJOR=1
  E: MINOR=1
  E: DEVNAME=/dev/mem
  E: SUBSYSTEM=mem
  
  P: /devices/virtual/mem/null
  N: null
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/mem/null
  E: MAJOR=1
  E: MINOR=3
  E: DEVNAME=/dev/null
  E: DEVMODE=0666
  E: SUBSYSTEM=mem
  
  P: /devices/virtual/mem/oldmem
  N: oldmem
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/mem/oldmem
  E: MAJOR=1
  E: MINOR=12
  E: DEVNAME=/dev/oldmem
  E: SUBSYSTEM=mem
  
  P: /devices/virtual/mem/port
  N: port
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/mem/port
  E: MAJOR=1
  E: MINOR=4
  E: DEVNAME=/dev/port
  E: SUBSYSTEM=mem
  
  P: /devices/virtual/mem/random
  N: random
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/mem/random
  E: MAJOR=1
  E: MINOR=8
  E: DEVNAME=/dev/random
  E: DEVMODE=0666
  E: SUBSYSTEM=mem
  
  P: /devices/virtual/mem/urandom
  N: urandom
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/mem/urandom
  E: MAJOR=1
  E: MINOR=9
  E: DEVNAME=/dev/urandom
  E: DEVMODE=0666
  E: SUBSYSTEM=mem
  
  P: /devices/virtual/mem/zero
  N: zero
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/mem/zero
  E: MAJOR=1
  E: MINOR=5
  E: DEVNAME=/dev/zero
  E: DEVMODE=0666
  E: SUBSYSTEM=mem
  
  P: /devices/virtual/misc/agpgart
  N: agpgart
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/misc/agpgart
  E: MAJOR=10
  E: MINOR=175
  E: DEVNAME=/dev/agpgart
  E: SUBSYSTEM=misc
  
  P: /devices/virtual/misc/cpu_dma_latency
  N: cpu_dma_latency
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/misc/cpu_dma_latency
  E: MAJOR=10
  E: MINOR=60
  E: DEVNAME=/dev/cpu_dma_latency
  E: SUBSYSTEM=misc
  
  P: /devices/virtual/misc/device-mapper
  N: mapper/control
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/misc/device-mapper
  E: MAJOR=10
  E: MINOR=236
  E: DEVNAME=/dev/mapper/control
  E: SUBSYSTEM=misc
  
  P: /devices/virtual/misc/ecryptfs
  N: ecryptfs
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/misc/ecryptfs
  E: MAJOR=10
  E: MINOR=61
  E: DEVNAME=/dev/ecryptfs
  E: SUBSYSTEM=misc
  
  P: /devices/virtual/misc/fuse
  N: fuse
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/misc/fuse
  E: MAJOR=10
  E: MINOR=229
  E: DEVNAME=/dev/fuse
  E: SUBSYSTEM=misc
  
  P: /devices/virtual/misc/hpet
  N: hpet
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/misc/hpet
  E: MAJOR=10
  E: MINOR=228
  E: DEVNAME=/dev/hpet
  E: SUBSYSTEM=misc
  
  P: /devices/virtual/misc/mcelog
  N: mcelog
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/misc/mcelog
  E: MAJOR=10
  E: MINOR=227
  E: DEVNAME=/dev/mcelog
  E: SUBSYSTEM=misc
  
  P: /devices/virtual/misc/network_latency
  N: network_latency
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/misc/network_latency
  E: MAJOR=10
  E: MINOR=59
  E: DEVNAME=/dev/network_latency
  E: SUBSYSTEM=misc
  
  P: /devices/virtual/misc/network_throughput
  N: network_throughput
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/misc/network_throughput
  E: MAJOR=10
  E: MINOR=58
  E: DEVNAME=/dev/network_throughput
  E: SUBSYSTEM=misc
  
  P: /devices/virtual/misc/psaux
  N: psaux
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/misc/psaux
  E: MAJOR=10
  E: MINOR=1
  E: DEVNAME=/dev/psaux
  E: SUBSYSTEM=misc
  
  P: /devices/virtual/misc/rfkill
  N: rfkill
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/misc/rfkill
  E: MAJOR=10
  E: MINOR=62
  E: DEVNAME=/dev/rfkill
  E: SUBSYSTEM=misc
  
  P: /devices/virtual/misc/snapshot
  N: snapshot
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/misc/snapshot
  E: MAJOR=10
  E: MINOR=231
  E: DEVNAME=/dev/snapshot
  E: SUBSYSTEM=misc
  
  P: /devices/virtual/misc/tun
  N: net/tun
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/misc/tun
  E: MAJOR=10
  E: MINOR=200
  E: DEVNAME=/dev/net/tun
  E: SUBSYSTEM=misc
  
  P: /devices/virtual/misc/uinput
  N: uinput
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/misc/uinput
  E: MAJOR=10
  E: MINOR=223
  E: DEVNAME=/dev/uinput
  E: SUBSYSTEM=misc
  
  P: /devices/virtual/misc/vboxdrv
  N: vboxdrv
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/misc/vboxdrv
  E: MAJOR=10
  E: MINOR=57
  E: DEVNAME=/dev/vboxdrv
  E: SUBSYSTEM=misc
  
  P: /devices/virtual/misc/vboxnetctl
  N: vboxnetctl
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/misc/vboxnetctl
  E: MAJOR=10
  E: MINOR=56
  E: DEVNAME=/dev/vboxnetctl
  E: SUBSYSTEM=misc
  
  P: /devices/virtual/misc/vga_arbiter
  N: vga_arbiter
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/misc/vga_arbiter
  E: MAJOR=10
  E: MINOR=63
  E: DEVNAME=/dev/vga_arbiter
  E: SUBSYSTEM=misc
  
  P: /devices/virtual/net/lo
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/net/lo
  E: INTERFACE=lo
  E: IFINDEX=1
  E: SUBSYSTEM=net
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/ppp/ppp
  N: ppp
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/ppp/ppp
  E: MAJOR=108
  E: MINOR=0
  E: DEVNAME=/dev/ppp
  E: SUBSYSTEM=ppp
  
  P: /devices/virtual/regulator/regulator.0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/regulator/regulator.0
  E: SUBSYSTEM=regulator
  
  P: /devices/virtual/sound/seq
  N: snd/seq
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/sound/seq
  E: MAJOR=116
  E: MINOR=1
  E: DEVNAME=/dev/snd/seq
  E: SUBSYSTEM=sound
  E: TAGS=:udev-acl:
  
  P: /devices/virtual/sound/timer
  N: snd/timer
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/sound/timer
  E: MAJOR=116
  E: MINOR=33
  E: DEVNAME=/dev/snd/timer
  E: SUBSYSTEM=sound
  E: TAGS=:udev-acl:
  
  P: /devices/virtual/thermal/cooling_device0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/thermal/cooling_device0
  E: SUBSYSTEM=thermal
  
  P: /devices/virtual/thermal/cooling_device1
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/thermal/cooling_device1
  E: SUBSYSTEM=thermal
  
  P: /devices/virtual/thermal/cooling_device2
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/thermal/cooling_device2
  E: SUBSYSTEM=thermal
  
  P: /devices/virtual/thermal/thermal_zone0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/thermal/thermal_zone0
  E: SUBSYSTEM=thermal
  
  P: /devices/virtual/tty/console
  N: console
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/console
  E: MAJOR=5
  E: MINOR=1
  E: DEVNAME=/dev/console
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/ptmx
  N: ptmx
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/ptmx
  E: MAJOR=5
  E: MINOR=2
  E: DEVNAME=/dev/ptmx
  E: DEVMODE=0666
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty
  N: tty
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty
  E: MAJOR=5
  E: MINOR=0
  E: DEVNAME=/dev/tty
  E: DEVMODE=0666
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty0
  N: tty0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty0
  E: MAJOR=4
  E: MINOR=0
  E: DEVNAME=/dev/tty0
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty1
  N: tty1
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty1
  E: MAJOR=4
  E: MINOR=1
  E: DEVNAME=/dev/tty1
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty10
  N: tty10
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty10
  E: MAJOR=4
  E: MINOR=10
  E: DEVNAME=/dev/tty10
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty11
  N: tty11
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty11
  E: MAJOR=4
  E: MINOR=11
  E: DEVNAME=/dev/tty11
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty12
  N: tty12
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty12
  E: MAJOR=4
  E: MINOR=12
  E: DEVNAME=/dev/tty12
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty13
  N: tty13
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty13
  E: MAJOR=4
  E: MINOR=13
  E: DEVNAME=/dev/tty13
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty14
  N: tty14
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty14
  E: MAJOR=4
  E: MINOR=14
  E: DEVNAME=/dev/tty14
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty15
  N: tty15
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty15
  E: MAJOR=4
  E: MINOR=15
  E: DEVNAME=/dev/tty15
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty16
  N: tty16
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty16
  E: MAJOR=4
  E: MINOR=16
  E: DEVNAME=/dev/tty16
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty17
  N: tty17
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty17
  E: MAJOR=4
  E: MINOR=17
  E: DEVNAME=/dev/tty17
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty18
  N: tty18
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty18
  E: MAJOR=4
  E: MINOR=18
  E: DEVNAME=/dev/tty18
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty19
  N: tty19
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty19
  E: MAJOR=4
  E: MINOR=19
  E: DEVNAME=/dev/tty19
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty2
  N: tty2
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty2
  E: MAJOR=4
  E: MINOR=2
  E: DEVNAME=/dev/tty2
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty20
  N: tty20
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty20
  E: MAJOR=4
  E: MINOR=20
  E: DEVNAME=/dev/tty20
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty21
  N: tty21
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty21
  E: MAJOR=4
  E: MINOR=21
  E: DEVNAME=/dev/tty21
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty22
  N: tty22
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty22
  E: MAJOR=4
  E: MINOR=22
  E: DEVNAME=/dev/tty22
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty23
  N: tty23
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty23
  E: MAJOR=4
  E: MINOR=23
  E: DEVNAME=/dev/tty23
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty24
  N: tty24
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty24
  E: MAJOR=4
  E: MINOR=24
  E: DEVNAME=/dev/tty24
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty25
  N: tty25
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty25
  E: MAJOR=4
  E: MINOR=25
  E: DEVNAME=/dev/tty25
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty26
  N: tty26
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty26
  E: MAJOR=4
  E: MINOR=26
  E: DEVNAME=/dev/tty26
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty27
  N: tty27
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty27
  E: MAJOR=4
  E: MINOR=27
  E: DEVNAME=/dev/tty27
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty28
  N: tty28
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty28
  E: MAJOR=4
  E: MINOR=28
  E: DEVNAME=/dev/tty28
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty29
  N: tty29
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty29
  E: MAJOR=4
  E: MINOR=29
  E: DEVNAME=/dev/tty29
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty3
  N: tty3
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty3
  E: MAJOR=4
  E: MINOR=3
  E: DEVNAME=/dev/tty3
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty30
  N: tty30
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty30
  E: MAJOR=4
  E: MINOR=30
  E: DEVNAME=/dev/tty30
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty31
  N: tty31
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty31
  E: MAJOR=4
  E: MINOR=31
  E: DEVNAME=/dev/tty31
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty32
  N: tty32
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty32
  E: MAJOR=4
  E: MINOR=32
  E: DEVNAME=/dev/tty32
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty33
  N: tty33
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty33
  E: MAJOR=4
  E: MINOR=33
  E: DEVNAME=/dev/tty33
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty34
  N: tty34
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty34
  E: MAJOR=4
  E: MINOR=34
  E: DEVNAME=/dev/tty34
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty35
  N: tty35
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty35
  E: MAJOR=4
  E: MINOR=35
  E: DEVNAME=/dev/tty35
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty36
  N: tty36
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty36
  E: MAJOR=4
  E: MINOR=36
  E: DEVNAME=/dev/tty36
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty37
  N: tty37
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty37
  E: MAJOR=4
  E: MINOR=37
  E: DEVNAME=/dev/tty37
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty38
  N: tty38
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty38
  E: MAJOR=4
  E: MINOR=38
  E: DEVNAME=/dev/tty38
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty39
  N: tty39
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty39
  E: MAJOR=4
  E: MINOR=39
  E: DEVNAME=/dev/tty39
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty4
  N: tty4
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty4
  E: MAJOR=4
  E: MINOR=4
  E: DEVNAME=/dev/tty4
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty40
  N: tty40
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty40
  E: MAJOR=4
  E: MINOR=40
  E: DEVNAME=/dev/tty40
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty41
  N: tty41
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty41
  E: MAJOR=4
  E: MINOR=41
  E: DEVNAME=/dev/tty41
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty42
  N: tty42
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty42
  E: MAJOR=4
  E: MINOR=42
  E: DEVNAME=/dev/tty42
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty43
  N: tty43
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty43
  E: MAJOR=4
  E: MINOR=43
  E: DEVNAME=/dev/tty43
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty44
  N: tty44
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty44
  E: MAJOR=4
  E: MINOR=44
  E: DEVNAME=/dev/tty44
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty45
  N: tty45
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty45
  E: MAJOR=4
  E: MINOR=45
  E: DEVNAME=/dev/tty45
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty46
  N: tty46
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty46
  E: MAJOR=4
  E: MINOR=46
  E: DEVNAME=/dev/tty46
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty47
  N: tty47
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty47
  E: MAJOR=4
  E: MINOR=47
  E: DEVNAME=/dev/tty47
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty48
  N: tty48
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty48
  E: MAJOR=4
  E: MINOR=48
  E: DEVNAME=/dev/tty48
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty49
  N: tty49
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty49
  E: MAJOR=4
  E: MINOR=49
  E: DEVNAME=/dev/tty49
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty5
  N: tty5
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty5
  E: MAJOR=4
  E: MINOR=5
  E: DEVNAME=/dev/tty5
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty50
  N: tty50
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty50
  E: MAJOR=4
  E: MINOR=50
  E: DEVNAME=/dev/tty50
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty51
  N: tty51
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty51
  E: MAJOR=4
  E: MINOR=51
  E: DEVNAME=/dev/tty51
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty52
  N: tty52
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty52
  E: MAJOR=4
  E: MINOR=52
  E: DEVNAME=/dev/tty52
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty53
  N: tty53
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty53
  E: MAJOR=4
  E: MINOR=53
  E: DEVNAME=/dev/tty53
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty54
  N: tty54
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty54
  E: MAJOR=4
  E: MINOR=54
  E: DEVNAME=/dev/tty54
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty55
  N: tty55
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty55
  E: MAJOR=4
  E: MINOR=55
  E: DEVNAME=/dev/tty55
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty56
  N: tty56
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty56
  E: MAJOR=4
  E: MINOR=56
  E: DEVNAME=/dev/tty56
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty57
  N: tty57
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty57
  E: MAJOR=4
  E: MINOR=57
  E: DEVNAME=/dev/tty57
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty58
  N: tty58
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty58
  E: MAJOR=4
  E: MINOR=58
  E: DEVNAME=/dev/tty58
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty59
  N: tty59
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty59
  E: MAJOR=4
  E: MINOR=59
  E: DEVNAME=/dev/tty59
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty6
  N: tty6
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty6
  E: MAJOR=4
  E: MINOR=6
  E: DEVNAME=/dev/tty6
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty60
  N: tty60
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty60
  E: MAJOR=4
  E: MINOR=60
  E: DEVNAME=/dev/tty60
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty61
  N: tty61
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty61
  E: MAJOR=4
  E: MINOR=61
  E: DEVNAME=/dev/tty61
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty62
  N: tty62
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty62
  E: MAJOR=4
  E: MINOR=62
  E: DEVNAME=/dev/tty62
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty63
  N: tty63
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty63
  E: MAJOR=4
  E: MINOR=63
  E: DEVNAME=/dev/tty63
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty7
  N: tty7
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty7
  E: MAJOR=4
  E: MINOR=7
  E: DEVNAME=/dev/tty7
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty8
  N: tty8
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty8
  E: MAJOR=4
  E: MINOR=8
  E: DEVNAME=/dev/tty8
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty9
  N: tty9
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty9
  E: MAJOR=4
  E: MINOR=9
  E: DEVNAME=/dev/tty9
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/ttyprintk
  N: ttyprintk
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/ttyprintk
  E: MAJOR=5
  E: MINOR=3
  E: DEVNAME=/dev/ttyprintk
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/usbmon/usbmon0
  N: usbmon0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/usbmon/usbmon0
  E: MAJOR=252
  E: MINOR=0
  E: DEVNAME=/dev/usbmon0
  E: SUBSYSTEM=usbmon
  
  P: /devices/virtual/vc/vcs
  N: vcs
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/vc/vcs
  E: MAJOR=7
  E: MINOR=0
  E: DEVNAME=/dev/vcs
  E: SUBSYSTEM=vc
  
  P: /devices/virtual/vc/vcs1
  N: vcs1
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/vc/vcs1
  E: MAJOR=7
  E: MINOR=1
  E: DEVNAME=/dev/vcs1
  E: SUBSYSTEM=vc
  
  P: /devices/virtual/vc/vcs2
  N: vcs2
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/vc/vcs2
  E: MAJOR=7
  E: MINOR=2
  E: DEVNAME=/dev/vcs2
  E: SUBSYSTEM=vc
  
  P: /devices/virtual/vc/vcs3
  N: vcs3
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/vc/vcs3
  E: MAJOR=7
  E: MINOR=3
  E: DEVNAME=/dev/vcs3
  E: SUBSYSTEM=vc
  
  P: /devices/virtual/vc/vcs4
  N: vcs4
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/vc/vcs4
  E: MAJOR=7
  E: MINOR=4
  E: DEVNAME=/dev/vcs4
  E: SUBSYSTEM=vc
  
  P: /devices/virtual/vc/vcs5
  N: vcs5
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/vc/vcs5
  E: MAJOR=7
  E: MINOR=5
  E: DEVNAME=/dev/vcs5
  E: SUBSYSTEM=vc
  
  P: /devices/virtual/vc/vcs6
  N: vcs6
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/vc/vcs6
  E: MAJOR=7
  E: MINOR=6
  E: DEVNAME=/dev/vcs6
  E: SUBSYSTEM=vc
  
  P: /devices/virtual/vc/vcsa
  N: vcsa
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/vc/vcsa
  E: MAJOR=7
  E: MINOR=128
  E: DEVNAME=/dev/vcsa
  E: SUBSYSTEM=vc
  
  P: /devices/virtual/vc/vcsa1
  N: vcsa1
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/vc/vcsa1
  E: MAJOR=7
  E: MINOR=129
  E: DEVNAME=/dev/vcsa1
  E: SUBSYSTEM=vc
  
  P: /devices/virtual/vc/vcsa2
  N: vcsa2
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/vc/vcsa2
  E: MAJOR=7
  E: MINOR=130
  E: DEVNAME=/dev/vcsa2
  E: SUBSYSTEM=vc
  
  P: /devices/virtual/vc/vcsa3
  N: vcsa3
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/vc/vcsa3
  E: MAJOR=7
  E: MINOR=131
  E: DEVNAME=/dev/vcsa3
  E: SUBSYSTEM=vc
  
  P: /devices/virtual/vc/vcsa4
  N: vcsa4
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/vc/vcsa4
  E: MAJOR=7
  E: MINOR=132
  E: DEVNAME=/dev/vcsa4
  E: SUBSYSTEM=vc
  
  P: /devices/virtual/vc/vcsa5
  N: vcsa5
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/vc/vcsa5
  E: MAJOR=7
  E: MINOR=133
  E: DEVNAME=/dev/vcsa5
  E: SUBSYSTEM=vc
  
  P: /devices/virtual/vc/vcsa6
  N: vcsa6
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/vc/vcsa6
  E: MAJOR=7
  E: MINOR=134
  E: DEVNAME=/dev/vcsa6
  E: SUBSYSTEM=vc
  
  P: /devices/virtual/vtconsole/vtcon0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/vtconsole/vtcon0
  E: SUBSYSTEM=vtconsole
  
  P: /devices/virtual/vtconsole/vtcon1
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/vtconsole/vtcon1
  E: SUBSYSTEM=vtconsole
  
  P: /devices/virtual/wmi/05901221-D566-11D1-B2F0-00A0C9062910
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/wmi/05901221-D566-11D1-B2F0-00A0C9062910
  E: MODALIAS=wmi:05901221-D566-11D1-B2F0-00A0C9062910
  E: SUBSYSTEM=wmi
  
  P: /devices/virtual/wmi/77BD0728-2E34-478C-B625-67F02A7E4897
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/wmi/77BD0728-2E34-478C-B625-67F02A7E4897
  E: MODALIAS=wmi:77BD0728-2E34-478C-B625-67F02A7E4897
  E: SUBSYSTEM=wmi
  
  P: /devices/virtual/wmi/8D9DDCBC-A997-11DA-B012-B622A1EF5492
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/wmi/8D9DDCBC-A997-11DA-B012-B622A1EF5492
  E: MODALIAS=wmi:8D9DDCBC-A997-11DA-B012-B622A1EF5492
  E: SUBSYSTEM=wmi
  
  P: /devices/virtual/wmi/9DBB5994-A997-11DA-B012-B622A1EF5492
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/wmi/9DBB5994-A997-11DA-B012-B622A1EF5492
  E: MODALIAS=wmi:9DBB5994-A997-11DA-B012-B622A1EF5492
  E: SUBSYSTEM=wmi
  
  P: /devices/virtual/wmi/A3776CE0-1E88-11DB-A98B-0800200C9A66
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/wmi/A3776CE0-1E88-11DB-A98B-0800200C9A66
  E: MODALIAS=wmi:A3776CE0-1E88-11DB-A98B-0800200C9A66
  E: SUBSYSTEM=wmi
  
  P: /devices/virtual/wmi/A80593CE-A997-11DA-B012-B622A1EF5492
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/wmi/A80593CE-A997-11DA-B012-B622A1EF5492
  E: MODALIAS=wmi:A80593CE-A997-11DA-B012-B622A1EF5492
  E: SUBSYSTEM=wmi
  
-----  udevinfo end -----
/devices/LNXSYSTM:00
/devices/LNXSYSTM:00/LNXCPU:00
/devices/LNXSYSTM:00/LNXCPU:01
/devices/LNXSYSTM:00/LNXCPU:02
/devices/LNXSYSTM:00/LNXCPU:03
/devices/LNXSYSTM:00/device:00
/devices/LNXSYSTM:00/device:00/ACPI0003:00
/devices/LNXSYSTM:00/device:00/ACPI0003:00/power_supply/AC
/devices/LNXSYSTM:00/device:00/PNP0A03:00
/devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:01
/devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:01/device:3d
/devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:01/device:3e
/devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:01/device:3f
/devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:01/device:40
/devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:01/device:41
/devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:01/device:42
/devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:01/input/input11
/devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:01/input/input11/event10
  name: /dev/input/event10
/devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:02
/devices/LNXSYSTM:00/device:00/PNP0A03:00/PNP0C01:02
/devices/LNXSYSTM:00/device:00/PNP0A03:00/PNP0C01:03
/devices/LNXSYSTM:00/device:00/PNP0A03:00/PNP0C0F:00
/devices/LNXSYSTM:00/device:00/PNP0A03:00/PNP0C0F:01
/devices/LNXSYSTM:00/device:00/PNP0A03:00/PNP0C0F:02
/devices/LNXSYSTM:00/device:00/PNP0A03:00/PNP0C0F:03
/devices/LNXSYSTM:00/device:00/PNP0A03:00/PNP0C0F:04
/devices/LNXSYSTM:00/device:00/PNP0A03:00/PNP0C0F:05
/devices/LNXSYSTM:00/device:00/PNP0A03:00/PNP0C0F:06
/devices/LNXSYSTM:00/device:00/PNP0A03:00/PNP0C0F:07
/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:01
/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:01/PNP0000:00
/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:01/PNP0100:00
/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:01/PNP0103:00
/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:01/PNP0200:00
/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:01/PNP0303:00
/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:01/PNP0401:00
/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:01/PNP0501:00
/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:01/PNP0800:00
/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:01/PNP0B00:00
/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:01/PNP0C01:00
/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:01/PNP0C01:01
/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:01/PNP0C04:00
/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:01/PNP0C09:00
/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:01/PNP0F13:00
/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:02
/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:02/device:03
/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:02/device:04
/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:05
/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:05/device:06
/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:05/device:06/device:07
/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:05/device:06/device:08
/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:09
/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:09/device:0a
/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:09/device:0a/device:0b
/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:09/device:0a/device:0c
/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:0d
/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:0d/device:0e
/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:0d/device:0e/device:0f
/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:0d/device:0e/device:10
/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:11
/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:11/device:12
/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:11/device:12/device:13
/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:11/device:12/device:14
/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:15
/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:15/device:16
/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:15/device:16/device:17
/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:15/device:16/device:18
/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:19
/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:19/device:1a
/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:19/device:1a/device:1b
/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:19/device:1a/device:1c
/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:1d
/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:1d/device:1e
/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:1d/device:1e/device:1f
/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:1d/device:1e/device:20
/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:1d/device:1e/device:21
/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:1d/device:1e/device:22
/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:1d/device:1e/device:23
/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:1d/device:1e/device:24
/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:25
/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:25/device:26
/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:25/device:26/device:27
/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:25/device:26/device:28
/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:25/device:26/device:29
/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:25/device:26/device:2a
/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:25/device:26/device:2b
/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:25/device:26/device:2c
/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:2d
/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:2d/device:2e
/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:2d/device:2f
/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:2d/device:2f/device:30
/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:31
/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:31/device:32
/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:31/device:32/device:33
/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:31/device:34
/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:35
/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:36
/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:36/LNXVIDEO:00
/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:36/LNXVIDEO:00/device:37
/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:36/LNXVIDEO:00/device:38
/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:36/LNXVIDEO:00/device:39
/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:36/LNXVIDEO:00/device:3a
/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:36/LNXVIDEO:00/device:3b
/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:36/LNXVIDEO:00/device:3c
/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:43
/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:43/device:44
/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:45
/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:45/device:46
/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:47
/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:47/device:48
/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:49
/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:49/device:4a
/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:4b
/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:4b/device:4c
/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:4d
/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:4d/device:4e
/devices/LNXSYSTM:00/device:00/PNP0C01:04
/devices/LNXSYSTM:00/device:00/PNP0C0A:00
/devices/LNXSYSTM:00/device:00/PNP0C0A:00/power_supply/BAT0
/devices/LNXSYSTM:00/device:00/PNP0C0A:01
/devices/LNXSYSTM:00/device:00/PNP0C0C:00
/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1/event1
  name: /dev/input/event1
/devices/LNXSYSTM:00/device:00/PNP0C0D:00
/devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
/devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0/event0
  name: /dev/input/event0
/devices/LNXSYSTM:00/device:00/PNP0C0E:00
/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2/event2
  name: /dev/input/event2
/devices/LNXSYSTM:00/device:00/PNP0C14:00
/devices/LNXSYSTM:00/device:4f
/devices/LNXSYSTM:00/device:4f/LNXTHERM:00
/devices/breakpoint
/devices/cpu
/devices/pci0000:00/0000:00:00.0
/devices/pci0000:00/0000:00:02.0
/devices/pci0000:00/0000:00:02.0/backlight/acpi_video0
/devices/pci0000:00/0000:00:02.0/drm/card0
  name: /dev/dri/card0
/devices/pci0000:00/0000:00:02.0/drm/card0/card0-DP-1
/devices/pci0000:00/0000:00:02.0/drm/card0/card0-DP-1/i2c-14
/devices/pci0000:00/0000:00:02.0/drm/card0/card0-DP-2
/devices/pci0000:00/0000:00:02.0/drm/card0/card0-DP-2/i2c-15
/devices/pci0000:00/0000:00:02.0/drm/card0/card0-DP-3
/devices/pci0000:00/0000:00:02.0/drm/card0/card0-DP-3/i2c-16
/devices/pci0000:00/0000:00:02.0/drm/card0/card0-HDMI-A-1
/devices/pci0000:00/0000:00:02.0/drm/card0/card0-HDMI-A-2
/devices/pci0000:00/0000:00:02.0/drm/card0/card0-LVDS-1
/devices/pci0000:00/0000:00:02.0/drm/card0/card0-LVDS-1/intel_backlight
/devices/pci0000:00/0000:00:02.0/drm/card0/card0-SVIDEO-1
/devices/pci0000:00/0000:00:02.0/drm/card0/card0-VGA-1
/devices/pci0000:00/0000:00:02.0/drm/controlD64
  name: /dev/dri/controlD64
/devices/pci0000:00/0000:00:02.0/graphics/fb0
  name: /dev/fb0
/devices/pci0000:00/0000:00:02.0/i2c-0
/devices/pci0000:00/0000:00:02.0/i2c-1
/devices/pci0000:00/0000:00:02.0/i2c-10
/devices/pci0000:00/0000:00:02.0/i2c-11
/devices/pci0000:00/0000:00:02.0/i2c-12
/devices/pci0000:00/0000:00:02.0/i2c-13
/devices/pci0000:00/0000:00:02.0/i2c-2
/devices/pci0000:00/0000:00:02.0/i2c-3
/devices/pci0000:00/0000:00:02.0/i2c-4
/devices/pci0000:00/0000:00:02.0/i2c-5
/devices/pci0000:00/0000:00:02.0/i2c-6
/devices/pci0000:00/0000:00:02.0/i2c-7
/devices/pci0000:00/0000:00:02.0/i2c-8
/devices/pci0000:00/0000:00:02.0/i2c-9
/devices/pci0000:00/0000:00:02.1
/devices/pci0000:00/0000:00:19.0
/devices/pci0000:00/0000:00:19.0/net/eth0
/devices/pci0000:00/0000:00:1a.0
/devices/pci0000:00/0000:00:1a.0/usb3
  name: /dev/bus/usb/003/001
/devices/pci0000:00/0000:00:1a.0/usb3/3-0:1.0
/devices/pci0000:00/0000:00:1a.0/usb3/3-1
  name: /dev/bus/usb/003/002
/devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1.1
  name: /dev/bus/usb/003/003
/devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1.1/3-1.1:1.0
/devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1.1/3-1.1:1.0/0003:413C:8157.0002
/devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1.1/3-1.1:1.0/0003:413C:8157.0002/hidraw/hidraw1
  name: /dev/hidraw1
/devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1.1/3-1.1:1.0/input/input5
/devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1.1/3-1.1:1.0/input/input5/event5
  name: /dev/input/event5
  links: /dev/input/by-id/usb-413c_8157-event-kbd, /dev/input/by-path/pci-0000:00:1a.0-usb-0:1.1:1.0-event-kbd
/devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1.2
  name: /dev/bus/usb/003/004
/devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1.2/3-1.2:1.0
/devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1:1.0
/devices/pci0000:00/0000:00:1a.0/usbmon/usbmon3
  name: /dev/usbmon3
/devices/pci0000:00/0000:00:1a.1
/devices/pci0000:00/0000:00:1a.1/usb4
  name: /dev/bus/usb/004/001
/devices/pci0000:00/0000:00:1a.1/usb4/4-0:1.0
/devices/pci0000:00/0000:00:1a.1/usbmon/usbmon4
  name: /dev/usbmon4
/devices/pci0000:00/0000:00:1a.2
/devices/pci0000:00/0000:00:1a.2/usb5
  name: /dev/bus/usb/005/001
/devices/pci0000:00/0000:00:1a.2/usb5/5-0:1.0
/devices/pci0000:00/0000:00:1a.2/usb5/5-1
  name: /dev/bus/usb/005/002
/devices/pci0000:00/0000:00:1a.2/usb5/5-1/5-1:0.0
/devices/pci0000:00/0000:00:1a.2/usb5/5-1/5-1:0.1
/devices/pci0000:00/0000:00:1a.2/usbmon/usbmon5
  name: /dev/usbmon5
/devices/pci0000:00/0000:00:1a.7
/devices/pci0000:00/0000:00:1a.7/usb1
  name: /dev/bus/usb/001/001
/devices/pci0000:00/0000:00:1a.7/usb1/1-0:1.0
/devices/pci0000:00/0000:00:1a.7/usb1/1-3
  name: /dev/bus/usb/001/003
/devices/pci0000:00/0000:00:1a.7/usb1/1-3/1-3.1
  name: /dev/bus/usb/001/007
/devices/pci0000:00/0000:00:1a.7/usb1/1-3/1-3.1/1-3.1.3
  name: /dev/bus/usb/001/010
/devices/pci0000:00/0000:00:1a.7/usb1/1-3/1-3.1/1-3.1.3/1-3.1.3:1.0
/devices/pci0000:00/0000:00:1a.7/usb1/1-3/1-3.1/1-3.1.3/1-3.1.3:1.0/host6
/devices/pci0000:00/0000:00:1a.7/usb1/1-3/1-3.1/1-3.1.3/1-3.1.3:1.0/host6/scsi_host/host6
/devices/pci0000:00/0000:00:1a.7/usb1/1-3/1-3.1/1-3.1.3/1-3.1.3:1.0/host6/target6:0:0
/devices/pci0000:00/0000:00:1a.7/usb1/1-3/1-3.1/1-3.1.3/1-3.1.3:1.0/host6/target6:0:0/6:0:0:0
/devices/pci0000:00/0000:00:1a.7/usb1/1-3/1-3.1/1-3.1.3/1-3.1.3:1.0/host6/target6:0:0/6:0:0:0/block/sdb
  name: /dev/sdb
  links: /dev/disk/by-id/ata-WDC_WD5000BMVV-11A1CS0_WD-WXM0A99S0731, /dev/disk/by-id/scsi-SWD_My_Passport_070WXM0A99S0731, /dev/disk/by-path/pci-0000:00:1a.7-usb-0:3.1.3:1.0-scsi-0:0:0:0, /dev/disk/by-id/wwn-0x50014ee2ae2b6104
/devices/pci0000:00/0000:00:1a.7/usb1/1-3/1-3.1/1-3.1.3/1-3.1.3:1.0/host6/target6:0:0/6:0:0:0/block/sdb/sdb1
  name: /dev/sdb1
  links: /dev/disk/by-id/ata-WDC_WD5000BMVV-11A1CS0_WD-WXM0A99S0731-part1, /dev/disk/by-id/scsi-SWD_My_Passport_070WXM0A99S0731-part1, /dev/disk/by-path/pci-0000:00:1a.7-usb-0:3.1.3:1.0-scsi-0:0:0:0-part1, /dev/disk/by-uuid/325220A852207331, /dev/disk/by-label/My\x20Passport, /dev/disk/by-id/wwn-0x50014ee2ae2b6104-part1
/devices/pci0000:00/0000:00:1a.7/usb1/1-3/1-3.1/1-3.1.3/1-3.1.3:1.0/host6/target6:0:0/6:0:0:0/bsg/6:0:0:0
  name: /dev/bsg/6:0:0:0
/devices/pci0000:00/0000:00:1a.7/usb1/1-3/1-3.1/1-3.1.3/1-3.1.3:1.0/host6/target6:0:0/6:0:0:0/scsi_device/6:0:0:0
/devices/pci0000:00/0000:00:1a.7/usb1/1-3/1-3.1/1-3.1.3/1-3.1.3:1.0/host6/target6:0:0/6:0:0:0/scsi_disk/6:0:0:0
/devices/pci0000:00/0000:00:1a.7/usb1/1-3/1-3.1/1-3.1.3/1-3.1.3:1.0/host6/target6:0:0/6:0:0:0/scsi_generic/sg2
  name: /dev/sg2
/devices/pci0000:00/0000:00:1a.7/usb1/1-3/1-3.1/1-3.1.3/1-3.1.3:1.0/host6/target6:0:0/6:0:0:1
/devices/pci0000:00/0000:00:1a.7/usb1/1-3/1-3.1/1-3.1.3/1-3.1.3:1.0/host6/target6:0:0/6:0:0:1/block/sr1
  name: /dev/sr1
  links: /dev/scd1, /dev/disk/by-id/usb-WD_Virtual_CD_070A_57584D304139395330373331-0:1, /dev/disk/by-path/pci-0000:00:1a.7-usb-0:3.1.3:1.0-scsi-0:0:0:1, /dev/disk/by-label/WD\x20SmartWare, /dev/cdrom
/devices/pci0000:00/0000:00:1a.7/usb1/1-3/1-3.1/1-3.1.3/1-3.1.3:1.0/host6/target6:0:0/6:0:0:1/bsg/6:0:0:1
  name: /dev/bsg/6:0:0:1
/devices/pci0000:00/0000:00:1a.7/usb1/1-3/1-3.1/1-3.1.3/1-3.1.3:1.0/host6/target6:0:0/6:0:0:1/scsi_device/6:0:0:1
/devices/pci0000:00/0000:00:1a.7/usb1/1-3/1-3.1/1-3.1.3/1-3.1.3:1.0/host6/target6:0:0/6:0:0:1/scsi_generic/sg3
  name: /dev/sg3
/devices/pci0000:00/0000:00:1a.7/usb1/1-3/1-3.1/1-3.1.3/1-3.1.3:1.0/host6/target6:0:0/6:0:0:2
/devices/pci0000:00/0000:00:1a.7/usb1/1-3/1-3.1/1-3.1.3/1-3.1.3:1.0/host6/target6:0:0/6:0:0:2/bsg/6:0:0:2
  name: /dev/bsg/6:0:0:2
/devices/pci0000:00/0000:00:1a.7/usb1/1-3/1-3.1/1-3.1.3/1-3.1.3:1.0/host6/target6:0:0/6:0:0:2/scsi_device/6:0:0:2
/devices/pci0000:00/0000:00:1a.7/usb1/1-3/1-3.1/1-3.1.3/1-3.1.3:1.0/host6/target6:0:0/6:0:0:2/scsi_generic/sg4
  name: /dev/sg4
/devices/pci0000:00/0000:00:1a.7/usb1/1-3/1-3.1/1-3.1:1.0
/devices/pci0000:00/0000:00:1a.7/usb1/1-3/1-3.2
  name: /dev/bus/usb/001/008
/devices/pci0000:00/0000:00:1a.7/usb1/1-3/1-3.2/1-3.2:1.0
/devices/pci0000:00/0000:00:1a.7/usb1/1-3/1-3:1.0
/devices/pci0000:00/0000:00:1a.7/usb1/1-4
  name: /dev/bus/usb/001/004
/devices/pci0000:00/0000:00:1a.7/usb1/1-4/1-4.2
  name: /dev/bus/usb/001/009
/devices/pci0000:00/0000:00:1a.7/usb1/1-4/1-4.2/1-4.2:1.0
/devices/pci0000:00/0000:00:1a.7/usb1/1-4/1-4.2/1-4.2:1.0/0003:046D:C016.0001
/devices/pci0000:00/0000:00:1a.7/usb1/1-4/1-4.2/1-4.2:1.0/0003:046D:C016.0001/hidraw/hidraw0
  name: /dev/hidraw0
/devices/pci0000:00/0000:00:1a.7/usb1/1-4/1-4.2/1-4.2:1.0/input/input4
/devices/pci0000:00/0000:00:1a.7/usb1/1-4/1-4.2/1-4.2:1.0/input/input4/event4
  name: /dev/input/event4
  links: /dev/input/by-id/usb-Logitech_Optical_USB_Mouse-event-mouse, /dev/input/by-path/pci-0000:00:1a.7-usb-0:4.2:1.0-event-mouse
/devices/pci0000:00/0000:00:1a.7/usb1/1-4/1-4.2/1-4.2:1.0/input/input4/mouse0
  name: /dev/input/mouse0
  links: /dev/input/by-id/usb-Logitech_Optical_USB_Mouse-mouse, /dev/input/by-path/pci-0000:00:1a.7-usb-0:4.2:1.0-mouse
/devices/pci0000:00/0000:00:1a.7/usb1/1-4/1-4:1.0
/devices/pci0000:00/0000:00:1a.7/usb1/1-6
  name: /dev/bus/usb/001/006
/devices/pci0000:00/0000:00:1a.7/usb1/1-6/1-6:1.0
/devices/pci0000:00/0000:00:1a.7/usb1/1-6/1-6:1.0/input/input10
/devices/pci0000:00/0000:00:1a.7/usb1/1-6/1-6:1.0/input/input10/event6
  name: /dev/input/event6
  links: /dev/input/by-id/usb-CN0K113P7248703G05EC_Integrated_Webcam_2M-event-if00, /dev/input/by-path/pci-0000:00:1a.7-usb-0:6:1.0-event
/devices/pci0000:00/0000:00:1a.7/usb1/1-6/1-6:1.0/video4linux/video0
  name: /dev/video0
  links: /dev/v4l/by-id/usb-CN0K113P7248703G05EC_Integrated_Webcam_2M-video-index0, /dev/v4l/by-path/pci-0000:00:1a.7-usb-0:6:1.0-video-index0
/devices/pci0000:00/0000:00:1a.7/usb1/1-6/1-6:1.1
/devices/pci0000:00/0000:00:1a.7/usbmon/usbmon1
  name: /dev/usbmon1
/devices/pci0000:00/0000:00:1b.0
/devices/pci0000:00/0000:00:1b.0/sound/card0
/devices/pci0000:00/0000:00:1b.0/sound/card0/hwC0D0
  name: /dev/snd/hwC0D0
/devices/pci0000:00/0000:00:1b.0/sound/card0/hwC0D1
  name: /dev/snd/hwC0D1
/devices/pci0000:00/0000:00:1b.0/sound/card0/hwC0D2
  name: /dev/snd/hwC0D2
/devices/pci0000:00/0000:00:1b.0/sound/card0/input12
/devices/pci0000:00/0000:00:1b.0/sound/card0/input12/event11
  name: /dev/input/event11
  links: /dev/input/by-path/pci-0000:00:1b.0-event-sndjack
/devices/pci0000:00/0000:00:1b.0/sound/card0/input13
/devices/pci0000:00/0000:00:1b.0/sound/card0/input13/event12
  name: /dev/input/event12
  links: /dev/input/by-path/pci-0000:00:1b.0-event-sndjack
/devices/pci0000:00/0000:00:1b.0/sound/card0/input14
/devices/pci0000:00/0000:00:1b.0/sound/card0/input14/event13
  name: /dev/input/event13
  links: /dev/input/by-path/pci-0000:00:1b.0-event-sndjack
/devices/pci0000:00/0000:00:1b.0/sound/card0/input15
/devices/pci0000:00/0000:00:1b.0/sound/card0/input15/event14
  name: /dev/input/event14
  links: /dev/input/by-path/pci-0000:00:1b.0-event-sndjack
/devices/pci0000:00/0000:00:1b.0/sound/card0/input16
/devices/pci0000:00/0000:00:1b.0/sound/card0/input16/event15
  name: /dev/input/event15
  links: /dev/input/by-path/pci-0000:00:1b.0-event-sndjack
/devices/pci0000:00/0000:00:1b.0/sound/card0/pcmC0D0c
  name: /dev/snd/pcmC0D0c
/devices/pci0000:00/0000:00:1b.0/sound/card0/pcmC0D0p
  name: /dev/snd/pcmC0D0p
/devices/pci0000:00/0000:00:1b.0/sound/card0/pcmC0D3p
  name: /dev/snd/pcmC0D3p
/devices/pci0000:00/0000:00:1b.0/sound/card0/controlC0
  name: /dev/snd/controlC0
  links: /dev/snd/by-path/pci-0000:00:1b.0
/devices/pci0000:00/0000:00:1c.0
/devices/pci0000:00/0000:00:1c.0/0000:00:1c.0:pcie08
/devices/pci0000:00/0000:00:1c.0/pci_bus/0000:0b
/devices/pci0000:00/0000:00:1c.1
/devices/pci0000:00/0000:00:1c.1/0000:00:1c.1:pcie08
/devices/pci0000:00/0000:00:1c.1/0000:0c:00.0
/devices/pci0000:00/0000:00:1c.1/0000:0c:00.0/net/eth2
/devices/pci0000:00/0000:00:1c.1/0000:0c:00.0/net/eth2/rfkill2
/devices/pci0000:00/0000:00:1c.1/pci_bus/0000:0c
/devices/pci0000:00/0000:00:1c.2
/devices/pci0000:00/0000:00:1c.2/0000:00:1c.2:pcie08
/devices/pci0000:00/0000:00:1c.2/pci_bus/0000:0d
/devices/pci0000:00/0000:00:1c.3
/devices/pci0000:00/0000:00:1c.3/0000:00:1c.3:pcie08
/devices/pci0000:00/0000:00:1c.3/pci_bus/0000:0e
/devices/pci0000:00/0000:00:1d.0
/devices/pci0000:00/0000:00:1d.0/usb6
  name: /dev/bus/usb/006/001
/devices/pci0000:00/0000:00:1d.0/usb6/6-0:1.0
/devices/pci0000:00/0000:00:1d.0/usb6/6-2
  name: /dev/bus/usb/006/002
/devices/pci0000:00/0000:00:1d.0/usb6/6-2/6-2:1.0
/devices/pci0000:00/0000:00:1d.0/usbmon/usbmon6
  name: /dev/usbmon6
/devices/pci0000:00/0000:00:1d.1
/devices/pci0000:00/0000:00:1d.1/usb7
  name: /dev/bus/usb/007/001
/devices/pci0000:00/0000:00:1d.1/usb7/7-0:1.0
/devices/pci0000:00/0000:00:1d.1/usbmon/usbmon7
  name: /dev/usbmon7
/devices/pci0000:00/0000:00:1d.2
/devices/pci0000:00/0000:00:1d.2/usb8
  name: /dev/bus/usb/008/001
/devices/pci0000:00/0000:00:1d.2/usb8/8-0:1.0
/devices/pci0000:00/0000:00:1d.2/usbmon/usbmon8
  name: /dev/usbmon8
/devices/pci0000:00/0000:00:1d.7
/devices/pci0000:00/0000:00:1d.7/usb2
  name: /dev/bus/usb/002/001
/devices/pci0000:00/0000:00:1d.7/usb2/2-0:1.0
/devices/pci0000:00/0000:00:1d.7/usbmon/usbmon2
  name: /dev/usbmon2
/devices/pci0000:00/0000:00:1e.0
/devices/pci0000:00/0000:00:1e.0/0000:03:01.0
/devices/pci0000:00/0000:00:1e.0/0000:03:01.0/pci_bus/0000:04
/devices/pci0000:00/0000:00:1e.0/0000:03:01.0/pcmcia_socket/pcmcia_socket0
/devices/pci0000:00/0000:00:1e.0/0000:03:01.1
/devices/pci0000:00/0000:00:1e.0/0000:03:01.1/fw0
  name: /dev/fw0
/devices/pci0000:00/0000:00:1e.0/0000:03:01.2
/devices/pci0000:00/0000:00:1e.0/0000:03:01.2/leds/mmc0::
/devices/pci0000:00/0000:00:1e.0/0000:03:01.2/mmc_host/mmc0
/devices/pci0000:00/0000:00:1e.0/0000:03:01.2/mmc_host/mmc0/mmc0:0007
/devices/pci0000:00/0000:00:1e.0/0000:03:01.2/mmc_host/mmc0/mmc0:0007/block/mmcblk0
  name: /dev/mmcblk0
  links: /dev/disk/by-id/mmc-SD04G_0xb000631b, /dev/disk/by-path/pci-0000:03:01.2
/devices/pci0000:00/0000:00:1e.0/0000:03:01.2/mmc_host/mmc0/mmc0:0007/block/mmcblk0/mmcblk0p1
  name: /dev/mmcblk0p1
  links: /dev/disk/by-id/mmc-SD04G_0xb000631b-part1, /dev/disk/by-path/pci-0000:03:01.2-part1, /dev/disk/by-uuid/3B2B-5097, /dev/disk/by-label/DATA
/devices/pci0000:00/0000:00:1e.0/pci_bus/0000:03
/devices/pci0000:00/0000:00:1f.0
/devices/pci0000:00/0000:00:1f.2
/devices/pci0000:00/0000:00:1f.2/ata1/ata_port/ata1
/devices/pci0000:00/0000:00:1f.2/ata1/link1/ata_link/link1
/devices/pci0000:00/0000:00:1f.2/ata1/link1/dev1.0/ata_device/dev1.0
/devices/pci0000:00/0000:00:1f.2/ata2/ata_port/ata2
/devices/pci0000:00/0000:00:1f.2/ata2/link2/ata_link/link2
/devices/pci0000:00/0000:00:1f.2/ata2/link2/dev2.0/ata_device/dev2.0
/devices/pci0000:00/0000:00:1f.2/ata3/ata_port/ata3
/devices/pci0000:00/0000:00:1f.2/ata3/link3/ata_link/link3
/devices/pci0000:00/0000:00:1f.2/ata3/link3/dev3.0/ata_device/dev3.0
/devices/pci0000:00/0000:00:1f.2/ata4/ata_port/ata4
/devices/pci0000:00/0000:00:1f.2/ata4/link4/ata_link/link4
/devices/pci0000:00/0000:00:1f.2/ata4/link4/dev4.0/ata_device/dev4.0
/devices/pci0000:00/0000:00:1f.2/ata5/ata_port/ata5
/devices/pci0000:00/0000:00:1f.2/ata5/link5/ata_link/link5
/devices/pci0000:00/0000:00:1f.2/ata5/link5/dev5.0/ata_device/dev5.0
/devices/pci0000:00/0000:00:1f.2/ata6/ata_port/ata6
/devices/pci0000:00/0000:00:1f.2/ata6/link6/ata_link/link6
/devices/pci0000:00/0000:00:1f.2/ata6/link6/dev6.0/ata_device/dev6.0
/devices/pci0000:00/0000:00:1f.2/host0
/devices/pci0000:00/0000:00:1f.2/host0/scsi_host/host0
/devices/pci0000:00/0000:00:1f.2/host0/target0:0:0
/devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0
/devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0/block/sda
  name: /dev/sda
  links: /dev/disk/by-id/ata-ST9250410ASG_5VG5AW0Z, /dev/disk/by-id/scsi-SATA_ST9250410ASG_5VG5AW0Z, /dev/disk/by-path/pci-0000:00:1f.2-scsi-0:0:0:0, /dev/disk/by-id/wwn-0x5000c500251025f4
/devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0/block/sda/sda1
  name: /dev/sda1
  links: /dev/disk/by-id/ata-ST9250410ASG_5VG5AW0Z-part1, /dev/disk/by-id/scsi-SATA_ST9250410ASG_5VG5AW0Z-part1, /dev/disk/by-path/pci-0000:00:1f.2-scsi-0:0:0:0-part1, /dev/disk/by-uuid/A8EE7F75EE7F3B20, /dev/disk/by-label/System\x20Reserved, /dev/disk/by-id/wwn-0x5000c500251025f4-part1
/devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0/block/sda/sda2
  name: /dev/sda2
  links: /dev/disk/by-id/ata-ST9250410ASG_5VG5AW0Z-part2, /dev/disk/by-id/scsi-SATA_ST9250410ASG_5VG5AW0Z-part2, /dev/disk/by-path/pci-0000:00:1f.2-scsi-0:0:0:0-part2, /dev/disk/by-uuid/2bdc1a9a-8cf1-4e51-8e7a-0717443ce6c8, /dev/disk/by-id/wwn-0x5000c500251025f4-part2
/devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0/block/sda/sda4
  name: /dev/sda4
  links: /dev/disk/by-id/ata-ST9250410ASG_5VG5AW0Z-part4, /dev/disk/by-id/scsi-SATA_ST9250410ASG_5VG5AW0Z-part4, /dev/disk/by-path/pci-0000:00:1f.2-scsi-0:0:0:0-part4, /dev/disk/by-id/wwn-0x5000c500251025f4-part4
/devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0/block/sda/sda5
  name: /dev/sda5
  links: /dev/disk/by-id/ata-ST9250410ASG_5VG5AW0Z-part5, /dev/disk/by-id/scsi-SATA_ST9250410ASG_5VG5AW0Z-part5, /dev/disk/by-path/pci-0000:00:1f.2-scsi-0:0:0:0-part5, /dev/disk/by-uuid/b2d1e233-8260-43f6-b0a0-be7c7d903301, /dev/disk/by-label/swap, /dev/disk/by-id/wwn-0x5000c500251025f4-part5
/devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0/block/sda/sda6
  name: /dev/sda6
  links: /dev/disk/by-id/ata-ST9250410ASG_5VG5AW0Z-part6, /dev/disk/by-id/scsi-SATA_ST9250410ASG_5VG5AW0Z-part6, /dev/disk/by-path/pci-0000:00:1f.2-scsi-0:0:0:0-part6, /dev/disk/by-uuid/25bdc29e-9e7c-467b-b63b-a6456e2c667b, /dev/disk/by-label/\x2fhome, /dev/disk/by-id/wwn-0x5000c500251025f4-part6
/devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0/bsg/0:0:0:0
  name: /dev/bsg/0:0:0:0
/devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0/scsi_device/0:0:0:0
/devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0/scsi_disk/0:0:0:0
/devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0/scsi_generic/sg0
  name: /dev/sg0
/devices/pci0000:00/0000:00:1f.2/host1
/devices/pci0000:00/0000:00:1f.2/host1/scsi_host/host1
/devices/pci0000:00/0000:00:1f.2/host1/target1:0:0
/devices/pci0000:00/0000:00:1f.2/host1/target1:0:0/1:0:0:0
/devices/pci0000:00/0000:00:1f.2/host1/target1:0:0/1:0:0:0/block/sr0
  name: /dev/sr0
  links: /dev/scd0, /dev/disk/by-id/ata-HL-DT-ST_DVD+_-RW_GU10N_KVEA3B93937, /dev/disk/by-path/pci-0000:00:1f.2-scsi-1:0:0:0, /dev/cdrom1, /dev/cdrw1, /dev/dvd1, /dev/dvdrw1
/devices/pci0000:00/0000:00:1f.2/host1/target1:0:0/1:0:0:0/bsg/1:0:0:0
  name: /dev/bsg/1:0:0:0
/devices/pci0000:00/0000:00:1f.2/host1/target1:0:0/1:0:0:0/scsi_device/1:0:0:0
/devices/pci0000:00/0000:00:1f.2/host1/target1:0:0/1:0:0:0/scsi_generic/sg1
  name: /dev/sg1
/devices/pci0000:00/0000:00:1f.2/host2
/devices/pci0000:00/0000:00:1f.2/host2/scsi_host/host2
/devices/pci0000:00/0000:00:1f.2/host3
/devices/pci0000:00/0000:00:1f.2/host3/scsi_host/host3
/devices/pci0000:00/0000:00:1f.2/host4
/devices/pci0000:00/0000:00:1f.2/host4/scsi_host/host4
/devices/pci0000:00/0000:00:1f.2/host5
/devices/pci0000:00/0000:00:1f.2/host5/scsi_host/host5
/devices/pci0000:00/0000:00:1f.3
/devices/pci0000:00/pci_bus/0000:00
/devices/platform/Fixed
/devices/platform/Fixed
/devices/platform/alarmtimer
/devices/platform/dcdbas
/devices/platform/dell-laptop
/devices/platform/dell-laptop/rfkill/rfkill0
/devices/platform/dell-laptop/rfkill/rfkill1
/devices/platform/i8042
/devices/platform/i8042/serio0
/devices/platform/i8042/serio0/input/input3
/devices/platform/i8042/serio0/input/input3/event3
  name: /dev/input/event3
  links: /dev/input/by-path/platform-i8042-serio-0-event-kbd
/devices/platform/i8042/serio1
/devices/platform/i8042/serio1/input/input8
/devices/platform/i8042/serio1/input/input8/event8
  name: /dev/input/event8
  links: /dev/input/by-path/platform-i8042-serio-1-event-mouse
/devices/platform/i8042/serio1/input/input8/mouse2
  name: /dev/input/mouse2
  links: /dev/input/by-path/platform-i8042-serio-1-mouse
/devices/platform/i8042/serio1/input/input9
/devices/platform/i8042/serio1/input/input9/event9
  name: /dev/input/event9
  links: /dev/input/by-path/platform-i8042-serio-1-event-mouse
/devices/platform/i8042/serio1/input/input9/mouse3
  name: /dev/input/mouse3
  links: /dev/input/by-path/platform-i8042-serio-1-mouse
/devices/platform/pcspkr
/devices/platform/reg-dummy
/devices/platform/serial8250
/devices/platform/serial8250/tty/ttyS1
  name: /dev/ttyS1
/devices/platform/serial8250/tty/ttyS10
  name: /dev/ttyS10
/devices/platform/serial8250/tty/ttyS11
  name: /dev/ttyS11
/devices/platform/serial8250/tty/ttyS12
  name: /dev/ttyS12
/devices/platform/serial8250/tty/ttyS13
  name: /dev/ttyS13
/devices/platform/serial8250/tty/ttyS14
  name: /dev/ttyS14
/devices/platform/serial8250/tty/ttyS15
  name: /dev/ttyS15
/devices/platform/serial8250/tty/ttyS16
  name: /dev/ttyS16
/devices/platform/serial8250/tty/ttyS17
  name: /dev/ttyS17
/devices/platform/serial8250/tty/ttyS18
  name: /dev/ttyS18
/devices/platform/serial8250/tty/ttyS19
  name: /dev/ttyS19
/devices/platform/serial8250/tty/ttyS2
  name: /dev/ttyS2
/devices/platform/serial8250/tty/ttyS20
  name: /dev/ttyS20
/devices/platform/serial8250/tty/ttyS21
  name: /dev/ttyS21
/devices/platform/serial8250/tty/ttyS22
  name: /dev/ttyS22
/devices/platform/serial8250/tty/ttyS23
  name: /dev/ttyS23
/devices/platform/serial8250/tty/ttyS24
  name: /dev/ttyS24
/devices/platform/serial8250/tty/ttyS25
  name: /dev/ttyS25
/devices/platform/serial8250/tty/ttyS26
  name: /dev/ttyS26
/devices/platform/serial8250/tty/ttyS27
  name: /dev/ttyS27
/devices/platform/serial8250/tty/ttyS28
  name: /dev/ttyS28
/devices/platform/serial8250/tty/ttyS29
  name: /dev/ttyS29
/devices/platform/serial8250/tty/ttyS3
  name: /dev/ttyS3
/devices/platform/serial8250/tty/ttyS30
  name: /dev/ttyS30
/devices/platform/serial8250/tty/ttyS31
  name: /dev/ttyS31
/devices/platform/serial8250/tty/ttyS4
  name: /dev/ttyS4
/devices/platform/serial8250/tty/ttyS5
  name: /dev/ttyS5
/devices/platform/serial8250/tty/ttyS6
  name: /dev/ttyS6
/devices/platform/serial8250/tty/ttyS7
  name: /dev/ttyS7
/devices/platform/serial8250/tty/ttyS8
  name: /dev/ttyS8
/devices/platform/serial8250/tty/ttyS9
  name: /dev/ttyS9
/devices/platform/vboxdrv.0
/devices/pnp0/00:00
/devices/pnp0/00:01
/devices/pnp0/00:02
/devices/pnp0/00:03
/devices/pnp0/00:03/rtc/rtc0
  name: /dev/rtc0
  links: /dev/rtc
/devices/pnp0/00:04
/devices/pnp0/00:05
/devices/pnp0/00:06
/devices/pnp0/00:07
/devices/pnp0/00:08
/devices/pnp0/00:09
/devices/pnp0/00:09/tty/ttyS0
  name: /dev/ttyS0
/devices/pnp0/00:0a
/devices/pnp0/00:0a/ppdev/parport0
  name: /dev/parport0
/devices/pnp0/00:0a/printer/lp0
  name: /dev/lp0
/devices/pnp0/00:0b
/devices/pnp0/00:0c
/devices/pnp0/00:0d
/devices/pnp0/00:0e
/devices/software
/devices/tracepoint
/devices/virtual/bdi/0:19
/devices/virtual/bdi/0:20
/devices/virtual/bdi/0:21
/devices/virtual/bdi/0:22
/devices/virtual/bdi/11:0
/devices/virtual/bdi/11:1
/devices/virtual/bdi/179:0
/devices/virtual/bdi/1:0
/devices/virtual/bdi/1:1
/devices/virtual/bdi/1:10
/devices/virtual/bdi/1:11
/devices/virtual/bdi/1:12
/devices/virtual/bdi/1:13
/devices/virtual/bdi/1:14
/devices/virtual/bdi/1:15
/devices/virtual/bdi/1:2
/devices/virtual/bdi/1:3
/devices/virtual/bdi/1:4
/devices/virtual/bdi/1:5
/devices/virtual/bdi/1:6
/devices/virtual/bdi/1:7
/devices/virtual/bdi/1:8
/devices/virtual/bdi/1:9
/devices/virtual/bdi/7:0
/devices/virtual/bdi/7:1
/devices/virtual/bdi/7:2
/devices/virtual/bdi/7:3
/devices/virtual/bdi/7:4
/devices/virtual/bdi/7:5
/devices/virtual/bdi/7:6
/devices/virtual/bdi/7:7
/devices/virtual/bdi/8:0
/devices/virtual/bdi/8:16
/devices/virtual/bdi/default
/devices/virtual/block/loop0
  name: /dev/loop0
/devices/virtual/block/loop1
  name: /dev/loop1
/devices/virtual/block/loop2
  name: /dev/loop2
/devices/virtual/block/loop3
  name: /dev/loop3
/devices/virtual/block/loop4
  name: /dev/loop4
/devices/virtual/block/loop5
  name: /dev/loop5
/devices/virtual/block/loop6
  name: /dev/loop6
/devices/virtual/block/loop7
  name: /dev/loop7
/devices/virtual/block/ram0
  name: /dev/ram0
/devices/virtual/block/ram1
  name: /dev/ram1
/devices/virtual/block/ram10
  name: /dev/ram10
/devices/virtual/block/ram11
  name: /dev/ram11
/devices/virtual/block/ram12
  name: /dev/ram12
/devices/virtual/block/ram13
  name: /dev/ram13
/devices/virtual/block/ram14
  name: /dev/ram14
/devices/virtual/block/ram15
  name: /dev/ram15
/devices/virtual/block/ram2
  name: /dev/ram2
/devices/virtual/block/ram3
  name: /dev/ram3
/devices/virtual/block/ram4
  name: /dev/ram4
/devices/virtual/block/ram5
  name: /dev/ram5
/devices/virtual/block/ram6
  name: /dev/ram6
/devices/virtual/block/ram7
  name: /dev/ram7
/devices/virtual/block/ram8
  name: /dev/ram8
/devices/virtual/block/ram9
  name: /dev/ram9
/devices/virtual/dmi/id
/devices/virtual/graphics/fbcon
/devices/virtual/hwmon/hwmon0
/devices/virtual/input/input7
/devices/virtual/input/input7/event7
  name: /dev/input/event7
/devices/virtual/input/mice
  name: /dev/input/mice
/devices/virtual/mem/full
  name: /dev/full
/devices/virtual/mem/kmsg
  name: /dev/kmsg
/devices/virtual/mem/mem
  name: /dev/mem
/devices/virtual/mem/null
  name: /dev/null
/devices/virtual/mem/oldmem
  name: /dev/oldmem
/devices/virtual/mem/port
  name: /dev/port
/devices/virtual/mem/random
  name: /dev/random
/devices/virtual/mem/urandom
  name: /dev/urandom
/devices/virtual/mem/zero
  name: /dev/zero
/devices/virtual/misc/agpgart
  name: /dev/agpgart
/devices/virtual/misc/cpu_dma_latency
  name: /dev/cpu_dma_latency
/devices/virtual/misc/device-mapper
  name: /dev/mapper/control
/devices/virtual/misc/ecryptfs
  name: /dev/ecryptfs
/devices/virtual/misc/fuse
  name: /dev/fuse
/devices/virtual/misc/hpet
  name: /dev/hpet
/devices/virtual/misc/mcelog
  name: /dev/mcelog
/devices/virtual/misc/network_latency
  name: /dev/network_latency
/devices/virtual/misc/network_throughput
  name: /dev/network_throughput
/devices/virtual/misc/psaux
  name: /dev/psaux
/devices/virtual/misc/rfkill
  name: /dev/rfkill
/devices/virtual/misc/snapshot
  name: /dev/snapshot
/devices/virtual/misc/tun
  name: /dev/net/tun
/devices/virtual/misc/uinput
  name: /dev/uinput
/devices/virtual/misc/vboxdrv
  name: /dev/vboxdrv
/devices/virtual/misc/vboxnetctl
  name: /dev/vboxnetctl
/devices/virtual/misc/vga_arbiter
  name: /dev/vga_arbiter
/devices/virtual/net/lo
/devices/virtual/ppp/ppp
  name: /dev/ppp
/devices/virtual/regulator/regulator.0
/devices/virtual/sound/seq
  name: /dev/snd/seq
/devices/virtual/sound/timer
  name: /dev/snd/timer
/devices/virtual/thermal/cooling_device0
/devices/virtual/thermal/cooling_device1
/devices/virtual/thermal/cooling_device2
/devices/virtual/thermal/thermal_zone0
/devices/virtual/tty/console
  name: /dev/console
/devices/virtual/tty/ptmx
  name: /dev/ptmx
/devices/virtual/tty/tty
  name: /dev/tty
/devices/virtual/tty/tty0
  name: /dev/tty0
/devices/virtual/tty/tty1
  name: /dev/tty1
/devices/virtual/tty/tty10
  name: /dev/tty10
/devices/virtual/tty/tty11
  name: /dev/tty11
/devices/virtual/tty/tty12
  name: /dev/tty12
/devices/virtual/tty/tty13
  name: /dev/tty13
/devices/virtual/tty/tty14
  name: /dev/tty14
/devices/virtual/tty/tty15
  name: /dev/tty15
/devices/virtual/tty/tty16
  name: /dev/tty16
/devices/virtual/tty/tty17
  name: /dev/tty17
/devices/virtual/tty/tty18
  name: /dev/tty18
/devices/virtual/tty/tty19
  name: /dev/tty19
/devices/virtual/tty/tty2
  name: /dev/tty2
/devices/virtual/tty/tty20
  name: /dev/tty20
/devices/virtual/tty/tty21
  name: /dev/tty21
/devices/virtual/tty/tty22
  name: /dev/tty22
/devices/virtual/tty/tty23
  name: /dev/tty23
/devices/virtual/tty/tty24
  name: /dev/tty24
/devices/virtual/tty/tty25
  name: /dev/tty25
/devices/virtual/tty/tty26
  name: /dev/tty26
/devices/virtual/tty/tty27
  name: /dev/tty27
/devices/virtual/tty/tty28
  name: /dev/tty28
/devices/virtual/tty/tty29
  name: /dev/tty29
/devices/virtual/tty/tty3
  name: /dev/tty3
/devices/virtual/tty/tty30
  name: /dev/tty30
/devices/virtual/tty/tty31
  name: /dev/tty31
/devices/virtual/tty/tty32
  name: /dev/tty32
/devices/virtual/tty/tty33
  name: /dev/tty33
/devices/virtual/tty/tty34
  name: /dev/tty34
/devices/virtual/tty/tty35
  name: /dev/tty35
/devices/virtual/tty/tty36
  name: /dev/tty36
/devices/virtual/tty/tty37
  name: /dev/tty37
/devices/virtual/tty/tty38
  name: /dev/tty38
/devices/virtual/tty/tty39
  name: /dev/tty39
/devices/virtual/tty/tty4
  name: /dev/tty4
/devices/virtual/tty/tty40
  name: /dev/tty40
/devices/virtual/tty/tty41
  name: /dev/tty41
/devices/virtual/tty/tty42
  name: /dev/tty42
/devices/virtual/tty/tty43
  name: /dev/tty43
/devices/virtual/tty/tty44
  name: /dev/tty44
/devices/virtual/tty/tty45
  name: /dev/tty45
/devices/virtual/tty/tty46
  name: /dev/tty46
/devices/virtual/tty/tty47
  name: /dev/tty47
/devices/virtual/tty/tty48
  name: /dev/tty48
/devices/virtual/tty/tty49
  name: /dev/tty49
/devices/virtual/tty/tty5
  name: /dev/tty5
/devices/virtual/tty/tty50
  name: /dev/tty50
/devices/virtual/tty/tty51
  name: /dev/tty51
/devices/virtual/tty/tty52
  name: /dev/tty52
/devices/virtual/tty/tty53
  name: /dev/tty53
/devices/virtual/tty/tty54
  name: /dev/tty54
/devices/virtual/tty/tty55
  name: /dev/tty55
/devices/virtual/tty/tty56
  name: /dev/tty56
/devices/virtual/tty/tty57
  name: /dev/tty57
/devices/virtual/tty/tty58
  name: /dev/tty58
/devices/virtual/tty/tty59
  name: /dev/tty59
/devices/virtual/tty/tty6
  name: /dev/tty6
/devices/virtual/tty/tty60
  name: /dev/tty60
/devices/virtual/tty/tty61
  name: /dev/tty61
/devices/virtual/tty/tty62
  name: /dev/tty62
/devices/virtual/tty/tty63
  name: /dev/tty63
/devices/virtual/tty/tty7
  name: /dev/tty7
/devices/virtual/tty/tty8
  name: /dev/tty8
/devices/virtual/tty/tty9
  name: /dev/tty9
/devices/virtual/tty/ttyprintk
  name: /dev/ttyprintk
/devices/virtual/usbmon/usbmon0
  name: /dev/usbmon0
/devices/virtual/vc/vcs
  name: /dev/vcs
/devices/virtual/vc/vcs1
  name: /dev/vcs1
/devices/virtual/vc/vcs2
  name: /dev/vcs2
/devices/virtual/vc/vcs3
  name: /dev/vcs3
/devices/virtual/vc/vcs4
  name: /dev/vcs4
/devices/virtual/vc/vcs5
  name: /dev/vcs5
/devices/virtual/vc/vcs6
  name: /dev/vcs6
/devices/virtual/vc/vcsa
  name: /dev/vcsa
/devices/virtual/vc/vcsa1
  name: /dev/vcsa1
/devices/virtual/vc/vcsa2
  name: /dev/vcsa2
/devices/virtual/vc/vcsa3
  name: /dev/vcsa3
/devices/virtual/vc/vcsa4
  name: /dev/vcsa4
/devices/virtual/vc/vcsa5
  name: /dev/vcsa5
/devices/virtual/vc/vcsa6
  name: /dev/vcsa6
/devices/virtual/vtconsole/vtcon0
/devices/virtual/vtconsole/vtcon1
/devices/virtual/wmi/05901221-D566-11D1-B2F0-00A0C9062910
/devices/virtual/wmi/77BD0728-2E34-478C-B625-67F02A7E4897
/devices/virtual/wmi/8D9DDCBC-A997-11DA-B012-B622A1EF5492
/devices/virtual/wmi/9DBB5994-A997-11DA-B012-B622A1EF5492
/devices/virtual/wmi/A3776CE0-1E88-11DB-A98B-0800200C9A66
/devices/virtual/wmi/A80593CE-A997-11DA-B012-B622A1EF5492
>> int.13: device names
>> int.14: soft raid
----- soft raid devices -----
----- soft raid devices end -----
>> int.15: geo
>> int.16: parent
  prop read: rdCR.lZF+r4EgHp4 (failed)
  old prop read: rdCR.lZF+r4EgHp4 (failed)
  prop read: rdCR.n_7QNeEnh23 (failed)
  old prop read: rdCR.n_7QNeEnh23 (failed)
  prop read: rdCR.EMpH5pjcahD (failed)
  old prop read: rdCR.EMpH5pjcahD (failed)
  prop read: rdCR.f5u1ucRm+H9 (failed)
  old prop read: rdCR.f5u1ucRm+H9 (failed)
  prop read: rdCR.8uRK7LxiIA2 (failed)
  old prop read: rdCR.8uRK7LxiIA2 (failed)
  prop read: rdCR.AJKleuxpiP0 (failed)
  old prop read: rdCR.AJKleuxpiP0 (failed)
  prop read: rdCR.9N+EecqykME (failed)
  old prop read: rdCR.9N+EecqykME (failed)
  prop read: YMnp.ecK7NLYWZ5D (failed)
  old prop read: YMnp.ecK7NLYWZ5D (failed)
  prop read: rdCR.CxwsZFjVASF (failed)
  old prop read: rdCR.CxwsZFjVASF (failed)
  prop read: qLht.g5e3bz_VyfC (failed)
  old prop read: qLht.g5e3bz_VyfC (failed)
  prop read: _Znp.fTsp+HYAhr8 (failed)
  old prop read: _Znp.fTsp+HYAhr8 (failed)
  prop read: ruGf.AwDSv7rqySE (failed)
  old prop read: ruGf.AwDSv7rqySE (failed)
  prop read: rBUF.DspxR_P+1HD (failed)
  old prop read: rBUF.DspxR_P+1HD (failed)
  prop read: pwJ7.zEmL3P1Lr01 (failed)
  old prop read: pwJ7.zEmL3P1Lr01 (failed)
  prop read: gFpy.Ufi5Yz82NP1 (failed)
  old prop read: gFpy.Ufi5Yz82NP1 (failed)
  prop read: XaIo.+3fr0YGlun1 (failed)
  old prop read: XaIo.+3fr0YGlun1 (failed)
  prop read: sClz.2K4HlJ6d+m7 (failed)
  old prop read: sClz.2K4HlJ6d+m7 (failed)
  prop read: u1Nb.SGxGJCiH+82 (failed)
  old prop read: u1Nb.SGxGJCiH+82 (failed)
  prop read: z8Q3.1HNJ3AEFeQ2 (failed)
  old prop read: z8Q3.1HNJ3AEFeQ2 (failed)
  prop read: qTvu.36Gp0JTfhB3 (failed)
  old prop read: qTvu.36Gp0JTfhB3 (failed)
  prop read: hoOk.5x8J_Ri3ly3 (failed)
  old prop read: hoOk.5x8J_Ri3ly3 (failed)
  prop read: Z7uZ.7m1pxaxToj4 (failed)
  old prop read: Z7uZ.7m1pxaxToj4 (failed)
  prop read: 1GTX.Q+w5dlK+FI1 (failed)
  old prop read: 1GTX.Q+w5dlK+FI1 (failed)
  prop read: vayM.xPtr5KSing1 (failed)
  old prop read: vayM.xPtr5KSing1 (failed)
  prop read: mvRC.SqpbauZPJ32 (failed)
  old prop read: mvRC.SqpbauZPJ32 (failed)
  prop read: 5YuN.0VBnnAtCy+6 (failed)
  old prop read: 5YuN.0VBnnAtCy+6 (failed)
  prop read: 6NW+.D0CgCP5hV+8 (failed)
  old prop read: 6NW+.D0CgCP5hV+8 (failed)
  prop read: BUZT.LfLT41XywmE (failed)
  old prop read: BUZT.LfLT41XywmE (failed)
  prop read: w7Y8.zLI+X3nl8w7 (failed)
  old prop read: w7Y8.zLI+X3nl8w7 (failed)
  prop read: nS1_.Om1XD1tHZ+D (failed)
  old prop read: nS1_.Om1XD1tHZ+D (failed)
  prop read: mY_N.gwDnaUUtfJC (failed)
  old prop read: mY_N.gwDnaUUtfJC (failed)
  prop read: x0Ln.N1DekKV55+6 (failed)
  old prop read: x0Ln.N1DekKV55+6 (failed)
  prop read: pLqc.mUT3jsg0pC9 (failed)
  old prop read: pLqc.mUT3jsg0pC9 (failed)
  prop read: ggJS.lyitnPuGpr6 (failed)
  old prop read: ggJS.lyitnPuGpr6 (failed)
  prop read: rdCR.7RG8lK_UzJ9 (failed)
  old prop read: rdCR.7RG8lK_UzJ9 (failed)
  prop read: HAKk.Fxp0d3BezAE (failed)
  old prop read: HAKk.Fxp0d3BezAE (failed)
  prop read: l7UW.SE1wIdpsiiC (failed)
  old prop read: l7UW.SE1wIdpsiiC (failed)
  prop read: 3OOL.UMahlgDMi66 (failed)
  old prop read: 3OOL.UMahlgDMi66 (failed)
  prop read: bdUI.SE1wIdpsiiC (failed)
  old prop read: bdUI.SE1wIdpsiiC (failed)
  prop read: 2pkM.SE1wIdpsiiC (failed)
  old prop read: 2pkM.SE1wIdpsiiC (failed)
  prop read: z9FV.SE1wIdpsiiC (failed)
  old prop read: z9FV.SE1wIdpsiiC (failed)
  prop read: QLVZ.SE1wIdpsiiC (failed)
  old prop read: QLVZ.SE1wIdpsiiC (failed)
  prop read: tWld.SE1wIdpsiiC (failed)
  old prop read: tWld.SE1wIdpsiiC (failed)
  prop read: KD9E.mEFpAo01le1 (failed)
  old prop read: KD9E.mEFpAo01le1 (failed)
  prop read: kzsy.6SYkiKiJsF0 (failed)
  old prop read: kzsy.6SYkiKiJsF0 (failed)
  prop read: uI_Q.c_88VrmYtvE (failed)
  old prop read: uI_Q.c_88VrmYtvE (failed)
  prop read: h4pj.SE1wIdpsiiC (failed)
  old prop read: h4pj.SE1wIdpsiiC (failed)
  prop read: k4bc.cO89g+iefn1 (failed)
  old prop read: k4bc.cO89g+iefn1 (failed)
  prop read: pBe4.9T1GDCLyFd9 (failed)
  old prop read: pBe4.9T1GDCLyFd9 (failed)
  prop read: uIhY.MxUuepIFPaE (failed)
  old prop read: uIhY.MxUuepIFPaE (failed)
  prop read: zPk0.7gZT0a5zLs5 (failed)
  old prop read: zPk0.7gZT0a5zLs5 (failed)
  prop read: 2XnU.uOe2OKugI8D (failed)
  old prop read: 2XnU.uOe2OKugI8D (failed)
  prop read: 7eqy.v+N+B0xY+P6 (failed)
  old prop read: 7eqy.v+N+B0xY+P6 (failed)
  prop read: BSFT.gkSaZmjGyhD (failed)
  old prop read: BSFT.gkSaZmjGyhD (failed)
  prop read: FZIx.RTX9xWW_uz4 (failed)
  old prop read: FZIx.RTX9xWW_uz4 (failed)
  prop read: 2UT6._H8jkZcj4d2 (failed)
  old prop read: 2UT6._H8jkZcj4d2 (failed)
  prop read: Uc5H._H8jkZcj4d2 (failed)
  old prop read: Uc5H._H8jkZcj4d2 (failed)
  prop read: MtLc.ZZ+SA7KltS2 (failed)
  old prop read: MtLc.ZZ+SA7KltS2 (failed)
  prop read: KRJj.SAMIiYMCz2F (failed)
  old prop read: KRJj.SAMIiYMCz2F (failed)
  prop read: cKwp.hVUwYQ7Uxx1 (failed)
  old prop read: cKwp.hVUwYQ7Uxx1 (failed)
  prop read: +u4I.bBFFBTjAOZ4 (failed)
  old prop read: +u4I.bBFFBTjAOZ4 (failed)
  prop read: vt3A.YCWTDwYJz_B (failed)
  old prop read: vt3A.YCWTDwYJz_B (failed)
  prop read: L0iK.YCWTDwYJz_B (failed)
  old prop read: L0iK.YCWTDwYJz_B (failed)
  prop read: Q7lo.R9wUZ167351 (failed)
  old prop read: Q7lo.R9wUZ167351 (failed)
  prop read: 7dS8.yvebFSWtvP1 (failed)
  old prop read: 7dS8.yvebFSWtvP1 (failed)
  prop read: Yl4J.O_flO7nZ+J6 (failed)
  old prop read: Yl4J.O_flO7nZ+J6 (failed)
  prop read: 9ui9.+49ps10DtUF (failed)
  old prop read: 9ui9.+49ps10DtUF (failed)
  prop read: AH6Q.5+smWHVjPI3 (failed)
  old prop read: AH6Q.5+smWHVjPI3 (failed)
  prop read: AH6Q.5+smWHVjPI3 (failed)
  old prop read: AH6Q.5+smWHVjPI3 (failed)
  prop read: rdCR.j8NaKXDZtZ6 (failed)
  old prop read: rdCR.j8NaKXDZtZ6 (failed)
  prop read: wkFv.j8NaKXDZtZ6 (failed)
  old prop read: wkFv.j8NaKXDZtZ6 (failed)
  prop read: ZsBS.GQNx7L4uPNA (failed)
  old prop read: ZsBS.GQNx7L4uPNA (failed)
  prop read: usDW.ndpeucax6V1 (failed)
  old prop read: usDW.ndpeucax6V1 (failed)
  prop read: pDke.ndpeucax6V1 (failed)
  old prop read: pDke.ndpeucax6V1 (failed)
----- /proc/modules -----
  rfcomm 47946 0 - Live 0x0000000000000000
  bnep 18436 2 - Live 0x0000000000000000
  bluetooth 166112 10 rfcomm,bnep, Live 0x0000000000000000
  pci_stub 12622 1 - Live 0x0000000000000000
  vboxpci 23200 0 - Live 0x0000000000000000
  vboxnetadp 13382 0 - Live 0x0000000000000000
  vboxnetflt 23441 0 - Live 0x0000000000000000
  vboxdrv 282548 3 vboxpci,vboxnetadp,vboxnetflt, Live 0x0000000000000000
  snd_hda_codec_hdmi 32040 1 - Live 0x0000000000000000
  snd_hda_codec_idt 70553 1 - Live 0x0000000000000000
  snd_hda_intel 33390 3 - Live 0x0000000000000000
  snd_hda_codec 104802 3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel, Live 0x0000000000000000
  snd_hwdep 13668 1 snd_hda_codec, Live 0x0000000000000000
  snd_pcm 96714 3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec, Live 0x0000000000000000
  lib80211_crypt_tkip 17390 0 - Live 0x0000000000000000
  snd_seq_midi 13324 0 - Live 0x0000000000000000
  uvcvideo 72711 0 - Live 0x0000000000000000
  videodev 92992 1 uvcvideo, Live 0x0000000000000000
  v4l2_compat_ioctl32 17083 1 videodev, Live 0x0000000000000000
  joydev 17693 0 - Live 0x0000000000000000
  wl 2568210 0 - Live 0x0000000000000000 (P)
  snd_rawmidi 30547 1 snd_seq_midi, Live 0x0000000000000000
  snd_seq_midi_event 14899 1 snd_seq_midi, Live 0x0000000000000000
  snd_seq 61896 2 snd_seq_midi,snd_seq_midi_event, Live 0x0000000000000000
  snd_timer 29991 2 snd_pcm,snd_seq, Live 0x0000000000000000
  snd_seq_device 14540 3 snd_seq_midi,snd_rawmidi,snd_seq, Live 0x0000000000000000
  pcmcia 49378 0 - Live 0x0000000000000000
  ppdev 17113 0 - Live 0x0000000000000000
  snd 68266 16 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device, Live 0x0000000000000000
  i915 566827 3 - Live 0x0000000000000000
  drm_kms_helper 42558 1 i915, Live 0x0000000000000000
  parport_pc 36962 1 - Live 0x0000000000000000
  drm 236290 4 i915,drm_kms_helper, Live 0x0000000000000000
  dell_laptop 13831 0 - Live 0x0000000000000000
  dcdbas 14490 1 dell_laptop, Live 0x0000000000000000
  i2c_algo_bit 13423 1 i915, Live 0x0000000000000000
  soundcore 12680 1 snd, Live 0x0000000000000000
  video 19412 1 i915, Live 0x0000000000000000
  psmouse 73882 0 - Live 0x0000000000000000
  yenta_socket 28084 0 - Live 0x0000000000000000
  serio_raw 13166 0 - Live 0x0000000000000000
  pcmcia_rsrc 18430 1 yenta_socket, Live 0x0000000000000000
  pcmcia_core 22614 3 pcmcia,yenta_socket,pcmcia_rsrc, Live 0x0000000000000000
  snd_page_alloc 18529 2 snd_hda_intel,snd_pcm, Live 0x0000000000000000
  dell_wmi 12681 0 - Live 0x0000000000000000
  sparse_keymap 13890 1 dell_wmi, Live 0x0000000000000000
  lib80211 14991 2 lib80211_crypt_tkip,wl, Live 0x0000000000000000
  wmi 19256 1 dell_wmi, Live 0x0000000000000000
  lp 17799 0 - Live 0x0000000000000000
  parport 46562 3 ppdev,parport_pc,lp, Live 0x0000000000000000
  ses 17417 0 - Live 0x0000000000000000
  enclosure 15269 1 ses, Live 0x0000000000000000
  usb_storage 57901 0 - Live 0x0000000000000000
  uas 18027 0 - Live 0x0000000000000000
  usbhid 47198 0 - Live 0x0000000000000000
  hid 95463 1 usbhid, Live 0x0000000000000000
  mmc_block 22923 0 - Live 0x0000000000000000
  firewire_ohci 40722 0 - Live 0x0000000000000000
  firewire_core 63626 1 firewire_ohci, Live 0x0000000000000000
  crc_itu_t 12707 1 firewire_core, Live 0x0000000000000000
  sdhci_pci 14032 0 - Live 0x0000000000000000
  sdhci 32166 1 sdhci_pci, Live 0x0000000000000000
  ahci 26002 3 - Live 0x0000000000000000
  libahci 26861 1 ahci, Live 0x0000000000000000
  e1000e 160582 0 - Live 0x0000000000000000
----- /proc/modules end -----
  used irqs: 0,1,3,4,7,8,9,12,17,18,19,20,21,22,40,41,42,43,44,45,46,47
=========== end debug info ============
01: None 00.0: 10105 BIOS
  [Created at bios.190]
  Unique ID: rdCR.lZF+r4EgHp4
  Hardware Class: bios
  BIOS Keyboard LED Status:
    Scroll Lock: off
    Num Lock: off
    Caps Lock: off
  Config Status: cfg=new, avail=yes, need=no, active=unknown

02: None 00.0: 10107 System
  [Created at sys.63]
  Unique ID: rdCR.n_7QNeEnh23
  Hardware Class: system
  Model: "System"
  Driver Info #0:
    Driver Status: thermal,fan are not active
    Driver Activation Cmd: "modprobe thermal; modprobe fan"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

03: None 00.0: 10104 FPU
  [Created at misc.192]
  Unique ID: rdCR.EMpH5pjcahD
  Hardware Class: unknown
  Model: "FPU"
  I/O Ports: 0xf0-0xff (rw)
  Config Status: cfg=new, avail=yes, need=no, active=unknown

04: None 00.0: 0801 DMA controller (8237)
  [Created at misc.206]
  Unique ID: rdCR.f5u1ucRm+H9
  Hardware Class: unknown
  Model: "DMA controller"
  I/O Ports: 0x00-0xcf7 (rw)
  I/O Ports: 0xc0-0xdf (rw)
  I/O Ports: 0x80-0x8f (rw)
  DMA: 4
  Config Status: cfg=new, avail=yes, need=no, active=unknown

05: None 00.0: 0800 PIC (8259)
  [Created at misc.219]
  Unique ID: rdCR.8uRK7LxiIA2
  Hardware Class: unknown
  Model: "PIC"
  I/O Ports: 0x20-0x21 (rw)
  I/O Ports: 0xa0-0xa1 (rw)
  Config Status: cfg=new, avail=yes, need=no, active=unknown

06: None 00.0: 0802 Timer (8254)
  [Created at misc.230]
  Unique ID: rdCR.AJKleuxpiP0
  Hardware Class: unknown
  Model: "Timer"
  IRQ: 0 (109850 events)
  Config Status: cfg=new, avail=yes, need=no, active=unknown

07: None 00.0: 0900 Keyboard controller
  [Created at misc.251]
  Unique ID: rdCR.9N+EecqykME
  Hardware Class: unknown
  Model: "Keyboard controller"
  I/O Port: 0x60 (rw)
  I/O Port: 0x64 (rw)
  Config Status: cfg=new, avail=yes, need=no, active=unknown

08: None 00.0: 0701 Parallel controller (SPP)
  [Created at misc.262]
  Unique ID: YMnp.ecK7NLYWZ5D
  Hardware Class: unknown
  Model: "Parallel controller"
  Device File: /dev/lp0
  I/O Ports: 0x378-0x37a (rw)
  I/O Ports: 0x778-0x77a (rw)
  DMA: 1
  IRQ: 7 (no events)
  Config Status: cfg=new, avail=yes, need=no, active=unknown

11: None 00.0: 10102 Main Memory
  [Created at memory.61]
  Unique ID: rdCR.CxwsZFjVASF
  Hardware Class: memory
  Model: "Main Memory"
  Memory Range: 0x00000000-0xf4a49fff (rw)
  Memory Size: 3 GB + 768 MB
  Config Status: cfg=new, avail=yes, need=no, active=unknown

12: PCI 00.0: 0600 Host bridge
  [Created at pci.318]
  Unique ID: qLht.g5e3bz_VyfC
  SysFS ID: /devices/pci0000:00/0000:00:00.0
  SysFS BusID: 0000:00:00.0
  Hardware Class: bridge
  Model: "Intel Mobile 4 Series Chipset Memory Controller Hub"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0x2a40 "Mobile 4 Series Chipset Memory Controller Hub"
  SubVendor: pci 0x1028 "Dell"
  SubDevice: pci 0x024f 
  Revision: 0x07
  Driver: "agpgart-intel"
  Module Alias: "pci:v00008086d00002A40sv00001028sd0000024Fbc06sc00i00"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

13: PCI 02.0: 0300 VGA compatible controller (VGA)
  [Created at pci.318]
  Unique ID: _Znp.fTsp+HYAhr8
  SysFS ID: /devices/pci0000:00/0000:00:02.0
  SysFS BusID: 0000:00:02.0
  Hardware Class: graphics card
  Model: "Intel Mobile 4 Series Chipset Integrated Graphics Controller"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0x2a42 "Mobile 4 Series Chipset Integrated Graphics Controller"
  SubVendor: pci 0x1028 "Dell"
  SubDevice: pci 0x024f 
  Revision: 0x07
  Driver: "i915"
  Driver Modules: "drm"
  Memory Range: 0xf6c00000-0xf6ffffff (rw,non-prefetchable)
  Memory Range: 0xe0000000-0xefffffff (ro,non-prefetchable)
  I/O Ports: 0xef98-0xef9f (rw)
  IRQ: 46 (65392 events)
  Module Alias: "pci:v00008086d00002A42sv00001028sd0000024Fbc03sc00i00"
  Driver Info #0:
    Driver Status: i915 is active
    Driver Activation Cmd: "modprobe i915"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

14: PCI 02.1: 0380 Display controller
  [Created at pci.318]
  Unique ID: ruGf.AwDSv7rqySE
  SysFS ID: /devices/pci0000:00/0000:00:02.1
  SysFS BusID: 0000:00:02.1
  Hardware Class: graphics card
  Model: "Intel Mobile 4 Series Chipset Integrated Graphics Controller"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0x2a43 "Mobile 4 Series Chipset Integrated Graphics Controller"
  SubVendor: pci 0x1028 "Dell"
  SubDevice: pci 0x024f 
  Revision: 0x07
  Memory Range: 0xf6b00000-0xf6bfffff (rw,non-prefetchable)
  Module Alias: "pci:v00008086d00002A43sv00001028sd0000024Fbc03sc80i00"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

15: PCI 19.0: 0200 Ethernet controller
  [Created at pci.318]
  Unique ID: rBUF.DspxR_P+1HD
  SysFS ID: /devices/pci0000:00/0000:00:19.0
  SysFS BusID: 0000:00:19.0
  Hardware Class: network
  Model: "Intel 82567LM Gigabit Network Connection"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0x10f5 "82567LM Gigabit Network Connection"
  SubVendor: pci 0x1028 "Dell"
  SubDevice: pci 0x024f 
  Revision: 0x03
  Driver: "e1000e"
  Driver Modules: "e1000e"
  Device File: eth0
  Memory Range: 0xf6ae0000-0xf6afffff (rw,non-prefetchable)
  Memory Range: 0xf6adb000-0xf6adbfff (rw,non-prefetchable)
  I/O Ports: 0xefe0-0xefff (rw)
  IRQ: 44 (3287 events)
  HW Address: 00:26:b9:c1:c5:00
  Link detected: yes
  Module Alias: "pci:v00008086d000010F5sv00001028sd0000024Fbc02sc00i00"
  Driver Info #0:
    Driver Status: e1000e is active
    Driver Activation Cmd: "modprobe e1000e"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

16: PCI 1a.0: 0c03 USB Controller (UHCI)
  [Created at pci.318]
  Unique ID: pwJ7.zEmL3P1Lr01
  SysFS ID: /devices/pci0000:00/0000:00:1a.0
  SysFS BusID: 0000:00:1a.0
  Hardware Class: usb controller
  Model: "Intel 82801I (ICH9 Family) USB UHCI Controller #4"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0x2937 "82801I (ICH9 Family) USB UHCI Controller #4"
  SubVendor: pci 0x1028 "Dell"
  SubDevice: pci 0x024f 
  Revision: 0x03
  Driver: "uhci_hcd"
  Driver Modules: "uhci_hcd"
  I/O Ports: 0x6f60-0x6f7f (rw)
  IRQ: 20 (172 events)
  Module Alias: "pci:v00008086d00002937sv00001028sd0000024Fbc0Csc03i00"
  Driver Info #0:
    Driver Status: uhci-hcd is not active
    Driver Activation Cmd: "modprobe uhci-hcd"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

17: PCI 1a.1: 0c03 USB Controller (UHCI)
  [Created at pci.318]
  Unique ID: gFpy.Ufi5Yz82NP1
  SysFS ID: /devices/pci0000:00/0000:00:1a.1
  SysFS BusID: 0000:00:1a.1
  Hardware Class: usb controller
  Model: "Intel 82801I (ICH9 Family) USB UHCI Controller #5"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0x2938 "82801I (ICH9 Family) USB UHCI Controller #5"
  SubVendor: pci 0x1028 "Dell"
  SubDevice: pci 0x024f 
  Revision: 0x03
  Driver: "uhci_hcd"
  Driver Modules: "uhci_hcd"
  I/O Ports: 0x6f80-0x6f9f (rw)
  IRQ: 21 (no events)
  Module Alias: "pci:v00008086d00002938sv00001028sd0000024Fbc0Csc03i00"
  Driver Info #0:
    Driver Status: uhci-hcd is not active
    Driver Activation Cmd: "modprobe uhci-hcd"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

18: PCI 1a.2: 0c03 USB Controller (UHCI)
  [Created at pci.318]
  Unique ID: XaIo.+3fr0YGlun1
  SysFS ID: /devices/pci0000:00/0000:00:1a.2
  SysFS BusID: 0000:00:1a.2
  Hardware Class: usb controller
  Model: "Intel 82801I (ICH9 Family) USB UHCI Controller #6"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0x2939 "82801I (ICH9 Family) USB UHCI Controller #6"
  SubVendor: pci 0x1028 "Dell"
  SubDevice: pci 0x024f 
  Revision: 0x03
  Driver: "uhci_hcd"
  Driver Modules: "uhci_hcd"
  I/O Ports: 0x6fa0-0x6fbf (rw)
  IRQ: 22 (17429 events)
  Module Alias: "pci:v00008086d00002939sv00001028sd0000024Fbc0Csc03i00"
  Driver Info #0:
    Driver Status: uhci-hcd is not active
    Driver Activation Cmd: "modprobe uhci-hcd"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

19: PCI 1a.7: 0c03 USB Controller (EHCI)
  [Created at pci.318]
  Unique ID: sClz.2K4HlJ6d+m7
  SysFS ID: /devices/pci0000:00/0000:00:1a.7
  SysFS BusID: 0000:00:1a.7
  Hardware Class: usb controller
  Model: "Intel 82801I (ICH9 Family) USB2 EHCI Controller #2"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0x293c "82801I (ICH9 Family) USB2 EHCI Controller #2"
  SubVendor: pci 0x1028 "Dell"
  SubDevice: pci 0x024f 
  Revision: 0x03
  Driver: "ehci_hcd"
  Driver Modules: "ehci_hcd"
  Memory Range: 0xfed1c400-0xfed1c7ff (rw,non-prefetchable)
  IRQ: 22 (17429 events)
  Module Alias: "pci:v00008086d0000293Csv00001028sd0000024Fbc0Csc03i20"
  Driver Info #0:
    Driver Status: ehci-hcd is not active
    Driver Activation Cmd: "modprobe ehci-hcd"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

20: PCI 1b.0: 0403 Audio device
  [Created at pci.318]
  Unique ID: u1Nb.SGxGJCiH+82
  SysFS ID: /devices/pci0000:00/0000:00:1b.0
  SysFS BusID: 0000:00:1b.0
  Hardware Class: sound
  Model: "Intel 82801I (ICH9 Family) HD Audio Controller"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0x293e "82801I (ICH9 Family) HD Audio Controller"
  SubVendor: pci 0x1028 "Dell"
  SubDevice: pci 0x024f 
  Revision: 0x03
  Driver: "HDA Intel"
  Driver Modules: "snd_hda_intel"
  Memory Range: 0xf6adc000-0xf6adffff (rw,non-prefetchable)
  IRQ: 47 (329 events)
  Module Alias: "pci:v00008086d0000293Esv00001028sd0000024Fbc04sc03i00"
  Driver Info #0:
    Driver Status: snd_hda_intel is active
    Driver Activation Cmd: "modprobe snd_hda_intel"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

21: PCI 1c.0: 0604 PCI bridge (Normal decode)
  [Created at pci.318]
  Unique ID: z8Q3.1HNJ3AEFeQ2
  SysFS ID: /devices/pci0000:00/0000:00:1c.0
  SysFS BusID: 0000:00:1c.0
  Hardware Class: bridge
  Model: "Intel 82801I (ICH9 Family) PCI Express Port 1"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0x2940 "82801I (ICH9 Family) PCI Express Port 1"
  SubVendor: pci 0x1028 "Dell"
  SubDevice: pci 0x024f 
  Revision: 0x03
  Driver: "pcieport"
  IRQ: 40 (no events)
  Module Alias: "pci:v00008086d00002940sv00001028sd0000024Fbc06sc04i00"
  Driver Info #0:
    Driver Status: shpchp is not active
    Driver Activation Cmd: "modprobe shpchp"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

22: PCI 1c.1: 0604 PCI bridge (Normal decode)
  [Created at pci.318]
  Unique ID: qTvu.36Gp0JTfhB3
  SysFS ID: /devices/pci0000:00/0000:00:1c.1
  SysFS BusID: 0000:00:1c.1
  Hardware Class: bridge
  Model: "Intel 82801I (ICH9 Family) PCI Express Port 2"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0x2942 "82801I (ICH9 Family) PCI Express Port 2"
  SubVendor: pci 0x1028 "Dell"
  SubDevice: pci 0x024f 
  Revision: 0x03
  Driver: "pcieport"
  IRQ: 41 (no events)
  Module Alias: "pci:v00008086d00002942sv00001028sd0000024Fbc06sc04i00"
  Driver Info #0:
    Driver Status: shpchp is not active
    Driver Activation Cmd: "modprobe shpchp"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

23: PCI 1c.2: 0604 PCI bridge (Normal decode)
  [Created at pci.318]
  Unique ID: hoOk.5x8J_Ri3ly3
  SysFS ID: /devices/pci0000:00/0000:00:1c.2
  SysFS BusID: 0000:00:1c.2
  Hardware Class: bridge
  Model: "Intel 82801I (ICH9 Family) PCI Express Port 3"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0x2944 "82801I (ICH9 Family) PCI Express Port 3"
  SubVendor: pci 0x1028 "Dell"
  SubDevice: pci 0x024f 
  Revision: 0x03
  Driver: "pcieport"
  IRQ: 42 (no events)
  Module Alias: "pci:v00008086d00002944sv00001028sd0000024Fbc06sc04i00"
  Driver Info #0:
    Driver Status: shpchp is not active
    Driver Activation Cmd: "modprobe shpchp"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

24: PCI 1c.3: 0604 PCI bridge (Normal decode)
  [Created at pci.318]
  Unique ID: Z7uZ.7m1pxaxToj4
  SysFS ID: /devices/pci0000:00/0000:00:1c.3
  SysFS BusID: 0000:00:1c.3
  Hardware Class: bridge
  Model: "Intel 82801I (ICH9 Family) PCI Express Port 4"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0x2946 "82801I (ICH9 Family) PCI Express Port 4"
  SubVendor: pci 0x1028 "Dell"
  SubDevice: pci 0x024f 
  Revision: 0x03
  Driver: "pcieport"
  IRQ: 43 (no events)
  Module Alias: "pci:v00008086d00002946sv00001028sd0000024Fbc06sc04i00"
  Driver Info #0:
    Driver Status: shpchp is not active
    Driver Activation Cmd: "modprobe shpchp"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

25: PCI 1d.0: 0c03 USB Controller (UHCI)
  [Created at pci.318]
  Unique ID: 1GTX.Q+w5dlK+FI1
  SysFS ID: /devices/pci0000:00/0000:00:1d.0
  SysFS BusID: 0000:00:1d.0
  Hardware Class: usb controller
  Model: "Intel 82801I (ICH9 Family) USB UHCI Controller #1"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0x2934 "82801I (ICH9 Family) USB UHCI Controller #1"
  SubVendor: pci 0x1028 "Dell"
  SubDevice: pci 0x024f 
  Revision: 0x03
  Driver: "uhci_hcd"
  Driver Modules: "uhci_hcd"
  I/O Ports: 0x6f00-0x6f1f (rw)
  IRQ: 20 (172 events)
  Module Alias: "pci:v00008086d00002934sv00001028sd0000024Fbc0Csc03i00"
  Driver Info #0:
    Driver Status: uhci-hcd is not active
    Driver Activation Cmd: "modprobe uhci-hcd"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

26: PCI 1d.1: 0c03 USB Controller (UHCI)
  [Created at pci.318]
  Unique ID: vayM.xPtr5KSing1
  SysFS ID: /devices/pci0000:00/0000:00:1d.1
  SysFS BusID: 0000:00:1d.1
  Hardware Class: usb controller
  Model: "Intel 82801I (ICH9 Family) USB UHCI Controller #2"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0x2935 "82801I (ICH9 Family) USB UHCI Controller #2"
  SubVendor: pci 0x1028 "Dell"
  SubDevice: pci 0x024f 
  Revision: 0x03
  Driver: "uhci_hcd"
  Driver Modules: "uhci_hcd"
  I/O Ports: 0x6f20-0x6f3f (rw)
  IRQ: 21 (no events)
  Module Alias: "pci:v00008086d00002935sv00001028sd0000024Fbc0Csc03i00"
  Driver Info #0:
    Driver Status: uhci-hcd is not active
    Driver Activation Cmd: "modprobe uhci-hcd"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

27: PCI 1d.2: 0c03 USB Controller (UHCI)
  [Created at pci.318]
  Unique ID: mvRC.SqpbauZPJ32
  SysFS ID: /devices/pci0000:00/0000:00:1d.2
  SysFS BusID: 0000:00:1d.2
  Hardware Class: usb controller
  Model: "Intel 82801I (ICH9 Family) USB UHCI Controller #3"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0x2936 "82801I (ICH9 Family) USB UHCI Controller #3"
  SubVendor: pci 0x1028 "Dell"
  SubDevice: pci 0x024f 
  Revision: 0x03
  Driver: "uhci_hcd"
  Driver Modules: "uhci_hcd"
  I/O Ports: 0x6f40-0x6f5f (rw)
  IRQ: 22 (17429 events)
  Module Alias: "pci:v00008086d00002936sv00001028sd0000024Fbc0Csc03i00"
  Driver Info #0:
    Driver Status: uhci-hcd is not active
    Driver Activation Cmd: "modprobe uhci-hcd"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

28: PCI 1d.7: 0c03 USB Controller (EHCI)
  [Created at pci.318]
  Unique ID: 5YuN.0VBnnAtCy+6
  SysFS ID: /devices/pci0000:00/0000:00:1d.7
  SysFS BusID: 0000:00:1d.7
  Hardware Class: usb controller
  Model: "Intel 82801I (ICH9 Family) USB2 EHCI Controller #1"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0x293a "82801I (ICH9 Family) USB2 EHCI Controller #1"
  SubVendor: pci 0x1028 "Dell"
  SubDevice: pci 0x024f 
  Revision: 0x03
  Driver: "ehci_hcd"
  Driver Modules: "ehci_hcd"
  Memory Range: 0xfed1c000-0xfed1c3ff (rw,non-prefetchable)
  IRQ: 20 (172 events)
  Module Alias: "pci:v00008086d0000293Asv00001028sd0000024Fbc0Csc03i20"
  Driver Info #0:
    Driver Status: ehci-hcd is not active
    Driver Activation Cmd: "modprobe ehci-hcd"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

29: PCI 1e.0: 0604 PCI bridge (Subtractive decode)
  [Created at pci.318]
  Unique ID: 6NW+.D0CgCP5hV+8
  SysFS ID: /devices/pci0000:00/0000:00:1e.0
  SysFS BusID: 0000:00:1e.0
  Hardware Class: bridge
  Model: "Intel 82801 Mobile PCI Bridge"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0x2448 "82801 Mobile PCI Bridge"
  SubVendor: pci 0x1028 "Dell"
  SubDevice: pci 0x024f 
  Revision: 0x93
  Module Alias: "pci:v00008086d00002448sv00001028sd0000024Fbc06sc04i01"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

30: PCI 1f.0: 0601 ISA bridge
  [Created at pci.318]
  Unique ID: BUZT.LfLT41XywmE
  SysFS ID: /devices/pci0000:00/0000:00:1f.0
  SysFS BusID: 0000:00:1f.0
  Hardware Class: bridge
  Model: "Intel ICH9M-E LPC Interface Controller"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0x2917 "ICH9M-E LPC Interface Controller"
  SubVendor: pci 0x1028 "Dell"
  SubDevice: pci 0x024f 
  Revision: 0x03
  Module Alias: "pci:v00008086d00002917sv00001028sd0000024Fbc06sc01i00"
  Driver Info #0:
    Driver Status: iTCO_wdt is not active
    Driver Activation Cmd: "modprobe iTCO_wdt"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

31: PCI 1f.2: 0104 RAID bus controller
  [Created at pci.318]
  Unique ID: w7Y8.zLI+X3nl8w7
  SysFS ID: /devices/pci0000:00/0000:00:1f.2
  SysFS BusID: 0000:00:1f.2
  Hardware Class: storage
  Model: "Intel Mobile 82801 SATA RAID Controller"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0x282a "Mobile 82801 SATA RAID Controller"
  SubVendor: pci 0x1028 "Dell"
  SubDevice: pci 0x024f 
  Revision: 0x03
  Driver: "ahci"
  Driver Modules: "ahci"
  I/O Ports: 0x6e70-0x6e77 (rw)
  I/O Ports: 0x6e78-0x6e7b (rw)
  I/O Ports: 0x6e80-0x6e87 (rw)
  I/O Ports: 0x6e88-0x6e8b (rw)
  I/O Ports: 0x6ea0-0x6ebf (rw)
  Memory Range: 0xfed1c800-0xfed1cfff (rw,non-prefetchable)
  IRQ: 45 (74222 events)
  Module Alias: "pci:v00008086d0000282Asv00001028sd0000024Fbc01sc04i00"
  Driver Info #0:
    Driver Status: ahci is active
    Driver Activation Cmd: "modprobe ahci"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

32: PCI 1f.3: 0c05 SMBus
  [Created at pci.318]
  Unique ID: nS1_.Om1XD1tHZ+D
  SysFS ID: /devices/pci0000:00/0000:00:1f.3
  SysFS BusID: 0000:00:1f.3
  Hardware Class: unknown
  Model: "Intel 82801I (ICH9 Family) SMBus Controller"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0x2930 "82801I (ICH9 Family) SMBus Controller"
  SubVendor: pci 0x1028 "Dell"
  SubDevice: pci 0x024f 
  Revision: 0x03
  Memory Range: 0xf6adaf00-0xf6adafff (rw,non-prefetchable)
  I/O Ports: 0x1100-0x111f (rw)
  IRQ: 3 (no events)
  Module Alias: "pci:v00008086d00002930sv00001028sd0000024Fbc0Csc05i00"
  Driver Info #0:
    Driver Status: i2c_i801 is not active
    Driver Activation Cmd: "modprobe i2c_i801"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

33: PCI c00.0: 0200 Ethernet controller
  [Created at pci.318]
  Unique ID: mY_N.gwDnaUUtfJC
  Parent ID: qTvu.36Gp0JTfhB3
  SysFS ID: /devices/pci0000:00/0000:00:1c.1/0000:0c:00.0
  SysFS BusID: 0000:0c:00.0
  Hardware Class: network
  Model: "Dell Wireless 1510 Wireless-N WLAN Mini-Card"
  Vendor: pci 0x14e4 "Broadcom"
  Device: pci 0x432b "BCM4322 802.11a/b/g/n Wireless LAN Controller"
  SubVendor: pci 0x1028 "Dell"
  SubDevice: pci 0x000d "Wireless 1510 Wireless-N WLAN Mini-Card"
  Revision: 0x01
  Driver: "wl"
  Driver Modules: "wl"
  Device File: eth2
  Memory Range: 0xf69fc000-0xf69fffff (rw,non-prefetchable)
  IRQ: 17 (1031 events)
  HW Address: f0:7b:cb:73:88:8d
  Link detected: yes
  Module Alias: "pci:v000014E4d0000432Bsv00001028sd0000000Dbc02sc80i00"
  Driver Info #0:
    Driver Status: ssb is not active
    Driver Activation Cmd: "modprobe ssb"
  Driver Info #1:
    Driver Status: wl is active
    Driver Activation Cmd: "modprobe wl"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #22 (PCI bridge)

34: PCI 301.0: 0607 CardBus bridge
  [Created at pci.318]
  Unique ID: x0Ln.N1DekKV55+6
  Parent ID: 6NW+.D0CgCP5hV+8
  SysFS ID: /devices/pci0000:00/0000:00:1e.0/0000:03:01.0
  SysFS BusID: 0000:03:01.0
  Hardware Class: bridge
  Model: "Ricoh RL5c476 II"
  Vendor: pci 0x1180 "Ricoh Co Ltd"
  Device: pci 0x0476 "RL5c476 II"
  SubVendor: pci 0x1028 "Dell"
  SubDevice: pci 0x024f 
  Revision: 0xba
  Driver: "yenta_cardbus"
  Driver Modules: "yenta_socket"
  Memory Range: 0xf6500000-0xf6500fff (rw,non-prefetchable)
  IRQ: 19 (no events)
  Module Alias: "pci:v00001180d00000476sv00001028sd0000024Fbc06sc07i00"
  Driver Info #0:
    Driver Status: yenta_socket is active
    Driver Activation Cmd: "modprobe yenta_socket"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #29 (PCI bridge)

35: PCI 301.1: 0c00 FireWire (IEEE 1394) (OHCI)
  [Created at pci.318]
  Unique ID: pLqc.mUT3jsg0pC9
  Parent ID: 6NW+.D0CgCP5hV+8
  SysFS ID: /devices/pci0000:00/0000:00:1e.0/0000:03:01.1
  SysFS BusID: 0000:03:01.1
  Hardware Class: firewire controller
  Model: "Ricoh R5C832 IEEE 1394 Controller"
  Vendor: pci 0x1180 "Ricoh Co Ltd"
  Device: pci 0x0832 "R5C832 IEEE 1394 Controller"
  SubVendor: pci 0x1028 "Dell"
  SubDevice: pci 0x024f 
  Revision: 0x04
  Driver: "firewire_ohci"
  Driver Modules: "firewire_ohci"
  Memory Range: 0xf65ff800-0xf65fffff (rw,non-prefetchable)
  IRQ: 17 (1031 events)
  Module Alias: "pci:v00001180d00000832sv00001028sd0000024Fbc0Csc00i10"
  Driver Info #0:
    Driver Status: ohci1394 is not active
    Driver Activation Cmd: "modprobe ohci1394"
  Driver Info #1:
    Driver Status: firewire_ohci is active
    Driver Activation Cmd: "modprobe firewire_ohci"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #29 (PCI bridge)

36: PCI 301.2: 0805 SD Host controller
  [Created at pci.318]
  Unique ID: ggJS.lyitnPuGpr6
  Parent ID: 6NW+.D0CgCP5hV+8
  SysFS ID: /devices/pci0000:00/0000:00:1e.0/0000:03:01.2
  SysFS BusID: 0000:03:01.2
  Hardware Class: unknown
  Model: "Ricoh R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter"
  Vendor: pci 0x1180 "Ricoh Co Ltd"
  Device: pci 0x0822 "R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter"
  SubVendor: pci 0x1028 "Dell"
  SubDevice: pci 0x024f 
  Revision: 0x21
  Driver: "sdhci-pci"
  Driver Modules: "sdhci_pci"
  Memory Range: 0xf65ff700-0xf65ff7ff (rw,non-prefetchable)
  IRQ: 18 (1031 events)
  Module Alias: "pci:v00001180d00000822sv00001028sd0000024Fbc08sc05i01"
  Driver Info #0:
    Driver Status: sdhci_pci is active
    Driver Activation Cmd: "modprobe sdhci_pci"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #29 (PCI bridge)

37: None 00.0: 0700 Serial controller
  [Created at misc.449]
  Unique ID: rdCR.7RG8lK_UzJ9
  Hardware Class: unknown
  Model: "Serial controller"
  I/O Ports: 0x3f8-0x3ff (rw)
  IRQ: 4 (3 events)
  Config Status: cfg=new, avail=yes, need=no, active=unknown

38: None 00.0: 10600 Disk
  [Created at block.243]
  Unique ID: HAKk.Fxp0d3BezAE
  Parent ID: ggJS.lyitnPuGpr6
  SysFS ID: /class/block/mmcblk0
  SysFS BusID: mmc0:0007
  SysFS Device Link: /devices/pci0000:00/0000:00:1e.0/0000:03:01.2/mmc_host/mmc0/mmc0:0007
  Hardware Class: disk
  Model: "Disk"
  Driver: "sdhci-pci", "mmcblk"
  Driver Modules: "sdhci_pci"
  Device File: /dev/mmcblk0
  Device Files: /dev/mmcblk0, /dev/disk/by-id/mmc-SD04G_0xb000631b, /dev/disk/by-path/pci-0000:03:01.2
  Device Number: block 179:0-179:7
  Drive status: no medium
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #36 (SD Host controller)

39: None 00.0: 11300 Partition
  [Created at block.412]
  Unique ID: l7UW.SE1wIdpsiiC
  Parent ID: HAKk.Fxp0d3BezAE
  SysFS ID: /class/block/mmcblk0/mmcblk0p1
  Hardware Class: partition
  Model: "Partition"
  Device File: /dev/mmcblk0p1
  Device Files: /dev/mmcblk0p1, /dev/disk/by-id/mmc-SD04G_0xb000631b-part1, /dev/disk/by-path/pci-0000:03:01.2-part1, /dev/disk/by-uuid/3B2B-5097, /dev/disk/by-label/DATA
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #38 (Disk)

40: IDE 00.0: 10600 Disk
  [Created at block.243]
  Unique ID: 3OOL.UMahlgDMi66
  Parent ID: w7Y8.zLI+X3nl8w7
  SysFS ID: /class/block/sda
  SysFS BusID: 0:0:0:0
  SysFS Device Link: /devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0
  Hardware Class: disk
  Model: "ST9250410ASG"
  Device: "ST9250410ASG"
  Revision: "0002"
  Driver: "ahci", "sd"
  Driver Modules: "ahci"
  Device File: /dev/sda
  Device Files: /dev/sda, /dev/disk/by-id/ata-ST9250410ASG_5VG5AW0Z, /dev/disk/by-id/scsi-SATA_ST9250410ASG_5VG5AW0Z, /dev/disk/by-path/pci-0000:00:1f.2-scsi-0:0:0:0, /dev/disk/by-id/wwn-0x5000c500251025f4
  Device Number: block 8:0-8:15
  Drive status: no medium
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #31 (RAID bus controller)

41: None 00.0: 11300 Partition
  [Created at block.412]
  Unique ID: bdUI.SE1wIdpsiiC
  Parent ID: 3OOL.UMahlgDMi66
  SysFS ID: /class/block/sda/sda1
  Hardware Class: partition
  Model: "Partition"
  Device File: /dev/sda1
  Device Files: /dev/sda1, /dev/disk/by-id/ata-ST9250410ASG_5VG5AW0Z-part1, /dev/disk/by-id/scsi-SATA_ST9250410ASG_5VG5AW0Z-part1, /dev/disk/by-path/pci-0000:00:1f.2-scsi-0:0:0:0-part1, /dev/disk/by-uuid/A8EE7F75EE7F3B20, /dev/disk/by-label/System\x20Reserved, /dev/disk/by-id/wwn-0x5000c500251025f4-part1
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #40 (Disk)

42: None 00.0: 11300 Partition
  [Created at block.412]
  Unique ID: 2pkM.SE1wIdpsiiC
  Parent ID: 3OOL.UMahlgDMi66
  SysFS ID: /class/block/sda/sda2
  Hardware Class: partition
  Model: "Partition"
  Device File: /dev/sda2
  Device Files: /dev/sda2, /dev/disk/by-id/ata-ST9250410ASG_5VG5AW0Z-part2, /dev/disk/by-id/scsi-SATA_ST9250410ASG_5VG5AW0Z-part2, /dev/disk/by-path/pci-0000:00:1f.2-scsi-0:0:0:0-part2, /dev/disk/by-uuid/2bdc1a9a-8cf1-4e51-8e7a-0717443ce6c8, /dev/disk/by-id/wwn-0x5000c500251025f4-part2
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #40 (Disk)

43: None 00.0: 11300 Partition
  [Created at block.412]
  Unique ID: z9FV.SE1wIdpsiiC
  Parent ID: 3OOL.UMahlgDMi66
  SysFS ID: /class/block/sda/sda4
  Hardware Class: partition
  Model: "Partition"
  Device File: /dev/sda4
  Device Files: /dev/sda4, /dev/disk/by-id/ata-ST9250410ASG_5VG5AW0Z-part4, /dev/disk/by-id/scsi-SATA_ST9250410ASG_5VG5AW0Z-part4, /dev/disk/by-path/pci-0000:00:1f.2-scsi-0:0:0:0-part4, /dev/disk/by-id/wwn-0x5000c500251025f4-part4
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #40 (Disk)

44: None 00.0: 11300 Partition
  [Created at block.412]
  Unique ID: QLVZ.SE1wIdpsiiC
  Parent ID: 3OOL.UMahlgDMi66
  SysFS ID: /class/block/sda/sda5
  Hardware Class: partition
  Model: "Partition"
  Device File: /dev/sda5
  Device Files: /dev/sda5, /dev/disk/by-id/ata-ST9250410ASG_5VG5AW0Z-part5, /dev/disk/by-id/scsi-SATA_ST9250410ASG_5VG5AW0Z-part5, /dev/disk/by-path/pci-0000:00:1f.2-scsi-0:0:0:0-part5, /dev/disk/by-uuid/b2d1e233-8260-43f6-b0a0-be7c7d903301, /dev/disk/by-label/swap, /dev/disk/by-id/wwn-0x5000c500251025f4-part5
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #40 (Disk)

45: None 00.0: 11300 Partition
  [Created at block.412]
  Unique ID: tWld.SE1wIdpsiiC
  Parent ID: 3OOL.UMahlgDMi66
  SysFS ID: /class/block/sda/sda6
  Hardware Class: partition
  Model: "Partition"
  Device File: /dev/sda6
  Device Files: /dev/sda6, /dev/disk/by-id/ata-ST9250410ASG_5VG5AW0Z-part6, /dev/disk/by-id/scsi-SATA_ST9250410ASG_5VG5AW0Z-part6, /dev/disk/by-path/pci-0000:00:1f.2-scsi-0:0:0:0-part6, /dev/disk/by-uuid/25bdc29e-9e7c-467b-b63b-a6456e2c667b, /dev/disk/by-label/\x2fhome, /dev/disk/by-id/wwn-0x5000c500251025f4-part6
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #40 (Disk)

46: SCSI 100.0: 10602 CD-ROM (DVD)
  [Created at block.247]
  Unique ID: KD9E.mEFpAo01le1
  Parent ID: w7Y8.zLI+X3nl8w7
  SysFS ID: /class/block/sr0
  SysFS BusID: 1:0:0:0
  SysFS Device Link: /devices/pci0000:00/0000:00:1f.2/host1/target1:0:0/1:0:0:0
  Hardware Class: cdrom
  Model: "HL-DT-ST DVD+-RW GU10N"
  Vendor: "HL-DT-ST"
  Device: "DVD+-RW GU10N"
  Revision: "A102"
  Driver: "ahci", "sr"
  Driver Modules: "ahci"
  Device File: /dev/sr0 (/dev/sg1)
  Device Files: /dev/sr0, /dev/scd0, /dev/disk/by-id/ata-HL-DT-ST_DVD+_-RW_GU10N_KVEA3B93937, /dev/disk/by-path/pci-0000:00:1f.2-scsi-1:0:0:0, /dev/cdrom1, /dev/cdrw1, /dev/dvd1, /dev/dvdrw1
  Device Number: block 11:0 (char 21:1)
  Features: DVD
  Drive status: no medium
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #31 (RAID bus controller)
  Drive Speed: 24

47: SCSI 600.1: 10602 CD-ROM
  [Created at block.247]
  Unique ID: kzsy.6SYkiKiJsF0
  Parent ID: sClz.2K4HlJ6d+m7
  SysFS ID: /class/block/sr1
  SysFS BusID: 6:0:0:1
  SysFS Device Link: /devices/pci0000:00/0000:00:1a.7/usb1/1-3/1-3.1/1-3.1.3/1-3.1.3:1.0/host6/target6:0:0/6:0:0:1
  Hardware Class: cdrom
  Model: "WD Virtual CD 070A"
  Vendor: usb 0x1058 "WD"
  Device: usb 0x070a "Virtual CD 070A"
  Revision: "1030"
  Serial ID: "57584D304139395330373331"
  Driver: "usb-storage", "sr"
  Driver Modules: "usb_storage"
  Device File: /dev/sr1 (/dev/sg3)
  Device Files: /dev/sr1, /dev/scd1, /dev/disk/by-id/usb-WD_Virtual_CD_070A_57584D304139395330373331-0:1, /dev/disk/by-path/pci-0000:00:1a.7-usb-0:3.1.3:1.0-scsi-0:0:0:1, /dev/disk/by-label/WD\x20SmartWare, /dev/cdrom
  Device Number: block 11:1 (char 21:3)
  Speed: 480 Mbps
  Module Alias: "usb:v1058p070Ad1030dc00dsc00dp00ic08isc06ip50"
  Driver Info #0:
    Driver Status: uas is active
    Driver Activation Cmd: "modprobe uas"
  Driver Info #1:
    Driver Status: usb_storage is active
    Driver Activation Cmd: "modprobe usb_storage"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #19 (USB Controller)
  Drive Speed: 51

48: SCSI 600.0: 10600 Disk
  [Created at block.243]
  Unique ID: uI_Q.c_88VrmYtvE
  Parent ID: sClz.2K4HlJ6d+m7
  SysFS ID: /class/block/sdb
  SysFS BusID: 6:0:0:0
  SysFS Device Link: /devices/pci0000:00/0000:00:1a.7/usb1/1-3/1-3.1/1-3.1.3/1-3.1.3:1.0/host6/target6:0:0/6:0:0:0
  Hardware Class: disk
  Model: "WD My Passport 070A"
  Vendor: usb 0x1058 "WD"
  Device: usb 0x070a "My Passport 070A"
  Revision: "1030"
  Driver: "usb-storage", "sd"
  Driver Modules: "usb_storage"
  Device File: /dev/sdb (/dev/sg2)
  Device Files: /dev/sdb, /dev/disk/by-id/ata-WDC_WD5000BMVV-11A1CS0_WD-WXM0A99S0731, /dev/disk/by-id/scsi-SWD_My_Passport_070WXM0A99S0731, /dev/disk/by-path/pci-0000:00:1a.7-usb-0:3.1.3:1.0-scsi-0:0:0:0, /dev/disk/by-id/wwn-0x50014ee2ae2b6104
  Device Number: block 8:16-8:31 (char 21:2)
  Drive status: no medium
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #19 (USB Controller)

49: None 00.0: 11300 Partition
  [Created at block.412]
  Unique ID: h4pj.SE1wIdpsiiC
  Parent ID: uI_Q.c_88VrmYtvE
  SysFS ID: /class/block/sdb/sdb1
  Hardware Class: partition
  Model: "Partition"
  Device File: /dev/sdb1
  Device Files: /dev/sdb1, /dev/disk/by-id/ata-WDC_WD5000BMVV-11A1CS0_WD-WXM0A99S0731-part1, /dev/disk/by-id/scsi-SWD_My_Passport_070WXM0A99S0731-part1, /dev/disk/by-path/pci-0000:00:1a.7-usb-0:3.1.3:1.0-scsi-0:0:0:0-part1, /dev/disk/by-uuid/325220A852207331, /dev/disk/by-label/My\x20Passport, /dev/disk/by-id/wwn-0x50014ee2ae2b6104-part1
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #48 (Disk)

50: USB 00.0: 10a00 Hub
  [Created at usb.122]
  Unique ID: k4bc.cO89g+iefn1
  Parent ID: sClz.2K4HlJ6d+m7
  SysFS ID: /devices/pci0000:00/0000:00:1a.7/usb1/1-0:1.0
  SysFS BusID: 1-0:1.0
  Hardware Class: hub
  Model: "Linux 3.0.0-14-generic ehci_hcd EHCI Host Controller"
  Hotplug: USB
  Vendor: usb 0x1d6b "Linux 3.0.0-14-generic ehci_hcd"
  Device: usb 0x0002 "EHCI Host Controller"
  Revision: "3.00"
  Serial ID: "0000:00:1a.7"
  Driver: "hub"
  Driver Modules: "usbcore"
  Speed: 480 Mbps
  Module Alias: "usb:v1D6Bp0002d0300dc09dsc00dp00ic09isc00ip00"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #19 (USB Controller)

51: USB 00.0: 10a00 Hub
  [Created at usb.122]
  Unique ID: pBe4.9T1GDCLyFd9
  Parent ID: 5YuN.0VBnnAtCy+6
  SysFS ID: /devices/pci0000:00/0000:00:1d.7/usb2/2-0:1.0
  SysFS BusID: 2-0:1.0
  Hardware Class: hub
  Model: "Linux 3.0.0-14-generic ehci_hcd EHCI Host Controller"
  Hotplug: USB
  Vendor: usb 0x1d6b "Linux 3.0.0-14-generic ehci_hcd"
  Device: usb 0x0002 "EHCI Host Controller"
  Revision: "3.00"
  Serial ID: "0000:00:1d.7"
  Driver: "hub"
  Driver Modules: "usbcore"
  Speed: 480 Mbps
  Module Alias: "usb:v1D6Bp0002d0300dc09dsc00dp00ic09isc00ip00"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #28 (USB Controller)

52: USB 00.0: 10a00 Hub
  [Created at usb.122]
  Unique ID: uIhY.MxUuepIFPaE
  Parent ID: pwJ7.zEmL3P1Lr01
  SysFS ID: /devices/pci0000:00/0000:00:1a.0/usb3/3-0:1.0
  SysFS BusID: 3-0:1.0
  Hardware Class: hub
  Model: "Linux 3.0.0-14-generic uhci_hcd UHCI Host Controller"
  Hotplug: USB
  Vendor: usb 0x1d6b "Linux 3.0.0-14-generic uhci_hcd"
  Device: usb 0x0001 "UHCI Host Controller"
  Revision: "3.00"
  Serial ID: "0000:00:1a.0"
  Driver: "hub"
  Driver Modules: "usbcore"
  Speed: 12 Mbps
  Module Alias: "usb:v1D6Bp0001d0300dc09dsc00dp00ic09isc00ip00"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #16 (USB Controller)

53: USB 00.0: 10a00 Hub
  [Created at usb.122]
  Unique ID: zPk0.7gZT0a5zLs5
  Parent ID: gFpy.Ufi5Yz82NP1
  SysFS ID: /devices/pci0000:00/0000:00:1a.1/usb4/4-0:1.0
  SysFS BusID: 4-0:1.0
  Hardware Class: hub
  Model: "Linux 3.0.0-14-generic uhci_hcd UHCI Host Controller"
  Hotplug: USB
  Vendor: usb 0x1d6b "Linux 3.0.0-14-generic uhci_hcd"
  Device: usb 0x0001 "UHCI Host Controller"
  Revision: "3.00"
  Serial ID: "0000:00:1a.1"
  Driver: "hub"
  Driver Modules: "usbcore"
  Speed: 12 Mbps
  Module Alias: "usb:v1D6Bp0001d0300dc09dsc00dp00ic09isc00ip00"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #17 (USB Controller)

54: USB 00.0: 10a00 Hub
  [Created at usb.122]
  Unique ID: 2XnU.uOe2OKugI8D
  Parent ID: XaIo.+3fr0YGlun1
  SysFS ID: /devices/pci0000:00/0000:00:1a.2/usb5/5-0:1.0
  SysFS BusID: 5-0:1.0
  Hardware Class: hub
  Model: "Linux 3.0.0-14-generic uhci_hcd UHCI Host Controller"
  Hotplug: USB
  Vendor: usb 0x1d6b "Linux 3.0.0-14-generic uhci_hcd"
  Device: usb 0x0001 "UHCI Host Controller"
  Revision: "3.00"
  Serial ID: "0000:00:1a.2"
  Driver: "hub"
  Driver Modules: "usbcore"
  Speed: 12 Mbps
  Module Alias: "usb:v1D6Bp0001d0300dc09dsc00dp00ic09isc00ip00"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #18 (USB Controller)

55: USB 00.0: 10a00 Hub
  [Created at usb.122]
  Unique ID: 7eqy.v+N+B0xY+P6
  Parent ID: 1GTX.Q+w5dlK+FI1
  SysFS ID: /devices/pci0000:00/0000:00:1d.0/usb6/6-0:1.0
  SysFS BusID: 6-0:1.0
  Hardware Class: hub
  Model: "Linux 3.0.0-14-generic uhci_hcd UHCI Host Controller"
  Hotplug: USB
  Vendor: usb 0x1d6b "Linux 3.0.0-14-generic uhci_hcd"
  Device: usb 0x0001 "UHCI Host Controller"
  Revision: "3.00"
  Serial ID: "0000:00:1d.0"
  Driver: "hub"
  Driver Modules: "usbcore"
  Speed: 12 Mbps
  Module Alias: "usb:v1D6Bp0001d0300dc09dsc00dp00ic09isc00ip00"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #25 (USB Controller)

56: USB 00.0: 10a00 Hub
  [Created at usb.122]
  Unique ID: BSFT.gkSaZmjGyhD
  Parent ID: vayM.xPtr5KSing1
  SysFS ID: /devices/pci0000:00/0000:00:1d.1/usb7/7-0:1.0
  SysFS BusID: 7-0:1.0
  Hardware Class: hub
  Model: "Linux 3.0.0-14-generic uhci_hcd UHCI Host Controller"
  Hotplug: USB
  Vendor: usb 0x1d6b "Linux 3.0.0-14-generic uhci_hcd"
  Device: usb 0x0001 "UHCI Host Controller"
  Revision: "3.00"
  Serial ID: "0000:00:1d.1"
  Driver: "hub"
  Driver Modules: "usbcore"
  Speed: 12 Mbps
  Module Alias: "usb:v1D6Bp0001d0300dc09dsc00dp00ic09isc00ip00"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #26 (USB Controller)

57: USB 00.0: 10a00 Hub
  [Created at usb.122]
  Unique ID: FZIx.RTX9xWW_uz4
  Parent ID: mvRC.SqpbauZPJ32
  SysFS ID: /devices/pci0000:00/0000:00:1d.2/usb8/8-0:1.0
  SysFS BusID: 8-0:1.0
  Hardware Class: hub
  Model: "Linux 3.0.0-14-generic uhci_hcd UHCI Host Controller"
  Hotplug: USB
  Vendor: usb 0x1d6b "Linux 3.0.0-14-generic uhci_hcd"
  Device: usb 0x0001 "UHCI Host Controller"
  Revision: "3.00"
  Serial ID: "0000:00:1d.2"
  Driver: "hub"
  Driver Modules: "usbcore"
  Speed: 12 Mbps
  Module Alias: "usb:v1D6Bp0001d0300dc09dsc00dp00ic09isc00ip00"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #27 (USB Controller)

58: USB 00.0: 10a00 Hub
  [Created at usb.122]
  Unique ID: 2UT6._H8jkZcj4d2
  Parent ID: k4bc.cO89g+iefn1
  SysFS ID: /devices/pci0000:00/0000:00:1a.7/usb1/1-3/1-3:1.0
  SysFS BusID: 1-3:1.0
  Hardware Class: hub
  Model: "Dell Hub"
  Hotplug: USB
  Vendor: usb 0x413c "Dell Computer Corp."
  Device: usb 0x2513 
  Revision: "a0.05"
  Driver: "hub"
  Driver Modules: "usbcore"
  Speed: 480 Mbps
  Module Alias: "usb:v413Cp2513dA005dc09dsc00dp02ic09isc00ip02"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #50 (Hub)

59: USB 00.0: 10a00 Hub
  [Created at usb.122]
  Unique ID: Uc5H._H8jkZcj4d2
  Parent ID: k4bc.cO89g+iefn1
  SysFS ID: /devices/pci0000:00/0000:00:1a.7/usb1/1-4/1-4:1.0
  SysFS BusID: 1-4:1.0
  Hardware Class: hub
  Model: "Dell Hub"
  Hotplug: USB
  Vendor: usb 0x413c "Dell Computer Corp."
  Device: usb 0x2513 
  Revision: "a0.05"
  Driver: "hub"
  Driver Modules: "usbcore"
  Speed: 480 Mbps
  Module Alias: "usb:v413Cp2513dA005dc09dsc00dp02ic09isc00ip02"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #50 (Hub)

60: USB 00.0: 0000 Unclassified device
  [Created at usb.122]
  Unique ID: MtLc.ZZ+SA7KltS2
  Parent ID: k4bc.cO89g+iefn1
  SysFS ID: /devices/pci0000:00/0000:00:1a.7/usb1/1-6/1-6:1.0
  SysFS BusID: 1-6:1.0
  Hardware Class: unknown
  Model: "Microdia Integrated_Webcam_2M"
  Hotplug: USB
  Vendor: usb 0x0c45 "Microdia"
  Device: usb 0x63f1 "Integrated_Webcam_2M"
  Revision: "94.16"
  Driver: "uvcvideo"
  Driver Modules: "uvcvideo"
  Device File: /dev/input/event6
  Device Files: /dev/input/event6, /dev/input/by-id/usb-CN0K113P7248703G05EC_Integrated_Webcam_2M-event-if00, /dev/input/by-path/pci-0000:00:1a.7-usb-0:6:1.0-event
  Device Number: char 13:70
  Speed: 480 Mbps
  Module Alias: "usb:v0C45p63F1d9416dcEFdsc02dp01ic0Eisc01ip00"
  Driver Info #0:
    Driver Status: uvcvideo is active
    Driver Activation Cmd: "modprobe uvcvideo"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #50 (Hub)

62: USB 00.0: 10a00 Hub
  [Created at usb.122]
  Unique ID: KRJj.SAMIiYMCz2F
  Parent ID: uIhY.MxUuepIFPaE
  SysFS ID: /devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1:1.0
  SysFS BusID: 3-1:1.0
  Hardware Class: hub
  Model: "Broadcom BCM2046B1"
  Hotplug: USB
  Vendor: usb 0x0a5c "Broadcom Corp."
  Device: usb 0x4500 "BCM2046B1"
  Revision: "1.00"
  Driver: "hub"
  Driver Modules: "usbcore"
  Speed: 12 Mbps
  Module Alias: "usb:v0A5Cp4500d0100dc09dsc00dp00ic09isc00ip00"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #52 (Hub)

63: USB 00.0: 0000 Unclassified device
  [Created at usb.122]
  Unique ID: cKwp.hVUwYQ7Uxx1
  Parent ID: 2XnU.uOe2OKugI8D
  SysFS ID: /devices/pci0000:00/0000:00:1a.2/usb5/5-1/5-1:0.0
  SysFS BusID: 5-1:0.0
  Hardware Class: unknown
  Model: "Broadcom 5880"
  Hotplug: USB
  Vendor: usb 0x0a5c "Broadcom Corp."
  Device: usb 0x5800 "5880"
  Revision: "1.01"
  Serial ID: "0123456789ABCD"
  Speed: 12 Mbps
  Module Alias: "usb:v0A5Cp5800d0101dc00dsc00dp00icFEisc00ip00"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #54 (Hub)

65: USB 00.0: 0000 Unclassified device
  [Created at usb.122]
  Unique ID: +u4I.bBFFBTjAOZ4
  Parent ID: 7eqy.v+N+B0xY+P6
  SysFS ID: /devices/pci0000:00/0000:00:1d.0/usb6/6-2/6-2:1.0
  SysFS BusID: 6-2:1.0
  Hardware Class: unknown
  Model: "U.S. Robotics 56K Faxmodem USB"
  Hotplug: USB
  Vendor: usb 0x0baf "U.S. Robotics"
  Device: usb 0x00ec "U.S. Robotics 56K Faxmodem USB"
  Revision: "0.01"
  Serial ID: "USBHCF00000006"
  Speed: 12 Mbps
  Module Alias: "usb:v0BAFp00ECd0001dcFFdscFFdpFFicFFiscFFipFF"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #55 (Hub)

66: USB 00.0: 10a00 Hub
  [Created at usb.122]
  Unique ID: vt3A.YCWTDwYJz_B
  Parent ID: 2UT6._H8jkZcj4d2
  SysFS ID: /devices/pci0000:00/0000:00:1a.7/usb1/1-3/1-3.1/1-3.1:1.0
  SysFS BusID: 1-3.1:1.0
  Hardware Class: hub
  Model: "Standard Microsystems Hub"
  Hotplug: USB
  Vendor: usb 0x0424 "Standard Microsystems Corp."
  Device: usb 0x2514 
  Driver: "hub"
  Driver Modules: "usbcore"
  Speed: 480 Mbps
  Module Alias: "usb:v0424p2514d0000dc09dsc00dp02ic09isc00ip02"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #58 (Hub)

67: USB 00.0: 10a00 Hub
  [Created at usb.122]
  Unique ID: L0iK.YCWTDwYJz_B
  Parent ID: 2UT6._H8jkZcj4d2
  SysFS ID: /devices/pci0000:00/0000:00:1a.7/usb1/1-3/1-3.2/1-3.2:1.0
  SysFS BusID: 1-3.2:1.0
  Hardware Class: hub
  Model: "Standard Microsystems Hub"
  Hotplug: USB
  Vendor: usb 0x0424 "Standard Microsystems Corp."
  Device: usb 0x2514 
  Revision: "b.b3"
  Driver: "hub"
  Driver Modules: "usbcore"
  Speed: 480 Mbps
  Module Alias: "usb:v0424p2514d0BB3dc09dsc00dp02ic09isc00ip02"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #58 (Hub)

68: USB 00.0: 10503 USB Mouse
  [Created at usb.122]
  Unique ID: Q7lo.R9wUZ167351
  Parent ID: Uc5H._H8jkZcj4d2
  SysFS ID: /devices/pci0000:00/0000:00:1a.7/usb1/1-4/1-4.2/1-4.2:1.0
  SysFS BusID: 1-4.2:1.0
  Hardware Class: mouse
  Model: "Logitech M-UV69a Optical Wheel Mouse"
  Hotplug: USB
  Vendor: usb 0x046d "Logitech, Inc."
  Device: usb 0xc016 "M-UV69a Optical Wheel Mouse"
  Revision: "3.40"
  Compatible to: int 0x0210 0x0013
  Driver: "usbhid"
  Driver Modules: "usbhid"
  Device File: /dev/input/mice (/dev/input/mouse0)
  Device Files: /dev/input/mice, /dev/input/mouse0, /dev/input/event4, /dev/input/by-id/usb-Logitech_Optical_USB_Mouse-event-mouse, /dev/input/by-path/pci-0000:00:1a.7-usb-0:4.2:1.0-event-mouse, /dev/input/by-id/usb-Logitech_Optical_USB_Mouse-mouse, /dev/input/by-path/pci-0000:00:1a.7-usb-0:4.2:1.0-mouse
  Device Number: char 13:63 (char 13:32)
  Speed: 1.5 Mbps
  Module Alias: "usb:v046DpC016d0340dc00dsc00dp00ic03isc01ip02"
  Driver Info #0:
    Buttons: 3
    Wheels: 1
    XFree86 Protocol: explorerps/2
    GPM Protocol: exps2
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #59 (Hub)

69: USB 00.0: 10800 Keyboard
  [Created at usb.122]
  Unique ID: 7dS8.yvebFSWtvP1
  Parent ID: KRJj.SAMIiYMCz2F
  SysFS ID: /devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1.1/3-1.1:1.0
  SysFS BusID: 3-1.1:1.0
  Hardware Class: keyboard
  Model: "Dell Keyboard"
  Hotplug: USB
  Vendor: usb 0x413c "Dell Computer Corp."
  Device: usb 0x8157 
  Revision: "1.00"
  Driver: "usbhid"
  Driver Modules: "usbhid"
  Device File: /dev/input/event5
  Device Files: /dev/input/event5, /dev/input/by-id/usb-413c_8157-event-kbd, /dev/input/by-path/pci-0000:00:1a.0-usb-0:1.1:1.0-event-kbd
  Device Number: char 13:69
  Speed: 12 Mbps
  Module Alias: "usb:v413Cp8157d0100dc00dsc00dp00ic03isc01ip01"
  Driver Info #0:
    XkbRules: xfree86
    XkbModel: pc104
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #62 (Hub)

70: USB 00.0: 10503 USB Mouse
  [Created at usb.122]
  Unique ID: Yl4J.O_flO7nZ+J6
  Parent ID: KRJj.SAMIiYMCz2F
  SysFS ID: /devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1.2/3-1.2:1.0
  SysFS BusID: 3-1.2:1.0
  Hardware Class: mouse
  Model: "Dell Generic USB Mouse"
  Hotplug: USB
  Vendor: usb 0x413c "Dell Computer Corp."
  Device: usb 0x8158 
  Revision: "1.00"
  Compatible to: int 0x0200 0x0001 "Generic USB Mouse"
  Speed: 12 Mbps
  Module Alias: "usb:v413Cp8158d0100dc00dsc00dp00ic03isc01ip02"
  Driver Info #0:
    XFree86 Protocol: explorerps/2
    GPM Protocol: exps2
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #62 (Hub)

72: PS/2 00.0: 10800 Keyboard
  [Created at input.161]
  Unique ID: 9ui9.+49ps10DtUF
  Hardware Class: keyboard
  Model: "AT Translated Set 2 keyboard"
  Vendor: 0x0001 
  Device: 0x0001 "AT Translated Set 2 keyboard"
  Compatible to: int 0x0211 0x0001
  Device File: /dev/input/event3
  Device Files: /dev/input/event3, /dev/input/by-path/platform-i8042-serio-0-event-kbd
  Device Number: char 13:67
  Driver Info #0:
    XkbRules: xfree86
    XkbModel: pc104
  Config Status: cfg=new, avail=yes, need=no, active=unknown

73: PS/2 00.0: 10500 PS/2 Mouse
  [Created at input.183]
  Unique ID: AH6Q.5+smWHVjPI3
  Hardware Class: mouse
  Model: "DualPoint Stick"
  Vendor: 0x0002 
  Device: 0x0008 "DualPoint Stick"
  Compatible to: int 0x0210 0x0003
  Device File: /dev/input/mice (/dev/input/mouse2)
  Device Files: /dev/input/mice, /dev/input/mouse2, /dev/input/event8, /dev/input/by-path/platform-i8042-serio-1-event-mouse, /dev/input/by-path/platform-i8042-serio-1-mouse
  Device Number: char 13:63 (char 13:34)
  Driver Info #0:
    Buttons: 3
    Wheels: 0
    XFree86 Protocol: explorerps/2
    GPM Protocol: exps2
  Config Status: cfg=new, avail=yes, need=no, active=unknown

74: PS/2 00.0: 10500 PS/2 Mouse
  [Created at input.183]
  Unique ID: AH6Q.5+smWHVjPI3
  Hardware Class: mouse
  Model: "AlpsPS/2 ALPS DualPoint TouchPad"
  Vendor: 0x0002 
  Device: 0x0008 "AlpsPS/2 ALPS DualPoint TouchPad"
  Compatible to: int 0x0210 0x0003
  Device File: /dev/input/mice (/dev/input/mouse3)
  Device Files: /dev/input/mice, /dev/input/mouse3, /dev/input/event9, /dev/input/by-path/platform-i8042-serio-1-event-mouse, /dev/input/by-path/platform-i8042-serio-1-mouse
  Device Number: char 13:63 (char 13:35)
  Driver Info #0:
    Buttons: 3
    Wheels: 0
    XFree86 Protocol: explorerps/2
    GPM Protocol: exps2
  Config Status: cfg=new, avail=yes, need=no, active=unknown

75: None 00.0: 10103 CPU
  [Created at cpu.304]
  Unique ID: rdCR.j8NaKXDZtZ6
  Hardware Class: cpu
  Arch: X86-64
  Vendor: "GenuineIntel"
  Model: 6.23.10 "Intel(R) Core(TM)2 Duo CPU     P8700  @ 2.53GHz"
  Features: fpu,vme,de,pse,tsc,msr,pae,mce,cx8,apic,sep,mtrr,pge,mca,cmov,pat,pse36,clflush,dts,acpi,mmx,fxsr,sse,sse2,ss,ht,tm,pbe,syscall,nx,lm,constant_tsc,arch_perfmon,pebs,bts,rep_good,nopl,aperfmperf,pni,dtes64,monitor,ds_cpl,vmx,smx,est,tm2,ssse3,cx16,xtpr,pdc
  Clock: 2533 MHz
  BogoMips: 5053.30
  Cache: 3072 kb
  Units/Processor: 2
  Config Status: cfg=new, avail=yes, need=no, active=unknown

76: None 01.0: 10103 CPU
  [Created at cpu.304]
  Unique ID: wkFv.j8NaKXDZtZ6
  Hardware Class: cpu
  Arch: X86-64
  Vendor: "GenuineIntel"
  Model: 6.23.10 "Intel(R) Core(TM)2 Duo CPU     P8700  @ 2.53GHz"
  Features: fpu,vme,de,pse,tsc,msr,pae,mce,cx8,apic,sep,mtrr,pge,mca,cmov,pat,pse36,clflush,dts,acpi,mmx,fxsr,sse,sse2,ss,ht,tm,pbe,syscall,nx,lm,constant_tsc,arch_perfmon,pebs,bts,rep_good,nopl,aperfmperf,pni,dtes64,monitor,ds_cpl,vmx,smx,est,tm2,ssse3,cx16,xtpr,pdc
  Clock: 2533 MHz
  BogoMips: 5053.95
  Cache: 3072 kb
  Units/Processor: 2
  Config Status: cfg=new, avail=yes, need=no, active=unknown

77: None 00.0: 10700 Loopback
  [Created at net.124]
  Unique ID: ZsBS.GQNx7L4uPNA
  SysFS ID: /class/net/lo
  Hardware Class: network interface
  Model: "Loopback network interface"
  Device File: lo
  Link detected: yes
  Config Status: cfg=new, avail=yes, need=no, active=unknown

78: None 00.0: 10701 Ethernet
  [Created at net.124]
  Unique ID: usDW.ndpeucax6V1
  Parent ID: rBUF.DspxR_P+1HD
  SysFS ID: /class/net/eth0
  SysFS Device Link: /devices/pci0000:00/0000:00:19.0
  Hardware Class: network interface
  Model: "Ethernet network interface"
  Driver: "e1000e"
  Driver Modules: "e1000e"
  Device File: eth0
  HW Address: 00:26:b9:c1:c5:00
  Link detected: yes
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #15 (Ethernet controller)

79: None 02.0: 10701 Ethernet
  [Created at net.124]
  Unique ID: pDke.ndpeucax6V1
  Parent ID: mY_N.gwDnaUUtfJC
  SysFS ID: /class/net/eth2
  SysFS Device Link: /devices/pci0000:00/0000:00:1c.1/0000:0c:00.0
  Hardware Class: network interface
  Model: "Ethernet network interface"
  Driver: "wl"
  Driver Modules: "wl"
  Device File: eth2
  HW Address: f0:7b:cb:73:88:8d
  Link detected: yes
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #33 (Ethernet controller)

```

Thank you and God bless,
Johnathan

---

### Post by johnathanamber on 2012-01-26
Anyone have any ideas?

---

### Post by johnathanamber on 2012-02-02
Has anyone run into this issue before?

---

