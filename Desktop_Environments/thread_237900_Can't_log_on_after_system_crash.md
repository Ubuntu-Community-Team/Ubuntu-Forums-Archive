---
title: "Can't log on after system crash"
date: 2006-08-16
forum: Desktop Environments
---

### Post by fpwind on 2006-08-16
I had a system crash today and now I can't seem to log on.  When I restart the machine x doesnt' start.  When I put in my user and password I get the message "unable to cd to /home/me"

I'm able to boot into recovery mode and then startx.
I then get the error 
Powermanager.
"This program cannot start until you start the dbus system service.
It is strongly recommended you reboot your compter after starting messagebus."
After searching the forums I found this [thread]("http://http://www.ubuntuforums.org/showthread.php?t=229182&highlight=program+start+dbus+system+service") which sounds exactly like my issue. 
The problem there turned out to be the boot partition being full. Mine isn't even close to capacity.
I wasn't installing updates when my system crashed.  The only think that I have done recently is I installed Kubuntu over Ubuntu last night to check out KDE.
Right before the crash I was plugging in a camera.  The Cameras USB plug is pretty sketchy so it may have come loose.  I'm not sure it this caused the crash.
In afore mentioned post the person in need was directed to post the output to 
less ~/.xsession-errors
```
Xsession: X session started for root at Wed Aug 16 15:00:46 MDT 2006
SESSION_MANAGER=local/Workstation:/tmp/.ICE-unix/4039
esd: Esound sound daemon already running or stale UNIX socket
/tmp/.esd-0/socket
This socket already exists indicating esd is already running.
Exiting...
Gnome-Message: gnome_execute_async_with_env_fds: returning -1

(gnome-panel:4105): GdkPixbuf-CRITICAL **: gdk_pixbuf_scale_simple: assertion `dest_width > 0' failed

** (update-notifier:4119): WARNING **: not starting because user is not in admin group


** (gnome-cups-icon:4130): WARNING **: IPP request failed with status 1280

** (gnome-cups-icon:4130): WARNING **: IPP request failed with status 1280

(gnome-panel:4105): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -5 and height 24
** (gnome-cups-icon:4130): WARNING **: Could not start the printer tray icon, because the CUPS server could not be contacted.

** (gnome-session:4039): WARNING **: Failed to establish a connection with GDM: No such file or directory

** (gnome-session:4039): WARNING **: Couldn't connect to PowerManager No reply within specified time

** (gnome-session:4039): WARNING **: Couldn't connect to PowerManager No reply within specified time
  Failed to connect to socket, sleep 1 second and retry
  Trying failed command again.  Try 2 of 5.
  Failed to connect to socket, sleep 1 second and retry
  Trying failed command again.  Try 3 of 5.
  Failed to connect to socket, sleep 1 second and retry
  Trying failed command again.  Try 4 of 5.
  Failed to connect to socket, sleep 1 second and retry
  Trying failed command again.  Try 5 of 5.
  Command failed 5 times, aborting.
Could not access configuration key <daemon/PidFile=/var/run/gdm.pid>
Using compiled in value </var/run/gdm.pid> for <daemon/PidFile=/var/run/gdm.pid>

** (gnome-session:4039): WARNING **: Failed to establish a connection with GDM: No such file or directory

** (gnome-session:4039): WARNING **: Couldn't connect to PowerManager No reply within specified time

** (gnome-session:4039): WARNING **: Couldn't connect to PowerManager No reply within specified time

** (gnome-session:4039): WARNING **: Failed to establish a connection with GDM: No such file or directory
  id: (null)
:
handle: 9
  connection: (nil)
  properties:
    ((name "RestartCommand") (type "LISTofARRAY8") (value "update-notifier"))
  id: 117f000001000115576205100000040390000
  handle: 1
  connection: 0x81080c8
  properties:
    ((name "Program") (type "ARRAY8") (value "metacity"))
    ((name "UserID") (type "ARRAY8") (value "root"))
    ((name "RestartStyleHint") (type "CARD8") (value "^B"))
    ((name "ProcessID") (type "ARRAY8") (value "4100"))
    ((name "CurrentDirectory") (type "ARRAY8") (value "/root"))
    ((name "_GSM_Priority") (type "CARD8") (value "^T"))
    ((name "RestartCommand") (type "LISTofARRAY8") (value "metacity") (value "--sm-save-file") (value " 1155762052-4100-2010375194.ms"))
    ((name "CloneCommand") (type "LISTofARRAY8") (value "metacity"))
    ((name "DiscardCommand") (type "LISTofARRAY8") (value "rm") (value "-f") (value "/root/.metacity/sessions/1155762052- 4100-2010375194.ms"))
  id: 117f000001000115576205100000040390001
  handle: 2
  connection: 0x8257f38
  properties:
    ((name "CurrentDirectory") (type "ARRAY8") (value "/root^@"))
    ((name "ProcessID") (type "ARRAY8") (value "4105^@"))
    ((name "Program") (type "ARRAY8") (value "gnome-panel^@"))
    ((name "CloneCommand") (type "LISTofARRAY8") (value "gnome-panel"))
    ((name "RestartCommand") (type "LISTofARRAY8") (value "gnome-panel") (value "--sm-client-id") (value "117f000001000115576205100000040390001") (value "--screen") (value "0"))
    ((name "UserID") (type "ARRAY8") (value "root^@"))
    ((name "RestartStyleHint") (type "CARD8") (value "^B"))
    ((name "_GSM_Priority") (type "CARD8") (value "("))
  id: 117f000001000115576205200000040390003
  handle: 3
  connection: 0x80d2488
  properties:
    ((name "CurrentDirectory") (type "ARRAY8") (value "/root^@"))
    ((name "ProcessID") (type "ARRAY8") (value "4107^@"))
    ((name "Program") (type "ARRAY8") (value "nautilus^@"))
    ((name "CloneCommand") (type "LISTofARRAY8") (value "nautilus"))
    ((name "RestartCommand") (type "LISTofARRAY8") (value "nautilus") (value "--sm-client-id") (value "117f000001000115576205200000040390003") (value "--screen") (value "0"))
    ((name "UserID") (type "ARRAY8") (value "root^@"))
