---
title: "How to fix Ubuntu booting to terminal login?"
date: 2010-07-16
forum: Desktop Environments
---

### Post by qopit on 2010-07-16
I had a miserably hellish Ubuntu 10.04 install experience after many different attempts, and finally realized the main problem was networking failing on my nForce board.  I used the alternative install disk and managed to get to the point where I could actually get to a command prompt to fix up my network settings (eth0 was not set up for some reason).

After I fixed my network settings, I did a full update+upgrade from the command line and rebooted, After rebooting, Ubuntu is now booting straight to a text based terminal login.  I can 'startx' ok from there, but this is non-ideal (and the shutdown button in the top right curiously does nothing when I do).

I am not booting to recovery mode, I'm selecting the normal boot from GRUB.

After much investigation I've tried reinstalling gdm, ubuntu-desktop, and have even done a full install of kubuntu-desktop in hopes that it would magically fix the problem.  It did not.  I still get a text login on boot.

I wondered if I had a runlevel issue, but looking into runlevel for Ubuntu seems to indicate that Ubuntu doesn't really use it.  Just in case, when I run "runlevel" I get "N 2".

Help!  How do I restore a normal graphical Ubuntu boot sequence?

---

### Post by pastalavista on 2010-07-16
It would help to know the cpu, gpu, memory etc. Have you tried reconfiguring the xserver? ```
sudo dpkg-reconfigure xserver-xorg
```...a shot in the dark

---

### Post by TechBeastie on 2010-07-16
A while back, I was actually trying to accomplish precisely what you've managed to achieve involuntarily: I have a server which I wanted to prevent from automatically launching the xserver upon startup, mostly to save system resources.  
To accomplish this, I know I had to modify the /etc/init/gdm file - and I also read somewhere that /etc/X11/default-display/manager might have a role to play in the X-startup process.  I'm not sure what lines you'll need to change in these files, but hopefully this will at least give you a starting point...

You might also want to check the system logs (with dmesg) to make sure that nothing X or gdm-related is erroring out upon bootup.  

Good luck!

---

### Post by qopit on 2010-07-17
> **pastalavista said:**
> It would help to know the cpu, gpu, memory etc. Have you tried reconfiguring the xserver? ```
sudo dpkg-reconfigure xserver-xorg
```...a shot in the dark

I've got a Zotac GeForce 9300-ITX mobo that has an nVidia Geforce 9300 in it.  CPU is Intel quad core.  Networking et al are all nForce on board.  I have 2 GB RAM.

Again - startx works fine once I hit the command prompt, the sequencing just seems messed up somehow.

I had tried:

```
sudo dpkg-reconfigure xserver-xorg
```

but nothing happened.  By nothing I mean I got no prompting or anything, it just silently accepted the command.  I was expecting some reconfiguration prompts, no?  On reboot nothing was changed.

For HW info if it helps somehow, here is a full lshw output:
```

my-desktop
    description: Desktop Computer
    product: MCP7A
    vendor: NVIDIA
    version: 2
    serial: 1
    width: 64 bits
    capabilities: smbios-2.5 dmi-2.5 vsyscall64 vsyscall32
    configuration: boot=normal chassis=desktop
  *-core
       description: Motherboard
       product: MCP7A
       vendor: NVIDIA
       physical id: 0
       version: 2
       serial: 1
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies, LTD
          physical id: 0
          version: 6.00 PG (02/02/2009)
          size: 128KiB
          capacity: 960KiB
          capabilities: isa pci pnp apm upgrade shadowing cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Core(TM)2 Quad CPU    Q8200  @ 2.33GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: Intel(R) Core(TM)2 Quad
          slot: Socket 775
          size: 2GHz
          capacity: 2GHz
          width: 64 bits
          clock: 333MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx x86-64 constant_tsc arch_perfmon pebs bts rep_good aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm sse4_1 xsave lahf_lm cpufreq
        *-cache:0
             description: L1 cache
             physical id: a
             slot: Internal Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: b
             slot: External Cache
             size: 4MiB
             capacity: 4MiB
             capabilities: synchronous external write-back
     *-memory
          description: System Memory
          physical id: 1e
          slot: System board or motherboard
          size: 2GiB
          capacity: 2GiB
        *-bank:0
             description: DIMM DRAM [empty]
             product: None
             vendor: None
             physical id: 0
             serial: None
             slot: A0
             width: 3584 bits
        *-bank:1
             description: DIMM DRAM 667 MHz (1.5 ns)
             product: None
             vendor: None
             physical id: 1
             serial: None
             slot: A1
             size: 2GiB
             width: 3 bits
             clock: 667MHz (1.5ns)
        *-bank:2
             description: DIMM DRAM [empty]
             product: None
             vendor: None
             physical id: 2
             serial: None
             slot: A2
             width: 515 bits
        *-bank:3
             description: DIMM DRAM [empty]
             product: None
             vendor: None
             physical id: 3
             serial: None
             slot: A3
             width: 3 bits
     *-pci
          description: Host bridge
          product: MCP79 Host Bridge
          vendor: nVidia Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: b1
          width: 32 bits
          clock: 66MHz
        *-memory:0 UNCLAIMED
             description: RAM memory
             product: MCP79 Memory Controller
             vendor: nVidia Corporation
             physical id: 0.1
             bus info: pci@0000:00:00.1
             version: b1
             width: 32 bits
             clock: 66MHz (15.2ns)
             capabilities: bus_master
             configuration: latency=0
        *-isa
             description: ISA bridge
             product: MCP79 LPC Bridge
             vendor: nVidia Corporation
             physical id: 3
             bus info: pci@0000:00:03.0
             version: b2
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-memory:1 UNCLAIMED
             description: RAM memory
             product: MCP79 Memory Controller
             vendor: nVidia Corporation
             physical id: 3.1
             bus info: pci@0000:00:03.1
             version: b1
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-serial
             description: SMBus
             product: MCP79 SMBus
             vendor: nVidia Corporation
             physical id: 3.2
             bus info: pci@0000:00:03.2
             version: b1
             width: 32 bits
             clock: 66MHz
             capabilities: pm cap_list
             configuration: driver=nForce2_smbus latency=0
             resources: irq:10 ioport:ff00(size=64) ioport:1c00(size=64) ioport:1c80(size=64)
        *-memory:2 UNCLAIMED
             description: RAM memory
             product: MCP79 Memory Controller
             vendor: nVidia Corporation
             physical id: 3.3
             bus info: pci@0000:00:03.3
             version: b1
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-memory:3 UNCLAIMED
             description: RAM memory
             product: nVidia Corporation
             vendor: nVidia Corporation
             physical id: 3.4
             bus info: pci@0000:00:03.4
             version: b1
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-processor UNCLAIMED
             description: Co-processor
             product: MCP79 Co-processor
             vendor: nVidia Corporation
             physical id: 3.5
             bus info: pci@0000:00:03.5
             version: b1
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: latency=0 maxlatency=1 mingnt=3
             resources: memory:fdf80000-fdffffff
        *-usb:0
             description: USB Controller
             product: MCP79 OHCI USB 1.1 Controller
             vendor: nVidia Corporation
             physical id: 4
             bus info: pci@0000:00:04.0
             version: b1
             width: 32 bits
             clock: 66MHz
             capabilities: pm bus_master cap_list
             configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3
             resources: irq:20 memory:fe02f000-fe02ffff
        *-usb:1
             description: USB Controller
             product: MCP79 EHCI USB 2.0 Controller
             vendor: nVidia Corporation
             physical id: 4.1
             bus info: pci@0000:00:04.1
             version: b1
             width: 32 bits
             clock: 66MHz
             capabilities: debug pm bus_master cap_list
             configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3
             resources: irq:22 memory:fe02e000-fe02e0ff
        *-usb:2
             description: USB Controller
             product: MCP79 OHCI USB 1.1 Controller
             vendor: nVidia Corporation
             physical id: 6
             bus info: pci@0000:00:06.0
             version: b1
             width: 32 bits
             clock: 66MHz
             capabilities: pm bus_master cap_list
             configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3
             resources: irq:23 memory:fe02d000-fe02dfff
        *-usb:3
             description: USB Controller
             product: MCP79 EHCI USB 2.0 Controller
             vendor: nVidia Corporation
             physical id: 6.1
             bus info: pci@0000:00:06.1
             version: b1
             width: 32 bits
             clock: 66MHz
             capabilities: debug pm bus_master cap_list
             configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3
             resources: irq:21 memory:fe02c000-fe02c0ff
        *-multimedia
             description: Audio device
             product: MCP79 High Definition Audio
             vendor: nVidia Corporation
             physical id: 8
             bus info: pci@0000:00:08.0
             version: b1
             width: 32 bits
             clock: 66MHz
             capabilities: pm bus_master cap_list
             configuration: driver=HDA Intel latency=0 maxlatency=5 mingnt=2
             resources: irq:20 memory:fe020000-fe023fff
        *-pci:0
             description: PCI bridge
             product: MCP79 PCI Bridge
             vendor: nVidia Corporation
             physical id: 9
             bus info: pci@0000:00:09.0
             version: b1
             width: 32 bits
             clock: 66MHz
             capabilities: pci bus_master cap_list
             resources: ioport:e000(size=4096) memory:fde00000-fdefffff memory:fdd00000-fddfffff(prefetchable)
        *-network
             description: Ethernet interface
             product: MCP79 Ethernet
             vendor: nVidia Corporation
             physical id: a
             bus info: pci@0000:00:0a.0
             logical name: eth0
             version: b1
             serial: 00:01:2e:24:3e:68
             size: 100MB/s
             capacity: 1GB/s
             width: 32 bits
             clock: 66MHz
             capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 duplex=full ip=192.168.1.6 latency=0 link=yes maxlatency=20 mingnt=1 multicast=yes port=MII speed=100MB/s
             resources: irq:22 memory:fe02b000-fe02bfff ioport:fc00(size=8) memory:fe02a000-fe02a0ff memory:fe029000-fe02900f
        *-ide
             description: IDE interface
             product: MCP79 SATA Controller
             vendor: nVidia Corporation
             physical id: b
             bus info: pci@0000:00:0b.0
             logical name: scsi0
             version: b1
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm msi bus_master cap_list emulated
             configuration: driver=ahci latency=0 maxlatency=1 mingnt=3
             resources: irq:29 ioport:9f0(size=8) ioport:bf0(size=4) ioport:970(size=8) ioport:b70(size=4) ioport:f700(size=16) memory:fe026000-fe027fff
           *-disk
                description: ATA Disk
                product: WDC WD3200BJKT-7
                vendor: Western Digital
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 11.0
                serial: WD-WXT0A49T9049
                size: 298GiB (320GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=f7b8f7b8
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   version: 3.1
                   serial: d411c5c8-8c3d-204d-ad1e-5b6cdb5191a8
                   size: 78GiB
                   capacity: 78GiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2009-06-28 14:00:04 filesystem=ntfs state=clean
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 219GiB
                   capacity: 219GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 7629MiB
                      capabilities: nofs
                 *-logicalvolume:1
                      description: Linux filesystem partition
                      physical id: 6
                      logical name: /dev/sda6
                      logical name: /
                      capacity: 212GiB
                      configuration: mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered state=mounted
        *-pci:1
             description: PCI bridge
             product: MCP79 PCI Express Bridge
             vendor: nVidia Corporation
             physical id: c
             bus info: pci@0000:00:0c.0
             version: b1
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress bus_master cap_list
             configuration: driver=pcieport
             resources: irq:24 ioport:d000(size=4096) memory:fdc00000-fdcfffff ioport:fdb00000(size=1048576)
        *-pci:2
             description: PCI bridge
             product: MCP79 PCI Express Bridge
             vendor: nVidia Corporation
             physical id: 10
             bus info: pci@0000:00:10.0
             version: b1
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi bus_master cap_list
             resources: ioport:c000(size=4096) memory:fb000000-fcffffff ioport:d0000000(size=536870912)
           *-display
                description: VGA compatible controller
                product: C79 [GeForce 9300 / nForce 730i]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:03:00.0
                version: b1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi bus_master cap_list rom
                configuration: driver=nouveau latency=0
                resources: irq:21 memory:fb000000-fbffffff memory:d0000000-dfffffff(prefetchable) memory:ee000000-efffffff(prefetchable) ioport:cf00(size=128) memory:e0000000-e001ffff(prefetchable)
        *-pci:3
             description: PCI bridge
             product: MCP79 PCI Express Bridge
             vendor: nVidia Corporation
             physical id: 15
             bus info: pci@0000:00:15.0
             version: b1
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress bus_master cap_list
             configuration: driver=pcieport
             resources: irq:25 ioport:b000(size=4096) memory:fda00000-fdafffff ioport:fd900000(size=1048576)
        *-pci:4
             description: PCI bridge
             product: MCP79 PCI Express Bridge
             vendor: nVidia Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: b1
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress bus_master cap_list
             configuration: driver=pcieport
             resources: irq:26 ioport:a000(size=4096) memory:fd800000-fd8fffff ioport:fd700000(size=1048576)
        *-pci:5
             description: PCI bridge
             product: MCP79 PCI Express Bridge
             vendor: nVidia Corporation
             physical id: 17
             bus info: pci@0000:00:17.0
             version: b1
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress bus_master cap_list
             configuration: driver=pcieport
             resources: irq:27 ioport:9000(size=4096) memory:fd600000-fd6fffff ioport:fd500000(size=1048576)
        *-pci:6
             description: PCI bridge
             product: MCP79 PCI Express Bridge
             vendor: nVidia Corporation
             physical id: 18
             bus info: pci@0000:00:18.0
             version: b1
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress bus_master cap_list
             configuration: driver=pcieport
             resources: irq:28 ioport:8000(size=4096) memory:fd400000-fd4fffff ioport:fd300000(size=1048576)
     *-scsi
          physical id: 1
          bus info: usb@2:6
          logical name: scsi6
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-cdrom
             description: DVD-RAM writer
             product: SBC-06D1S-U
             vendor: ASUS
             physical id: 0.0.0
             bus info: scsi@6:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/dvdrw
             logical name: /dev/scd0
             logical name: /dev/sr0
             version: A201
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: status=open
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: eth1
       serial: 00:00:00:00:00:01
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=802.11-a/b/g
```

