---
title: "random crashes"
date: 2009-06-10
forum: General Help
---

### Post by masterp904 on 2009-06-10
hey guys, im prety nub to unix. i installed jaunty on my work computer and it keeps doing random crashes. its mainly when im doin something, like browsing the internet or if im in gedit looking at a file. i have some of my sys log here if anyone can help because i have no idea what im looking at really. 


un  9 14:34:26 powell-desktop kernel: [    3.027437] registered taskstats version 1
Jun  9 14:34:26 powell-desktop kernel: [    3.027588]   Magic number: 13:613:594
Jun  9 14:34:26 powell-desktop kernel: [    3.027685] rtc_cmos 00:03: setting system clock to 2009-06-09 18:34:11 UTC (1244572451)
Jun  9 14:34:26 powell-desktop kernel: [    3.027691] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Jun  9 14:34:26 powell-desktop kernel: [    3.027694] EDD information not available.
Jun  9 14:34:26 powell-desktop kernel: [    3.028170] Freeing unused kernel memory: 532k freed
Jun  9 14:34:26 powell-desktop kernel: [    3.028377] Write protecting the kernel text: 4128k
Jun  9 14:34:26 powell-desktop kernel: [    3.028441] Write protecting the kernel read-only data: 1532k
Jun  9 14:34:26 powell-desktop kernel: [    3.064143] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
Jun  9 14:34:26 powell-desktop kernel: [    3.524045] usb 2-2: new low speed USB device using uhci_hcd and address 2
Jun  9 14:34:26 powell-desktop kernel: [    3.699931] usb 2-2: configuration #1 chosen from 1 choice
Jun  9 14:34:26 powell-desktop kernel: [    3.743118] Floppy drive(s): fd0 is 1.44M
Jun  9 14:34:26 powell-desktop kernel: [    3.759856] FDC 0 is a post-1991 82077
Jun  9 14:34:26 powell-desktop kernel: [    3.859560] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
Jun  9 14:34:26 powell-desktop kernel: [    3.859604] 8139cp 0000:01:05.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip, use 8139too
Jun  9 14:34:26 powell-desktop kernel: [    3.864232] 8139too Fast Ethernet driver 0.9.28
Jun  9 14:34:26 powell-desktop kernel: [    3.864301] 8139too 0000:01:05.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
Jun  9 14:34:26 powell-desktop kernel: [    3.865924] eth0: RealTek RTL8139 at 0xe800, 00:14:2a:7b:e9:1f, IRQ 22
Jun  9 14:34:26 powell-desktop kernel: [    4.815850] usbcore: registered new interface driver hiddev
Jun  9 14:34:26 powell-desktop kernel: [    4.829341] input: Logitech USB Optical Mouse as /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.0/input/input4
Jun  9 14:34:26 powell-desktop kernel: [    4.836194] generic-usb 0003:046D:C018.0001: input,hidraw0: USB HID v1.11 Mouse [Logitech USB Optical Mouse] on usb-0000:00:1d.0-2/input0
Jun  9 14:34:26 powell-desktop kernel: [    4.836230] usbcore: registered new interface driver usbhid
Jun  9 14:34:26 powell-desktop kernel: [    4.836237] usbhid: v2.6:USB HID core driver
Jun  9 14:34:26 powell-desktop kernel: [    4.947238] PM: Starting manual resume from disk
Jun  9 14:34:26 powell-desktop kernel: [    4.996157] kjournald starting.  Commit interval 5 seconds
Jun  9 14:34:26 powell-desktop kernel: [    4.996181] EXT3-fs: mounted filesystem with ordered data mode.
Jun  9 14:34:26 powell-desktop kernel: [   10.821341] udev: starting version 141
Jun  9 14:34:26 powell-desktop kernel: [   11.020270] Linux agpgart interface v0.103
Jun  9 14:34:26 powell-desktop kernel: [   11.118213] parport_pc 00:07: reported by Plug and Play ACPI
Jun  9 14:34:26 powell-desktop kernel: [   11.118341] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
Jun  9 14:34:26 powell-desktop kernel: [   11.277582] intel_rng: FWH not detected
Jun  9 14:34:26 powell-desktop kernel: [   11.776546] nvidia: module license 'NVIDIA' taints kernel.
Jun  9 14:34:26 powell-desktop kernel: [   12.055433] input: PC Speaker as /devices/platform/pcspkr/input/input5
Jun  9 14:34:26 powell-desktop kernel: [   12.159045] iTCO_vendor_support: vendor-support=0
Jun  9 14:34:26 powell-desktop kernel: [   12.161942] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.05
Jun  9 14:34:26 powell-desktop kernel: [   12.162352] iTCO_wdt: Found a ICH6 or ICH6R TCO device (Version=2, TCOBASE=0x0860)
Jun  9 14:34:26 powell-desktop kernel: [   12.162533] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
Jun  9 14:34:26 powell-desktop kernel: [   12.190728] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jun  9 14:34:26 powell-desktop kernel: [   12.191114] NVRM: loading NVIDIA Linux x86 Kernel Module  96.43.10  Sat Jan 24 19:49:38 PST 2009
Jun  9 14:34:26 powell-desktop kernel: [   12.480390] Intel ICH 0000:00:1e.2: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Jun  9 14:34:26 powell-desktop kernel: [   12.511768] ppdev: user-space parallel port driver
Jun  9 14:34:26 powell-desktop kernel: [   12.804028] intel8x0_measure_ac97_clock: measured 54531 usecs
Jun  9 14:34:26 powell-desktop kernel: [   12.804034] intel8x0: clocking to 48000
Jun  9 14:34:26 powell-desktop kernel: [   13.057813] lp0: using parport0 (interrupt-driven).
Jun  9 14:34:26 powell-desktop kernel: [   13.224523] Adding 1646620k swap on /dev/sda5.  Priority:-1 extents:1 across:1646620k
Jun  9 14:34:26 powell-desktop kernel: [   13.812939] EXT3 FS on sda1, internal journal
Jun  9 14:34:26 powell-desktop kernel: [   15.208490] type=1505 audit(1244572463.680:2): operation=&quot;profile_load&quot; name=&quot;/usr/share/gdm/guest-session/Xsession&quot; name2=&quot;default&quot; pid=1880
Jun  9 14:34:26 powell-desktop kernel: [   15.295582] type=1505 audit(1244572463.764:3): operation=&quot;profile_load&quot; name=&quot;/sbin/dhclient-script&quot; name2=&quot;default&quot; pid=1884
Jun  9 14:34:26 powell-desktop kernel: [   15.295819] type=1505 audit(1244572463.764:4): operation=&quot;profile_load&quot; name=&quot;/sbin/dhclient3&quot; name2=&quot;default&quot; pid=1884
Jun  9 14:34:26 powell-desktop kernel: [   15.295935] type=1505 audit(1244572463.764:5): operation=&quot;profile_load&quot; name=&quot;/usr/lib/NetworkManager/nm-dhcp-client.action&quot; name2=&quot;default&quot; pid=1884
Jun  9 14:34:26 powell-desktop kernel: [   15.296068] type=1505 audit(1244572463.768:6): operation=&quot;profile_load&quot; name=&quot;/usr/lib/connman/scripts/dhclient-script&quot; name2=&quot;default&quot; pid=1884
Jun  9 14:34:26 powell-desktop kernel: [   15.535931] type=1505 audit(1244572464.004:7): operation=&quot;profile_load&quot; name=&quot;/usr/lib/cups/backend/cups-pdf&quot; name2=&quot;default&quot; pid=1889
Jun  9 14:34:26 powell-desktop kernel: [   15.536290] type=1505 audit(1244572464.008:8): operation=&quot;profile_load&quot; name=&quot;/usr/sbin/cupsd&quot; name2=&quot;default&quot; pid=1889
Jun  9 14:34:26 powell-desktop kernel: [   15.588583] type=1505 audit(1244572464.060:9): operation=&quot;profile_load&quot; name=&quot;/usr/sbin/tcpdump&quot; name2=&quot;default&quot; pid=1893
Jun  9 14:34:28 powell-desktop kernel: [   20.374060] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Jun  9 14:34:28 powell-desktop kernel: [   20.374067] Bluetooth: BNEP filters: protocol multicast
Jun  9 14:34:28 powell-desktop kernel: [   20.398460] Bridge firewalling registered
Jun  9 14:34:34 powell-desktop kernel: [   25.528799] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Jun  9 14:34:36 powell-desktop kernel: [   27.831736] RPC: Registered udp transport module.
Jun  9 14:34:36 powell-desktop kernel: [   27.831743] RPC: Registered tcp transport module.
Jun  9 14:34:54 powell-desktop pulseaudio[3153]: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 48000 Hz.
Jun  9 14:34:54 powell-desktop pulseaudio[3153]: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 48000 Hz.
Jun  9 14:54:25 powell-desktop -- MARK --
Jun  9 15:02:57 powell-desktop syslogd 1.5.0#5ubuntu3: restart.
Jun  9 15:02:57 powell-desktop kernel: Inspecting /boot/System.map-2.6.28-11-generic
Jun  9 15:02:57 powell-desktop kernel: Cannot find map file.
Jun  9 15:02:57 powell-desktop kernel: Loaded 63453 symbols from 41 modules.
Jun  9 15:02:57 powell-desktop kernel: [    0.000000] BIOS EBDA/lowmem at: 0009fc00/0009fc00
Jun  9 15:02:57 powell-desktop kernel: [    0.000000] Initializing cgroup subsys cpuset
Jun  9 15:02:57 powell-desktop kernel: [    0.000000] Initializing cgroup subsys cpu
Jun  9 15:02:57 powell-desktop kernel: [    0.000000] Linux version 2.6.28-11-generic (buildd@palmer) (gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) ) #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 (Ubuntu 2.6.28-11.42-generic)

---

