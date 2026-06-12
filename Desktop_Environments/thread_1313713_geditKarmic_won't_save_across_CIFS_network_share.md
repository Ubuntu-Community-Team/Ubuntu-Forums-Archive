---
title: "gedit/Karmic won't save across CIFS network share"
date: 2009-11-04
forum: Desktop Environments
---

### Post by dmclennan on 2009-11-04
Just upgraded to Ubuntu 9.10, Karmic and I'm finding problems with gedit.  I have a Windows 2008 server network share with Ubuntu accessing a mount setup in fstab using CIFS.  With gedit, I can browse, open and edit files on the network share; however, I can not save the file. gedit returns a red alert box, with 'Could not find the file /mnt/server/filename.  Please check that you typed the location correctly and try again.'

This worked fine in Ubuntu 9.04.  There are numerous bugs and prior debates about using gedit over SMB, CIFS, NTFS, etc., with what appears to be no solution offered.  There are suggested code changes that may have been lost between gedit in 9.04 and 9.10.

I've used CIFS to access the network share reliably for over 6 months with Ubuntu 9.04 and CIFS file access seems fine with Ubuntu 9.10.  For the record, OpenOffice can read/write to/from the same network drive.  This problem appears to be isolated to gedit.

Any suggestions/help? Thank you

---

### Post by fcornillie on 2009-11-10
Similar problem here, though I don't get an error message when saving from Gedit. Gedit just freezes upon saving.

Saving to a network drive through CIFS/SMB works perfectly with other editors (Scite, Geany) or OpenOffice.

---

### Post by jmr on 2009-11-13
This is quite an old problem, and there are bugs reported with the problem pinpointed to a particular strategy for dealing with backup files.  It's not absolutely clear whom to blame.  Anyway, suggested patches for gedit would solve it, but nothing has changed...

I noticed it using Ubuntu 6.06, gedit 2.14, over a CIFS mounted network drive.  My fix was downgrading to gedit 2.12.

I'm now using Ubuntu 9.04, current gedit, and the CIFS mounted disk is a NetApp file server.  The problem persists.  I'd like to find out if changing some configuration in the CIFS client or in the file server would solve it.

Do you know which kind of file server you're using?

João R.

---

### Post by Boondoklife on 2009-11-13
I have seen this issue myself but not often maybe one out of every 30 saves I will get that error and just have to click save again and it is fine. I am using karmic and the server is a WD MyBook running samba.

I have not made any tweaks on the ubuntu side and just use the network browser to get to the share an mount it.

---

### Post by aedwards on 2010-04-26
just wondering if you found a resolution to this issue.  Having same problem here using CIFS shares via automount.

---

