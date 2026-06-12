---
title: "CD/DVD will not auto play..."
date: 2006-01-15
forum: General Help
---

### Post by bluevoodoo1 on 2006-01-15
I cannot get a CD or DVD to autoplay after inserting it into the drive. It worked before yesterday, I do not know what happened. If, after I insert it, eject it, then insert it again, it will work, but the disc should be read upon first insertion!!! I have been searching here and trying things on my own for over 3.5 hours and have come up with nothing... I have not had this much trouble with anything on Ubuntu yet. Here is the output of some files...

```

## This is the default configuration for hdparm for Debian.  It is a 
## rather simple script, so please follow the following guidelines :)
## Any line that begins with a comment is ignored - add as many as you 
## like.  Note that an in-line comment is not supported.  If a line 
## consists of whitespace only (tabs, spaces, carriage return), it will be
## ignored, so you can space control fields as you like.  ANYTHING ELSE
## IS PARSED!!  This means that lines with stray characters or lines that 
## use non # comment characters will be interpreted by the initscript.  
## This has probably minor, but potentially serious, side effects for your 
## hard drives, so please follow the guidelines.  Patches to improve 
## flexibilty welcome.  Please read /usr/share/doc/hdparm/README.Debian for 
## notes about known issues, especially if you have an MD array.
##
## Note that if the init script causes boot problems, you can pass 'nohdparm' 
## on the kernel command line, and the script will not be run.
##
## Uncommenting the options below will cause them to be added to the DEFAULT
## string which is prepended to options listed in the blocks below.
##
## If an option is listed twice, the second instance replaces the first.
##
## /sbin/hdparm is not run unless a block of the form:
##      DEV {
##         option
##         option
##         ...
##      }
## exists.  This blocks will cause /sbin/hdparm OPTIONS DEV to be run.
## Where OPTIONS is the concatenation of all options previously defined
## outside of a block and all options defined with in the block.

# -q be quiet
quiet 
# -a sector count for filesystem read-ahead
#read_ahead_sect = 12
# -A disable/enable the IDE drive's read-lookahead feature
#lookahead = on
# -b bus state
#bus = on
# -B apm setting
#apm = 255
# -c enable (E)IDE 32-bit I/O support - can be any of 0,1,3
#io32_support = 1
# -d disable/enable the "using_dma" flag for this drive
#dma = on
# -D enable/disable the on-drive defect management
#defect_mana = off
# -E cdrom speed
#cd_speed = 16
# -k disable/enable the "keep_settings_over_reset" flag for this drive
#keep_settings_over_reset = off
# -K disable/enable the drive's "keep_features_over_reset" flag
#keep_features_over_reset = on
# -m sector count for multiple sector I/O
#mult_sect_io = 32
# -P maximum sector count for the drive's internal prefetch mechanism
#prefetch_sect = 12
# -r read-only flag for device
#read_only = off
# -S standby (spindown) timeout for the drive
#spindown_time = 24
# -u interrupt-unmask flag for the drive
#interrupt_unmask = on
# -W Disable/enable the IDE drive's write-caching feature
#write_cache = off
# -X IDE transfer mode for newer (E)IDE/ATA2 drives
#transfer_mode = 34
# -y force to immediately enter the standby mode
#standby
# -Y force to immediately enter the sleep mode
#sleep
# -Z Disable the power-saving function of certain Seagate drives
#disable_seagate
# -M Set the acoustic management properties of a drive
#acoustic_management
# -p Set the chipset PIO mode
# chipset_pio_mode

# Root file systems.  Please see README.Debian for details
# ROOTFS = /dev/hda

## New note - you can use straight hdparm commands in this config file 
## as well - the set up is ugly, but it keeps backwards compatibility
## Additionally, it should be noted that any blocks that begin with 
## the keyword 'command_line' are not run until after the root filesystem
## is mounted.  This is done to avoid running blocks twice.  If you need 
## to run hdparm to set parameters for your root disk, please use the 
## standard format.

#Samples follow:
#First three are good for devfs systems, fourth one for systems that do 
#not use devfs.  The fifth example uses straight hdparm command line
#syntax.  Any of the blocks that use command line syntax must begin with
#the keyword 'command_line', and no attempt is made to validate syntax.  
#It is provided for those more comfortable with hdparm syntax. 

#/dev/discs/disc0/disc {
#	mult_sect_io = 16
#	write_cache = off
#	spindown_time = 240
#}

#/dev/discs/disc1/disc {
#	mult_sect_io = 32
#	spindown_time = 36
#	write_cache = off
#}

#/dev/cdroms/cdrom0 {
#	dma = on		   
#	interrupt_unmask = on
#	io32_support = 0
#}

#/dev/hda {
#	mult_sect_io = 16
#	write_cache = off
#	dma = on
#}

#command_line {
#       hdparm -q -m16 -q -W0 -q -d1 /dev/hda
#}

# Added by debian-installer

/dev/hda {
	dma = on
}

```