((name "_GSM_Priority") (type "CARD8") (value "("))
    ((name "RestartStyleHint") (type "CARD8") (value "^B"))
The application 'Gecko' lost its connection to the display :0.0;
most likely the X server was shut down or you killed/destroyed
the application.
Xsession: X session started for root at Wed Aug 16 15:21:48 MDT 2006
SESSION_MANAGER=local/Workstation:/tmp/.ICE-unix/4033
esd: Esound sound daemon already running or stale UNIX socket
/tmp/.esd-0/socket
This socket already exists indicating esd is already running.
Exiting...
Gnome-Message: gnome_execute_async_with_env_fds: returning -1

(gnome-panel:4101): GdkPixbuf-CRITICAL **: gdk_pixbuf_scale_simple: assertion `dest_width > 0' failed

** (update-notifier:4113): WARNING **: not starting because user is not in admin group


** (gnome-cups-icon:4127): WARNING **: IPP request failed with status 1280

** (gnome-cups-icon:4127): WARNING **: IPP request failed with status 1280

(gnome-panel:4101): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -21 and height 24

** (gnome-cups-icon:4127): WARNING **: Could not start the printer tray icon, because the CUPS server could not be contacted.

** (gnome-session:4033): WARNING **: Failed to establish a connection with GDM: No such file or directory

** (gnome-session:4033): WARNING **: Couldn't connect to PowerManager No reply within specified time

** (gnome-session:4033): WARNING **: Couldn't connect to PowerManager No reply within specified time

** (gnome-session:4033): WARNING **: Failed to establish a connection with GDM: No such file or directory

** (gnome-session:4033): WARNING **: Couldn't connect to PowerManager No reply within specified time

** (gnome-session:4033): WARNING **: Couldn't connect to PowerManager Activation of org.gnome.PowerManager timed out

** (nautilus:4103): WARNING **: Error writing file 'computer:///Filesystem.desktop': Operation not permitted

** (nautilus:4103): WARNING **: Error writing file 'computer:///Filesystem.desktop': Operation not permitted
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  149
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  149
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Link points to "/tmp/ksocket-root"
Link points to "/tmp/kde-root"
:
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  149
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  149
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kbuildsycoca running...
Reusing existing ksycoca
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
ScimInputContextPlugin()
~ScimInputContextPlugin()
glibtop: This machine has 1 CPUs, 1 are being monitored.
smooth_refresh is active = 1
(END)

```

---

