---
title: "Samba mounting and hibernation"
date: 2007-02-12
forum: Desktop Environments
---

### Post by Sirkent on 2007-02-12
I mount several samba shares by default (via fstab), but after hibernation those shares no longer appear to work for quite some time. I often have to manually unmount and remount a share. Is there a way around this, or to automatically unmount/remount after hibernation?

---

### Post by g8m on 2007-02-12
Create a script under acpi.

	/etc/acpi/suspend.d/30-smbfs-umount.sh
	

Let it unmount all shares if you go to suspend

	# Unmount SAMBA shares - open files on these don't survive suspending.
	umount -a -l -t smbfs

---

### Post by ltmon on 2007-02-12
Another way is to edit the file /etc/default/acpi-support and change the line:

STOP_SERVICES="mysql"

to:

STOP_SERVICES="mysql umountnfs.sh"

This will cause "/etc/init.d/umountnfs.sh stop" to be called when you hibernate, which will cause all mounted networked file systems to be unmounted.

---