```

brian@ubuntu:~$ sudo hdparm /dev/cdrom

/dev/cdrom:
 IO_support   =  0 (default 16-bit)
 unmaskirq    =  0 (off)
 using_dma    =  0 (off)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Invalid argument

brian@ubuntu:~$ sudo hdparm /dev/hda

/dev/hda:
 IO_support   =  0 (default 16-bit)
 unmaskirq    =  0 (off)
 using_dma    =  0 (off)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Invalid argument

```

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdc1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdc5       /home           ext3    defaults        0       2
/dev/hdc6       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

```

brian@ubuntu:~$ mount
/dev/hdc1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /dev/shm type tmpfs (rw)
usbfs on /proc/bus/usb type usbfs (rw)
/dev/hdc5 on /home type ext3 (rw)
tmpfs on /dev type tmpfs (rw,size=10M,mode=0755)
/dev/hda on /media/cdrom0 type iso9660 (ro,noexec,nosuid,nodev,user=brian)

```

```

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
mousedev
psmouse
sbp2
sr_mod

#----cut here----
# I2C adapter drivers
i2c-isa
# I2C chip drivers
it87
#----cut here----

```

Fstab: if I change /dev/hda to 'auto' instead of 'noauto' at boot it will read "mounting local filesystem...............failed.

DMA: **DMA will NOT stay on** after I eject a disc or restart and I tried adding by hand to hdparm.conf
```

/dev/cdrom {
	dma = on
}
```

and doing  sudo hdparm -d1 /dev/cdrom and both of those don't work.

I have also made sure I was added to the hal user group... still nothing...

Could it be another package I need? Firmware? (This is an ASUS CDRW/DVD+-R drive) Now that I think of it, this all started after I unplugged the CD/DVD drive and plugged in another HD to transfer some files to this computer... This is really driving me nuts!!! Please help!!!

---

### Post by bluevoodoo1 on 2006-01-15
Well, tried everything again, and it was hal. Completely uninstalled it and installed again and auto play now works, but can't seem to get DMA to stay on. Each attempt at making DMA stay on stops the auto play from working... ideas?

---

### Post by dcstar on 2006-01-15
[QUOTE=bluevoodoo1]Well, tried everything again, and it was hal. Completely uninstalled it and installed again and auto play now works, but can't seem to get DMA to stay on. Each attempt at making DMA stay on stops the auto play from working... ideas?[/QUOTE]
There is a kernel value called something like "Check for CD media type", you can turn it off using things like "Powertweak" but I do not know where it is done directly.

It seems to have an affect on automounting and autoplaying, when it is on it stuffs things up!

It could be that reinstalling HAL resets this value.

---

### Post by bluevoodoo1 on 2006-01-15
hmmmm.... hal seems to have worked for making the auto play feature work. Most guides say to add...

```

/dev/hdc {
   dma = on
   }

```

(in my case the cd-drive is hda)

...to the hdparm.conf file to turn DMA on but that makes the autoplay stop functioning. Uncommenting anything in the hdparm.conf also makes it stop functioning. I'd love to know more about this 'powertweak!'

---