### Post by fpwind on 2006-08-16
and here is the output to
dmesg | less
```
[17179569.184000] Linux version 2.6.15-26-386 (buildd@terranova) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Thu Aug 3 02:52:00 UTC 2006
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[17179569.184000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000003fff0000 (usable)
[17179569.184000]  BIOS-e820: 000000003fff0000 - 000000003fff3000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 000000003fff3000 - 0000000040000000 (ACPI data)
[17179569.184000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[17179569.184000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[17179569.184000] 127MB HIGHMEM available.
[17179569.184000] 896MB LOWMEM available.
[17179569.184000] On node 0 totalpages: 262128
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   DMA32 zone: 0 pages, LIFO batch:0
[17179569.184000]   Normal zone: 225280 pages, LIFO batch:31
[17179569.184000]   HighMem zone: 32752 pages, LIFO batch:7
[17179569.184000] DMI 2.2 present.
[17179569.184000] ACPI: RSDP (v000 Nvidia                                ) @ 0x000f7130
[17179569.184000] ACPI: RSDT (v001 Nvidia AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x3fff3000
[17179569.184000] ACPI: FADT (v001 Nvidia AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x3fff3040
[17179569.184000] ACPI: MADT (v001 Nvidia AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x3fff7b40
[17179569.184000] ACPI: DSDT (v001 NVIDIA AWRDACPI 0x00001000 MSFT 0x0100000a) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x4008
[17179569.184000] ACPI: Local APIC address 0xfee00000
[17179569.184000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[17179569.184000] Processor #0 6:10 APIC version 16
[17179569.184000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[17179569.184000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[17179569.184000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[17179569.184000] ACPI: BIOS IRQ0 pin2 override ignored.
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[17179569.184000] ACPI: IRQ9 used by override.
[17179569.184000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[17179569.184000] Using ACPI (MADT) for SMP configuration information
[17179569.184000] Allocating PCI resources starting at 50000000 (gap: 40000000:bec00000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/hda3 ro single
[17179569.184000] mapped APIC to ffffd000 (fee00000)
[17179569.184000] mapped IOAPIC to ffffc000 (fec00000)
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 4096 (order: 12, 65536 bytes)
[17179569.184000] Detected 2191.392 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179573.216000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[17179573.216000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179573.240000] Memory: 1028816k/1048512k available (1976k kernel code, 18932k reserved, 606k data, 288k init, 131008k highmem)
[17179573.240000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179573.320000] Calibrating delay using timer specific routine.. 4387.39 BogoMIPS (lpj=8774797)
:
[17179573.320000] Security Framework v1.0.0 initialized
[17179573.320000] SELinux:  Disabled at boot.
[17179573.320000] Mount-cache hash table entries: 512
[17179573.320000] CPU: After generic identify, caps: 0383fbff c1cbfbff 00000000 00000000 00000000 00000000 00000000
[17179573.320000] CPU: After vendor identify, caps: 0383fbff c1cbfbff 00000000 00000000 00000000 00000000 00000000
[17179573.320000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[17179573.320000] CPU: L2 Cache: 512K (64 bytes/line)
[17179573.320000] CPU: After all inits, caps: 0383fbff c1cbfbff 00000000 00000420 00000000 00000000 00000000
[17179573.320000] mtrr: v2.0 (20020519)
[17179573.320000] CPU: AMD Sempron(tm)  3300+ stepping 00
[17179573.320000] Enabling fast FPU save and restore... done.
[17179573.320000] Enabling unmasked SIMD FPU exception support... done.
[17179573.320000] Checking 'hlt' instruction... OK.
[17179573.336000] checking if image is initramfs... it is
[17179573.804000] Freeing initrd memory: 6615k freed
[17179573.820000] ACPI: Looking for DSDT ... not found!
[17179573.820000] ENABLING IO-APIC IRQs
[17179573.820000] ..TIMER: vector=0x31 apic1=0 pin1=0 apic2=-1 pin2=-1
[17179573.964000] NET: Registered protocol family 16
[17179573.964000] EISA bus registered
[17179573.964000] ACPI: bus type pci registered
[17179573.980000] PCI: PCI BIOS revision 2.10 entry at 0xfb550, last bus=2
[17179573.980000] PCI: Using configuration type 1
[17179573.980000] ACPI: Subsystem revision 20051216
[17179573.988000] ACPI: Interpreter enabled
[17179573.988000] ACPI: Using IOAPIC for interrupt routing
[17179573.988000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179573.988000] PCI: Probing PCI hardware (bus 00)
[17179573.992000] PCI: nForce2 C1 Halt Disconnect fixup
[17179573.996000] Boot video device is 0000:02:00.0
[17179573.996000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179574.056000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[17179574.056000] ACPI: Power Resource [ISAV] (on)
[17179574.056000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGPB._PRT]
[17179574.060000] ACPI: PCI Interrupt Link [LNK1] (IRQs *0 20), disabled.
[17179574.060000] ACPI: PCI Interrupt Link [LNK2] (IRQs *0 20), disabled.
[17179574.060000] ACPI: PCI Interrupt Link [LNK3] (IRQs *0 20), disabled.
[17179574.060000] ACPI: PCI Interrupt Link [LNK4] (IRQs *0 20)
[17179574.060000] ACPI: PCI Interrupt Link [LNK5] (IRQs *0 20), disabled.
[17179574.060000] ACPI: PCI Interrupt Link [LUBA] (IRQs *0 20)
[17179574.060000] ACPI: PCI Interrupt Link [LUBB] (IRQs *0 20)
[17179574.064000] ACPI: PCI Interrupt Link [LMAC] (IRQs *0 20)
[17179574.064000] ACPI: PCI Interrupt Link [LAPU] (IRQs *0 20), disabled.
[17179574.064000] ACPI: PCI Interrupt Link [LACI] (IRQs *0 20)
[17179574.064000] ACPI: PCI Interrupt Link [LMCI] (IRQs *0 20), disabled.
:
[17179574.064000] ACPI: PCI Interrupt Link [LSMB] (IRQs *0 20)
[17179574.064000] ACPI: PCI Interrupt Link [LUB2] (IRQs *0 20)
[17179574.068000] ACPI: PCI Interrupt Link [LFIR] (IRQs *0 20), disabled.
[17179574.068000] ACPI: PCI Interrupt Link [L3CM] (IRQs *0 20), disabled.
[17179574.068000] ACPI: PCI Interrupt Link [LIDE] (IRQs *0 20), disabled.
[17179574.068000] ACPI: PCI Interrupt Link [APC1] (IRQs *16), disabled.
[17179574.068000] ACPI: PCI Interrupt Link [APC2] (IRQs *17), disabled.
[17179574.068000] ACPI: PCI Interrupt Link [APC3] (IRQs *18), disabled.
[17179574.068000] ACPI: PCI Interrupt Link [APC4] (IRQs *19), disabled.
[17179574.068000] ACPI: PCI Interrupt Link [APC5] (IRQs *16), disabled.
[17179574.072000] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22) *0, disabled.
[17179574.072000] ACPI: PCI Interrupt Link [APCG] (IRQs 20 21 22) *0, disabled.
[17179574.072000] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22) *0, disabled.
[17179574.072000] ACPI: PCI Interrupt Link [APCI] (IRQs 20 21 22) *0, disabled.
[17179574.072000] ACPI: PCI Interrupt Link [APCJ] (IRQs 20 21 22) *0, disabled.
[17179574.072000] ACPI: PCI Interrupt Link [APCK] (IRQs 20 21 22) *0, disabled.
[17179574.076000] ACPI: PCI Interrupt Link [APCS] (IRQs *23), disabled.
[17179574.076000] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22) *0, disabled.
[17179574.076000] ACPI: PCI Interrupt Link [APCM] (IRQs 20 21 22) *0, disabled.
[17179574.076000] ACPI: PCI Interrupt Link [AP3C] (IRQs 20 21 22) *0, disabled.
[17179574.076000] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22) *0, disabled.
[17179574.080000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179574.080000] pnp: PnP ACPI init
[17179574.088000] pnp: PnP ACPI: found 15 devices
[17179574.088000] PnPBIOS: Disabled by ACPI PNP
[17179574.088000] PCI: Using ACPI for IRQ routing
[17179574.088000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179574.124000] pnp: 00:00: ioport range 0x4000-0x407f could not be reserved
[17179574.124000] pnp: 00:00: ioport range 0x4080-0x40ff has been reserved
[17179574.124000] pnp: 00:00: ioport range 0x4400-0x447f has been reserved
[17179574.124000] pnp: 00:00: ioport range 0x4480-0x44ff could not be reserved
[17179574.124000] pnp: 00:00: ioport range 0x4200-0x427f has been reserved
[17179574.124000] pnp: 00:00: ioport range 0x4280-0x42ff has been reserved
[17179574.124000] pnp: 00:01: ioport range 0x5000-0x503f has been reserved
[17179574.124000] pnp: 00:01: ioport range 0x5100-0x513f has been reserved
[17179574.124000] PCI: Bridge: 0000:00:08.0
[17179574.124000]   IO window: disabled.
[17179574.124000]   MEM window: disabled.
[17179574.124000]   PREFETCH window: disabled.
[17179574.124000] PCI: Bridge: 0000:00:1e.0
[17179574.124000]   IO window: c000-cfff
[17179574.124000]   MEM window: e4000000-e5ffffff
[17179574.124000]   PREFETCH window: d0000000-dfffffff
[17179574.124000] PCI: Setting latency timer of device 0000:00:08.0 to 64
[17179574.124000] audit: initializing netlink socket (disabled)
[17179574.124000] audit(1155741664.124:1): initialized
[17179574.128000] highmem bounce pool size: 64 pages
[17179574.128000] VFS: Disk quotas dquot_6.5.1
:
[17179574.128000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179574.128000] Initializing Cryptographic API
[17179574.128000] io scheduler noop registered
[17179574.128000] io scheduler anticipatory registered
[17179574.128000] io scheduler deadline registered
[17179574.128000] io scheduler cfq registered
[17179574.128000] isapnp: Scanning for PnP cards...
[17179574.480000] isapnp: No Plug & Play device found
[17179574.492000] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[17179574.496000] serio: i8042 AUX port at 0x60,0x64 irq 12
[17179574.496000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179574.496000] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
[17179574.496000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179574.496000] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179574.496000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179574.496000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179574.496000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179574.496000] mice: PS/2 mouse device common for all mice
[17179574.500000] EISA: Probing bus 0 at eisa.0
[17179574.500000] Cannot allocate resource for EISA slot 4
[17179574.500000] Cannot allocate resource for EISA slot 5
[17179574.500000] EISA: Detected 0 cards.
[17179574.500000] NET: Registered protocol family 2
[17179574.524000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179574.544000] IP route cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179574.544000] TCP established hash table entries: 262144 (order: 8, 1048576 bytes)
[17179574.544000] TCP bind hash table entries: 65536 (order: 6, 262144 bytes)
[17179574.544000] TCP: Hash tables configured (established 262144 bind 65536)
[17179574.544000] TCP reno registered
[17179574.544000] TCP bic registered
[17179574.544000] NET: Registered protocol family 1
[17179574.544000] NET: Registered protocol family 8
[17179574.544000] NET: Registered protocol family 20
[17179574.544000] Using IPI Shortcut mode
[17179574.544000] ACPI wakeup devices:
[17179574.544000] SLPB HUB0 HUB1 USB0 USB1 USB2 F139 MMAC MMCI UAR1
[17179574.544000] ACPI: (supports S0 S1 S4 S5)
[17179574.544000] Freeing unused kernel memory: 288k freed
[17179574.584000] Capability LSM initialized
[17179574.612000] ACPI: Fan [FAN] (on)
[17179574.616000] ACPI: Thermal Zone [THRM] (43 C)
[17179574.896000] SCSI subsystem initialized
[17179574.896000] ACPI: bus type scsi registered
[17179574.896000] libata version 1.20 loaded.
[17179574.896000] NFORCE2: IDE controller at PCI slot 0000:00:09.0
[17179574.896000] NFORCE2: chipset revision 162
:
[17179574.896000] NFORCE2: not 100% native mode: will probe irqs later
[17179574.896000] NFORCE2: BIOS didn't set cable bits correctly. Enabling workaround.
[17179574.896000] NFORCE2: BIOS didn't set cable bits correctly. Enabling workaround.
[17179574.896000] NFORCE2: 0000:00:09.0 (rev a2) UDMA133 controller
[17179574.896000]     ide0: BM-DMA at 0xf000-0xf007, BIOS settings: hda:DMA, hdb:DMA
[17179574.900000]     ide1: BM-DMA at 0xf008-0xf00f, BIOS settings: hdc:DMA, hdd:DMA
[17179574.900000] Probing IDE interface ide0...
[17179575.188000] hda: HDT722516DLAT80, ATA DISK drive
[17179575.636000] hdb: CD-RW IDE5232, ATAPI CD/DVD-ROM drive
[17179575.692000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179575.700000] Probing IDE interface ide1...
[17179575.992000] hdc: ST3200822A, ATA DISK drive
[17179576.664000] ide1 at 0x170-0x177,0x376 on irq 15
[17179576.672000] hda: max request size: 1024KiB
[17179576.684000] hda: 321672960 sectors (164696 MB) w/7674KiB Cache, CHS=20023/255/63, UDMA(133)
[17179576.684000] hda: cache flushes supported
[17179576.684000]  hda: hda1 hda2 hda3 hda4
[17179576.712000] hdc: max request size: 1024KiB
[17179576.712000] hdc: 390721968 sectors (200049 MB) w/8192KiB Cache, CHS=24321/255/63, UDMA(100)
[17179576.712000] hdc: cache flushes supported
[17179576.712000]  hdc:<6>hdb: ATAPI 52X CD-ROM CD-R/RW drive, 2048kB Cache
[17179576.712000] Uniform CD-ROM driver Revision: 3.20
[17179576.712000]  hdc1
[17179577.084000] usbcore: registered new driver usbfs
[17179577.084000] usbcore: registered new driver hub
[17179577.088000] ohci_hcd: 2005 April 22 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
[17179577.088000] **** SET: Misaligned resource pointer: dfaf2e02 Type 07 Len 0
[17179577.088000] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 22
[17179577.088000] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [APCF] -> GSI 22 (level, high) -> IRQ 177
[17179577.088000] PCI: Setting latency timer of device 0000:00:02.0 to 64
[17179577.088000] ohci_hcd 0000:00:02.0: OHCI Host Controller
[17179577.104000] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 1
[17179577.104000] ohci_hcd 0000:00:02.0: irq 177, io mem 0xe6004000
[17179577.160000] hub 1-0:1.0: USB hub found
[17179577.160000] hub 1-0:1.0: 3 ports detected
[17179577.264000] **** SET: Misaligned resource pointer: dfaf2b02 Type 07 Len 0
[17179577.264000] ACPI: PCI Interrupt Link [APCG] enabled at IRQ 21
[17179577.264000] ACPI: PCI Interrupt 0000:00:02.1[B] -> Link [APCG] -> GSI 21 (level, high) -> IRQ 185
[17179577.264000] PCI: Setting latency timer of device 0000:00:02.1 to 64
[17179577.264000] ohci_hcd 0000:00:02.1: OHCI Host Controller
[17179577.280000] ohci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 2
[17179577.280000] ohci_hcd 0000:00:02.1: irq 185, io mem 0xe6005000
[17179577.336000] hub 2-0:1.0: USB hub found
[17179577.336000] hub 2-0:1.0: 3 ports detected
[17179577.440000] **** SET: Misaligned resource pointer: dfaf2802 Type 07 Len 0
[17179577.440000] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 20
[17179577.440000] ACPI: PCI Interrupt 0000:00:02.2[C] -> Link [APCL] -> GSI 20 (level, high) -> IRQ 193
[17179577.440000] PCI: Setting latency timer of device 0000:00:02.2 to 64
[17179577.440000] ehci_hcd 0000:00:02.2: EHCI Host Controller
[17179577.440000] ehci_hcd 0000:00:02.2: debug port 1
[17179577.440000] PCI: cache line size of 64 is not supported by device 0000:00:02.2
[17179577.440000] ehci_hcd 0000:00:02.2: new USB bus registered, assigned bus number 3
[17179577.440000] ehci_hcd 0000:00:02.2: irq 193, io mem 0xe6000000
[17179577.440000] ehci_hcd 0000:00:02.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
:
[17179577.440000] hub 3-0:1.0: USB hub found
[17179577.440000] hub 3-0:1.0: 6 ports detected
[17179577.604000] Attempting manual resume
[17179577.628000] EXT3-fs: mounted filesystem with ordered data mode.
[17179577.644000] kjournald starting.  Commit interval 5 seconds
[17179578.192000] usb 3-2: new high speed USB device using ehci_hcd and address 3
[17179578.324000] hub 3-2:1.0: USB hub found
[17179578.324000] hub 3-2:1.0: 4 ports detected
[17179578.732000] usb 1-1: new low speed USB device using ohci_hcd and address 3
[17179585.076000] Linux agpgart interface v0.101 (c) Dave Jones
[17179585.076000] agpgart: Detected NVIDIA nForce2 chipset
[17179585.080000] agpgart: AGP aperture is 64M @ 0xe0000000
[17179585.348000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179585.348000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179585.492000] forcedeth.c: Reverse Engineered nForce ethernet driver. Version 0.54.
[17179585.492000] **** SET: Misaligned resource pointer: dfb03722 Type 07 Len 0
[17179585.492000] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 22
[17179585.492000] ACPI: PCI Interrupt 0000:00:04.0[A] -> Link [APCH] -> GSI 22 (level, high) -> IRQ 177
[17179585.492000] PCI: Setting latency timer of device 0000:00:04.0 to 64
[17179585.528000] i2c_adapter i2c-0: nForce2 SMBus adapter at 0x5000
[17179585.528000] i2c_adapter i2c-1: nForce2 SMBus adapter at 0x5100
[17179585.764000] FDC 0 is a post-1991 82077
[17179585.796000] parport: PnPBIOS parport detected.
[17179585.796000] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[17179585.912000] usbcore: registered new driver hiddev
[17179585.956000] Real Time Clock Driver v1.12
[17179585.964000] input: PC Speaker as /class/input/input1
[17179586.012000] eth0: forcedeth.c: subsystem: 01565:2301 bound to 0000:00:04.0
[17179586.012000] **** SET: Misaligned resource pointer: f7c134a2 Type 07 Len 0
[17179586.012000] ACPI: PCI Interrupt Link [APCJ] enabled at IRQ 21
[17179586.012000] ACPI: PCI Interrupt 0000:00:06.0[A] -> Link [APCJ] -> GSI 21 (level, high) -> IRQ 185
[17179586.012000] PCI: Setting latency timer of device 0000:00:06.0 to 64
[17179586.028000] hiddev96: USB HID v1.11 Device [Belkin UPS] on usb-0000:00:02.0-1
[17179586.028000] usbcore: registered new driver usbhid
[17179586.028000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[17179586.320000] eth0: no link during initialization.
[17179586.332000] intel8x0_measure_ac97_clock: measured 120893345 usecs
[17179586.332000] intel8x0: measured clock 21 rejected
[17179586.332000] intel8x0: clocking to 48000
[17179586.440000] input: ImExPS/2 Generic Explorer Mouse as /class/input/input2
[17179586.492000] ts: Compaq touchscreen protocol output
[17179586.604000] lp0: using parport0 (interrupt-driven).
[17179586.652000] Adding 1028152k swap on /dev/hda2.  Priority:-1 extents:1 across:1028152k
[17179586.688000] EXT3 FS on hda3, internal journal
[17179586.824000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[17179586.824000] md: bitmap version 4.39
[17179587.108000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: dm-devel@redhat.com
[17179587.172000] eth0: link up.
[17179587.584000] cdrom: open failed.
[17179587.600000] NET: Registered protocol family 10
[17179587.600000] lo: Disabled Privacy Extensions
[17179587.600000] IPv6 over IPv4 tunneling driver
[17179598.528000] eth0: no IPv6 routers present
[17179603.864000] NTFS driver 2.1.25 [Flags: R/O MODULE].
[17179603.864000] NTFS driver 2.1.25 [Flags: R/O MODULE].
[17179603.908000] NTFS volume version 3.1.
[17179604.256000] NET: Registered protocol family 17
[17179619.280000] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[17179619.284000] [fglrx] Maximum main memory to use for locked dma buffers: 929 MBytes.
[17179619.284000] [fglrx] module loaded - fglrx 8.25.18 [May 18 2006] on minor 0
[17179619.484000] **** SET: Misaligned resource pointer: e7b702a2 Type 07 Len 0
[17179619.484000] ACPI: PCI Interrupt Link [APC4] enabled at IRQ 19
[17179619.484000] ACPI: PCI Interrupt 0000:02:00.0[A] -> Link [APC4] -> GSI 19 (level, high) -> IRQ 201
[17179620.372000] [fglrx] Internal AGP support requested, but kernel AGP support active.
[17179620.372000] [fglrx] Have to use kernel AGP support to avoid conflicts.
[17179620.372000] [fglrx] AGP detected, AgpState   = 0x1f00421b (hardware caps of chipset)
[17179620.372000] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
[17179620.372000] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[17179620.372000] agpgart: Putting AGP V3 device at 0000:02:00.0 into 8x mode
[17179620.372000] [fglrx] AGP enabled,  AgpCommand = 0x1f004312 (selected caps)
[17179620.380000] [fglrx] total      GART = 67108864
[17179620.380000] [fglrx] free       GART = 51113984
[17179620.380000] [fglrx] max single GART = 51113984
[17179620.380000] [fglrx] total      LFB  = 121630720
[17179620.380000] [fglrx] free       LFB  = 100659200
[17179620.380000] [fglrx] max single LFB  = 100659200
[17179620.380000] [fglrx] total      Inv  = 0
[17179620.380000] [fglrx] free       Inv  = 0
[17179620.380000] [fglrx] max single Inv  = 0
[17179620.380000] [fglrx] total      TIM  = 0
(END)
```

