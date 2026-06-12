---
title: "sdhc not automount besides the first time."
date: 2008-07-25
forum: Desktop Environments
---

### Post by slchen1013 on 2008-07-25
Hi, All:

When I plug my SDHC card, remove it (both unmount and not umount first), and plug it again, gnome will not mount it automatically sometimes.

I need to rmmod mmc_block manually then it will automount again.

In the case gnome automounts, the hal-device give the folloing message:

0: udi = '/org/freedesktop/Hal/devices/volume_uuid_7C53_160D'

 volume.partition.label =   (string)
 volume.partition.uuid =   (string)
 volume.partition.flags = {  } (string list)
 linux.hotplug_type = 3  (0x3)  (int)
 volume.ignore = false  (bool)
 storage.model =   (string)
 org.freedesktop.Hal.Device.Volume.method_names = { 'Mount', 'Unmount', 'Eject' } (string list)
 org.freedesktop.Hal.Device.Volume.method_signatures = { 'ssas', 'as', 'as' } (string list)
 info.product = 'Volume (vfat)'  (string)
 org.freedesktop.Hal.Device.Volume.method_argnames = { 'mount_point fstype extra_options', 'extra_options', 'extra_options' } (string list)
 info.udi = '/org/freedesktop/Hal/devices/volume_uuid_7C53_160D'  (string)
 org.freedesktop.Hal.Device.Volume.method_execpaths = { 'hal-storage-mount', 'hal-storage-unmount', 'hal-storage-eject' } (string list)
 info.category = 'volume'  (string)
 volume.mount.valid_options = { 'ro', 'sync', 'dirsync', 'noatime', 'nodiratime', 'noexec', 'quiet', 'remount', 'exec', 'utf8', 'shortname=', 'codepage=', 'iocharset=', 'umask=', 'dmask=', 'fmask=', 'uid=', 'flush' } (string list)
 info.capabilities = { 'volume', 'block' } (string list)
 volume.unmount.valid_options = { 'lazy' } (string list)
 block.storage_device = '/org/freedesktop/Hal/devices/storage_serial_0x00011406'  (string)
 volume.fstype = 'vfat'  (string)
 volume.fsusage = 'filesystem'  (string)
 volume.fsversion = 'FAT32'  (string)
 volume.uuid = '7C53-160D'  (string)
 volume.label =   (string)
 info.interfaces = { 'org.freedesktop.Hal.Device.Volume' } (string list)
 volume.mount_point = '/media/disk'  (string)
 volume.is_mounted = true  (bool)
 volume.is_mounted_read_only = false  (bool)
 volume.linux.is_device_mapper = false  (bool)
 linux.sysfs_path = '/sys/block/mmcblk0/mmcblk0p1'  (string)
 volume.is_disc = false  (bool)
 info.parent = '/org/freedesktop/Hal/devices/storage_serial_0x00011406'  (string)
 volume.is_partition = true  (bool)
 volume.partition.number = 1  (0x1)  (int)
 volume.block_size = 512  (0x200)  (int)
 volume.num_blocks = 15743637  (0xf03a95)  (int)
 volume.size = 8060742144  (0x1e0752a00)  (uint64)
 block.device = '/dev/mmcblk0p1'  (string)
 volume.partition.start = 32256  (0x7e00)  (uint64)
 block.major = 179  (0xb3)  (int)
 volume.partition.media_size = 8068268032  (0x1e0e80000)  (uint64)
 block.minor = 1  (0x1)  (int)
 volume.partition.scheme = 'mbr'  (string)
 block.is_volume = true  (bool)
 volume.partition.type = '0x0b'  (string)


the lshal --monitor gives: 22:15:59.284: storage_serial_0x00011406 added 22:15:59.456: volume_uuid_8f674bee_1128_4379_b061_c94c5995f8e0 added 22:16:00.007: volume_uuid_8f674bee_1128_4379_b061_c94c5995f8e0 property volume.mount_point = '/media/disk' 22:16:00.022: volume_uuid_8f674bee_1128_4379_b061_c94c5995f8e0 property volume.is_mounted = true

/media/.hal-mtab contains:

/dev/mmcblk0p1 1000 0 ext2 nosuid,nodev,uhelper=hal /media/disk



In the case gui will NOT automount the sdhc card, hal-device gives:

0: udi = '/org/freedesktop/Hal/devices/pci_1106_95d0_mmc_host_mmc_card_rca45928'

 mmc.date = '01/2008'  (string)
 mmc.hwrev = 1  (0x1)  (int)
 linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:0c.0/mmc_host/mmc0/mmc0:b368'  (string)
 info.subsystem = 'mmc'  (string)
 info.vendor = 'Unknown (28)'  (string)
 mmc.fwrev = 0  (0x0)  (int)
 info.parent = '/org/freedesktop/Hal/devices/pci_1106_95d0_mmc_host'  (string)
 info.product = 'SDC'  (string)
 mmc.serial = 70662  (0x11406)  (int)
 mmc.rca = 45928  (0xb368)  (int)
 linux.hotplug_type = 2  (0x2)  (int)
 info.udi = '/org/freedesktop/Hal/devices/pci_1106_95d0_mmc_host_mmc_card_rca45928'  (string)
 mmc.cid = '1c535653444320201000011406008100'  (string)
 linux.subsystem = 'mmc'  (string)
 info.linux.driver = 'mmcblk'  (string)
 mmc.csd = '400e00325b5900003c1c7f800a400000'  (string)
 mmc.type = 'SD'  (string)
 mmc.scr = '0235000000000000'  (string)
 mmc.vendor = 'Unknown (28)'  (string)
 mmc.oem = 'Unknown (21334)'  (string)

lshal --monitor gives:

22:16:28.225: pci_1106_95d0_mmc_host_mmc_card_rca45928 added

/media/.hal-mtab contains nothing.

Is there any hint about this issue? Thanks very much.

slchen

---

### Post by teachop on 2008-08-23
I am bumping this because I have the same problem.  When I put in my SD card, it automounts the first time.  After I unmount it (that is the right thing for eject I assume) then it will not longer automount.  Anybody know how to address this?  Thanks.

---

### Post by GoldWing on 2008-09-08
somebody has a solution for this already ?

---

