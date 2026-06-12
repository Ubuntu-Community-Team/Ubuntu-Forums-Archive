---
title: "How to mount flash drive as read-only"
date: 2009-03-13
forum: General Help
---

### Post by rbc on 2009-03-13
I would like to mount a flash drive/thumb drive as read-only. I know that I can go into gconf-editor/apps/nautilus/preferences and uncheck “automount”, then mount the drive as read-only via terminal. But what file, similar to fstab, I guess, dictates how and where removable drives are mounted?

---

### Post by kanikilu on 2009-03-13
I think you can still use fstab. I would just add it by UUID so as to not cause confusion in the future.

For example:

Plug the flash drive in and find the device name: ```
dmesg | tail
```

Once you have the device name, let's say it's /dev/sdb1 in this case, find the UUID that corresponds to sdb1: ```
ls -lA /dev/disk/by-uuid/
```

Now you can edit fstab with the options you want and just refer to it by the id (UUID=...).

Or are you saying you want to mount *all* flash drives as read-only? In that case, I'm not sure what to suggest, but fstab is probably not practical...

---

### Post by rbc on 2009-03-13
If this were an external hard drive that would always remain attached to the computer, I would include it in fstab, but it's just a thumb drive, and I don't want startup to hang because I forget to insert it

---

### Post by Neo_The_User on 2009-03-13
using "ro" mounts as read only.

Try this:
```

man mount

```

In terminal.

---

### Post by rbc on 2009-03-13
Thanks, Neo, for the reply. I know the -ro option is to mount as read-only, but my question is....is there an fstab type file for removable where I can include that option, instead of doing it from terminal every time

---

### Post by heindsight on 2009-03-13
In GNOME, you can insert the drive, let it be automounted.
Right click on it's icon on the desktop (or go to Places>Computer and right click on the flash drive's icon there) and select Properties.
Go to the Volume tab, click on the little arrow next to Settings and enter ```
ro
```
in the Mount Options field.

Now unmount the device and next time you insert it, it should automatically be mounted read-only.

If you go into the gconf-editor (Applications>System Tools>Configuration Editor) you'll see that an entry for the flash drive was created at:
/system/storage/volumes/_org_freedesktop_Hal_devices_volume_uuid_X
where X is the uuid of your flash drive file system.
Under that entry you'll see a mount_options key with the value "[ro]"
So, if you know the uuid of the drive's filesystem you can manaully create such a gconf entry to set its mount options...

---

### Post by rbc on 2009-03-13
Wow. Not exactly the easy answer I was looking for, but it works, especially if I wanted the read-only option to be unique to one flash drive. Thanks heindsight. Is the "Mark thread as solved" still broken or am I missing something?

---