If any one can help me fix this I would greatly appreciate it.
Please help me fix this big ole' mess.

---

### Post by zxee on 2006-08-16
Well a quick diagnosis  is that something is messed up with gnome now. 
Check /var/log/gdm for error messages.

---

### Post by fpwind on 2006-08-16
zxee
Thanks for the quick reply here is my
var/log/gdm
```
X Window System Version 7.0.0
Release Date: 21 December 2005
X Protocol Version 11, Revision 0, Release 7.0
Build Operating System:Linux 2.6.15.7 i686
Current Operating System: Linux Workstation 2.6.15-26-386 #1 PREEMPT Thu Aug 3 02:52:00 UTC 2006 i686
Build Date: 16 March 2006
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Aug 16 10:40:23 2006
(==) Using config file: "/etc/X11/xorg.conf"
(WW) fglrx: No matching Device section for instance (BusID PCI:2:0:1) found
(EE) fglrx(0): === [R200DALGetControllerInfo] === CWDDC ControllerGetConfig failed: 6
(EE) fglrx(0): === [R200DALGetControllerInfo] === CWDDC ControllerGetConfig failed: 6
error opening security policy file /etc/X11/xserver/SecurityPolicy
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument
FreeFontPath: FPE "/usr/share/X11/fonts/misc" refcount is 2, should be 1; fixing.
(EE) fglrx(0): [agp] Failed to remmap MC AGP aperture base!
(EE) fglrx(0): === [R200DALGetControllerInfo] === CWDDC ControllerGetConfig failed: 6
Unsupported Mode: 1280x1024@0.000000
error opening security policy file /etc/X11/xserver/SecurityPolicy
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument
```