---

### Post by qopit on 2010-07-17
> **TechBeastie said:**
> A while back, I was actually trying to accomplish precisely what you've managed to achieve involuntarily: I have a server which I wanted to prevent from automatically launching the xserver upon startup, mostly to save system resources.  
To accomplish this, I know I had to modify the /etc/init/gdm file - and I also read somewhere that /etc/X11/default-display/manager might have a role to play in the X-startup process.  I'm not sure what lines you'll need to change in these files, but hopefully this will at least give you a starting point...

Thanks.  I checked /etc/init/gdm.conf and it seems to just be a generic file.  Here is my copy:```

# gdm - GNOME Display Manager
#
# The display manager service manages the X servers running on the
# system, providing login and auto-login services

description	"GNOME Display Manager"
author		"William Jon McCann <mccann@jhu.edu>"

start on (filesystem
          and started dbus
          and (graphics-device-added fb0 PRIMARY_DEVICE_FOR_DISPLAY=1
               or drm-device-added card0 PRIMARY_DEVICE_FOR_DISPLAY=1
               or stopped udevtrigger))
stop on runlevel [016]

emits starting-dm

env XORGCONFIG=/etc/X11/xorg.conf

script
    if [ -n "$UPSTART_EVENTS" ]
    then
	[ ! -f /etc/X11/default-display-manager -o "$(cat /etc/X11/default-display-manager 2>/dev/null)" = "/usr/sbin/gdm" ] || { stop; exit 0; }

	# Check kernel command-line for inhibitors
	for ARG in $(cat /proc/cmdline)
	do
	    case "${ARG}" in
		text|-s|s|S|single)
		    plymouth quit || :  # We have the ball here
		    exit 0
		    ;;
	    esac
	done
    fi

    if [ -r /etc/default/locale ]; then
	. /etc/default/locale
	export LANG LANGUAGE
    elif [ -r /etc/environment ]; then
	. /etc/environment
	export LANG LANGUAGE
    fi
    export XORGCONFIG

    exec gdm-binary $CONFIG_FILE
end script
```

As for "/etc/X11/default-display-manager", it is just a single line, and mine is:```
kdm
```
I recall choosing kde as my default desktop when doing the desperation kubuntu-desktop install.  What is curious and maybe a clue where my sequencing problem is is that when I do "startx" from my command-line it actually launches into Gnome.


> **TechBeastie said:**
> You might also want to check the system logs (with dmesg) to make sure that nothing X or gdm-related is erroring out upon bootup.


