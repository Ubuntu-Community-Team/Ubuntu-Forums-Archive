---
title: "Auto-creation of mount points"
date: 2009-03-17
forum: General Help
---

### Post by ToniWiki on 2009-03-17
I would like to know if it's possible mount resources without a previous mount point creation. 

For instance, i don't have the mount point /media/smb (not exists) but with

$ mount -t cifs //192.168.0.1/public /media/smb

the mount point /media/smb is created, and with

$ umount /media/smb

the mount point /media/smb is destroyed.


Any ideas ?
Thanks.

---

### Post by eldragon on 2009-03-17
> **ToniWiki said:**
> I would like to know if it's possible mount resources without a previous mount point creation. 

For instance, i don't have the mount point /media/smb (not exists) but with

$ mount -t cifs //192.168.0.1/public /media/smb

the mount point /media/smb is created, and with

$ umount /media/smb

the mount point /media/smb is destroyed.


Any ideas ?
Thanks.

read a bit about bash scripting and edit .bashrc

that ought to do it.

---

### Post by ToniWiki on 2009-03-17
I search a general solution for anything mount need in a moment. The mount point should be created by a procedure associate to mount, not inside a bash script, because for instance, one day i need mount /media/smb, another day i need /media/peter, another day /media/coco, etc. Something temporal, for a while. 

A friend told me that he has a ArchLinux distro where it works but he don't know how is the mechanism.


Thanks and sorry, for my explanation, i only speak a little english.

---

