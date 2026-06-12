---
title: "Ubuntu server 2012 x64 istallation can't read  hard drive on dell poweredge 1900"
date: 2013-01-08
forum: Dell Ubuntu Support (CLOSED)
---

### Post by toloykhan on 2013-01-08
Hello...
Am trying to install ubuntu server 2012 x64 on dell poweredge 1900, the installation process went fine untill  the partioning part where it can't be able to recognize the hard drives all i can get is 
iSCSI login and 
undo partioning
finish and write changes to disk
help plz...

---

### Post by tgalati4 on 2013-01-08
I assume the drives are to be wiped clean so you are performing a fresh installation.  Boot into the RAID BIOS.  There should be an option to wipe the drive--one at a time.  Now try the installation.

---

### Post by toloykhan on 2013-01-08
> **tgalati4 said:**
> I assume the drives are to be wiped clean so you are performing a fresh installation.  Boot into the RAID BIOS.  There should be an option to wipe the drive--one at a time.  Now try the installation.

thanx for replay
actually there are win server 2000 already installed, but who want that crap... Yes i need to wipe the drive
i well try that and post back

---

### Post by tgalati4 on 2013-01-08
Don't forget to go to the Dell website and burn a bootable CD with the latest BIOS and RAID BIOS and flash your machine.  It will make the machine run better and make installation easier.

---

