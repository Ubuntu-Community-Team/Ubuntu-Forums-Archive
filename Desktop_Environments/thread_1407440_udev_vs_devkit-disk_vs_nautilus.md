---
title: "udev vs devkit-disk vs nautilus"
date: 2010-02-15
forum: Desktop Environments
---

### Post by samarium on 2010-02-15
My Nautilus "removable" partition list when running jaunty was manageable at about 8.  When I upgraded to karmic, it suddenly expanded to about 50 when it decided to include all the zfs partitions that it had no idea how to manage and/or mount.  50 paritions in the removable list is unmanageable, so it was off down the rabbit hole trying to find out how to deal with it.

Eventually o I added a rule to /etc/udev/rules.d/hide-zfs.conf:

ENV{ID_FS_TYPE}=="zfs", ENV{DKD_PRESENTATION_HIDE}="1", ENV{DKD_PRESENTATION_NOPOLICY}="1"

and did some testing with "udevadm test", and finally did "/etc/init.d/udev restart" however I haven't figured out how to convince devkit-disks to rescan and reinterpret the disk, nor how to get nautilus to do so either.  Maybe if devkit-disks rescanned, it would pass the update on to nautilus.

Killing devkit-disks-daemon doesn't see to work, even though the doco says it should be respawned by dbus if required.

Rebooting does solve that immediate problem, however I would like to know how to signal disk parition changes up through devkit-disks and through to nautilus.  Having to reboot every time I an a udev rule is ridiculous, especially given how long the bios takes to load all the option roms.

Any feedback would be appreciated, thanks.

---

