---
title: "Saving to floppy"
date: 2005-12-18
forum: Desktop Environments
---

### Post by %hMa@?b&lt;C on 2005-12-18
I have already mounted my floppy disk drive
but cant save to it, because it says that i dont have permission. when i look in properties, it says that only root can write and execute on that folder. How do i switch it

---

### Post by hajk on 2005-12-18
You may need to do some or all of the following:

Make sure you have the latest "pmount" package from backports installed.
Now, edit the floppy line in /etc/fstab to read

/dev/fd0 /media/floppy0  msdos  rw,users,noauto,umask=0000  0  0

You must also, for proper write permission, change the floppy mount point /media/floppy0 
(with no floppy mounted) with the command

sudo chmod 777 /media/floppy0

since otherwise the ``rw'' option in /etc/fstab won't take effect.

Mounting a floppy is now done by clicking on the Floppy Drive icon in Nautilus (Places/Computer).

---

