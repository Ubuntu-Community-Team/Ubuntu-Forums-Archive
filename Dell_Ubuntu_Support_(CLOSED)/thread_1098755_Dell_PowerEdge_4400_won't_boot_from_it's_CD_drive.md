---
title: "Dell PowerEdge 4400 won't boot from it's CD drive"
date: 2009-03-17
forum: Dell Ubuntu Support (CLOSED)
---

### Post by RoboJ1M on 2009-03-17
Hi,

We've got an old Dell PowerEdge 4400 server which we're going to run trac and svn on.

But I can't get it to boot the ubuntu install CD.

I've set the BIOS boot order to:

Floppy
SCSI CD-ROM on AIC 7880
C:

With the device priority set to:

BIOS devices
AIC 7899

In the firmware settings for the AIC 7880 controller I've reset to default settings with F6 and the set the boot device to #5 (where the CD drive is)

But:

The PC tried to boot from the floppy, then can't find anything else and you're left at the Hit F1 to Retry screen.

Booting from C: works as well (if it's plugged in, which it isn't at the moment)

Apparently this all worked fine a few months ago (booting from the Dell OpenManage CD), but now it doesn't. It's unknown if the CD-ROM drive is dead.

Does anybody else know of any secret voodoo to make this stupid thing boot off of a CD drive?

Thanks,

J1M.

---

### Post by armandh on 2009-03-18
be sure the CD drive is on the primary eide line

---

### Post by RoboJ1M on 2009-03-18
Thanks, but it's a SCSI CD-ROM on the AIC 7880 controller.

---

### Post by RoboJ1M on 2009-03-18
Managed to boot a previous installation of Dell OpenManage on one of the other hard disks we put it from a different server.

Hardware test says CD ROM is alive, but reports every disk as empty.

J1M.

---

### Post by armandh on 2009-03-18
try a different cd drive existing one may be bad.
if there is an eide line you could test with a eide drive
[rather than spend for a $cuzzy CD that may not be needed]
and I would move the floppy down the list to be sure.

It takes about 2 years of regular use and CD drives wear out.
in my experience

---

### Post by RoboJ1M on 2009-03-18
No ide channel on the mobo, scsi only.
We have a second scsi CD-ROM to test with though.

---

