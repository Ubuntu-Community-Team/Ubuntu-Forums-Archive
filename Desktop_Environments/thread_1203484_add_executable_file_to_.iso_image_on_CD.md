---
title: "add executable file to .iso image on CD"
date: 2009-07-03
forum: Desktop Environments
---

### Post by raymondvillain on 2009-07-03
I'm trying to salvage an XP installation that got messed up when installing Jaunty.

I have downloaded a bootable DOS and burned the .iso to a CD.

I need to add another (Windows) executable to the disk, NTFSDOS**.exe.

Can't drag and drop, or use terminal.  Apparently when one burns an ISO image to a CD, the disk is marked "read only".

Is there a way to add my executable to the burn process?  Or is there another way to get it on there?

---

### Post by natravis on 2009-07-03
Using a program like "Iso Master" or Archive Manager (which should be on your default Jaunty installation) you can edit .iso files. Just rt-click on your .iso, select open with Archive Manager (not Archive Mounter) and add the file you need, then save and burn new disc.

---

### Post by raymondvillain on 2009-07-03
I can't get it to work with archive manager.  It keeps saying "destination is read-only".

Is "ISO master" available online?

P. S.  I just added it using Applications>add/remove.

---

### Post by natravis on 2009-07-04
> **raymondvillain said:**
> I can't get it to work with archive manager.  It keeps saying "destination is read-only".

Is "ISO master" available online?

P. S.  I just added it using Applications>add/remove.

You were probably trying to add it to the CD you had already created. You need to add it to an .iso file on your computer then burn the edited one to a disc. You can make an .iso file from a current CD if you want to go about it that way. Keep in mind that .exe files do not work the same way in Ubuntu as they do in Windows environments.

---