Any suggestions?
The thing is if I boot into Recovery mode then I can startx from the shell and gnome starts up and runs with only that error message about the Powermanager thing

---

### Post by zxee on 2006-08-17
I don't see anything in that file that helps point to the problem. :(
What does synaptic tell you about the status of your installed packages? (or you could use sudo apt-get check if you prefer)
I'm thinking that something got clobbered in the kde install/crash.

---

### Post by fpwind on 2006-08-17
So It looks like I'm going to have to reinstall if I can't fix this.  As I'm currently in  Recovery mode is there an easy way to Reinstall everything with out a reformat.  I tried reinstalling ubuntu-desktop via synaptic and it didn't help.

thanks

---

### Post by lupine_nickt on 2006-08-17
Is your /home directory foobar'd? 

One thing that comes to mind is, if it's on a separate partition then that might not be mounting - leading to the error about not being able to cd to it.

If that's not the case, then in the recovery mode console (not in an x-window terminal), run "cd /home" then "ls". If your home directory is listed, then "mv <home-directory> <home-directory>-backup" followed by "cp -a /etc/skel /home/<home-directory>", then "chown -R <home-directory>" and "chgrp -R <home-directory>"

If that solves the problem, then you can hopefully recover any content you have from your backup of the home directory; if it wasn't there, then if you're lucky you might find it in /lost+found

