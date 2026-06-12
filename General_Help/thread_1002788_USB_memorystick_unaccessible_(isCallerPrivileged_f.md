---
title: "USB memorystick unaccessible (isCallerPrivileged failed) workaround"
date: 2008-12-05
forum: General Help
---

### Post by tjaf on 2008-12-05
I have kubuntu 8.04.1 (fully upgraded) and around september 2008, the media automount stopped working. Whenever a memorystick is inserted, it is detected, the appropriate icon appears, but it is unaccessible. Doubleclicking opens dolphin which displays the error message:

```
isCallerPrivileged() failed
```

The bug has been reported previously, but so far no solution seems to present itself. From my understanding it is somewhere a problem of permissions according to PolicyKit and dbus/hal.

Anyhow, a simple (but somewhat dirty) workaround is to simply add the device to fstab, so that any user can mount it the old fashioned way.

- **Find out the device node**:

insert the stick, and wait untill the icon appears. Just hover the mouse over the icon and it will display this (at least in kde). Alternatively dmesg will give you the info as well. In my case, the output looks like this:

```

[ 7824.686687] sd 10:0:0:0: [sde] Write Protect is off
[ 7824.686692] sd 10:0:0:0: [sde] Mode Sense: 00 00 00 00
[ 7824.686695] sd 10:0:0:0: [sde] Assuming drive cache: write through
[ 7824.686701]  sde: sde1
[ 7824.715320] sd 10:0:0:0: [sde] Attached SCSI removable disk
[ 7824.715373] sd 10:0:0:0: Attached scsi generic sg6 type 0

```

The relevant part is sde1. In my case, the memorystick is mapped to /dev/sde and the first (and only partition on it is /dev/sde1)

- **Edit /dev/fstab**:

Edit fstab e.g.:

```
sudo kate /etc/fstab
```

and add the following line at the bottom:

```
/dev/sde1       /media/stick   vfat user,noauto,exec 0       0

```

Be sure to change the device node to the proper one. Also change the filesystem if it is not formatted in vfat.

- **Create mount point**

```
sudo mkdir /media/stick
sudo chown root\:users /media/stick
sudo chmod g+w /media/stick
```

And that's it. From now on, you should be able to use the stick as a regular user and have read/write permissions on it. Make sure to unmount the stick before removing it (right click on the icon and safely remove).

This is a dirty workaround because it will only work for sticks that are mapped to (in my case) sde. If you insert a second stick, it will be mapped to sdf and off course that won't work unless you add again a new line in fstab. The whole point of using hal and dbus is obvioulsy to avoid this fuss...

A similar approach can be followed for cdrom and dvd drives.

If someone knows a proper fix, please let me know.

Regards,
Nick

---

