---
title: "takes very long to load after login"
date: 2005-08-05
forum: Desktop Environments
---

### Post by dlee27 on 2005-08-05
Hi,

I've been using Hoary on my toshiba laptop for about a week and it worked flawlessly(I'm relatively new to Linux). 
Today however, when I started and loged in it showed nothing but gnome background. At first I thought the computer froze but after 5 minutes I've got my menu and the desktop. Other things worked fine after that but every login takes very long. 
So I first deleted session file in ~/.gnome2 directory but it didn't help. I also created another user and loged in to that but it's the same.
At this point, I'm clueless. Can anyone help me? 
Thank you.

---

### Post by strikeforce on 2005-08-05
run the following command.

> 
sudo tail -n 100 /var/log/messages


That will generate a log of what you need up to 100 lines.  Look for error messages.

---

### Post by dlee27 on 2005-08-05
I just ran the command but I don't see any error message there. I'm attaching the output just in case.

> 
Aug  4 23:28:42 localhost kernel: ACPI: Thermal Zone [THRM] (36 C)
Aug  4 23:28:42 localhost kernel: NET: Registered protocol family 1
Aug  4 23:28:42 localhost kernel: Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
Aug  4 23:28:42 localhost kernel: ide: Assuming 33MHz system bus speed for PIO m odes; override with idebus=xx
Aug  4 23:28:42 localhost kernel: ALI15X3: IDE controller at PCI slot 0000:00:04 .0
Aug  4 23:28:42 localhost kernel: ACPI: PCI interrupt 0000:00:04.0[A]: no GSI
Aug  4 23:28:42 localhost kernel: ALI15X3: chipset revision 195
Aug  4 23:28:42 localhost kernel: ALI15X3: not 100%% native mode: will probe irq s later
Aug  4 23:28:42 localhost kernel:     ide0: BM-DMA at 0xeff0-0xeff7, BIOS settin gs: hda:DMA, hdb:pio
Aug  4 23:28:42 localhost kernel: ALI15X3: simplex device: DMA forced
Aug  4 23:28:42 localhost kernel:     ide1: BM-DMA at 0xeff8-0xefff, BIOS settin gs: hdc:DMA, hdd:DMA
Aug  4 23:28:42 localhost kernel: hda: TOSHIBA MK2003GAH, ATA DISK drive
Aug  4 23:28:42 localhost kernel: elevator: using anticipatory as default io sch eduler
Aug  4 23:28:42 localhost kernel: ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
Aug  4 23:28:42 localhost kernel: hda: max request size: 128KiB
Aug  4 23:28:42 localhost kernel: hda: 39062520 sectors (20000 MB),  CHS=38752/16 /63, UDMA(33)
Aug  4 23:28:42 localhost kernel:  /dev/ide/host0/bus0/target0/lun0: p1 p2 < p5 >
Aug  4 23:28:42 localhost kernel: Stopping tasks: ==|
Aug  4 23:28:42 localhost kernel: Freeing memory...  ^H-^H\^H|^H/^Hdone (464 pag es freed)
Aug  4 23:28:42 localhost kernel: Restarting tasks... done
Aug  4 23:28:42 localhost kernel: EXT3-fs: mounted filesystem with ordered data mode.
Aug  4 23:28:42 localhost kernel: kjournald starting.  Commit interval 5 seconds
Aug  4 23:28:42 localhost kernel: Adding 827308k swap on /dev/hda5.  Priority:-1  extents:1
Aug  4 23:28:42 localhost kernel: EXT3 FS on hda1, internal journal
Aug  4 23:28:42 localhost kernel: lp: driver loaded but no devices found
Aug  4 23:28:42 localhost kernel: mice: PS/2 mouse device common for all mice
Aug  4 23:28:42 localhost kernel: input: PS/2 Generic Mouse on isa0060/serio1
Aug  4 23:28:42 localhost kernel: ts: Compaq touchscreen protocol output
Aug  4 23:28:42 localhost kernel: Capability LSM initialized
Aug  4 23:28:42 localhost kernel: device-mapper: 4.3.0-ioctl (2004-09-30) initia lised: [email]dm-devel@redhat.com[/email]
Aug  4 23:28:42 localhost kernel: md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DI SKS=27
Aug  4 23:28:42 localhost kernel: input: PC Speaker
Aug  4 23:28:42 localhost kernel: Real Time Clock Driver v1.12
Aug  4 23:28:42 localhost kernel: Linux agpgart interface v0.100 (c) Dave Jones
Aug  4 23:28:42 localhost kernel: agpgart: Detected ALi M1644 chipset
Aug  4 23:28:42 localhost kernel: agpgart: Maximum main memory to use for agp me mory: 424M
Aug  4 23:28:42 localhost kernel: agpgart: AGP aperture is 64M @ 0xf0000000
Aug  4 23:28:42 localhost kernel: cpci_hotplug: CompactPCI Hot Plug Core version : 0.2
Aug  4 23:28:42 localhost kernel: pci_hotplug: PCI Hot Plug PCI Core version: 0. 5
Aug  4 23:28:42 localhost kernel: ACPI: PCI interrupt 0000:00:06.0[A] -> GSI 11 (level, low) -> IRQ 11
Aug  4 23:28:42 localhost kernel: e100: Intel(R) PRO/100 Network Driver, 3.2.3-k 2-NAPI
Aug  4 23:28:42 localhost kernel: e100: Copyright(c) 1999-2004 Intel Corporation
Aug  4 23:28:42 localhost kernel: ACPI: PCI interrupt 0000:00:0a.0[A] -> GSI 11 (level, low) -> IRQ 11
Aug  4 23:28:42 localhost kernel: e100: eth0: e100_probe: addr 0xf7eff000, irq 1 1, MAC addr 00:00:39:E2:C6:F1
Aug  4 23:28:42 localhost kernel: usbcore: registered new driver usbfs
Aug  4 23:28:42 localhost kernel: usbcore: registered new driver hub
Aug  4 23:28:42 localhost kernel: ACPI: PCI interrupt 0000:00:0c.0[A] -> GSI 11 (level, low) -> IRQ 11
Aug  4 23:28:42 localhost kernel: ohci_hcd 0000:00:0c.0: NEC Corporation USB
Aug  4 23:28:42 localhost kernel: ohci_hcd 0000:00:0c.0: irq 11, pci mem 0xf7ebf 000
Aug  4 23:28:42 localhost kernel: ohci_hcd 0000:00:0c.0: new USB bus registered,  assigned bus number 1
Aug  4 23:28:42 localhost kernel: hub 1-0:1.0: USB hub found
Aug  4 23:28:42 localhost kernel: hub 1-0:1.0: 3 ports detected
Aug  4 23:28:42 localhost kernel: ACPI: PCI interrupt 0000:00:0c.1[B] -> GSI 11 (level, low) -> IRQ 11
Aug  4 23:28:42 localhost kernel: ohci_hcd 0000:00:0c.1: NEC Corporation USB (#2 )
Aug  4 23:28:42 localhost kernel: ohci_hcd 0000:00:0c.1: irq 11, pci mem 0x20001 000
Aug  4 23:28:42 localhost kernel: ohci_hcd 0000:00:0c.1: new USB bus registered,  assigned bus number 2
Aug  4 23:28:42 localhost kernel: hub 2-0:1.0: USB hub found
Aug  4 23:28:42 localhost kernel: hub 2-0:1.0: 2 ports detected
Aug  4 23:28:42 localhost kernel: Linux Kernel Card Services
Aug  4 23:28:42 localhost kernel:   options:  [pci] [cardbus] [pm]
Aug  4 23:28:42 localhost kernel: ACPI: PCI interrupt 0000:00:10.0[A] -> GSI 11 (level, low) -> IRQ 11
Aug  4 23:28:42 localhost kernel: Yenta: CardBus bridge found at 0000:00:10.0 [1 2a3:ab01]
Aug  4 23:28:42 localhost kernel: Yenta: Enabling burst memory read transactions
Aug  4 23:28:42 localhost kernel: Yenta: Using CSCINT to route CSC interrupts to  PCI
Aug  4 23:28:42 localhost kernel: Yenta: Routing CardBus interrupts to PCI
Aug  4 23:28:42 localhost kernel: Yenta TI: socket 0000:00:10.0, mfunc 0x0100000 2, devctl 0x60
Aug  4 23:28:42 localhost kernel: Yenta: ISA IRQ mask 0x0000, PCI irq 11
Aug  4 23:28:42 localhost kernel: Socket status: 30000010
Aug  4 23:28:42 localhost kernel: ACPI: PCI interrupt 0000:00:11.0[A] -> GSI 11 (level, low) -> IRQ 11
Aug  4 23:28:42 localhost kernel: Yenta: CardBus bridge found at 0000:00:11.0 [1 179:0001]
Aug  4 23:28:42 localhost kernel: Yenta: ISA IRQ mask 0x04b8, PCI irq 11
Aug  4 23:28:42 localhost kernel: Socket status: 30000007
Aug  4 23:28:45 localhost kernel: ACPI: AC Adapter [ADP1] (on-line)
Aug  4 23:28:45 localhost kernel: ACPI: Battery Slot [BAT1] (battery absent)
Aug  4 23:28:45 localhost kernel: ACPI: Battery Slot [BAT2] (battery absent)
Aug  4 23:28:45 localhost kernel: ACPI: Power Button (FF) [PWRF]
Aug  4 23:28:45 localhost kernel: ACPI: Lid Switch [LID]
Aug  4 23:28:46 localhost kernel: toshiba_acpi: Toshiba Laptop ACPI Extras versi on 0.19a
Aug  4 23:28:46 localhost kernel: toshiba_acpi:     HCI method: \_SB_.VALD.GHCI
Aug  4 23:28:46 localhost kernel: toshiba_acpi: Toshiba hotkeys are sent as ACPI  events
Aug  4 23:28:46 localhost kernel: toshiba_acpi: ktoshkeyd will check 2 times per  second
Aug  4 23:28:46 localhost kernel: toshiba_acpi: Dropped 0 keys from the queue on  startup
Aug  4 23:28:46 localhost kernel: ACPI: Video Device [VGA] (multi-head: yes  rom : yes  post: no)
Aug  4 23:28:47 localhost kernel: apm: BIOS version 1.2 Flags 0x02 (Driver versi on 1.16ac)
Aug  4 23:28:47 localhost kernel: apm: overridden by ACPI.
Aug  4 23:28:52 localhost kernel: cs: IO port probe 0x0100-0x04ff: excluding 0x1 e0-0x1e7 0x200-0x207 0x220-0x22f 0x330-0x337 0x388-0x38f 0x408-0x40f 0x480-0x48f  0x4d0-0x4d7
Aug  4 23:28:52 localhost kernel: cs: IO port probe 0x0800-0x08ff: clean.
Aug  4 23:28:52 localhost kernel: cs: IO port probe 0x0c00-0x0cff: clean.
Aug  4 23:28:52 localhost kernel: cs: IO port probe 0x0a00-0x0aff: clean.
Aug  4 23:28:52 localhost kernel: cs: memory probe 0xa0000000-0xa0ffffff: clean.
Aug  4 23:28:54 localhost kernel: NET: Registered protocol family 17
Aug  4 23:28:54 localhost kernel: acpi-cpufreq: CPU0 - ACPI performance manageme nt activated.
Aug  4 23:28:55 localhost kernel: eth1: New link status: Connected (0001)
Aug  4 23:29:18 localhost gconfd (dlee27-6536): starting (version 2.10.0), pid 6 536 user 'dlee27'
Aug  4 23:29:19 localhost gconfd (dlee27-6536): Resolved address "xml:readonly:/ etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Aug  4 23:29:19 localhost gconfd (dlee27-6536): Resolved address "xml:readwrite: /home/dlee27/.gconf" to a writable configuration source at position 1
Aug  4 23:29:19 localhost gconfd (dlee27-6536): Resolved address "xml:readonly:/ etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Aug  4 23:29:20 localhost kernel: NET: Registered protocol family 10
Aug  4 23:29:20 localhost kernel: IPv6 over IPv4 tunneling driver
Aug  4 23:35:53 localhost gconfd (dlee27-6536): Resolved address "xml:readwrite: /home/dlee27/.gconf" to a writable configuration source at position 0



---

### Post by strikeforce on 2005-08-05
Try these two commands and put the output up.

```

 sudo tail -n 100 Xorg.0.log

```

```

sudo tail -n 100 gdm/\:0.log

```

It might provide some errors relating to X loading and or gdm issues.

---

### Post by dlee27 on 2005-08-05
Please look for the output below.
Thanks.

[QUOTE=strikeforce]Try these two commands and put the output up.

```

 sudo tail -n 100 Xorg.0.log

```

        [22] 0  0       0x000b8000 - 0x000bffff (0x8000) MS[B](OprU)
        [23] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [24] -1 0       0x00000000 - 0x000000ff (0x100) IX[B]
        [25] -1 0       0x0000eec0 - 0x0000eeff (0x40) IX[B]
        [26] -1 0       0x00001000 - 0x000010ff (0x100) IX[B]
        [27] -1 0       0x0000eff0 - 0x0000efff (0x10) IX[B]
        [28] 0  0       0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
        [29] 0  0       0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(==) TRIDENT(0): Write-combining range (0xfc000000,0x1000000)
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/X11R6/lib/modules/linux/libint10.a
(II) TRIDENT(0): Initializing int10
(II) TRIDENT(0): Primary V_BIOS segment is: 0xc000
(II) TRIDENT(0): Overriding Horizontal timings.
(II) TRIDENT(0): Shadow off
(II) TRIDENT(0): H-timing shadow registers: 0xa3           0x00 0x84 0x94
(II) TRIDENT(0): H-timing registers:        0xa3 0x7f 0x7f 0x00 0x84 0x94
(II) TRIDENT(0): V-timing shadow registers: 0x24 0xf5 0x03 0x09           0x24 (0x08)
(II) TRIDENT(0): V-timing registers:        0x24 0xf5 0x03 0x09 0xff 0x00 0x24
(II) TRIDENT(0): Setting BIOS Mode Regs: 3b 63
(II) TRIDENT(0): Found Clock  65.00 n=219 m=23 k=1
(II) TRIDENT(0): Using 1279 scanlines of offscreen memory for area's
(II) TRIDENT(0): Using 8392704 bytes of offscreen memory for linear (offset=0x7ff000)
(II) TRIDENT(0): Using XFree86 Acceleration Architecture (XAA)
        Screen to screen bit blits
        Solid filled rectangles
        8x8 mono pattern filled rectangles
        Solid Horizontal and Vertical Lines
        Offscreen Pixmaps
        Setting up tile and stipple cache:
                32 128x128 slots
                10 256x256 slots
(==) TRIDENT(0): Backing store disabled
(==) TRIDENT(0): Silken mouse enabled
(**) Option "dpms"
(**) TRIDENT(0): DPMS enabled
(II) TRIDENT(0): Trident Video Flags: VID_ZOOM_INV  VID_OFF_SHIFT_4
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension LBX
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc104"
(**) Generic Keyboard: XkbModel: "pc104"
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ImPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ImPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 5
(II) Synaptics touchpad driver version 0.13.6
Synaptics Touchpad no synaptics event device found (checked 4 nodes)
(**) Option "Device" "/dev/psaux"
(**) Option "HorizScrollDelta" "0"
Query no Synaptics: 6003C8
(EE) Synaptics Touchpad no synaptics touchpad detected and no repeater device
(EE) Synaptics Touchpad Unable to query/initialize Synaptics hardware.
(EE) PreInit failed for input device "Synaptics Touchpad"
(II) UnloadModule: "synaptics"
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Warning: font renderer for ".pcf" already registered at priority 0
Warning: font renderer for ".pcf.Z" already registered at priority 0
Warning: font renderer for ".pcf.gz" already registered at priority 0
Warning: font renderer for ".snf" already registered at priority 0
Warning: font renderer for ".snf.Z" already registered at priority 0
Warning: font renderer for ".snf.gz" already registered at priority 0
Warning: font renderer for ".bdf" already registered at priority 0
Warning: font renderer for ".bdf.Z" already registered at priority 0
Warning: font renderer for ".bdf.gz" already registered at priority 0
Warning: font renderer for ".pmf" already registered at priority 0
Could not init font path element unix/:7100, removing from list!


```

sudo tail -n 100 gdm/\:0.log

```


X Window System Version 6.8.2 (Ubuntu 6.8.2-10 20050405154308 [email]root@terranova.warthogs.hbd.com[/email])
Release Date: 9 February 2005
X Protocol Version 11, Revision 0, Release 6.8.2
Build Operating System: Linux 2.6.10 i686 [ELF]
Current Operating System: Linux portege 2.6.10-5-686 #1 Fri Jun 24 17:33:34 UTC 2005 i686
Build Date: 05 April 2005
        Before reporting problems, check [http://wiki.X.Org](http://wiki.X.Org)
        to make sure that you have the latest version.
Module Loader present
OS Kernel: Linux version 2.6.10-5-686 (buildd@vernadsky) (gcc version 3.3.5 (Debian 1:3.3.5-8ubuntu2)) #1 Fri Jun 24 17:33:34 UTC 2005
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Aug  4 23:28:44 2005
(==) Using config file: "/etc/X11/xorg.conf"
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_clip.o":  No symbols found
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_norm.o":  No symbols found
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_xform.o":  No symbols found
Skipping "/usr/X11R6/lib/modules/libfb.a:fbmmx.o":  No symbols found
Synaptics Touchpad no synaptics event device found (checked 4 nodes)
Query no Synaptics: 6003C8
(EE) Synaptics Touchpad no synaptics touchpad detected and no repeater device
(EE) Synaptics Touchpad Unable to query/initialize Synaptics hardware.
(EE) PreInit failed for input device "Synaptics Touchpad"
Warning: font renderer for ".pcf" already registered at priority 0
Warning: font renderer for ".pcf.Z" already registered at priority 0
Warning: font renderer for ".pcf.gz" already registered at priority 0
Warning: font renderer for ".snf" already registered at priority 0
Warning: font renderer for ".snf.Z" already registered at priority 0
Warning: font renderer for ".snf.gz" already registered at priority 0
Warning: font renderer for ".bdf" already registered at priority 0
Warning: font renderer for ".bdf.Z" already registered at priority 0
Warning: font renderer for ".bdf.gz" already registered at priority 0
Warning: font renderer for ".pmf" already registered at priority 0
Could not init font path element unix/:7100, removing from list!





It might provide some errors relating to X loading and or gdm issues.[/QUOTE]

---

### Post by dlee27 on 2005-08-05
I think I found what is causing it but still don't know the solution. If I connect ethernet cable it loads fast. It seems like finding/configuring network takes very long. 
FYI, I turned off networking service during boot up to expidite booting and I manually bring up when I need it. Is it something to do with this?
Thanks.

---

### Post by anando on 2005-08-06
[QUOTE=dlee27]I think I found what is causing it but still don't know the solution. If I connect ethernet cable it loads fast. It seems like finding/configuring network takes very long. 
FYI, I turned off networking service during boot up to expidite booting and I manually bring up when I need it. Is it something to do with this?
Thanks.[/QUOTE]


I don't know if you have solved your problem already - you may try to speed things up during boot time by reducing the 'timeout' value in your /etc/dhcp3/dhclient.conf file. Set it to 10 - by default I think it waits for a much longer time. This works very well for me on wireless as well as ethernet network connections.

---