Here is the latter part of my dmesg output:
```
[    0.850698] ACPI: PCI Interrupt Link [LE5D] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.850904] ACPI: PCI Interrupt Link [LE6A] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.851109] ACPI: PCI Interrupt Link [LE6B] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.851315] ACPI: PCI Interrupt Link [LE6C] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.851520] ACPI: PCI Interrupt Link [LE6D] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.851724] ACPI: PCI Interrupt Link [LE7A] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.851929] ACPI: PCI Interrupt Link [LE7B] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.852134] ACPI: PCI Interrupt Link [LE7C] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.852338] ACPI: PCI Interrupt Link [LE7D] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.852542] ACPI: PCI Interrupt Link [LP2P] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.852747] ACPI: PCI Interrupt Link [LIGP] (IRQs *5 7 9 10 11 14 15)
[    0.852952] ACPI: PCI Interrupt Link [LUBA] (IRQs 5 7 9 10 *11 14 15)
[    0.853156] ACPI: PCI Interrupt Link [LUB2] (IRQs 5 *7 9 10 11 14 15)
[    0.853360] ACPI: PCI Interrupt Link [LU1B] (IRQs *5 7 9 10 11 14 15)
[    0.853572] ACPI: PCI Interrupt Link [LU2B] (IRQs 5 7 9 *10 11 14 15)
[    0.853776] ACPI: PCI Interrupt Link [LMAC] (IRQs 5 7 9 10 11 14 *15)
[    0.853984] ACPI: PCI Interrupt Link [LAZA] (IRQs 5 *7 9 10 11 14 15)
[    0.854193] ACPI: PCI Interrupt Link [LPMU] (IRQs 5 7 9 10 *11 14 15)
[    0.854398] ACPI: PCI Interrupt Link [LSMB] (IRQs 5 7 9 *10 11 14 15)
[    0.854606] ACPI: PCI Interrupt Link [LIDE] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.854815] ACPI: PCI Interrupt Link [LSID] (IRQs 5 7 9 10 *11 14 15)
[    0.855060] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0, disabled.
[    0.855297] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0, disabled.
[    0.855532] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0, disabled.
[    0.855767] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0, disabled.
[    0.856002] ACPI: PCI Interrupt Link [AE0A] (IRQs 16) *0, disabled.
[    0.856237] ACPI: PCI Interrupt Link [AE0B] (IRQs 16) *0, disabled.
[    0.856472] ACPI: PCI Interrupt Link [AE0C] (IRQs 16) *0, disabled.
[    0.856708] ACPI: PCI Interrupt Link [AE0D] (IRQs 16) *0, disabled.
[    0.856943] ACPI: PCI Interrupt Link [AE1A] (IRQs 16) *0, disabled.
[    0.857178] ACPI: PCI Interrupt Link [AE1B] (IRQs 16) *0, disabled.
[    0.857413] ACPI: PCI Interrupt Link [AE1C] (IRQs 16) *0, disabled.
[    0.857648] ACPI: PCI Interrupt Link [AE1D] (IRQs 16) *0, disabled.
[    0.857883] ACPI: PCI Interrupt Link [AE2A] (IRQs 16) *0, disabled.
[    0.858118] ACPI: PCI Interrupt Link [AE2B] (IRQs 16) *0, disabled.
[    0.858354] ACPI: PCI Interrupt Link [AE2C] (IRQs 16) *0, disabled.
[    0.858588] ACPI: PCI Interrupt Link [AE2D] (IRQs 16) *0, disabled.
[    0.858823] ACPI: PCI Interrupt Link [AE3A] (IRQs 16) *0, disabled.
[    0.859058] ACPI: PCI Interrupt Link [AE3B] (IRQs 16) *0, disabled.
[    0.859293] ACPI: PCI Interrupt Link [AE3C] (IRQs 16) *0, disabled.
[    0.859528] ACPI: PCI Interrupt Link [AE3D] (IRQs 16) *0, disabled.
[    0.859763] ACPI: PCI Interrupt Link [AE4A] (IRQs 16) *0, disabled.
[    0.860024] ACPI: PCI Interrupt Link [AE4B] (IRQs 16) *0, disabled.
[    0.860261] ACPI: PCI Interrupt Link [AE4C] (IRQs 16) *0, disabled.
[    0.860499] ACPI: PCI Interrupt Link [AE4D] (IRQs 16) *0, disabled.
[    0.860739] ACPI: PCI Interrupt Link [AE5A] (IRQs 16) *0, disabled.
[    0.860974] ACPI: PCI Interrupt Link [AE5B] (IRQs 16) *0, disabled.
[    0.861209] ACPI: PCI Interrupt Link [AE5C] (IRQs 16) *0, disabled.
[    0.861444] ACPI: PCI Interrupt Link [AE5D] (IRQs 16) *0, disabled.
[    0.861678] ACPI: PCI Interrupt Link [AE6A] (IRQs 16) *0, disabled.
[    0.861914] ACPI: PCI Interrupt Link [AE6B] (IRQs 16) *0, disabled.
[    0.862149] ACPI: PCI Interrupt Link [AE6C] (IRQs 16) *0, disabled.
[    0.862384] ACPI: PCI Interrupt Link [AE6D] (IRQs 16) *0, disabled.
[    0.862619] ACPI: PCI Interrupt Link [AE7A] (IRQs 16) *0, disabled.
[    0.862854] ACPI: PCI Interrupt Link [AE7B] (IRQs 16) *0, disabled.
[    0.863090] ACPI: PCI Interrupt Link [AE7C] (IRQs 16) *0, disabled.
[    0.863328] ACPI: PCI Interrupt Link [AE7D] (IRQs 16) *0, disabled.
[    0.863563] ACPI: PCI Interrupt Link [AIGP] (IRQs 20 21 22 23) *0
[    0.863799] ACPI: PCI Interrupt Link [AUBA] (IRQs 20 21 22 23) *0
[    0.864034] ACPI: PCI Interrupt Link [AUB2] (IRQs 20 21 22 23) *0
[    0.864270] ACPI: PCI Interrupt Link [AU1B] (IRQs 20 21 22 23) *0
[    0.864505] ACPI: PCI Interrupt Link [AU2B] (IRQs 20 21 22 23) *0
[    0.864741] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22 23) *0
[    0.864976] ACPI: PCI Interrupt Link [APMU] (IRQs 20 21 22 23) *0
[    0.865212] ACPI: PCI Interrupt Link [AAZA] (IRQs 20 21 22 23) *0
[    0.865448] ACPI: PCI Interrupt Link [APCS] (IRQs 20 21 22 23) *0
[    0.865683] ACPI: PCI Interrupt Link [APCM] (IRQs 20 21 22 23) *0, disabled.
[    0.865921] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22 23) *0, disabled.
[    0.866162] ACPI: PCI Interrupt Link [APSI] (IRQs 20 21 22 23) *0
[    0.866300] vgaarb: device added: PCI:0000:03:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.866302] vgaarb: loaded
[    0.866401] SCSI subsystem initialized
[    0.866441] libata version 3.00 loaded.
[    0.866441] usbcore: registered new interface driver usbfs
[    0.866441] usbcore: registered new interface driver hub
[    0.866441] usbcore: registered new device driver usb
[    0.866441] ACPI: WMI: Mapper loaded
[    0.866441] PCI: Using ACPI for IRQ routing
[    0.866441] NetLabel: Initializing
[    0.866441] NetLabel:  domain hash size = 128
[    0.866441] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.866441] NetLabel:  unlabeled traffic allowed by default
[    0.866441] hpet0: at MMIO 0xfeff0000, IRQs 2, 8, 31, 31
[    0.866441] hpet0: 4 comparators, 64-bit 25.000000 MHz counter
[    0.880018] Switching to clocksource tsc
[    0.881893] AppArmor: AppArmor Filesystem Enabled
[    0.881923] pnp: PnP ACPI init
[    0.881951] ACPI: bus type pnp registered
[    0.889515] pnp: PnP ACPI: found 11 devices
[    0.889517] ACPI: ACPI bus type pnp unregistered
[    0.889530] system 00:01: ioport range 0x1000-0x107f has been reserved
[    0.889533] system 00:01: ioport range 0x1080-0x10ff has been reserved
[    0.889536] system 00:01: ioport range 0x1400-0x147f has been reserved
[    0.889538] system 00:01: ioport range 0x1480-0x14ff has been reserved
[    0.889540] system 00:01: ioport range 0x1800-0x187f has been reserved
[    0.889542] system 00:01: ioport range 0x1880-0x18ff has been reserved
[    0.889546] system 00:01: iomem range 0xfefe1000-0xfefe10ff has been reserved
[    0.889549] system 00:01: iomem range 0x6ff00000-0x7fefffff has been reserved
[    0.889554] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
[    0.889556] system 00:02: ioport range 0x880-0x88f has been reserved
[    0.889563] system 00:09: iomem range 0xf0000000-0xf1ffffff has been reserved
[    0.889568] system 00:0a: iomem range 0xf0000-0xfffff could not be reserved
[    0.889571] system 00:0a: iomem range 0xfeff0000-0xfeff00ff has been reserved
[    0.889573] system 00:0a: iomem range 0x6fee0000-0x6fefffff could not be reserved
[    0.889576] system 00:0a: iomem range 0xffff0000-0xffffffff has been reserved
[    0.889578] system 00:0a: iomem range 0x0-0x9ffff could not be reserved
[    0.889581] system 00:0a: iomem range 0x100000-0x6fedffff could not be reserved
[    0.889583] system 00:0a: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.889586] system 00:0a: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.889589] system 00:0a: iomem range 0xfeff0000-0xfeff03ff could not be reserved
[    0.894420] pci 0000:00:09.0: PCI bridge, secondary bus 0000:01
[    0.894423] pci 0000:00:09.0:   IO window: 0xe000-0xefff
[    0.894427] pci 0000:00:09.0:   MEM window: 0xfde00000-0xfdefffff
[    0.894431] pci 0000:00:09.0:   PREFETCH window: 0xfdd00000-0xfddfffff
[    0.894436] pci 0000:00:0c.0: PCI bridge, secondary bus 0000:02
[    0.894440] pci 0000:00:0c.0:   IO window: 0xd000-0xdfff
[    0.894450] pci 0000:00:0c.0:   MEM window: 0xfdc00000-0xfdcfffff
[    0.894458] pci 0000:00:0c.0:   PREFETCH window: 0x000000fdb00000-0x000000fdbfffff
[    0.894473] pci 0000:00:10.0: PCI bridge, secondary bus 0000:03
[    0.894475] pci 0000:00:10.0:   IO window: 0xc000-0xcfff
[    0.894479] pci 0000:00:10.0:   MEM window: 0xfb000000-0xfcffffff
[    0.894481] pci 0000:00:10.0:   PREFETCH window: 0x000000d0000000-0x000000efffffff
[    0.894485] pci 0000:00:15.0: PCI bridge, secondary bus 0000:04
[    0.894490] pci 0000:00:15.0:   IO window: 0xb000-0xbfff
[    0.894500] pci 0000:00:15.0:   MEM window: 0xfda00000-0xfdafffff
[    0.894507] pci 0000:00:15.0:   PREFETCH window: 0x000000fd900000-0x000000fd9fffff
[    0.894520] pci 0000:00:16.0: PCI bridge, secondary bus 0000:05
[    0.894525] pci 0000:00:16.0:   IO window: 0xa000-0xafff
[    0.894535] pci 0000:00:16.0:   MEM window: 0xfd800000-0xfd8fffff
[    0.894542] pci 0000:00:16.0:   PREFETCH window: 0x000000fd700000-0x000000fd7fffff
[    0.894555] pci 0000:00:17.0: PCI bridge, secondary bus 0000:06
[    0.894559] pci 0000:00:17.0:   IO window: 0x9000-0x9fff
[    0.894569] pci 0000:00:17.0:   MEM window: 0xfd600000-0xfd6fffff
[    0.894577] pci 0000:00:17.0:   PREFETCH window: 0x000000fd500000-0x000000fd5fffff
[    0.894589] pci 0000:00:18.0: PCI bridge, secondary bus 0000:07
[    0.894594] pci 0000:00:18.0:   IO window: 0x8000-0x8fff
[    0.894604] pci 0000:00:18.0:   MEM window: 0xfd400000-0xfd4fffff
[    0.894611] pci 0000:00:18.0:   PREFETCH window: 0x000000fd300000-0x000000fd3fffff
[    0.894631] pci 0000:00:09.0: setting latency timer to 64
[    0.894993] ACPI: PCI Interrupt Link [AE0A] enabled at IRQ 16
[    0.894997]   alloc irq_desc for 16 on node -1
[    0.894999]   alloc kstat_irqs on node -1
[    0.895003] pci 0000:00:0c.0: PCI INT A -> Link[AE0A] -> GSI 16 (level, low) -> IRQ 16
[    0.895012] pci 0000:00:0c.0: setting latency timer to 64
[    0.895020] pci 0000:00:10.0: setting latency timer to 64
[    0.895370] ACPI: PCI Interrupt Link [AE3A] enabled at IRQ 16
[    0.895374] pci 0000:00:15.0: PCI INT A -> Link[AE3A] -> GSI 16 (level, low) -> IRQ 16
[    0.895382] pci 0000:00:15.0: setting latency timer to 64
[    0.895733] ACPI: PCI Interrupt Link [AE4A] enabled at IRQ 16
[    0.895736] pci 0000:00:16.0: PCI INT A -> Link[AE4A] -> GSI 16 (level, low) -> IRQ 16
[    0.895744] pci 0000:00:16.0: setting latency timer to 64
[    0.896094] ACPI: PCI Interrupt Link [AE5A] enabled at IRQ 16
[    0.896097] pci 0000:00:17.0: PCI INT A -> Link[AE5A] -> GSI 16 (level, low) -> IRQ 16
[    0.896105] pci 0000:00:17.0: setting latency timer to 64
[    0.896457] ACPI: PCI Interrupt Link [AE6A] enabled at IRQ 16
[    0.896460] pci 0000:00:18.0: PCI INT A -> Link[AE6A] -> GSI 16 (level, low) -> IRQ 16
[    0.896468] pci 0000:00:18.0: setting latency timer to 64
[    0.896474] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.896476] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffffffffffff]
[    0.896479] pci_bus 0000:01: resource 0 io:  [0xe000-0xefff]
[    0.896481] pci_bus 0000:01: resource 1 mem: [0xfde00000-0xfdefffff]
[    0.896483] pci_bus 0000:01: resource 2 pref mem [0xfdd00000-0xfddfffff]
[    0.896485] pci_bus 0000:01: resource 3 io:  [0x00-0xffff]
[    0.896487] pci_bus 0000:01: resource 4 mem: [0x000000-0xffffffffffffffff]
[    0.896489] pci_bus 0000:02: resource 0 io:  [0xd000-0xdfff]
[    0.896491] pci_bus 0000:02: resource 1 mem: [0xfdc00000-0xfdcfffff]
[    0.896493] pci_bus 0000:02: resource 2 pref mem [0xfdb00000-0xfdbfffff]
[    0.896496] pci_bus 0000:03: resource 0 io:  [0xc000-0xcfff]
[    0.896498] pci_bus 0000:03: resource 1 mem: [0xfb000000-0xfcffffff]
[    0.896500] pci_bus 0000:03: resource 2 pref mem [0xd0000000-0xefffffff]
[    0.896502] pci_bus 0000:04: resource 0 io:  [0xb000-0xbfff]
[    0.896504] pci_bus 0000:04: resource 1 mem: [0xfda00000-0xfdafffff]
[    0.896506] pci_bus 0000:04: resource 2 pref mem [0xfd900000-0xfd9fffff]
[    0.896508] pci_bus 0000:05: resource 0 io:  [0xa000-0xafff]
[    0.896510] pci_bus 0000:05: resource 1 mem: [0xfd800000-0xfd8fffff]
[    0.896512] pci_bus 0000:05: resource 2 pref mem [0xfd700000-0xfd7fffff]
[    0.896514] pci_bus 0000:06: resource 0 io:  [0x9000-0x9fff]
[    0.896516] pci_bus 0000:06: resource 1 mem: [0xfd600000-0xfd6fffff]
[    0.896518] pci_bus 0000:06: resource 2 pref mem [0xfd500000-0xfd5fffff]
[    0.896520] pci_bus 0000:07: resource 0 io:  [0x8000-0x8fff]
[    0.896522] pci_bus 0000:07: resource 1 mem: [0xfd400000-0xfd4fffff]
[    0.896524] pci_bus 0000:07: resource 2 pref mem [0xfd300000-0xfd3fffff]
[    0.896562] NET: Registered protocol family 2
[    0.896690] IP route cache hash table entries: 65536 (order: 7, 524288 bytes)
[    0.897339] TCP established hash table entries: 262144 (order: 10, 4194304 bytes)
[    0.899862] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.900543] TCP: Hash tables configured (established 262144 bind 65536)
[    0.900545] TCP reno registered
[    0.900701] NET: Registered protocol family 1
[    0.939994] pci 0000:03:00.0: Boot video device
[    0.940319] Scanning for low memory corruption every 60 seconds
[    0.940448] audit: initializing netlink socket (disabled)
[    0.940460] type=2000 audit(1279355835.939:1): initialized
[    0.949050] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.950421] VFS: Disk quotas dquot_6.5.2
[    0.950471] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.951003] fuse init (API version 7.13)
[    0.951078] msgmni has been set to 3507
[    0.951360] alg: No test for stdrng (krng)
[    0.951415] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.951418] io scheduler noop registered
[    0.951420] io scheduler anticipatory registered
[    0.951422] io scheduler deadline registered
[    0.951454] io scheduler cfq registered (default)
[    0.951756]   alloc irq_desc for 24 on node -1
[    0.951758]   alloc kstat_irqs on node -1
[    0.951778] pcieport 0000:00:0c.0: irq 24 for MSI/MSI-X
[    0.951799] pcieport 0000:00:0c.0: setting latency timer to 64
[    0.952158]   alloc irq_desc for 25 on node -1
[    0.952159]   alloc kstat_irqs on node -1
[    0.952176] pcieport 0000:00:15.0: irq 25 for MSI/MSI-X
[    0.952195] pcieport 0000:00:15.0: setting latency timer to 64
[    0.952543]   alloc irq_desc for 26 on node -1
[    0.952544]   alloc kstat_irqs on node -1
[    0.952560] pcieport 0000:00:16.0: irq 26 for MSI/MSI-X
[    0.952579] pcieport 0000:00:16.0: setting latency timer to 64
[    0.952925]   alloc irq_desc for 27 on node -1
[    0.952927]   alloc kstat_irqs on node -1
[    0.952943] pcieport 0000:00:17.0: irq 27 for MSI/MSI-X
[    0.952962] pcieport 0000:00:17.0: setting latency timer to 64
[    0.953307]   alloc irq_desc for 28 on node -1
[    0.953309]   alloc kstat_irqs on node -1
[    0.953325] pcieport 0000:00:18.0: irq 28 for MSI/MSI-X
[    0.953344] pcieport 0000:00:18.0: setting latency timer to 64
[    0.953502] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.953523] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.953647] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.953651] ACPI: Power Button [PWRB]
[    0.953718] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.953720] ACPI: Power Button [PWRF]
[    0.954872] ACPI: SSDT 000000006feeb200 0022A (v01  PmRef  Cpu0Ist 00003000 INTL 20040311)
[    0.955203] processor LNXCPU:00: registered as cooling_device0
[    0.955573] ACPI: SSDT 000000006feeb6c0 00152 (v01  PmRef  Cpu1Ist 00003000 INTL 20040311)
[    0.955880] processor LNXCPU:01: registered as cooling_device1
[    0.956243] ACPI: SSDT 000000006feeb820 00152 (v01  PmRef  Cpu2Ist 00003000 INTL 20040311)
[    0.956547] processor LNXCPU:02: registered as cooling_device2
[    0.956910] ACPI: SSDT 000000006feeb980 00152 (v01  PmRef  Cpu3Ist 00003000 INTL 20040311)
[    0.957214] processor LNXCPU:03: registered as cooling_device3
[    0.966357] Linux agpgart interface v0.103
[    0.966386] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.966459] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.966723] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.967621] brd: module loaded
[    0.968040] loop: module loaded
[    0.968109] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    0.968590] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 23
[    0.968594]   alloc irq_desc for 23 on node -1
[    0.968596]   alloc kstat_irqs on node -1
[    0.968602] pata_acpi 0000:00:0b.0: PCI INT A -> Link[APSI] -> GSI 23 (level, low) -> IRQ 23
[    0.968627] pata_acpi 0000:00:0b.0: setting latency timer to 64
[    0.968637] pata_acpi 0000:00:0b.0: PCI INT A disabled
[    0.968880] Fixed MDIO Bus: probed
[    0.968908] PPP generic driver version 2.4.2
[    0.968936] tun: Universal TUN/TAP device driver, 1.6
[    0.968938] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.969006] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.969365] ACPI: PCI Interrupt Link [AUB2] enabled at IRQ 22
[    0.969368]   alloc irq_desc for 22 on node -1
[    0.969370]   alloc kstat_irqs on node -1
[    0.969373] ehci_hcd 0000:00:04.1: PCI INT B -> Link[AUB2] -> GSI 22 (level, low) -> IRQ 22
[    0.969382] ehci_hcd 0000:00:04.1: setting latency timer to 64
[    0.969385] ehci_hcd 0000:00:04.1: EHCI Host Controller
[    0.969416] ehci_hcd 0000:00:04.1: new USB bus registered, assigned bus number 1
[    0.969434] ehci_hcd 0000:00:04.1: debug port 1
[    0.969442] ehci_hcd 0000:00:04.1: cache line size of 32 is not supported
[    0.969458] ehci_hcd 0000:00:04.1: irq 22, io mem 0xfe02e000
[    0.979804] ehci_hcd 0000:00:04.1: USB 2.0 started, EHCI 1.00
[    0.979892] usb usb1: configuration #1 chosen from 1 choice
[    0.979916] hub 1-0:1.0: USB hub found
[    0.979923] hub 1-0:1.0: 6 ports detected
[    0.980179] ACPI: PCI Interrupt Link [AU2B] disabled and referenced, BIOS bug
[    0.980320] ACPI: PCI Interrupt Link [AU2B] enabled at IRQ 21
[    0.980322]   alloc irq_desc for 21 on node -1
[    0.980324]   alloc kstat_irqs on node -1
[    0.980328] ehci_hcd 0000:00:06.1: PCI INT B -> Link[AU2B] -> GSI 21 (level, low) -> IRQ 21
[    0.980335] ehci_hcd 0000:00:06.1: setting latency timer to 64
[    0.980337] ehci_hcd 0000:00:06.1: EHCI Host Controller
[    0.980363] ehci_hcd 0000:00:06.1: new USB bus registered, assigned bus number 2
[    0.980380] ehci_hcd 0000:00:06.1: debug port 1
[    0.980387] ehci_hcd 0000:00:06.1: cache line size of 32 is not supported
[    0.980398] ehci_hcd 0000:00:06.1: irq 21, io mem 0xfe02c000
[    0.999802] ehci_hcd 0000:00:06.1: USB 2.0 started, EHCI 1.00
[    0.999863] usb usb2: configuration #1 chosen from 1 choice
[    0.999884] hub 2-0:1.0: USB hub found
[    0.999889] hub 2-0:1.0: 6 ports detected
[    0.999935] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.000293] ACPI: PCI Interrupt Link [AUBA] enabled at IRQ 20
[    1.000295]   alloc irq_desc for 20 on node -1
[    1.000297]   alloc kstat_irqs on node -1
[    1.000301] ohci_hcd 0000:00:04.0: PCI INT A -> Link[AUBA] -> GSI 20 (level, low) -> IRQ 20
[    1.000308] ohci_hcd 0000:00:04.0: setting latency timer to 64
[    1.000311] ohci_hcd 0000:00:04.0: OHCI Host Controller
[    1.000337] ohci_hcd 0000:00:04.0: new USB bus registered, assigned bus number 3
[    1.000355] ohci_hcd 0000:00:04.0: irq 20, io mem 0xfe02f000
[    1.062068] usb usb3: configuration #1 chosen from 1 choice
[    1.062089] hub 3-0:1.0: USB hub found
[    1.062095] hub 3-0:1.0: 6 ports detected
[    1.062485] ACPI: PCI Interrupt Link [AU1B] enabled at IRQ 23
[    1.062488] ohci_hcd 0000:00:06.0: PCI INT A -> Link[AU1B] -> GSI 23 (level, low) -> IRQ 23
[    1.062496] ohci_hcd 0000:00:06.0: setting latency timer to 64
[    1.062498] ohci_hcd 0000:00:06.0: OHCI Host Controller
[    1.062530] ohci_hcd 0000:00:06.0: new USB bus registered, assigned bus number 4
[    1.062547] ohci_hcd 0000:00:06.0: irq 23, io mem 0xfe02d000
[    1.123309] usb usb4: configuration #1 chosen from 1 choice
[    1.123334] hub 4-0:1.0: USB hub found
[    1.123340] hub 4-0:1.0: 6 ports detected
[    1.123379] uhci_hcd: USB Universal Host Controller Interface driver
[    1.123441] PNP: No PS/2 controller found. Probing ports directly.
[    1.124918] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.124925] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.125057] mice: PS/2 mouse device common for all mice
[    1.125165] rtc_cmos 00:05: RTC can wake from S4
[    1.125201] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    1.125248] rtc0: alarms up to one year, y3k, 242 bytes nvram, hpet irqs
[    1.125384] device-mapper: uevent: version 1.0.3
[    1.125486] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    1.125627] device-mapper: multipath: version 1.1.0 loaded
[    1.125630] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.125906] cpuidle: using governor ladder
[    1.125908] cpuidle: using governor menu
[    1.126205] TCP cubic registered
[    1.126311] NET: Registered protocol family 10
[    1.126696] lo: Disabled Privacy Extensions
[    1.126932] NET: Registered protocol family 17
[    1.127858] PM: Resume from disk failed.
[    1.127870] registered taskstats version 1
[    1.128435]   Magic number: 2:710:624
[    1.128493] pci_link PNP0C0F:55: hash matches
[    1.128586] rtc_cmos 00:05: setting system clock to 2010-07-17 08:37:17 UTC (1279355837)
[    1.128589] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.128591] EDD information not available.
[    1.128649] Freeing unused kernel memory: 880k freed
[    1.128890] Write protecting the kernel read-only data: 7692k
[    1.143076] udev: starting version 151
[    1.201900] ahci 0000:00:0b.0: version 3.0
[    1.201935] ahci 0000:00:0b.0: PCI INT A -> Link[APSI] -> GSI 23 (level, low) -> IRQ 23
[    1.202001]   alloc irq_desc for 29 on node -1
[    1.202003]   alloc kstat_irqs on node -1
[    1.202014] ahci 0000:00:0b.0: irq 29 for MSI/MSI-X
[    1.202090] ahci 0000:00:0b.0: AHCI 0001.0200 32 slots 6 ports 3 Gbps 0x3f impl IDE mode
[    1.202094] ahci 0000:00:0b.0: flags: 64bit ncq sntf led pmp pio boh 
[    1.202098] ahci 0000:00:0b.0: setting latency timer to 64
[    1.205427] scsi0 : ahci
[    1.209919] scsi1 : ahci
[    1.210145] scsi2 : ahci
[    1.210239] scsi3 : ahci
[    1.211298] scsi4 : ahci
[    1.211400] scsi5 : ahci
[    1.211606] ata1: SATA max UDMA/133 abar m8192@0xfe026000 port 0xfe026100 irq 29
[    1.211609] ata2: SATA max UDMA/133 abar m8192@0xfe026000 port 0xfe026180 irq 29
[    1.211612] ata3: SATA max UDMA/133 abar m8192@0xfe026000 port 0xfe026200 irq 29
[    1.211614] ata4: SATA max UDMA/133 abar m8192@0xfe026000 port 0xfe026280 irq 29
[    1.211616] ata5: SATA max UDMA/133 abar m8192@0xfe026000 port 0xfe026300 irq 29
[    1.211619] ata6: SATA max UDMA/133 abar m8192@0xfe026000 port 0xfe026380 irq 29
[    1.211703] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
[    1.212268] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 22
[    1.212273] forcedeth 0000:00:0a.0: PCI INT A -> Link[APCH] -> GSI 22 (level, low) -> IRQ 22
[    1.212278] forcedeth 0000:00:0a.0: setting latency timer to 64
[    1.292548] forcedeth 0000:00:0a.0: ifname eth0, PHY OUI 0x732 @ 3, addr 00:01:2e:24:3e:68
[    1.292552] forcedeth 0000:00:0a.0: highdma csum pwrctl gbit lnktim msi desc-v3
[    1.560016] ata4: SATA link down (SStatus 0 SControl 300)
[    1.560022] ata6: SATA link down (SStatus 0 SControl 300)
[    1.560045] ata2: SATA link down (SStatus 0 SControl 300)
[    1.560068] ata3: SATA link down (SStatus 0 SControl 300)
[    1.560072] ata5: SATA link down (SStatus 0 SControl 300)
[    1.580011] usb 3-5: new low speed USB device using ohci_hcd and address 2
[    1.740008] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.777564] ata1.00: ATA-8: WDC WD3200BJKT-75F4T0, 11.01A11, max UDMA/133
[    1.777567] ata1.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    1.780144] ata1.00: configured for UDMA/133
[    1.780250] scsi 0:0:0:0: Direct-Access     ATA      WDC WD3200BJKT-7 11.0 PQ: 0 ANSI: 5
[    1.780440] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.780482] sd 0:0:0:0: [sda] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[    1.780577] sd 0:0:0:0: [sda] Write Protect is off
[    1.780580] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.780607] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.780753]  sda: sda1 sda2 < sda5 sda6 >
[    1.804286] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.822139] usb 3-5: configuration #1 chosen from 1 choice
[    1.833231] usbcore: registered new interface driver hiddev
[    1.840293] input: Logitech Logitech USB Keyboard as /devices/pci0000:00/0000:00:04.0/usb3/3-5/3-5:1.0/input/input3
[    1.840384] generic-usb 0003:046D:C309.0001: input,hidraw0: USB HID v1.10 Keyboard [Logitech Logitech USB Keyboard] on usb-0000:00:04.0-5/input0
[    1.857113] input: Logitech Logitech USB Keyboard as /devices/pci0000:00/0000:00:04.0/usb3/3-5/3-5:1.1/input/input4
[    1.857203] generic-usb 0003:046D:C309.0002: input,hidraw1: USB HID v1.10 Mouse [Logitech Logitech USB Keyboard] on usb-0000:00:04.0-5/input1
[    1.857228] usbcore: registered new interface driver usbhid
[    1.857231] usbhid: v2.6:USB HID core driver
[    1.952517] usb 2-1: new high speed USB device using ehci_hcd and address 2
[    2.100910] usb 2-1: configuration #1 chosen from 1 choice
[    2.101192] hub 2-1:1.0: USB hub found
[    2.101313] hub 2-1:1.0: 2 ports detected
[    2.113829] EXT4-fs (sda6): mounted filesystem with ordered data mode
[    2.230068] usb 2-3: new high speed USB device using ehci_hcd and address 3
[    2.401548] usb 2-3: configuration #1 chosen from 1 choice
[    2.580010] usb 2-6: new high speed USB device using ehci_hcd and address 5
[    2.731499] usb 2-6: configuration #1 chosen from 1 choice
[    3.080008] usb 4-5: new low speed USB device using ohci_hcd and address 2
[    3.307869] usb 4-5: configuration #1 chosen from 1 choice
[    3.318055] input: Microsoft Microsoft 3-Button Mouse with IntelliEye(TM) as /devices/pci0000:00/0000:00:06.0/usb4/4-5/4-5:1.0/input/input5
[    3.318124] generic-usb 0003:045E:0040.0003: input,hidraw2: USB HID v1.10 Mouse [Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)] on usb-0000:00:06.0-5/input0
[    3.410587] usb 2-1.2: new high speed USB device using ehci_hcd and address 6
[    3.669036] usb 2-1.2: configuration #1 chosen from 1 choice
[    6.717894] udev: starting version 151
[    6.725940] Adding 7812088k swap on /dev/sda5.  Priority:-1 extents:1 across:7812088k 
[    6.729586] lp: driver loaded but no devices found
[    6.794120] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[    6.806147] i2c i2c-0: nForce2 SMBus adapter at 0x1c00
[    6.806152] ACPI: resource nForce2_smbus [0x1c80-0x1cbf] conflicts with ACPI region SM01 [0x001c80-0x001cbf]
[    6.806154] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    6.806156] nForce2_smbus 0000:00:03.2: Error probing SMB2.
[    6.822328] [Firmware Bug]: ACPI(IGPU) defines _DOD but not _DOS
[    6.835572] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:08/LNXVIDEO:00/input/input6
[    6.835712] ACPI: Video Device [IGPU] (multi-head: yes  rom: no  post: no)
[    6.894025] [drm] Initialized drm 1.1.0 20060810
[    6.905035] vt6656_stage: module is from the staging directory, the quality is unknown, you have been warned.
[    6.907524] VIA Networking Wireless LAN USB Driver 1.19_12
[    6.907580] VIA Networking Wireless LAN USB Driver Ver. 1.19_12
[    6.907582] Copyright (c) 2004 VIA Networking Technologies, Inc.
[    6.911185] Initializing USB Mass Storage driver...
[    6.914043] scsi6 : SCSI emulation for USB Mass Storage devices
[    6.914273] usbcore: registered new interface driver usb-storage
[    6.914276] USB Mass Storage support registered.
[    6.918399] usb-storage: device found at 5
[    6.918401] usb-storage: waiting for device to settle before scanning
[    6.921624] Linux video capture interface: v2.00
[    6.925007] uvcvideo: Found UVC 1.00 device <unnamed> (046d:0990)
[    6.933128] type=1505 audit(1279370243.302:2):  operation="profile_load" pid=722 name="/sbin/dhclient3"
[    6.933719] type=1505 audit(1279370243.302:3):  operation="profile_load" pid=722 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[    6.934025] type=1505 audit(1279370243.302:4):  operation="profile_load" pid=722 name="/usr/lib/connman/scripts/dhclient-script"
[    6.942830] ACPI: PCI Interrupt Link [AIGP] enabled at IRQ 21
[    6.942844] nouveau 0000:03:00.0: PCI INT A -> Link[AIGP] -> GSI 21 (level, low) -> IRQ 21
[    6.942855] nouveau 0000:03:00.0: setting latency timer to 64
[    6.950342] [drm] nouveau 0000:03:00.0: Detected an NV50 generation card (0x0ac600b1)
[    6.950714] [drm] nouveau 0000:03:00.0: Attempting to load BIOS image from PRAMIN
[    6.956521] input: UVC Camera (046d:0990) as /devices/pci0000:00/0000:00:06.1/usb2/2-1/2-1.2/2-1.2:1.0/input/input7
[    6.956579] usbcore: registered new interface driver uvcvideo
[    6.956582] USB Video Class driver (v0.1.0)
[    7.001692] ACPI: PCI Interrupt Link [AAZA] enabled at IRQ 20
[    7.001699] HDA Intel 0000:00:08.0: PCI INT A -> Link[AAZA] -> GSI 20 (level, low) -> IRQ 20
[    7.001702] hda_intel: Disable MSI for Nvidia chipset
[    7.001729] HDA Intel 0000:00:08.0: setting latency timer to 64
[    7.017563] [drm] nouveau 0000:03:00.0: ... appears to be valid
[    7.017567] [drm] nouveau 0000:03:00.0: BIT BIOS found
[    7.017570] [drm] nouveau 0000:03:00.0: Bios version 62.79.3c.00
[    7.017573] [drm] nouveau 0000:03:00.0: TMDS table revision 2.0 not currently supported
[    7.017576] [drm] nouveau 0000:03:00.0: Found Display Configuration Block version 4.0
[    7.017579] [drm] nouveau 0000:03:00.0: DCB connector table: VHER 0x40 5 16 4
[    7.017581] [drm] nouveau 0000:03:00.0:   0: 0x00000000: type 0x00 idx 0 tag 0xff
[    7.017583] [drm] nouveau 0000:03:00.0:   1: 0x00005146: type 0x46 idx 1 tag 0x07
[    7.017586] [drm] nouveau 0000:03:00.0:   2: 0x00002261: type 0x61 idx 2 tag 0x08
[    7.017588] [drm] nouveau 0000:03:00.0:   3: 0x00001361: type 0x61 idx 3 tag 0x07
[    7.017590] [drm] nouveau 0000:03:00.0: Raw DCB entry 0: 01000300 0000001e
[    7.017593] [drm] nouveau 0000:03:00.0: Raw DCB entry 1: 01022322 00020010
[    7.017595] [drm] nouveau 0000:03:00.0: Raw DCB entry 2: 02011386 0f200010
[    7.017597] [drm] nouveau 0000:03:00.0: Raw DCB entry 3: 02013332 00020010
[    7.017599] [drm] nouveau 0000:03:00.0: Raw DCB entry 4: 0000000e 00000000
[    7.020759] usbcore: registered new interface driver snd-usb-audio
[    7.026949] [drm] nouveau 0000:03:00.0: Parsing VBIOS init table 0 at offset 0xDB11
[    7.033771] usb 2-3: reset high speed USB device using ehci_hcd and address 3
[    7.138430] type=1505 audit(1279370243.503:5):  operation="profile_load" pid=911 name="/usr/share/gdm/guest-session/Xsession"
[    7.139958] type=1505 audit(1279370243.503:6):  operation="profile_replace" pid=912 name="/sbin/dhclient3"
[    7.140532] type=1505 audit(1279370243.503:7):  operation="profile_replace" pid=912 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[    7.140851] type=1505 audit(1279370243.503:8):  operation="profile_replace" pid=912 name="/usr/lib/connman/scripts/dhclient-script"
[    7.143554] type=1505 audit(1279370243.513:9):  operation="profile_load" pid=913 name="/usr/bin/evince"
[    7.150936] type=1505 audit(1279370243.513:10):  operation="profile_load" pid=913 name="/usr/bin/evince-previewer"
[    7.151378] [drm] nouveau 0000:03:00.0: Parsing VBIOS init table 1 at offset 0xDDC5
[    7.151382] [drm] nouveau 0000:03:00.0: Parsing VBIOS init table 2 at offset 0xDDC7
[    7.151390] [drm] nouveau 0000:03:00.0: Parsing VBIOS init table 3 at offset 0xDEAC
[    7.151397] [drm] nouveau 0000:03:00.0: Parsing VBIOS init table 4 at offset 0xDF71
[    7.151399] [drm] nouveau 0000:03:00.0: Parsing VBIOS init table at offset 0xDFD6
[    7.155516] type=1505 audit(1279370243.523:11):  operation="profile_load" pid=913 name="/usr/bin/evince-thumbnailer"
[    7.181275] [drm] nouveau 0000:03:00.0: 0xDFD6: Condition still not met after 20ms, skipping following opcodes
[    7.181289] [drm] nouveau 0000:03:00.0: 0xC646: parsing output script 0
[    7.181295] [drm] nouveau 0000:03:00.0: 0xC824: parsing output script 0
[    7.181297] [drm] nouveau 0000:03:00.0: 0xC646: parsing output script 0
[    7.194834] usbcore: registered new interface driver vt6656
[    7.272994] [TTM] Zone  kernel: Available graphics memory: 898292 kiB.
[    7.273003] [drm] nouveau 0000:03:00.0: 256 MiB VRAM
[    7.287378] [drm] nouveau 0000:03:00.0: 512 MiB GART (aperture)
[    7.288708] [drm] nouveau 0000:03:00.0: Allocating FIFO number 1
[    7.291467] [drm] nouveau 0000:03:00.0: nouveau_channel_alloc: initialised FIFO 1
[    7.291839] [drm] nouveau 0000:03:00.0: Detected a DAC output
[    7.291841] [drm] nouveau 0000:03:00.0: Detected a TMDS output
[    7.291843] [drm] nouveau 0000:03:00.0: Detected a DP output
[    7.291845] [drm] nouveau 0000:03:00.0: Detected a TMDS output
[    7.291848] [drm] nouveau 0000:03:00.0: Detected a VGA connector
[    7.292031] [drm] nouveau 0000:03:00.0: Detected a DVI-D connector
[    7.292106] [drm] nouveau 0000:03:00.0: Detected a DisplayPort connector
[    7.292181] [drm] nouveau 0000:03:00.0: Detected a DVI-D connector
[    7.433817] [drm] nouveau 0000:03:00.0: allocated 1920x1200 fb: 0x40250000, bo ffff880066917600
[    7.433901] fb0: nouveaufb frame buffer device
[    7.433903] registered panic notifier
[    7.433909] [drm] Initialized nouveau 0.0.15 20090420 for 0000:03:00.0 on minor 0
[    7.435723] vga16fb: initializing
[    7.435726] vga16fb: mapped to 0xffff8800000a0000
[    7.435729] vga16fb: not registering due to another framebuffer present
[    7.446310] [drm] nouveau 0000:03:00.0: 0x11D5: parsing clock script 0
[    7.448473] Console: switching to colour frame buffer device 240x75
[    7.465150] ppdev: user-space parallel port driver
[    8.840012] hda_codec: ALC662 rev1: BIOS auto-probing.
[    9.640082] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:08.0/input/input8
[   11.910144] usb-storage: device scan complete
[   11.911868] scsi 6:0:0:0: CD-ROM            ASUS     SBC-06D1S-U      A201 PQ: 0 ANSI: 0
[   11.920721] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[   11.920724] Uniform CD-ROM driver Revision: 3.20
[   11.920869] sr 6:0:0:0: Attached scsi CD-ROM sr0
[   11.921182] sr 6:0:0:0: Attached scsi generic sg1 type 5
[   17.960009] eth0: no IPv6 routers present
[   49.330443] [drm] nouveau 0000:03:00.0: Allocating FIFO number 2
[   49.333116] [drm] nouveau 0000:03:00.0: nouveau_channel_alloc: initialised FIFO 2

```