xF,

...Nick

---

### Post by fpwind on 2006-08-17
My home directory is still there I can access the data no problem via nautlius as well as the terminal while i'm in Recovery mode.  It just doesn't want to cd to that directory on start up.  Then Gnome fails to load and I have to boot into Recovery mode.  Then I startx and I can move around in the OS no problem.

---

### Post by fpwind on 2006-08-17
I was able to fix the issue with the good ole' REINSTALL!  Either my KDE install or my crappy usb cable FUBAR'd Gnome.
I guess I needed the practice reconfiguring everything.
My ATI and dual monitor set up went pretty darn quick this time.
Thanks for the responses zxee and lupine

---

### Post by erdalronahi on 2006-08-30
I got the same problem, but am not very keen on reinstalling. I am working now in KDE and XFCE, because I cannot log into GNOME anymore. 

Here is my /var/log/gdm:


X Window System Version 7.0.0
Release Date: 21 December 2005
X Protocol Version 11, Revision 0, Release 7.0
Build Operating System:Linux 2.6.17-6-686 i686
Current Operating System: Linux erdal-laptop 2.6.15-26-686 #1 SMP PREEMPT Thu Aug 3 03:13:28 UTC 2006 i686
Build Date: 16 March 2006
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Aug 30 19:03:00 2006
(==) Using config file: "/etc/X11/xorg.conf"
(**) RADEON(0): RADEONPreInit
(**) RADEON(0): RADEONScreenInit f0000000 0
(**) RADEON(0): Map: 0xf0000000, 0x04000000
(**) RADEON(0): RADEONSave
(**) RADEON(0): RADEONSaveMode(0x81fef7c)
(**) RADEON(0): Read: 0x00000006 0x00040048 0x00000000
(**) RADEON(0): Read: rd=6, fd=72, pd=4
(**) RADEON(0): RADEONSaveMode returns 0x81fef7c
(**) RADEON(0): DRI New memory map param
(**) RADEON(0): RADEONInitMemoryMap() : 
(**) RADEON(0):   mem_size         : 0x04000000
(**) RADEON(0):   agp_size         : 0x081fee50
(**) RADEON(0):   agp_base         : 0x081fee50
(**) RADEON(0):   MC_FB_LOCATION   : 0xf3fff000
(**) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
(**) RADEON(0): RADEONModeInit()
1400x1050     108.00  1400 34208 34320 1688  1050 1050 1053 1063 (24,32)
1400x1050     108.00  1400 34208 34320 1688  1050 1050 1053 1063 (24,32)
(**) RADEON(0): Pitch = 11534512 bytes (virtualX = 1400, displayWidth = 1408)
(**) RADEON(0): RADEONInit returns 0x81ff92c
(**) RADEON(0): RADEONRestoreMode()
(**) RADEON(0): RADEONRestoreMode(0x81ff92c)
(**) RADEON(0): RADEONRestoreMemMapRegisters() : 
(**) RADEON(0):   MC_FB_LOCATION   : 0xf3fff000
(**) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
(**) RADEON(0):   Map Changed ! Applying ...
(**) RADEON(0):   Map applied, resetting engine ...
(**) RADEON(0): Updating display base addresses...
(**) RADEON(0): Memory map updated.
(**) RADEON(0): Programming CRTC1, offset: 0x00000000
(**) RADEON(0): GRPH_BUFFER_CNTL from 20057c7c to 200e5c5c
(**) RADEON(0): RADEONSaveScreen(0)
(**) RADEON(0): Setting up initial surfaces
(**) RADEON(0): Initializing fb layer
(**) RADEON(0): Setting up accel memmap
(**) RADEON(0): Initializing backing store
(**) RADEON(0): DRI Finishing init !
(**) RADEON(0): EngineRestore (32/32)
(**) RADEON(0): GRPH_BUFFER_CNTL from 20057c7c to 200e5c5c
(**) RADEON(0): Setting up final surfaces
(**) RADEON(0): Initializing Acceleration
(**) RADEON(0): EngineInit (32/32)
(**) RADEON(0): Pitch for acceleration = 176
(**) RADEON(0): EngineRestore (32/32)
(**) RADEON(0): Initializing DPMS
(**) RADEON(0): Initializing Cursor
(**) RADEON(0): Initializing color map
(**) RADEON(0): Initializing DGA
(**) RADEON(0): Initializing Xv
(**) RADEON(0): RADEONScreenInit finished
error opening security policy file /etc/X11/xserver/SecurityPolicy
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument
Synaptics DeviceInit called
SynapticsCtrl called.
Synaptics DeviceOn called
(**) RADEON(0): RADEONSaveScreen(2)
ProcXCloseDevice to close or not ?

   *** If unresolved symbols were reported above, they might not
   *** be the reason for the server aborting.

