---
title: "Can't umount cdrom in multi-user"
date: 2009-05-21
forum: General Help
---

### Post by Mithrandir95 on 2009-05-21
In a multi-session environment (multiple users) if for example I put in a cd-rom into the drive on one session then switch sessions, in the second session I can't unmount the cd without using sudo.

I get that this is 'propper' behaviour.  My question is, can I change this so that any user at the console can eject removable media?

System -> Administration -> Authorizations seems to allow that capability specifically "org->hal->storage->Unmount file systems mounted by other users" or "org->hal->storage->Eject removable media" but no matter what permissions I set Implicit or Explicit it doesn't seem to have any affect.

Anyone know how this can be done?

Thanks in advance.

---

### Post by lensman3 on 2009-05-22
From a command prompt do:

"umount -f <mnt/pt"

where <mnt/pt> is determined from the "du" command.  The "-f" is "force a umount".  Sometimes this works.  You need to be superuser.

---

