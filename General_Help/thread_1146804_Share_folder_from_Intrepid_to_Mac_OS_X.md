---
title: "Share folder from Intrepid to Mac OS X"
date: 2009-05-02
forum: General Help
---

### Post by cupoange on 2009-05-02
I have an external USB drive connected to my Ubuntu desktop.  I'm primarily using it to back up all my computers.  I've set it up to back up the desktop, my laptop running Ubuntu Jaunty, and I'm trying to set it up to back up via Time Machine my Macbook pro.  I can connect to the desktop just fine from the Mac, and see all the shared drives.  I can edit files/folders on all the shares, except for the external USB.  I've checked file permissions/owner and everything seems good.  I can edit files from my ubuntu laptop, just not the mac to that drive.  i'm not sure where else to check.  Specifically what I am trying is to just create a new folder on that shared drive and the Mac tells me I don't have enough priveledges....though creating a folder on another drive works just fine.  any help is appreciated.

EDIT:  I figured it out (kinda dumb).  All I had to do was right-click on the folder in nautilus and select share folder/allow users to write/allow guest access.  I only had one of the subfolders selected for write access (the one I used to backup the laptop)

---

### Post by SentientFluid on 2009-05-03
Time Machine won't work unless the drive had the correct partition table AND be formatted as Mac OS Extended (Journaled).

For your Macbook Pro it will need to have a GUID partition table.
Older PPC processor Macs need to use APM (Apple Partition Map).

IIRC, Ubuntu can't read/write Mac OS Extended partitions natively.  I don't own a Mac so I've never tested it so I could be wrong.

---

### Post by cupoange on 2009-05-03
I understand that, I can create a new partition.  But that doesn't really answer my question, which has to do with write access from the Mac to the Linux external shared drive.  Until I can get write access nothing will work anyway.

Oh and I'm pretty sure that's not completely correct.  There are ways to have Time Machine backup to a non-Journaled partition.

---

### Post by SentientFluid on 2009-05-04
> **cupoange said:**
> Oh and I'm pretty sure that's not completely correct.  There are ways to have Time Machine backup to a non-Journaled partition.

Sure there may be ways to get it started without journaling however I guarantee you that Time Machine will fail or your backups will have major errors at some point.  Not to mention that Apple doesn't support Time Machine on a non-journaled system.

---