Nothing that seems relevant to me, although the entry showing a firmware bug with ACPI is interesting:```
[    6.822328] [Firmware Bug]: ACPI(IGPU) defines _DOD but not _DOS

```

Another possible clue is that when I boot I do NOT choose recovery mode from GRUB.  After selection I get my command prompt.  Then, when I startx I get my Gnome setup (which I'm in right now).  The power button at top right does not work.  What is interesting is that when I do "sudo shutdown now", I actually get taken to the recovery menu, even though I did not launch recovery mode.  Why would this be?

Is there any way to step through start scripts, or at least see what startup scripts are running in what order in case I'm going down a weird startup branch?

---

### Post by pastalavista on 2010-07-17
Download and extract the attached boot-info script to your home folder. Make it executable, run it (read it first to make sure I'm not a black-hat) and post the output here.```
 sudo chmod +x boot_info_script055.sh && sudo ./boot_info_script055.sh
```

---

### Post by pastalavista on 2010-07-17
also, check and see if you have installed the 'acpi-support' package and if not, install it. See if any options in /etc/default/acpi-support might address your problem and also see if 'plymouth' is installed.

---

### Post by qopit on 2010-07-17
> **pastalavista said:**
> Download and extract the attached boot-info script to your home folder. Make it executable, run it (read it first to make sure I'm not a black-hat) and post the output here.```
 sudo chmod +x boot_info_script055.sh && sudo ./boot_info_script055.sh
```

Wow - that is quite a script.  Here is the output:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   163,846,934   163,846,872   7 HPFS/NTFS
/dev/sda2         163,848,190   625,141,759   461,293,570   5 Extended
/dev/sda5         609,517,568   625,141,759    15,624,192  82 Linux swap / Solaris
/dev/sda6         163,848,192   609,517,567   445,669,376  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        4294449E94449677                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        f93caf98-78e0-4b3e-821e-6e0a9fa41e28   swap                                     
/dev/sda6        2f689b9c-f305-4a59-bacf-93097abc94e8   ext4                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext4       (rw,errors=remount-ro)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=2

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn


=========================== sda6/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd0,6)'
search --no-floppy --fs-uuid --set 2f689b9c-f305-4a59-bacf-93097abc94e8
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd0,6)'
search --no-floppy --fs-uuid --set 2f689b9c-f305-4a59-bacf-93097abc94e8
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 2f689b9c-f305-4a59-bacf-93097abc94e8
	linux	/boot/vmlinuz-2.6.32-23-generic root=UUID=2f689b9c-f305-4a59-bacf-93097abc94e8 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 2f689b9c-f305-4a59-bacf-93097abc94e8
	echo	'Loading Linux 2.6.32-23-generic ...'
	linux	/boot/vmlinuz-2.6.32-23-generic root=UUID=2f689b9c-f305-4a59-bacf-93097abc94e8 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 2f689b9c-f305-4a59-bacf-93097abc94e8
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=2f689b9c-f305-4a59-bacf-93097abc94e8 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 2f689b9c-f305-4a59-bacf-93097abc94e8
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=2f689b9c-f305-4a59-bacf-93097abc94e8 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 2f689b9c-f305-4a59-bacf-93097abc94e8
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 2f689b9c-f305-4a59-bacf-93097abc94e8
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 4294449e94449677
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=2f689b9c-f305-4a59-bacf-93097abc94e8 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=f93caf98-78e0-4b3e-821e-6e0a9fa41e28 none            swap    sw              0       0
/dev/scd0       /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda6: Location of files loaded by Grub: ===================


 142.0GB: boot/grub/core.img
 146.5GB: boot/grub/grub.cfg
 142.0GB: boot/initrd.img-2.6.32-21-generic
 142.1GB: boot/initrd.img-2.6.32-23-generic
 118.5GB: boot/vmlinuz-2.6.32-21-generic
 142.0GB: boot/vmlinuz-2.6.32-23-generic
 142.1GB: initrd.img
 142.0GB: initrd.img.old
 142.0GB: vmlinuz
 118.5GB: vmlinuz.old

```

ooc - why bother chmod'ing +x?

---

### Post by qopit on 2010-07-17
> **pastalavista said:**
> also, check and see if you have installed the 'acpi-support' package and if not, install it. See if any options in /etc/default/acpi-support might address your problem and also see if 'plymouth' is installed.

Both seem installed...
```
qopit@my-desktop:~$ sudo aptitude search acpi
p   acpi                                        
i   acpi-support                                
i   acpid                                       
p   acpidump                                    
p   acpitail                                    
p   acpitool                                    
p   acpitool-dbg                                
p   claws-mail-acpi-notifier                    
p   eeepc-acpi-scripts                          
p   libacpi-dev                                 
p   libacpi0                                    
v   sylpheed-claws-gtk2-acpi-notifier           
p   wmacpi                                      
p   yacpi                                       

qopit@my-desktop:~$ sudo aptitude search plymouth
p   libplymouth-dev                                
i   libplymouth2                                   
p   lubuntu-plymouth-theme                         
i   plymouth                                       
i   plymouth-label                                 
v   plymouth-theme                                 
p   plymouth-theme-fade-in                         
p   plymouth-theme-glow                            
i   plymouth-theme-kubuntu-logo                    
p   plymouth-theme-sabily                          
p   plymouth-theme-script                          
p   plymouth-theme-solar                           
p   plymouth-theme-spinfinity                      
p   plymouth-theme-text                            
i   plymouth-theme-ubuntu-logo                     
i   plymouth-theme-ubuntu-text                     
p   plymouth-theme-ubuntustudio                    
i   plymouth-x11                                   
p   xubuntu-plymouth-theme                         

```

---

### Post by qopit on 2010-07-18
Digging into the Ubuntu boot sequence led me to this wiki page:
[https://help.ubuntu.com/community/UbuntuBootupHowto](https://help.ubuntu.com/community/UbuntuBootupHowto)

where some comments led me to a handy runlevel configuration tool called "sysv-rc-conf".

The configuration I see when running that script is below.  Neither gdm nor kdm are selected in each so I'm about to try enabling gdm on runlevels 2-5 and see what happens.

Can someone with a functioning and vanilla Lucid install please post their sysv-rc-conf output for comparison?

My sysv-rc-conf config right now:
```
&#9484; SysV Runlevel Config   -: stop service  =/+: start service  h: help  q: quit &#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
&#9474;                                                                                                                                                                                                                                           &#9474;
&#9474; service      1       2       3       4       5       0       6       S                                                                                                                                                                    &#9474;
&#9474; ----------------------------------------------------------------------------                                                                                                                                                              &#9474;
&#9474; acpi-supp$  [ ]     [X]     [X]     [X]     [X]     [ ]     [ ]     [ ]                                                                                                                                                                   &#9474;
&#9474; acpid       [ ]     [ ]     [ ]     [ ]     [ ]     [ ]     [ ]     [ ]                                                                                                                                                                   &#9474;
&#9474; alsa-mixe$  [ ]     [ ]     [ ]     [ ]     [ ]     [ ]     [ ]     [ ]                                                                                                                                                                   &#9474;
&#9474; anacron     [ ]     [ ]     [ ]     [ ]     [ ]     [ ]     [ ]     [ ]                                                                                                                                                                   &#9474;
&#9474; apparmor    [ ]     [ ]     [ ]     [ ]     [ ]     [ ]     [ ]     [X]                                                                                                                                                                   &#9474;
&#9474; apport      [ ]     [ ]     [ ]     [ ]     [ ]     [ ]     [ ]     [ ]                                                                                                                                                                   &#9474;
&#9474; atd         [ ]     [ ]     [ ]     [ ]     [ ]     [ ]     [ ]     [ ]                                                                                                                                                                   &#9474;
&#9474; avahi-dae$  [ ]     [ ]     [ ]     [ ]     [ ]     [ ]     [ ]     [ ]                                                                                                                                                                   &#9474;
&#9474; binfmt-su$  [ ]     [X]     [X]     [X]     [X]     [ ]     [ ]     [ ]                                                                                                                                                                   &#9474;
&#9474; bluetooth   [ ]     [X]     [X]     [X]     [X]     [ ]     [ ]     [ ]                                                                                                                                                                   &#9474;
&#9474; bootlogd    [ ]     [ ]     [ ]     [ ]     [ ]     [ ]     [ ]     [ ]                                                                                                                                                                   &#9474;
&#9474; brltty      [ ]     [ ]     [ ]     [ ]     [ ]     [ ]     [ ]     [X]                                                                                                                                                                   &#9474;
&#9474; console-s$  [ ]     [ ]     [ ]     [ ]     [ ]     [ ]     [ ]     [ ]                                                                                                                                                                   &#9474;
&#9474; cron        [ ]     [ ]     [ ]     [ ]     [ ]     [ ]     [ ]     [ ]                                                                                                                                                                   &#9474;
&#9474; cups        [ ]     [X]     [X]     [X]     [X]     [ ]     [ ]     [ ]                                                                                                                                                                   &#9474;
&#9474; dbus        [ ]     [ ]     [ ]     [ ]     [ ]     [ ]     [ ]     [ ]                                                                                                                                                                   &#9474;
&#9474; dmesg       [ ]     [ ]     [ ]     [ ]     [ ]     [ ]     [ ]     [ ]                                                                                                                                                                   &#9474;
&#9474; dns-clean   [X]     [X]     [X]     [X]     [X]     [ ]     [ ]     [ ]                                                                                                                                                                   &#9474;
&#9474; failsafe-x  [ ]     [ ]     [ ]     [ ]     [ ]     [ ]     [ ]     [ ]                                                                                                                                                                   &#9474;
&#9474; fancontrol  [ ]     [X]     [X]     [X]     [X]     [ ]     [ ]     [ ]                                                                                                                                                                   &#9474;
&#9474; gdm         [ ]     [ ]     [ ]     [ ]     [ ]     [ ]     [ ]     [ ]                                                                                                                                                                   &#9474;
&#9474; grub-comm$  [ ]     [X]     [X]     [X]     [X]     [ ]     [ ]     [ ]                                                                                                                                                                   &#9474;
&#9474; halt        [ ]     [ ]     [ ]     [ ]     [ ]     [X]     [ ]     [ ]                                                                                                                                                                   &#9474;
&#9474; hostname    [ ]     [ ]     [ ]     [ ]     [ ]     [ ]     [ ]     [ ]                                                                                                                                                                   &#9474;
&#9474; hwclock     [ ]     [ ]     [ ]     [ ]     [ ]     [ ]     [ ]     [ ]                                                                                                                                                                   &#9474;
&#9474; hwclock-s$  [ ]     [ ]     [ ]     [ ]     [ ]     [ ]     [ ]     [ ]                                                                                                                                                                   &#9474;
&#9474; irqbalance  [ ]     [ ]     [ ]     [ ]     [ ]     [ ]     [ ]     [ ]                                                                                                                                                                   &#9474;
&#9474; kdm         [ ]     [ ]     [ ]     [ ]     [ ]     [ ]     [ ]     [ ]                                                                                                                                                                   &#9474;
&#9474; kerneloops  [ ]     [X]     [X]     [X]     [X]     [ ]     [ ]     [ ]                                                                                                                                                                   &#9474;
&#9474; killprocs   [X]     [ ]     [ ]     [ ]     [ ]     [ ]     [ ]     [ ]                                                                                                                                                                   &#9474;
&#9474; lm-sensors  [ ]     [ ]     [ ]     [ ]     [ ]     [ ]     [ ]     [X]                                                                                                                                                                   &#9474;
&#9474; module-in$  [ ]     [ ]     [ ]     [ ]     [ ]     [ ]     [ ]     [ ]                                                                                                                                                                   &#9474;
&#9474; network-i$  [ ]     [ ]     [ ]     [ ]     [ ]     [ ]     [ ]     [ ]                                                                                                                                                                   &#9474;
&#9474; network-i$  [ ]     [ ]     [ ]     [ ]     [ ]     [ ]     [ ]     [ ]                                                                                                                                                                   &#9474;
&#9474; network-m$  [ ]     [ ]     [ ]     [ ]     [ ]     [ ]     [ ]     [ ]                                                                                                                                                                   &#9474;
&#9474; networking  [ ]     [ ]     [ ]     [ ]     [ ]     [X]     [X]     [ ]                                                                                                                                                                   &#9474;
&#9474; ondemand    [ ]     [X]     [X]     [X]     [X]     [ ]     [ ]     [ ]                                                                                                                                                                   &#9474;
&#9474; pcmciauti$  [ ]     [ ]     [ ]     [ ]     [ ]     [ ]     [ ]     [X]                                                                                                                                                                   &#9474;
&#9474; plymouth    [ ]     [ ]     [ ]     [ ]     [ ]     [ ]     [ ]     [ ]                                                                                                                                                                   &#9474;
&#9474; plymouth-$  [ ]     [ ]     [ ]     [ ]     [ ]     [ ]     [ ]     [ ]                                                                                                                                                                   &#9474;
&#9474; plymouth-$  [ ]     [ ]     [ ]     [ ]     [ ]     [ ]     [ ]     [ ]                                                                                                                                                                   &#9474;
&#9474; plymouth-$  [ ]     [ ]     [ ]     [ ]     [ ]     [ ]     [ ]     [ ]                                                                                                                                                                   &#9474;
&#9474; pppd-dns    [X]     [X]     [X]     [X]     [X]     [ ]     [ ]     [ ]                                                                                                                                                                   &#9474;
&#9474; procps      [ ]     [ ]     [ ]     [ ]     [ ]     [ ]     [ ]     [ ]                                                                                                                                                                   &#9474;
&#9474; pulseaudio  [ ]     [X]     [X]     [X]     [X]     [ ]     [ ]     [ ]                                                                                                                                                                   &#9474;
&#9474; rc.local    [ ]     [X]     [X]     [X]     [X]     [ ]     [ ]     [ ]                                                                                                                                                                   &#9474;
&#9474; reboot      [ ]     [ ]     [ ]     [ ]     [ ]     [ ]     [X]     [ ]                                                                                                                                                                   &#9474;
&#9474; rsync       [ ]     [X]     [X]     [X]     [X]     [ ]     [ ]     [ ]                                                                                                                                                                   &#9474;
&#9474; rsyslog     [ ]     [ ]     [ ]     [ ]     [ ]     [ ]     [ ]     [ ]                                                                                                                                                                   &#9474;
&#9474; saned       [ ]     [X]     [X]     [X]     [X]     [ ]     [ ]     [ ]                                                                                                                                                                   &#9474;
&#9474; screen-cl$  [ ]     [ ]     [ ]     [ ]     [ ]     [ ]     [ ]     [X]                                                                                                                                                                   &#9474;
&#9474; sendsigs    [ ]     [ ]     [ ]     [ ]     [ ]     [X]     [X]     [ ]                                                                                                                                                                   &#9474;
&#9474; single      [X]     [ ]     [ ]     [ ]     [ ]     [ ]     [ ]     [ ]                                                                                                                                                                   &#9474;
&#9474;                                                                                                                                                                                                                                           &#9474;
&#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;
&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
&#9474; Use the arrow keys or mouse to move around.      ^n: next pg     ^p: prev pg                                                                                                                                                              &#9474;
&#9474;                        space: toggle service on / off                                                                                                                                                                                     &#9474;
&#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;
```

---

### Post by qopit on 2010-07-18
Hmm... selecting gdm alone seemingly did nothing.  Still straight to tty.

Anyone else have other ideas?  I'm regretting not having posted this in the "General Help" forum... seems like more traffic over there.

---

### Post by qopit on 2010-07-18
Problem solved in another way... unplugging my wifi and starting from scratch did the trick as per this thread:
[http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=9238065](http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=9238065)

I'm still curious what the right path to repairing my install was, though.

---

