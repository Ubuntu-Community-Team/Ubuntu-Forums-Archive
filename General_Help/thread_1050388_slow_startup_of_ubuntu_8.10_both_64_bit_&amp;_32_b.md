---
title: "slow startup of ubuntu 8.10 both 64 bit &amp; 32 bit"
date: 2009-01-25
forum: General Help
---

### Post by anson123 on 2009-01-25
Hi,

i am experiencing very slow startup times.

i am currently using ubuntu 8.10 64 bit, but have experienced the same problem with the 32 bit version as well.

below i posted output from the "dmesg" command, two spots where there is a big gap in time.

this seems to happen at random places, and it only continues after i press the "Enter" key.

any ideas as to how to fix this and speed up my startup time?

thanks for any help/advice!!

[   15.055752] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input9
[   15.098734] iTCO_wdt: Found a ICH8M TCO device (Version=2, TCOBASE=0x1060)
[   15.098823] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   15.865897] lp: driver loaded but no devices found
[   16.016069] Adding 2000084k swap on /dev/sda5.  Priority:-1 extents:1 across:2000084k
[   17.481099] EXT3 FS on sda2, internal journal
[  122.845178] kjournald starting.  Commit interval 5 seconds
[  122.848087] EXT3 FS on sda1, internal journal
[  122.848091] EXT3-fs: mounted filesystem with ordered data mode.
[  123.489193] kjournald starting.  Commit interval 5 seconds





[  125.969724] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[  126.138423] ppdev: user-space parallel port driver
[  131.176454] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[  131.176471] vboxdrv: Successfully done.
[  131.176475] vboxdrv: Found 2 processor cores.
[  131.181506] vboxdrv: fAsync=0 offMin=0x41a offMax=0xf16b
[  131.181519] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[  131.181524] vboxdrv: Successfully loaded version 2.0.6 (interface 0x00090000).
[  274.690098] tun: Universal TUN/TAP device driver, 1.6
[  274.690106] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[  277.517700] Bluetooth: Core ver 2.13

---

