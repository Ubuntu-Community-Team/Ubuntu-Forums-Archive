---
title: "User switching issue"
date: 2005-12-15
forum: General Help
---

### Post by amokoura on 2005-12-15
Ok I've posted about this before and I've sent stuff to the bug database without any results but I'll give it a shot once more:

How to get the user switching to work? After trying to jump from the current session to an session in the background, it goes to command line login.

Anybody having Breezy with a well functioning user switching feature? If yes, how did you do it?!

---

### Post by amohanty on 2005-12-16
Teh default install works great for me. Wife and I switch one's session to the others all the time. Only if my wife logsout and I am still logged in does the command prompt flash by for a sec or so, but switches right back to gdm.

Can you post the output of ```
dmesg | tail -n 50
```

right after you switch and end up with the command prompt.

AM

---

### Post by DaMasta on 2005-12-16
You have gdm running right?
ps -ef | grep gdm

---

### Post by amokoura on 2005-12-16
I performed the commands right after jumping to console and logging in with command line.

**[SIZE="3"]$ dmesg | tail -n 50[/SIZE]**
```
[4294681.013000] EXT3 FS on hdb5, internal journal
[4294686.127000] parport: PnPBIOS parport detected.
[4294686.127000] parport0: PC-style at 0x378 (0x778), irq 7, using FIFO [PCSPP,TRISTATE,COMPAT,ECP]
[4294686.214000] lp0: using parport0 (interrupt-driven).
[4294686.235000] mice: PS/2 mouse device common for all mice
[4294686.680000] input: ImPS/2 Logitech Wheel Mouse on isa0060/serio1
[4294687.054000] ts: Compaq touchscreen protocol output
[4294689.779000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: dm-devel@redhat.com
[4294690.361000] cdrom: open failed.
[4294690.919000] NTFS driver 2.1.22 [Flags: R/O MODULE].
[4294690.965000] NTFS volume version 3.1.
[4294691.001000] NTFS volume version 3.1.
[4294692.079000] Linux agpgart interface v0.101 (c) Dave Jones
[4294692.087000] agpgart: Detected an Intel 865 Chipset.
[4294692.087000] agpgart: Detected 892K stolen memory.
[4294692.114000] agpgart: AGP aperture is 128M @ 0xe8000000
[4294692.438000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[4294692.442000] shpchp: acpi_shpchprm:\_SB_.PCI0 evaluate _BBN fail=0x5
[4294692.442000] shpchp: acpi_shpchprm:get_device PCI ROOT HID fail=0x5
[4294692.514000] hw_random hardware driver 1.0.0 loaded
[4294692.970000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 21 (level, low) -> IRQ 21
[4294692.970000] Model 1003 Rev 00000000 Serial 10031102
[4294693.330000] gameport: EMU10K1 is pci0000:01:00.1/gameport0, io 0xdf18, speed 1084kHz
[4294694.902000] input: PC Speaker
[4294694.947000] Real Time Clock Driver v1.12
[4294695.007000] Floppy drive(s): fd0 is 1.44M
[4294695.020000] FDC 0 is a post-1991 82077
[4294696.682000] e100: eth0: e100_watchdog: link up, 10Mbps, half-duplex
[4294696.691000] NET: Registered protocol family 17
[4294699.847000] NET: Registered protocol family 10
[4294699.847000] Disabled Privacy Extensions on device c02eb280(lo)
[4294699.847000] IPv6 over IPv4 tunneling driver
[4294700.914000] ACPI: Power Button (FF) [PWRF]
[4294700.914000] ACPI: Power Button (CM) [VBTN]
[4294701.016000] ibm_acpi: ec object not found
[4294705.192000] [drm] Initialized drm 1.0.0 20040925
[4294705.196000] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
[4294705.200000] [drm] Initialized i915 1.2.0 20040405 on minor 0: Intel Corporation 82865G Integrated Graphics Controller
[4294705.200000] mtrr: base(0xe8020000) is not aligned on a size(0x800000) boundary
[4294707.545000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[4294707.545000] apm: overridden by ACPI.
[4294708.405000] Bluetooth: Core ver 2.7
[4294708.405000] NET: Registered protocol family 31
[4294708.405000] Bluetooth: HCI device and connection manager initialized
[4294708.405000] Bluetooth: HCI socket layer initialized
[4294708.430000] Bluetooth: L2CAP ver 2.7
[4294708.430000] Bluetooth: L2CAP socket layer initialized
[4294708.475000] Bluetooth: RFCOMM ver 1.5
[4294708.475000] Bluetooth: RFCOMM socket layer initialized
[4294708.475000] Bluetooth: RFCOMM TTY layer initialized
[4294710.020000] eth0: no IPv6 routers present

```
[B][SIZE="3"]
$ ps -ef | grep gdm[/SIZE][/B]
```
root      7034     1  0 12:00 ?        00:00:00 /usr/sbin/gdm
root      7039  7034  0 12:00 ?        00:00:00 /usr/sbin/gdm
root      7666  7034  0 12:00 ?        00:00:00 /usr/sbin/gdm
root      7671  7666 41 12:00 ?        00:09:09 /usr/X11R6/bin/X :20 -auth /var/lib/gdm/:20.Xauth -nolisten tcp vt8
antti     8745  8703  0 12:22 tty1     00:00:00 grep gdm
```


[SIZE="1"]Thanks for the help this far..[/SIZE]

---

### Post by amohanty on 2005-12-16
Looks ok. Ok do it again, this time post the contents of the following file:

/var/log/Xorg.0.log

---

### Post by amokoura on 2005-12-16
[http://h1.ripway.com/amokoura/temp/xorgi.txt]("http://h1.ripway.com/amokoura/temp/xorgi.txt")

---

### Post by amohanty on 2005-12-16
This:

> Fatal server error:
Caught signal 11.  Server aborting

is the source of your problem.

Look at this thread and see if it helps:
[http://ubuntuforums.org/showthread.php?t=77326.html](http://ubuntuforums.org/showthread.php?t=77326.html)

HTH
AM

---

### Post by amokoura on 2005-12-16
[QUOTE=amohanty]
Look at this thread and see if it helps:
[http://ubuntuforums.org/showthread.php?t=77326.html](http://ubuntuforums.org/showthread.php?t=77326.html)
[/QUOTE]

That's about nVidia. I have Intel's integrated card.

Thank you for the help this far. The signal 11 seems to be a pretty widespread error and I have totally no idea how to solve it.

---

### Post by amohanty on 2005-12-16
I think I saw that as a bug report, some time back. I thought that that had been addressed but I guess not. Sorry couldnt help you more. I guess you should repost with the Signal 11 in the title and see if some guru can come up with an answer.

---

