---
title: "USB Disk Write Error"
date: 2009-04-08
forum: General Help
---

### Post by measekite on 2009-04-08
I have a USB2 Hard Disk formatted for NTFS that has been working fine for over 3 years.

Now I am no longer able to **create new files**.  I cannot copy anything to this drive.  I can edit a file located on the drive and save (overwrite) it but cannot save under a new name.  I can read the files on the drive fine.

[COLOR=Red]**The error I get is:  ERROR Unsupported operation while copying**[/COLOR]

Does anybody know what to do?


Can you use fsck on an NTFS drive?  If so what is the syntax.  If not what command will do the job?

---

### Post by dcstar on 2009-04-09
> **measekite said:**
> I have a USB2 Hard Disk formatted for NTFS that has been working fine for over 3 years.

Now I am no longer able to **create new files**.  I cannot copy anything to this drive.  I can edit a file located on the drive and save (overwrite) it but cannot save under a new name.  I can read the files on the drive fine.

[COLOR=Red]**The error I get is:  ERROR Unsupported operation while copying**[/COLOR]

Does anybody know what to do?


Can you use fsck on an NTFS drive?  If so what is the syntax.  If not what command will do the job?

If you do a search you should find many posts explaining how to do a fsck on the drive.

Also, these devices only have a finite life, it could be broken now.

---

### Post by measekite on 2009-04-09
> **dcstar said:**
> If you do a search you should find many posts explaining how to do a fsck on the drive.

Also, these devices only have a finite life, it could be broken now.

While I do not know what caused the free space to become allocated (that was the problem) I did find out that fsck will not work on an ntfs drive so I booted Windows and ran chkdsk /f driveletter: and the problem was corrected.  When I returned to Ubuntu all was fine.

I sure would have like to know how it got that way to begin with.  It appears I cannot get rid of Windows until I get rid of ntfs.

---