### Post by dcstar on 2006-01-15
[QUOTE=bluevoodoo1]hmmmm.... hal seems to have worked for making the auto play feature work. Most guides say to add...
.....
...to the hdparm.conf file to turn DMA on but that makes the autoplay stop functioning. Uncommenting anything in the hdparm.conf also makes it stop functioning. I'd love to know more about this 'powertweak!'[/QUOTE]
[http://powertweak.sourceforge.net/](http://powertweak.sourceforge.net/)

It is in the standard repositories.

---

### Post by bluevoodoo1 on 2006-01-15
Great! Found it and installed it... what do you think I should do? turn 'check for media' off? then remove and reinstall hal and/or adjust my hdparm.conf file?

---

### Post by dcstar on 2006-01-15
[QUOTE=bluevoodoo1]Great! Found it and installed it... what do you think I should do? turn 'check for media' off? then remove and reinstall hal and/or adjust my hdparm.conf file?[/QUOTE]
Just turn it off (and "Apply" it) and see if the automount now works.

---

### Post by bluevoodoo1 on 2006-01-16
Well I turned it off, but on or off the autoplay works... it's whenever I try to turn DMA on the autoplay stops. Anytime I uncomment anything in the hdparm.conf or do sudo hdparm -d1 /dev/hda from the command line, eject the cd, then put it back in, the disc won't be recognized. So then I have to recomment the lines in hdparm.conf again for the disc to be recognized. I'll give powertweak some more look later today. Thanks for that tip!

---

### Post by dcstar on 2006-01-16
[QUOTE=bluevoodoo1]Well I turned it off, but on or off the autoplay works... it's whenever I try to turn DMA on the autoplay stops. Anytime I uncomment anything in the hdparm.conf or do sudo hdparm -d1 /dev/hda from the command line, eject the cd, then put it back in, the disc won't be recognized. So then I have to recomment the lines in hdparm.conf again for the disc to be recognized. I'll give powertweak some more look later today. Thanks for that tip![/QUOTE]
There are also different DMA modes that you can specifically set for the drive.

If you do:

sudo hdparm -i /dev/hda

You can see the current settings (with the "*" identifying them).

You might want to experiment with them, and possibly your BIOS DMA settings as well.

If you type "dmesg" after you insert a CD you can also see how your system is reacting to the event.

---

### Post by bluevoodoo1 on 2006-01-16
[QUOTE=dcstar]
You might want to experiment with them, and possibly your BIOS DMA settings as well.[/QUOTE]

Yup, Tried that, put it on UDMA4 instead of AUTO in BIOS, no luck. Also tried switching the jumper to 'master' instead of 'cable select.' Nada.

here's the output of sudo hdparm -i /dev/hda

```

/dev/hda:

 Model=DRW-1608P2, FwRev=1.17, SerialNo=
 Config={ Fixed Removeable DTR<=5Mbs DTR>10Mbs nonMagnetic }
 RawCHS=0/0/0, TrkSize=0, SectSize=0, ECCbytes=0
 BuffType=13395, BuffSize=64kB, MaxMultSect=0
 (maybe): CurCHS=0/0/0, CurSects=0, LBA=yes, LBAsects=0
 IORDY=on/off, tPIO={min:240,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4
 DMA modes:  mdma0 mdma1 mdma2
 UDMA modes: udma0 udma1 udma2 udma3 *udma4
 AdvancedPM=no
 Drive conforms to: device does not report version:

 * signifies the current active mode

```

here's output of dmesg: (I''m not sure what much of it means)

```

brian@ubuntu:~$ dmesg
 2-0:1.0: 3 ports detected
[4294676.774000] ACPI: PCI Interrupt 0000:00:13.2[A] -> GSI 19 (level, low) -> IRQ 19
[4294676.774000] ehci_hcd 0000:00:13.2: ATI Technologies Inc EHCI USB Controller[4294676.774000] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 3
[4294676.774000] ehci_hcd 0000:00:13.2: irq 19, io mem 0xfeb00000
[4294676.774000] ehci_hcd 0000:00:13.2: USB 2.0 initialized, EHCI 1.00, driver 10 Dec 2004
[4294676.774000] hub 3-0:1.0: USB hub found
[4294676.774000] hub 3-0:1.0: 6 ports detected
[4294676.849000] ACPI: PCI Interrupt 0000:02:08.0[A] -> GSI 18 (level, low) -> IRQ 18
[4294676.849000] 3c59x: Donald Becker and others. www.scyld.com/network/vortex.html
[4294676.849000] 0000:02:08.0: 3Com PCI 3c920B-EMB-WNM (ATI Radeon 9100 IGP) at 0xec00. Vers LK1.1.19
[4294677.435000] usb 2-3: new full speed USB device using ohci_hcd and address 2[4294679.383000] ACPI: CPU0 (power states: C1[C1])
[4294679.634000] Attempting manual resume
[4294679.634000] swsusp: Suspend partition has wrong signature?
[4294679.652000] kjournald starting.  Commit interval 5 seconds
[4294679.652000] EXT3-fs: mounted filesystem with ordered data mode.
[4294680.556000] md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
[4294683.551000] Adding 2072344k swap on /dev/hdc6.  Priority:-1 extents:1
[4294683.819000] EXT3 FS on hdc1, internal journal
[4294685.450000] parport: PnPBIOS parport detected.
[4294685.450000] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP]
[4294685.537000] lp0: using parport0 (interrupt-driven).
[4294685.571000] mice: PS/2 mouse device common for all mice
[4294685.662000] ieee1394: Initialized config rom entry `ip1394'
[4294685.699000] SCSI subsystem initialized
[4294685.705000] sbp2: $Rev: 1219 $ Ben Collins <bcollins@debian.org>
[4294685.814000] it87: Found IT8712F chip at 0x260, revision 6
[4294685.946000] input: ImPS/2 Logitech Wheel Mouse on isa0060/serio1
[4294686.315000] ts: Compaq touchscreen protocol output
[4294689.242000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: dm-devel@redhat.com
[4294690.282000] cdrom: open failed.
[4294691.061000] kjournald starting.  Commit interval 5 seconds
[4294691.061000] EXT3 FS on hdc5, internal journal
[4294691.061000] EXT3-fs: mounted filesystem with ordered data mode.
[4294693.735000] Linux agpgart interface v0.101 (c) Dave Jones
[4294693.745000] agpgart: Detected Ati IGP9100/M chipset
[4294693.766000] agpgart: AGP aperture is 64M @ 0xf8000000
[4294693.922000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[4294693.966000] shpchp: shpc_init : shpc_cap_offset == 0
[4294693.966000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[4294695.895000] ACPI: PCI Interrupt 0000:00:14.5[B] -> GSI 17 (level, low) -> IRQ 17
[4294696.803000] ohci1394: $Rev: 1250 $ Ben Collins <bcollins@debian.org>
[4294696.803000] ACPI: PCI Interrupt 0000:02:0a.0[A] -> GSI 18 (level, low) -> IRQ 18
[4294696.803000] PCI: Via IRQ fixup for 0000:02:0a.0, from 3 to 2
[4294696.861000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[18]  MMIO=[fe000000-fe0007ff]  Max Packet=[2048]
[4294697.002000] Linux Kernel Card Services
[4294697.002000]   options:  [pci] [cardbus] [pm]
[4294697.020000] ACPI: PCI Interrupt 0000:02:0c.0[A] -> GSI 16 (level, low) -> IRQ 16
[4294697.020000] Yenta: CardBus bridge found at 0000:02:0c.0 [1524:1411]
[4294697.140000] Yenta: ISA IRQ mask 0x0040, PCI irq 16
[4294697.140000] Socket status: 30000006
[4294698.126000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0011d80000436368][4294698.470000] drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 2 if 0 alt 0 proto 2 vid 0x043D pid 0x0078
[4294698.476000] usbcore: registered new driver usblp
[4294698.476000] drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driver
[4294698.606000] Real Time Clock Driver v1.12
[4294698.759000] input: PC Speaker
[4294700.490000] ACPI: PCI Interrupt 0000:02:08.0[A] -> GSI 18 (level, low) -> IRQ 18
[4294700.514000] NET: Registered protocol family 17
[4294704.482000] NET: Registered protocol family 10
[4294704.482000] Disabled Privacy Extensions on device c02eb280(lo)
[4294704.482000] IPv6 over IPv4 tunneling driver
[4294705.988000] ACPI: Power Button (FF) [PWRF]
[4294705.988000] ACPI: Power Button (CM) [PWRB]
[4294706.104000] ibm_acpi: ec object not found
[4294712.294000] [drm] Initialized drm 1.0.0 20040925
[4294712.308000] ACPI: PCI Interrupt 0000:01:05.0[A] -> GSI 16 (level, low) -> IRQ 16
[4294712.310000] [drm] Initialized radeon 1.16.0 20050311 on minor 0: ATI Technologies Inc Radeon 9100 IGP
[4294712.311000] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
[4294712.311000] agpgart: reserved bits set in mode 0x1f00020f. Fixed.
[4294712.311000] agpgart: Xorg tried to set rate=x12. Setting to AGP3 x8 mode.
[4294712.311000] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[4294712.311000] agpgart: Putting AGP V3 device at 0000:01:05.0 into 8x mode
[4294712.737000] [drm] Loading R200 Microcode
[4294715.108000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[4294715.108000] apm: overridden by ACPI.
[4294715.186000] ip_tables: (C) 2000-2002 Netfilter core team
[4294715.291000] ip_conntrack version 2.1 (7674 buckets, 61392 max) - 248 bytes per conntrack
[4294715.352000] eth0: no IPv6 routers present
[4294718.475000] cs: IO port probe 0x100-0x4ff: excluding 0x408-0x40f 0x4d0-0x4d7
[4294718.477000] cs: IO port probe 0xc00-0xcf7: excluding 0xc00-0xc07 0xc10-0xc17 0xc50-0xc57 0xc68-0xc6f 0xcd0-0xcd7
[4294718.478000] cs: IO port probe 0xa00-0xaff: clean.
[4294718.968000] Bluetooth: Core ver 2.7
[4294718.968000] NET: Registered protocol family 31
[4294718.969000] Bluetooth: HCI device and connection manager initialized
[4294718.969000] Bluetooth: HCI socket layer initialized
[4294718.969000] Warning: /proc/ide/hd?/settings interface is obsolete, and will be removed soon!
[4294719.094000] Bluetooth: L2CAP ver 2.7
[4294719.094000] Bluetooth: L2CAP socket layer initialized
[4294719.101000] Bluetooth: RFCOMM ver 1.5
[4294719.101000] Bluetooth: RFCOMM socket layer initialized
[4294719.101000] Bluetooth: RFCOMM TTY layer initialized
[4296920.202000] hda: cdrom_decode_status: status=0x51 { DriveReady SeekComplete Error }
[4296920.202000] hda: cdrom_decode_status: error=0x40 { LastFailedSense=0x04 }
[4296920.202000] ide: failed opcode was: unknown
[4296922.208000] hda: cdrom_decode_status: status=0x51 { DriveReady SeekComplete Error }
[4296922.208000] hda: cdrom_decode_status: error=0x40 { LastFailedSense=0x04 }
[4296922.208000] ide: failed opcode was: unknown
[4296924.214000] hda: cdrom_decode_status: status=0x51 { DriveReady SeekComplete Error }
[4296924.214000] hda: cdrom_decode_status: error=0x40 { LastFailedSense=0x04 }
[4296924.214000] ide: failed opcode was: unknown
[4296926.220000] hda: cdrom_decode_status: status=0x51 { DriveReady SeekComplete Error }
[4296926.220000] hda: cdrom_decode_status: error=0x40 { LastFailedSense=0x04 }
[4296926.220000] ide: failed opcode was: unknown
[4296926.220000] hda: DMA disabled
[4296926.220000] hda: ide_intr: huh? expected NULL handler on exit
[4296926.270000] hda: ATAPI reset complete
[4296953.015000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4296953.015000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4296953.132000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4296953.132000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4296953.970000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4296953.970000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4296954.064000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4296954.064000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4296954.234000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4296954.234000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4296954.338000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4296954.338000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4296954.509000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4296954.509000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4296954.602000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4296954.602000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297047.349000] hda: cdrom_decode_status: status=0x51 { DriveReady SeekComplete Error }
[4297047.349000] hda: cdrom_decode_status: error=0x40 { LastFailedSense=0x04 }
[4297047.349000] ide: failed opcode was: unknown
[4297049.355000] hda: cdrom_decode_status: status=0x51 { DriveReady SeekComplete Error }
[4297049.355000] hda: cdrom_decode_status: error=0x40 { LastFailedSense=0x04 }
[4297049.355000] ide: failed opcode was: unknown
[4297051.361000] hda: cdrom_decode_status: status=0x51 { DriveReady SeekComplete Error }
[4297051.361000] hda: cdrom_decode_status: error=0x40 { LastFailedSense=0x04 }
[4297051.361000] ide: failed opcode was: unknown
[4297053.367000] hda: cdrom_decode_status: status=0x51 { DriveReady SeekComplete Error }
[4297053.367000] hda: cdrom_decode_status: error=0x40 { LastFailedSense=0x04 }
[4297053.367000] ide: failed opcode was: unknown
[4297053.367000] hda: DMA disabled
[4297053.367000] hda: ide_intr: huh? expected NULL handler on exit
[4297053.417000] hda: ATAPI reset complete
[4297222.185000] hda: cdrom_decode_status: status=0x51 { DriveReady SeekComplete Error }
[4297222.185000] hda: cdrom_decode_status: error=0x40 { LastFailedSense=0x04 }
[4297222.185000] ide: failed opcode was: unknown
[4297224.191000] hda: cdrom_decode_status: status=0x51 { DriveReady SeekComplete Error }
[4297224.191000] hda: cdrom_decode_status: error=0x40 { LastFailedSense=0x04 }
[4297224.191000] ide: failed opcode was: unknown
[4297226.197000] hda: cdrom_decode_status: status=0x51 { DriveReady SeekComplete Error }
[4297226.197000] hda: cdrom_decode_status: error=0x40 { LastFailedSense=0x04 }
[4297226.197000] ide: failed opcode was: unknown
[4297228.203000] hda: cdrom_decode_status: status=0x51 { DriveReady SeekComplete Error }
[4297228.203000] hda: cdrom_decode_status: error=0x40 { LastFailedSense=0x04 }
[4297228.203000] ide: failed opcode was: unknown
[4297228.203000] hda: DMA disabled
[4297228.203000] hda: ide_intr: huh? expected NULL handler on exit
[4297228.253000] hda: ATAPI reset complete
[4297552.669000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4297552.669000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297552.746000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4297552.746000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297553.655000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4297553.655000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297553.722000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4297553.722000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297553.833000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4297553.833000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297553.914000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4297553.914000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297554.004000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4297554.004000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297554.092000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4297554.092000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297554.288000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4297554.288000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297554.374000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4297554.374000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297554.858000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4297554.858000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297554.968000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4297554.968000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297627.009000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4297627.009000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297627.107000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4297627.107000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297627.254000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4297627.254000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297627.340000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4297627.340000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297746.648000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4297746.648000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297749.148000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4297749.148000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4309432.798000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4309432.798000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4309432.869000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4309432.869000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4309453.380000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4309453.380000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4309453.457000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4309453.457000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4309456.758000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4309456.758000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4309456.830000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4309456.830000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4309474.748000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4309474.748000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4309474.818000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4309474.818000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4309480.031000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4309480.031000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4309480.104000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4309480.104000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4309992.294000] ISO 9660 Extensions: Microsoft Joliet Level 3
[4309992.486000] ISOFS: changing to secondary root
[4315388.800000] ISO 9660 Extensions: Microsoft Joliet Level 3
[4315388.801000] ISOFS: changing to secondary root
[4328888.798000] ISO 9660 Extensions: Microsoft Joliet Level 3
[4328888.800000] ISOFS: changing to secondary root

```

---

### Post by dcstar on 2006-01-16
[QUOTE=bluevoodoo1]
.......
here's output of dmesg: (I''m not sure what much of it means)
.......
[4297226.197000] ide: failed opcode was: unknown
[4297228.203000] hda: cdrom_decode_status: status=0x51 { DriveReady SeekComplete Error }
[4297228.203000] hda: cdrom_decode_status: error=0x40 { LastFailedSense=0x04 }
[4297228.203000] ide: failed opcode was: unknown
[4297228.203000] hda: DMA disabled
[4297228.203000] hda: ide_intr: huh? expected NULL handler on exit
[4297228.253000] hda: ATAPI reset complete
.......[/QUOTE]
I think these messages just mean that there is something incompatible at kernel level with your particular DVD/hardware combination when used in DMA mode.

Safest thing would be to set the drive using (hdparm) to use the highest PIO mode available, and if it all works leave it be.

Things may improve with the next kernel - or Ubuntu release.

---

### Post by bluevoodoo1 on 2006-01-16
I'll keep toying around with it. Perhaps I will just have to wait until the next kernel or release as you stated. Thank you very much for all of your suggestions and help!

---

### Post by dcstar on 2006-01-17
[QUOTE=dcstar]There is a kernel value called something like "Check for CD media type", you can turn it off using things like "Powertweak" but I do not know where it is done directly.

It seems to have an affect on automounting and autoplaying, when it is on it stuffs things up!

It could be that reinstalling HAL resets this value.[/QUOTE]
Ok, I found where this little item can be set (without having to use Powertweak to do it):

Try adding this to your /etc/sysctl.conf file (and reboot):

dev.cdrom.check_media = 0

---

### Post by bluevoodoo1 on 2006-01-17
[QUOTE=dcstar]
Try adding this to your /etc/sysctl.conf file (and reboot):

dev.cdrom.check_media = 0[/QUOTE]

ok, added that. rebooted. Autoplay. So I tried turning on DMA via uncommenting last lines of etc/hdparm.conf... rebooted, no autoplay but DMA on. Reinstalled hal, (DMA on), rebooted, no autoplay. It definitely has to do with DMA, since any attempt to turn it on affects the autoplay. With DMA off, auotplay works....

---

### Post by Turin Turambar on 2006-01-23
[QUOTE=bluevoodoo1]ok, added that. rebooted. Autoplay. So I tried turning on DMA via uncommenting last lines of etc/hdparm.conf... rebooted, no autoplay but DMA on. Reinstalled hal, (DMA on), rebooted, no autoplay. It definitely has to do with DMA, since any attempt to turn it on affects the autoplay. With DMA off, auotplay works....[/QUOTE]

Hey, I had the same problem as you - couldn't make autoplay work everytime. I use Asus DVD & CDRW devices too.
However, I cleared this problem when I added the following line in hdparm.conf

```
command_line {
	hdparm -d1 /dev/cdrom
}

command_line {
	hdparm -d1 /dev/cdrom1
}
```

It only works when using "command_line" mode.
It fixed everything and from now on I always have DMA enabled & autoplay!

---

### Post by bluevoodoo1 on 2006-01-25
EDIT: hmmmm, working on this... I'll post a reply in a few hours to see how it goes....

---

### Post by bluevoodoo1 on 2006-01-25
well I added...

command_line {
	hdparm -d1 /dev/cdrom0
}

Since adding /dev/cdrom or /dev/cdrom1 stop the autoplay feature. With any of those 3 DMA is still not on. /dev/cdrom0 is the only one where autoplay will still work. I only have one drive, so it should be cdrom0 correct? I tried those 3 combinations as well as uncommenting...

#/dev/hda {
#	dma = on
#}

...but uncommenting that stops the autoplay and doesn't turn DMA on anyway. Here's the "new" hdparm.conf file... Still stumped..... Still no DMA...

```

## This is the default configuration for hdparm for Debian.  It is a 
## rather simple script, so please follow the following guidelines :)
## Any line that begins with a comment is ignored - add as many as you 
## like.  Note that an in-line comment is not supported.  If a line 
## consists of whitespace only (tabs, spaces, carriage return), it will be
## ignored, so you can space control fields as you like.  ANYTHING ELSE
## IS PARSED!!  This means that lines with stray characters or lines that 
## use non # comment characters will be interpreted by the initscript.  
## This has probably minor, but potentially serious, side effects for your 
## hard drives, so please follow the guidelines.  Patches to improve 
## flexibilty welcome.  Please read /usr/share/doc/hdparm/README.Debian for 
## notes about known issues, especially if you have an MD array.
##
## Note that if the init script causes boot problems, you can pass 'nohdparm' 
## on the kernel command line, and the script will not be run.
##
## Uncommenting the options below will cause them to be added to the DEFAULT
## string which is prepended to options listed in the blocks below.
##
## If an option is listed twice, the second instance replaces the first.
##
## /sbin/hdparm is not run unless a block of the form:
##      DEV {
##         option
##         option
##         ...
##      }
## exists.  This blocks will cause /sbin/hdparm OPTIONS DEV to be run.
## Where OPTIONS is the concatenation of all options previously defined
## outside of a block and all options defined with in the block.

# -q be quiet
quiet 
# -a sector count for filesystem read-ahead
#read_ahead_sect = 12
# -A disable/enable the IDE drive's read-lookahead feature
#lookahead = on
# -b bus state
#bus = on
# -B apm setting
#apm = 255
# -c enable (E)IDE 32-bit I/O support - can be any of 0,1,3
#io32_support = 1
# -d disable/enable the "using_dma" flag for this drive
#dma = off
# -D enable/disable the on-drive defect management
#defect_mana = off
# -E cdrom speed
#cd_speed = 16
# -k disable/enable the "keep_settings_over_reset" flag for this drive
#keep_settings_over_reset = off
# -K disable/enable the drive's "keep_features_over_reset" flag
#keep_features_over_reset = on
# -m sector count for multiple sector I/O
#mult_sect_io = 32
# -P maximum sector count for the drive's internal prefetch mechanism
#prefetch_sect = 12
# -r read-only flag for device
#read_only = off
# -S standby (spindown) timeout for the drive
#spindown_time = 24
# -u interrupt-unmask flag for the drive
#interrupt_unmask = on
# -W Disable/enable the IDE drive's write-caching feature
#write_cache = off
# -X IDE transfer mode for newer (E)IDE/ATA2 drives
#transfer_mode = 34
# -y force to immediately enter the standby mode
#standby
# -Y force to immediately enter the sleep mode
#sleep
# -Z Disable the power-saving function of certain Seagate drives
#disable_seagate
# -M Set the acoustic management properties of a drive
#acoustic_management
# -p Set the chipset PIO mode
# chipset_pio_mode

# Root file systems.  Please see README.Debian for details
# ROOTFS = /dev/hda

## New note - you can use straight hdparm commands in this config file 
## as well - the set up is ugly, but it keeps backwards compatibility
## Additionally, it should be noted that any blocks that begin with 
## the keyword 'command_line' are not run until after the root filesystem
## is mounted.  This is done to avoid running blocks twice.  If you need 
## to run hdparm to set parameters for your root disk, please use the 
## standard format.

#Samples follow:
#First three are good for devfs systems, fourth one for systems that do 
#not use devfs.  The fifth example uses straight hdparm command line
#syntax.  Any of the blocks that use command line syntax must begin with
#the keyword 'command_line', and no attempt is made to validate syntax.  
#It is provided for those more comfortable with hdparm syntax. 

#/dev/discs/disc0/disc {
#	mult_sect_io = 16
#	write_cache = off
#	spindown_time = 240
#}

#/dev/discs/disc1/disc {
#	mult_sect_io = 32
#	spindown_time = 36
#	write_cache = off
#}

#/dev/cdroms/cdrom0 {
#	dma = on		   
#	interrupt_unmask = on
#	io32_support = 0
#}

#/dev/hda {
#	mult_sect_io = 16
#	write_cache = off
#	dma = on
#}

#command_line {
#       hdparm -q -m16 -q -W0 -q -d1 /dev/hda
#}

# Added by debian-installer

#/dev/hda {
#	dma = on
#}

command_line {
	hdparm -d1 /dev/cdrom0
}

```

---

### Post by Turin Turambar on 2006-01-25
?! Still no DMA even with "command_line"? Eh? Well, that's strange.
The "cdrom" is a symlink to "cdrom0" on my machine.

Have you tried this in terminal:
```
sudo hdparm -d1 /dev/cdrom
```
Does it say anything?

I also noticed that you don't have write cache enabled for your hard drive. That slows the total preformance.
Do you have a hdparm service enabled in a boot-up process at all?

Here are my outputs:

sudo hdparm /dev/cdrom

```
/dev/cdrom:

 IO_support   =  1 (32-bit)
 unmaskirq    =  1 (on)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Invalid argument

ivan@ubuntu-ivan:~$ 
```

sudo hdparm /dev/hda

```
/dev/hda:
 multcount    =  0 (off)
 IO_support   =  1 (32-bit)
 unmaskirq    =  1 (on)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 geometry     = 65535/16/63, sectors = 156301488, start = 0
ivan@ubuntu-ivan:~$
```

Since adding the "command_line" parametar in hdparm.conf, I *always* have DMA enabled for my two cd/dvd drives.

---

### Post by bluevoodoo1 on 2006-01-25
sudo hdparm -d1 /dev/cdrom gives the same as you...

/dev/cdrom:
 setting using_dma to 1 (on)
 using_dma    =  1 (on)

It turns it on, but after ejecting or inserting a disc or restarting the computer, DMA is off again.  (and now that I did sudo hdparm -d1 /dev/cdrom the autoplay will not work). But right-clicking the cdrom folder in file system and opening with xine I can watch a DVD. But, I run xine-check and it says dma is off...

here's the output of sudo hdparm -i /dev/cdrom

```

/dev/cdrom:

 Model=DRW-1608P2, FwRev=1.17, SerialNo=
 Config={ Fixed Removeable DTR<=5Mbs DTR>10Mbs nonMagnetic }
 RawCHS=0/0/0, TrkSize=0, SectSize=0, ECCbytes=0
 BuffType=13395, BuffSize=64kB, MaxMultSect=0
 (maybe): CurCHS=0/0/0, CurSects=0, LBA=yes, LBAsects=0
 IORDY=on/off, tPIO={min:240,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4
 DMA modes:  mdma0 mdma1 mdma2
 UDMA modes: udma0 udma1 udma2 udma3 *udma4
 AdvancedPM=no
 Drive conforms to: device does not report version:

 * signifies the current active mode

```

I've had some problems with DMA ever since the install, when I had to install with 'expert' so I could manually turn DMA on via '-d1' in one of the cdrom command lines.

EDIT: Could it be a hardware problem? I have the jumper cables set to "cable select," should I try master? Or does it not matter?

---

### Post by GTvulse on 2006-02-03
IN case you are still fighting with this problem. Check your cable. Make sure it is an 80-wire cable and that the connectors are firmly in place. I had the same problem happen to me with a spare hard drive I plugged recently in my box. Nothing worked until I opened the case and discovered to my dismay that I had left the cable loose on the HD connector...

---

### Post by bluevoodoo1 on 2006-02-04
[QUOTE=dradul]IN case you are still fighting with this problem. Check your cable. Make sure it is an 80-wire cable and that the connectors are firmly in place. I had the same problem happen to me with a spare hard drive I plugged recently in my box. Nothing worked until I opened the case and discovered to my dismay that I had left the cable loose on the HD connector...[/QUOTE]


That's a good idea, I should try another cable and see if it's that... The drive works otherwise, that is the strange thing. I can listen to CDs, rip them at 3x :(, and watch CHOPPY DVDs :(. DMA just won't turn on and stay on. I'm going to experiment with the jumper cable as well. Changing it from cable select to master perhaps.

---

### Post by cabbage on 2006-02-09
Greetings,

I recently had the automounting problem. It was working fine and then stopped. At the time it stopped I had made two changes. The first was to start using the 686 kernel as opposed to the 386, and the other was to add "dma = on" for /dev/hdc to my hdparm.conf file.

Having read this thread I tried removing the lines from hdparm.conf, but this made no difference, so I reinstalled hal and automounting started working!

Thanks guys!

---

### Post by bluevoodoo1 on 2006-02-09
[QUOTE=cabbage]I recently had the automounting problem. It was working fine and then stopped. At the time it stopped I had made two changes. The first was to start using the 686 kernel as opposed to the 386[/QUOTE]

Hmmm you know, when I look in synaptic it says I have the linux-image-2.6.12-9-386 installed, and uname -a tells me this...

"Linux ubuntu 2.6.12-9-386 #1 Mon Oct 10 13:14:36 BST 2005 i686 GNU/Linux"

what is that i686 part? (hmm the date and time aren't set for my local date/time either)

---

### Post by bluevoodoo1 on 2006-03-08
Well, I've solved my own problem.. and...

I GOT IT TO WORK!! I took out the ASUS drive and tested it in my other computer, worked in Breezy and Windows, so I figured it had to be some hardware related here. So I found a few sites that really saved me. They are...

[http://planet.gentoo.org/developers/johnm/2005/06/24/asus_pundit_r_s_asterisk_and_kids_on_bik](http://planet.gentoo.org/developers/johnm/2005/06/24/asus_pundit_r_s_asterisk_and_kids_on_bik)
[http://www.unicom.com/chrome/a/001023.html](http://www.unicom.com/chrome/a/001023.html)

Turns out it's a known problem, DMA and the ASUS Pudit-r... I had to do the following... plug IDE cable into "other" input, switch drive to slave and change drive from hda to hdb in /etc/fstab. I don't know if all of those are actually necessary... but DMA WORKS NOW! 3 months of torture now resolved!!! Thank you for all of your ideas and help regarding everything! Time for a DVD!!!

---

