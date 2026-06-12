---
title: "umount external drives missing and failure with crypted external drives"
date: 2010-06-01
forum: Desktop Environments
---

### Post by alterpinguin on 2010-06-01
umount external drives missing and failure with crypted external drives
-
Its ubuntu 10.04 and
i did not have this problem with 9.04.
In 10.04 there is only the menu-entry to "securely remove" an external drive. Not any more to unmount it. This fails if there are more partitions on the external storage mounted and if there are encrypted partitions mounted of this external usb-storage.
Next, if multiple partitions from one usb-storage are mounted, the "remove disk" trys to powerdown the external usb-storage and fails if the mounted partitions cannot unmounted and for crypted partitions closed (the map-device).
The only workaround till now is to use manual steps like this way (for me):
1.look for the name of the mounted mapper device with "mount"
2. umount /dev/mapper/name_of_the_mapper_device
3. cryptsetup luksClose   name_of_the_mapper_device
---
if i umount only the mount in /media/-label-name-of-partition
i end up with a luksDevice mapped to "Null" device and cannot remove/close
it. I had to reboot to clean this entry.
-
One may call this workaround as partial solving my problem. But the changes are in the new way to power-down the external storages as a default in the desktop-setup.
Or does
anyone know a way to enable the "unmount" menu-entry like it is shown in the menu for build-in storage-devices (like sda5, sda6, sda7 ...sdb1, sdb2... and so on)?

---

