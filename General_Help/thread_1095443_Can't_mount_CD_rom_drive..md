---
title: "Can't mount CD rom drive."
date: 2009-03-13
forum: General Help
---

### Post by racerraul on 2009-03-13
Ok I think I have the hang of this but need some help.

If I understand this right, I need to use the mount command, specify the dev I need to use and assign it to a folder to the contents..

The problem is this...

My /etc/fstab says that my CDROM is /dev/scd0 and that is mounted to /media/cdrom0.  Or should be mounted there...

So I try to mount /dev/scd0 /media/cdrom0 and it tells me the device /dev/sdc0 does not exist.

Indeed it does not.

How do I find out where it is?

---

### Post by racerraul on 2009-03-14
Anyone know a command so that I can see what devices Linux has found?
It doesn't look like Ubuntu Studio ever saw the optical drives for me to mount.

---

### Post by racerraul on 2009-03-14
I found my problem...

Turns out that when my son & I replaced the IDE cables with nice round ones, we forgot to disconnect the cd that went bad in the chain... its jumpers were conflicting with the other drive even though it was off...

Disconnected it and now I see the drive in /etc/fstab

---

