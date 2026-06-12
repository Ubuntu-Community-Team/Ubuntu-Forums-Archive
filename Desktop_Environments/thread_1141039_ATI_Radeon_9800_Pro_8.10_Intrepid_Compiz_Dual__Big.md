---
title: "ATI Radeon 9800 Pro: 8.10 Intrepid: Compiz: Dual / Big Desktop"
date: 2009-04-28
forum: Desktop Environments
---

### Post by configt on 2009-04-28
Sorry if this has already been addressed elsewhere, I have spent uber hours hacking and doing google searches for the solution, to no avail.

Problem Statement / Objective:

I am attempting to use ubu 8.10 with compiz on a ATI Radeon 9800 pro, with two monitors (2 ViewSonic 1280x1024 LCD monitors).  I can use big desktop as long as compiz is not enabled, otherwise the monitors only go into mirror mode when using fglrx driver.  Also, in mirror mode I am getting a terrible(?) ~3000 fps with compiz enabled.  Lots of tearing/screen flicker.  I disabled most features from the catalyst driver console to get this fps, before it was only ~300fps (thanks to other community posters for advice on configuring the catalyst console).

jbutler@latenight:~$ glxgears
15419 frames in 5.0 seconds = 3083.730 FPS
15561 frames in 5.0 seconds = 3112.029 FPS
15558 frames in 5.0 seconds = 3111.494 FPS

My objective is to eliminate or massively reduce the screen flicker (screen saver is horrible for example), and enable big screen (dual monitor desktop) while compiz is enabled.  Compiz is super mega awesome and IMO, increases productivity where most people seem to think it decreases productivity.

I am very appreciative of anyone that can provide the solution to having a big desktop (dual monitor desktop) with the ATI Radeon 9800 Pro and running compiz.

System Info:

uname:

```

jbutler@latenight:~$ uname -a
Linux latenight.port2002.com 2.6.27-11-generic #1 SMP Wed Apr 1 20:57:48 UTC 2009 i686 GNU/Linux

```lshw:

```

jbutler@latenight:~$ cat system-hardware-info.txt 
latenight.port2002.com
    description: Computer
    product: Springdale-G
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3 smp-1.4 smp
    configuration: boot=normal cpus=1 uuid=948D8AD9-4013-11D9-84F6-00E018874439
  *-core
       description: Motherboard
       product: D865PERL
       vendor: Intel Corporation
       physical id: 0
       version: AAC27646-213
       serial: BTRL44826916
       slot: Audio Mic In
     *-firmware
          description: BIOS
          vendor: Intel Corp.
          physical id: 0
          version: RL86510A.86A.0089.P21.0502132202 (02/13/2005)
          size: 64KiB
          capacity: 448KiB
          capabilities: pci pnp apm upgrade shadowing cdboot bootselect edd int13floppynec int13floppytoshiba int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) 4 CPU 3.40GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 15.3.4
          serial: 0000-0F34-0000-0000-0000-0000
          slot: J2E1
          size: 3400MHz
          capacity: 3400MHz
          width: 32 bits
          clock: 200MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe constant_tsc pebs bts pni monitor ds_cpl cid xtpr
          configuration: id=1
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: None
             size: 16KiB
             capacity: 16KiB
             capabilities: pipeline-burst internal varies data
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: None
             size: 1MiB
             capacity: 1MiB
             capabilities: pipeline-burst internal varies unified
        *-logicalcpu:0
             description: Logical CPU
             physical id: 1.1
             width: 32 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 1.2
             width: 32 bits
             capabilities: logical
     *-memory
          description: System Memory
          physical id: 39
          slot: System board or motherboard
          size: 1GiB
        *-bank:0
             description: DIMM DDR Synchronous 400 MHz (2.5 ns)
             product: PartNum1
             vendor: Manufacturer1
             physical id: 0
             serial: SerNum1
             slot: J5G1
             size: 512MiB
             width: 64 bits
             clock: 400MHz (2.5ns)
        *-bank:1
             description: DIMM DDR Synchronous 400 MHz (2.5 ns) [empty]
             product: PartNum2
             vendor: Manufacturer2
             physical id: 1
             serial: SerNum2
             slot: J5G2
             width: 64 bits
             clock: 400MHz (2.5ns)
        *-bank:2
             description: DIMM DDR Synchronous 400 MHz (2.5 ns)
             product: PartNum3
             vendor: Manufacturer3
             physical id: 2
             serial: SerNum3
             slot: J5H1
             size: 512MiB
             width: 64 bits
             clock: 400MHz (2.5ns)
        *-bank:3
             description: DIMM DDR Synchronous 400 MHz (2.5 ns) [empty]
             product: PartNum4
             vendor: Manufacturer4
             physical id: 3
             serial: SerNum4
             slot: J5H2
             width: 64 bits
             clock: 400MHz (2.5ns)
     *-pci
          description: Host bridge
          product: 82865G/PE/P DRAM Controller/Host-Hub Interface
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel module=intel_agp
        *-pci:0
             description: PCI bridge
             product: 82865G/PE/P PCI to AGP Controller
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: pci bus_master
           *-display:0
                description: VGA compatible controller
                product: Radeon R350 [Radeon 9800 Pro]
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: agp agp-3.0 pm bus_master cap_list
                configuration: driver=fglrx_pci latency=255 mingnt=8 module=fglrx
           *-display:1 UNCLAIMED
                description: Display controller
                product: Radeon R350 [Radeon 9800 Pro] (Secondary)
                vendor: ATI Technologies Inc
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: pm bus_master cap_list
                configuration: latency=32 mingnt=8
        *-usb:0
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:3
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:4
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-pci:1
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: c2
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master
           *-display:0 UNCLAIMED
                description: VGA compatible controller
                product: RV280 [Radeon 9200 PRO]
                vendor: ATI Technologies Inc
                physical id: 3
                bus info: pci@0000:02:03.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pm cap_list
                configuration: latency=0 mingnt=8
           *-display:1 UNCLAIMED
                description: Display controller
                product: RV280 [Radeon 9200 PRO] (Secondary)
                vendor: ATI Technologies Inc
                physical id: 3.1
                bus info: pci@0000:02:03.1
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: latency=32 mingnt=8
           *-network:0
                description: Ethernet interface
                product: RTL8139 Ethernet
                vendor: D-Link System Inc
                physical id: 4
                bus info: pci@0000:02:04.0
                logical name: eth1
                version: 10
                serial: 00:0d:88:3b:bd:4c
                size: 100MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full latency=32 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s
           *-firewire
                description: FireWire (IEEE 1394)
                product: FW323
                vendor: Agere Systems
                physical id: 7
                bus info: pci@0000:02:07.0
                version: 61
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=ohci1394 latency=32 maxlatency=24 mingnt=12 module=ohci1394
           *-network:1
                description: Ethernet interface
                product: 82562EZ 10/100 Ethernet Controller
                vendor: Intel Corporation
                physical id: 8
                bus info: pci@0000:02:08.0
                logical name: eth0
                version: 01
                serial: 00:11:11:b3:4c:c0
                size: 100MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI duplex=full firmware=N/A ip=192.168.0.45 latency=32 link=yes maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=100MB/s
        *-isa
             description: ISA bridge
             product: 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide:0
             description: IDE interface
             product: 82801EB/ER (ICH5/ICH5R) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             logical name: scsi0
             logical name: scsi1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0 module=ata_piix
           *-cdrom
                description: DVD reader
                product: 48MAX 244816AJ
                vendor: Memorex
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: KWH8
                capabilities: removable audio cd-r cd-rw dvd
                configuration: ansiversion=5 status=ready
              *-medium
                   physical id: 0
                   logical name: /dev/cdrom
           *-disk
                description: ATA Disk
                product: MAXTOR STM350063
                vendor: Maxtor
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/sda
                version: 3.AA
                serial: 9QG1F0DS
                size: 465GiB (500GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=19991b1c
              *-volume
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@1:0.0.0,1
                   logical name: /dev/sda1
                   version: 3.1
                   serial: c6b9db74-d314-2e48-91e2-cb815f4cc9f5
                   size: 465GiB
                   capacity: 465GiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2007-10-21 17:24:36 filesystem=ntfs label=BACKUPS state=clean
        *-ide:1
             description: IDE interface
             product: 82801EB (ICH5) SATA Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi2
             logical name: scsi3
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0 module=ata_piix
           *-disk:0
                description: ATA Disk
                product: ST3300622AS
                vendor: Seagate
                physical id: 0
                bus info: scsi@2:0.0.0
                logical name: /dev/sdb
                version: 3.AA
                serial: 5NF28DYY
                size: 279GiB (300GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=0b23abec
              *-volume
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@2:0.0.0,1
                   logical name: /dev/sdb1
                   logical name: /host
                   logical name: /boot
                   version: 3.1
                   serial: 1a654cd0-5796-d44b-96ab-9c72fcd92a40
                   size: 279GiB
                   capacity: 279GiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2006-07-12 23:23:29 filesystem=ntfs label=DISK3_VOL1 mount.fstype=fuseblk mount.options=rw,nosuid,nodev,user_id=0,group_id=0,allow_other,blksize=4096 state=mounted
           *-disk:1
                description: ATA Disk
                product: ST3300622AS
                vendor: Seagate
                physical id: 1
                bus info: scsi@3:0.0.0
                logical name: /dev/sdc
                version: 3.AA
                serial: 5NF25ZE1
                size: 279GiB (300GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=216b5230
              *-volume
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@3:0.0.0,1
                   logical name: /dev/sdc1
                   version: 3.1
                   serial: 16b2f94c-e849-ee46-ad2c-1e98807b1110
                   size: 279GiB
                   capacity: 279GiB
                   capabilities: primary ntfs initialized
                   configuration: clustersize=4096 created=2006-07-13 00:13:22 filesystem=ntfs label=DISK4_VOL1 state=clean
        *-serial UNCLAIMED
             description: SMBus
             product: 82801EB/ER (ICH5/ICH5R) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
        *-multimedia
             description: Multimedia audio controller
             product: 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=Intel ICH latency=0 module=snd_intel8x0
     *-scsi
          physical id: 1
          bus info: usb@4:2
          logical name: scsi4
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@4:0.0.0
             logical name: /dev/sdd
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 96:57:4d:93:79:67
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```lsmod:

```

jbutler@latenight:~$ cat system-module-info.txt 
Module                  Size  Used by
af_packet              25728  2 
binfmt_misc            16904  1 
rfcomm                 44560  0 
bridge                 56980  0 
stp                    10628  1 bridge
bnep                   20480  2 
sco                    18308  2 
l2cap                  30464  6 rfcomm,bnep
bluetooth              61924  6 rfcomm,bnep,sco,l2cap
ppdev                  15748  0 
ipv6                  263972  14 
speedstep_lib          12676  0 
cpufreq_conservative    14600  0 
cpufreq_stats          13188  0 
cpufreq_userspace      11396  0 
cpufreq_ondemand       14988  0 
freq_table             12672  2 cpufreq_stats,cpufreq_ondemand
cpufreq_powersave       9856  0 
video                  25232  0 
output                 11008  1 video
pci_slot               12680  0 
wmi                    14504  0 
sbs                    19464  0 
sbshc                  13440  1 sbs
container              11520  0 
battery                18436  0 
iptable_filter         10752  0 
ip_tables              19600  1 iptable_filter
x_tables               22916  1 ip_tables
ac                     12292  0 
sbp2                   29324  0 
lp                     17156  0 
snd_intel8x0           37532  3 
snd_ac97_codec        111652  1 snd_intel8x0
ac97_bus                9856  1 snd_ac97_codec
snd_pcm_oss            46848  0 
snd_mixer_oss          22784  1 snd_pcm_oss
snd_pcm                83204  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy          10884  0 
evdev                  17696  6 
pcspkr                 10624  0 
snd_seq_oss            38528  0 
snd_seq_midi           14336  0 
psmouse                45200  0 
serio_raw              13444  0 
snd_rawmidi            29824  1 snd_seq_midi
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
parport_pc             39332  1 
parport                42604  3 ppdev,lp,parport_pc
fglrx                1813960  30 
snd_timer              29960  2 snd_pcm,snd_seq
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    63268  16 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15328  1 snd
snd_page_alloc         16136  2 snd_intel8x0,snd_pcm
iTCO_wdt               18596  0 
iTCO_vendor_support    11652  1 iTCO_wdt
button                 14224  0 
intel_agp              33724  1 
agpgart                42184  2 fglrx,intel_agp
shpchp                 38036  0 
pci_hotplug            34976  1 shpchp
ext3                  133256  1 
jbd                    55828  1 ext3
mbcache                16004  1 ext3
loop                   23180  2 
sd_mod                 42392  2 
sr_mod                 22212  1 
crc_t10dif              9984  1 sd_mod
cdrom                  43168  1 sr_mod
sg                     39732  0 
usb_storage            82624  0 
libusual               30356  1 usb_storage
ata_piix               24708  2 
pata_acpi              12160  0 
ata_generic            12932  0 
libata                178208  3 ata_piix,pata_acpi,ata_generic
ohci1394               37936  0 
scsi_mod              155212  6 sbp2,sd_mod,sr_mod,sg,usb_storage,libata
dock                   16656  1 libata
ieee1394               96324  2 sbp2,ohci1394
e100                   41356  0 
8139too                31616  0 
mii                    13440  2 e100,8139too
ehci_hcd               43788  0 
uhci_hcd               30864  0 
usbcore               149488  5 usb_storage,libusual,ehci_hcd,uhci_hcd
thermal                23708  0 
processor              42156  1 thermal
fan                    12548  0 
fbcon                  47648  0 
tileblit               10880  1 fbcon
font                   16512  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
fuse                   60828  5 

```lspci:

```

jbutler@latenight:~$ cat system-pci-info.txt 
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:01.0 PCI bridge: Intel Corporation 82865G/PE/P PCI to AGP Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon R350 [Radeon 9800 Pro]
01:00.1 Display controller: ATI Technologies Inc Radeon R350 [Radeon 9800 Pro] (Secondary)
02:03.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200 PRO] (rev 01)
02:03.1 Display controller: ATI Technologies Inc RV280 [Radeon 9200 PRO] (Secondary) (rev 01)
02:04.0 Ethernet controller: D-Link System Inc RTL8139 Ethernet (rev 10)
02:07.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 61)
02:08.0 Ethernet controller: Intel Corporation 82562EZ 10/100 Ethernet Controller (rev 01)

```fglrxinfo:

```

jbutler@latenight:~$ cat video-info.txt 
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9800 PRO
OpenGL version string: 2.1.8087 Release

```xorg.conf:

```

jbutler@latenight:~$ cat /etc/X11/xorg.conf
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
    Option        "Dualhead" "true"
EndSection

Section "Files"
EndSection

Section "Module"
    Load  "glx"
EndSection

Section "InputDevice"
    Identifier  "Generic Keyboard"
    Driver      "kbd"
    Option        "XkbRules" "xorg"
    Option        "XkbModel" "pc105"
    Option        "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier  "Configured Mouse"
    Driver      "mouse"
EndSection

Section "Monitor"
    Identifier   "Monitor0"
EndSection

Section "Monitor"
    Identifier   "Monitor1"
EndSection

Section "Device"
    Identifier  "Device0"
    Driver      "fglrx"
    Option      "TexturedVideo" "on"
    Option        "DesktopSetup" "horizontal"
    Option        "OverlayOnCRTC2" "1"
EndSection

Section "Device"
    Identifier  "Device1"
    Driver      "fglrx"
EndSection

Section "Screen"
    Identifier "Screen0"
    Device     "Device0"
    Monitor    "Monitor0"
    DefaultDepth     24
        SubSection "Display"
                Virtual 2560 1024
        EndSubSection
EndSection

Section "Screen"
    Identifier "Screen1"
    Device     "Device1"
    Monitor    "Monitor1"
    DefaultDepth     24
        SubSection "Display"
                Virtual 2560 1024
        EndSubSection
EndSection

```

---

### Post by configt on 2009-04-29
To all the folks out there trying to get the ATI Radeon 9800 Pro 128MB card to run dual heads with compiz enabled, the bottom line is this:

The ATI 9800 Radeon Pro 128MB card has a maximum 3D texture resolution of 2048x1536.  Translation: once you get dual desktop (big desktop across dual heads) running with each monitor set at 1024x768 in your xorg.conf, then choosing the combined virtual desktop size of 2048x1536, then enabling compiz it will work.  This is actually a bit of a let down for those of us running dual 1280x1024 LCD monitors such as myself and a lot of the people trying to get this going.

There is a comprehensive tutorial (written for gutsy 7.10, but worked for me on intrepid 8.10) at this link here.  If you do this, you can get the compiz running in big desktop at the price of decreased resolution per screen (1024x768 instead of 1280x1024).

Here is the link to the thread that has the excellent tutorial and information (start on page 1):

[http://ubuntuforums.org/showthread.php?t=592016&page=4](http://ubuntuforums.org/showthread.php?t=592016&page=4)

---

