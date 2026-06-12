---
title: "CD mounts but no desktop icon"
date: 2006-06-08
forum: Desktop Environments
---

### Post by pele325 on 2006-06-08
I am using Ubuntu 6.06 (Dapper) with Gnome.  I have two DVD Drives installed.  Both work fine, but when I insert a CD or DVD into the master drive, no icon appears on the Desktop.  It automounts fine and can be accessed from /media/cdrom, but no icon gets created.  Also, for some reason pushing the eject button on the drive does not unmount and eject the disc, I have to do a umount myself first.

On the secondary drive, everything works as expected.  I insert a disc, it gets automounted and an icon gets created on the desktop.  I push the eject button on the drive and it ejects.  So it seems this is only a problem with the master drive.

I double checked gconf and the option for displaying mounted drives on the desktop is selected, so I'm not sure why the behavior is different between the two drives.

Any help would be appreciated.

---

### Post by meng on 2006-06-08
Don't know the answer (sorry) but I have a question for you: does the drive appear under the Places menu?

---

### Post by pele325 on 2006-06-08
Thanks for the question.  It does not appear on the Places menu or on the sidebar of the file browser.  Discs inserted in the secondary drive show up in both of these places though.

---

### Post by pele325 on 2006-06-08
Another quick update.  I noticed today that desktop icons actually DO appear for CDs, but just not for DVDs.  On the secondary drive, both CDs and DVDs show up on the desktop, but with the primary, it's only CDs.  I don't even know what configuration files to check for this, so if anyone has anny suggestions at all I would be very appreciative.  Thanks!

---

