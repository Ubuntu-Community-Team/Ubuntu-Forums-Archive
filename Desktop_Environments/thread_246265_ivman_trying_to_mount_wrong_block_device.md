---
title: "ivman trying to mount wrong block device"
date: 2006-08-29
forum: Desktop Environments
---

### Post by beamish on 2006-08-29
Hi All,
I have a USB hard drive which is not being mounted properly by ivman. The device coming back from hal is /dev/sde, which ivman attempts to mount. Unfortunately, it is /dev/sde1 which must be mounted. Manually mounting the slice works fine.
Can anyone give me any pointers on where I should be looking, and how this is supposed to work?
Thanks.
```
IvmConfigCommon.c:131 (ivm_device_is_mountable) /org/freedesktop/Hal/devices/volume_uuid_4346_B229 is /dev/sde
IvmConfigCommon.c:233 (ivm_device_is_mountable) /dev/sde appears to be mountable
manager.c:686 (ivm_media_changed) Attempting to mount /dev/sde
manager.c:493 (ivm_run_command) Running: /usr/bin/pmount -t vfat  /dev/sde  usbdisk || /usr/bin/pmount -t vfat  /dev/sde
manager.c:493 (ivm_run_command) Running: MOUNT=/dev/sde; kfmclient openURL media:/${MOUNT#/*/}
mount: /dev/sde: can't read superblock
mount: /dev/sde: can't read superblock

```

---

### Post by beamish on 2006-08-29
I have done more investigation on this.
I inserted a known working usb stick into a port, piped lshal into a file, replaced it with the other, not-working drive, and diff'ed the outputs.
The significant differences were:

Working drive:
1. volume.partition.number = 1  (0x1)  (int)
2. volume.is_mounted = true  (bool)
3. volume.mount_point = '/media/iAUDIO'  (string)
4. volume.label = 'iAUDIO'  (string)
5. volume.uuid = ''  (string)
6. linux.sysfs_path_device = '/sys/block/sde/sde1'  (string)
7. linux.sysfs_path = '/sys/block/sde/sde1'  (string)
8. info.addons = {'hald-addon-storage'} (string list)
9. storage.removable = true  (bool)
10.storage.media_check_enabled = true  (bool)

Non-Working drive:
1. <no entry>
2. volume.is_mounted = false  (bool)
3. volume.mount_point = ''  (string)
4. volume.label = ''  (string)
5. volume.uuid = '4346-B229'  (string)
6. linux.sysfs_path_device = '/sys/block/sde/fakevolume'  (string)
7. linux.sysfs_path = '/sys/block/sde/fakevolume'  (string)
8. <no entry>
9. storage.removable = false  (bool)
10.storage.media_check_enabled = false  (bool)

From this, it seems that the partition is not being detected by hal, and ivman is attempting to mount the parent block device.
Will look a bit deeper....

---

### Post by beamish on 2006-08-30
Well, here I am answering my own question again!
It seems as though my USB drive was reporting itself incorrectly, because upon a re-format, all was sweet, and it now loads correctly. Drastic fix, but there you go.

---

