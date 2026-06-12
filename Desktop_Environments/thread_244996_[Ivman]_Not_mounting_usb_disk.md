---
title: "[Ivman] Not mounting usb disk"
date: 2006-08-27
forum: Desktop Environments
---

### Post by l_b on 2006-08-27
Hi,

I installed ivman and I thought it would take care of the automatic mounting of usb disks. But I installed it, and it didn't happen. I get this output when I start ivman:

```
manager.c:1340 (do_startup_configure) Directory /etc/ivman/ will be used for configuration files.
manager.c:259 (set_mount_command) No mount command was specified in IvmConfigBase.xml.  Ivman will try to automatically detect the command to use. If Ivman incorrectly detects the program(s) available on your system, first make sure the program(s) are in the default shell PATH, then please report it as a bug.
manager.c:291 (set_mount_command) pmount-hal detection skipped, as we are a root instance of Ivman.  pmount-hal is only used for user instances.
manager.c:333 (set_mount_command) pmount accepts -u <umask>
manager.c:336 (set_mount_command) pmount was found on your system. It will be used for mounting.
manager.c:768 (ivm_run_command) Running: echo 0 > /proc/sys/dev/cdrom/lock
/bin/sh: /proc/sys/dev/cdrom/lock: No such file or directory
manager.c:1211 (setupHAL)  Running through rules for every current property.
IvmConfig/IvmConfigCommon.c:152 (ivm_device_is_mountable) UDI /org/freedesktop/Hal/devices/volume_part1_size_98671104 is device /dev/hda1
IvmConfig/IvmConfigCommon.c:215 (ivm_device_is_mountable) Device /dev/hda1 won't be mounted because no mount policy was specified on volume and mount policy on parent device says not to mount
IvmConfig/IvmConfigCommon.c:152 (ivm_device_is_mountable) UDI /org/freedesktop/Hal/devices/volume_uuid_f6e01031_691d_4e30_a2a3_39660c6107b7 is device /dev/hda2
IvmConfig/IvmConfigCommon.c:292 (ivm_device_is_mountable) Device /dev/hda2 appears to be mountable
IvmConfig/IvmConfigCommon.c:152 (ivm_device_is_mountable) UDI /org/freedesktop/Hal/devices/volume_uuid_d564f885_3194_4183_8041_3ec2955e7e52 is device /dev/hda3
IvmConfig/IvmConfigCommon.c:292 (ivm_device_is_mountable) Device /dev/hda3 appears to be mountable
IvmConfig/IvmConfigCommon.c:152 (ivm_device_is_mountable) UDI /org/freedesktop/Hal/devices/volume_uuid_97d4345b_d21d_41d1_b292_c6c360dc38c5 is device /dev/hda4
IvmConfig/IvmConfigCommon.c:292 (ivm_device_is_mountable) Device /dev/hda4 appears to be mountable
IvmConfig/IvmConfigCommon.c:152 (ivm_device_is_mountable) UDI /org/freedesktop/Hal/devices/storage_serial_VNR43EC4CEAVUM is device /dev/hda
IvmConfig/IvmConfigCommon.c:172 (ivm_device_is_mountable) Device /dev/hda can't be mounted because it is not a volume
IvmConfig/IvmConfigCommon.c:152 (ivm_device_is_mountable) UDI /org/freedesktop/Hal/devices/volume_uuid_4c9019f3_e55f_4469_98e7_9f8e43370fd6 is device /dev/sda1
IvmConfig/IvmConfigCommon.c:292 (ivm_device_is_mountable) Device /dev/sda1 appears to be mountable
IvmConfig/IvmConfigCommon.c:152 (ivm_device_is_mountable) UDI /org/freedesktop/Hal/devices/storage_serial_HDT72251_6DLAT80_77783C87 is device /dev/sda
IvmConfig/IvmConfigCommon.c:172 (ivm_device_is_mountable) Device /dev/sda can't be mounted because it is not a volume
manager.c:1387 (main) ivman 0.6.10, http:/ivman.sourceforge.net
manager.c:1392 (main) Compiled against HAL 0.5.x or later
manager.c:1396 (main) Running in system mode.
daemonize.c:39 (daemonize) Forking to background...

```

I even had to start ivman myself. No init.d script! Is this package maintained by ubuntu? Because, I think, it's not as the same quality as the other ubuntu software.

Can anybody explain how I can add support for auto-mounting this device? Thanks in advance!

---

### Post by fakie_flip on 2006-08-27
If you want automatic mounting of your usb disk when your computer boots up, then edit the /etc/fstab. You shouldn't need any special software to get your usb disk to automount in Ubuntu. I believe Gnome in Ubuntu comes with software that autmatically mounts removable drives when you plug them in.

---

### Post by graphius on 2006-08-27
I have a similar problem.
when I first installed Ubuntu, my usb thumbdrives automounted. I set up my wireless network, and now my drives will not mount at all.
I have read a lot of forums, but nothing seems to work. I really don't want to have to reinstall and lose all my customization.

---

### Post by fakie_flip on 2006-08-28
That might be a bug in Ubuntu. Have you reported the bug to [https://launchpad.net/distros/ubuntu](https://launchpad.net/distros/ubuntu) , so the developers can fix this problem with an update or have it fixed in the next release of Ubuntu. If it's not a bug, they may reply with a solution to your problem. I've recieved email when I submitted bugs before.

---

### Post by fakie_flip on 2006-08-28
Gnome volume manager is responsible for automounting a usbdisk in Ubuntu. You may want to have a look at this howto to see where your configuration is wrong. Then you can correct the problem.
[http://gentoo-wiki.com/HOWTO_gnome-volume-manager](http://gentoo-wiki.com/HOWTO_gnome-volume-manager)

---

