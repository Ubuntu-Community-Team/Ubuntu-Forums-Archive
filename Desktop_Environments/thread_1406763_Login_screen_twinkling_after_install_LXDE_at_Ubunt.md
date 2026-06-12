---
title: "Login screen twinkling after install LXDE at Ubuntu 8.04.3"
date: 2010-02-14
forum: Desktop Environments
---

### Post by good5209 on 2010-02-14
Hi, everybody


Environment: Ubuntu 8.04.3

I surf to LXDE website and download tarball for compile by myself.

It say need newer version gtk+ library, so I go to download gtk+ tarball too. And make install it.

When glib-2.22.4 install finish, I attend LXDE's deb files for install, I add lxde apt information and use apt-get install lxde.

Install finish, so I logout gnome and want login LXDE, but it happen this problem:
NVIDIA Logo -> orange screen, waiting cursor -> black terminal screen -> NVIDIA Logo -> ...

I has tried these to solve this problem, but not work:
1.sudo dpkg-reconfigure gnome-desktop-environment
terminal say nothing after this.

2.sudo apt-get remove lxde openbox lxde-*

3.sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf_backup

4.sudo /etc/init.d/kdm start
terminal say kdm isn't default setting.

5.sudo aptitude remove xserver; sudo aptitude install ubuntu-desktop


a part of dmesg:
```
[   23.860912] EXT3-fs: mounted filesystem with ordered data mode.
[   32.403587] ip_tables: (C) 2000-2006 Netfilter Core Team
[   32.472170] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
[   33.469996] Linux agpgart interface v0.102
[   33.757214] agpgart: Detected SiS chipset - id:1633
[   33.762151] agpgart: AGP aperture is 64M @ 0xe0000000
[   33.807525] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   33.848893] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   34.001069] input: Power Button (FF) as /devices/virtual/input/input3
[   34.012786] ACPI: Power Button (FF) [PWRF]
[   34.013013] input: Power Button (CM) as /devices/virtual/input/input4
[   34.020763] ACPI: Power Button (CM) [PWRB]
[   35.735103] nvidia: module license 'NVIDIA' taints kernel.
[   36.683428] ACPI: PCI Interrupt 0000:00:02.7[C] -> GSI 18 (level, low) -> IRQ 23
[   36.902776] parport_pc 00:07: reported by Plug and Play ACPI
[   36.902889] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[   37.004469] intel8x0_measure_ac97_clock: measured 54752 usecs
[   37.004475] intel8x0: clocking to 48000
[   37.069550] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 17
[   37.069955] NVRM: loading NVIDIA UNIX x86 Kernel Module  169.12  Thu Feb 14 17:53:07 PST 2008
[   40.174063] lp0: using parport0 (interrupt-driven).
[   40.249246] p4-clockmod: P4/Xeon(TM) CPU On-Demand Clock Modulation available
[   40.304351] w83627ehf: Found W83627EHG chip at 0x290
[   40.304541] w83627ehf w83627ehf.656: Setting VID input voltage to VRM10
[   40.434569] Adding 2096440k swap on /dev/sdb7.  Priority:-1 extents:1 across:2096440k
[   41.025045] EXT3 FS on sdb6, internal journal
[   41.274630] device-mapper: uevent: version 1.0.3
[   41.274678] device-mapper: ioctl: 4.12.0-ioctl (2007-10-02) initialised: dm-devel@redhat.com
[   43.084559] PPP generic driver version 2.4.2
[   43.126879] NET: Registered protocol family 17
[   43.183850] NET: Registered protocol family 10
[   43.184235] lo: Disabled Privacy Extensions
[   44.769463] No dock devices found.
[   47.249220] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   47.249229] apm: overridden by ACPI.
[   53.315817] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   55.568705] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   56.439587] agpgart: Found an AGP 3.5 compliant device at 0000:00:00.0.
[   56.439617] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[   56.440648] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
[   57.866133] usbcore: registered new interface driver wacom
[   57.866145] /build/buildd/linux-2.6.24/drivers/input/tablet/wacom_sys.c: v1.47:USB Wacom Graphire and Wacom Intuos tablet driver
[   63.437692] agpgart: Found an AGP 3.5 compliant device at 0000:00:00.0.
[   63.437724] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[   63.437774] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
[   65.691263] eth0: no IPv6 routers present
[   69.414440] agpgart: Found an AGP 3.5 compliant device at 0000:00:00.0.
[   69.414470] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[   69.414517] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
[   76.182585] agpgart: Found an AGP 3.5 compliant device at 0000:00:00.0.
[   76.182613] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[   76.182660] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
[   87.895655] agpgart: Found an AGP 3.5 compliant device at 0000:00:00.0.
[   87.895684] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[   87.895731] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
[  103.604882] agpgart: Found an AGP 3.5 compliant device at 0000:00:00.0.
[  103.604911] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[  103.604959] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode

```

cat /var/log/syslog | grep GLib:
```
Feb  9 00:19:19 ugplinux gdmgreeter[31250]: GLib-GObject-CRITICAL: g_object_get_qdata: assertion `G_IS_OBJECT (object)' failed
Feb  9 00:19:19 ugplinux gdmgreeter[31250]: GLib-GObject-CRITICAL: g_object_set_qdata_full: assertion `G_IS_OBJECT (object)' failed

Feb  9 00:32:22 ugplinux gdmgreeter[402]: GLib-GObject-CRITICAL: g_object_get_qdata: assertion `G_IS_OBJECT (object)' failed
Feb  9 00:32:22 ugplinux gdmgreeter[402]: GLib-GObject-CRITICAL: g_object_set_qdata_full: assertion `G_IS_OBJECT (object)' failed

Feb  9 00:32:27 ugplinux gdm[430]: GLib-GObject-CRITICAL: g_object_get_qdata: assertion `G_IS_OBJECT (object)' failed
Feb  9 00:32:27 ugplinux gdm[430]: GLib-GObject-CRITICAL: g_object_set_qdata_full: assertion `G_IS_OBJECT (object)' failed

```


Just ask me if need other information for want know.

Thank for your attention and your time.;)

---

### Post by good5209 on 2010-02-19
push and cross finger...

---