Backtrace:
0: /usr/bin/X(xf86SigHandler+0x86) [0x80b4ab6]
1: [0xffffe420]
2: /usr/lib/xorg/modules/libfb.so(fbCompositeCopyAreammx+0x60) [0xb7878c81]
3: /usr/lib/xorg/modules/libfb.so(fbComposite+0x569) [0xb786c2a6]
4: /usr/lib/xorg/modules/libxaa.so(XAAComposite+0x214) [0xb7825545]
5: /usr/bin/X [0x8146eaf]
6: /usr/bin/X(CompositePicture+0xef) [0x813ab43]
7: /usr/bin/X [0x813c208]
8: /usr/bin/X [0x813e9de]
9: /usr/bin/X(Dispatch+0x19e) [0x8085d56]
10: /usr/bin/X(main+0x47c) [0x806e0d8]
11: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xd2) [0xb7d4dea2]
12: /usr/bin/X(FontFileCompleteXLFD+0x85) [0x806d641]

Fatal server error:
Caught signal 11.  Server aborting

(**) RADEON(0): RADEONLeaveVT
(**) RADEON(0): EngineRestore (32/32)
(**) RADEON(0): RADEONRestore
(**) RADEON(0): RADEONRestoreMode()
(**) RADEON(0): RADEONRestoreMode(0x81fef7c)
(**) RADEON(0): RADEONRestoreMemMapRegisters() : 
(**) RADEON(0):   MC_FB_LOCATION   : 0x1fff0000
(**) RADEON(0):   MC_AGP_LOCATION  : 0x27ff2000
(**) RADEON(0):   Map Changed ! Applying ...
(**) RADEON(0):   Map applied, resetting engine ...
(**) RADEON(0): Updating display base addresses...
(**) RADEON(0): Memory map updated.
(**) RADEON(0): Programming CRTC1, offset: 0x00000000
(**) RADEON(0): Ok, leaving now...

---

### Post by xtknight on 2006-08-30
Sounds like your having the same powermanager problems as this guy: [http://www.ubuntuforums.org/showthread.php?t=225671](http://www.ubuntuforums.org/showthread.php?t=225671)

---

