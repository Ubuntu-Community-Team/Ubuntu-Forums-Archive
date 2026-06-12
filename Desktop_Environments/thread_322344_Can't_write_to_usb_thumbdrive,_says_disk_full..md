---
title: "Can't write to usb thumbdrive, says disk full."
date: 2006-12-20
forum: Desktop Environments
---

### Post by boralyl on 2006-12-20
I've just encountered a problem this morning with my usb thumb drive.  I am running Efty Edge and I've had no problems with my 256mb thumb drive.  Today however I mounted it and began to copy files to it and it stated that it couldn't copy the files because the disk was full.  However, when I check out the properties it has 256mb of free memory.  So I then tried to use my 1gb sd card.  I plugged it into the usb adapter and mounted that.  When I tried to copy files I got the same message about the disk being full, even though looking at the properties it tells me that it has over 755mb free.  Any ideas?

---

### Post by kazuya on 2006-12-20
Crazy. I had this same issue happen to me this morning with my USB card. I am going through formatting everything now. Only thing I can speculate is that sometimes, the trash in the usb is full. Try emptying that. 
If that fails move all stuff in flash drive away to a safe spot and reformat USB device with Gparted or something like that.  I shall investigate.

---

### Post by boralyl on 2006-12-20
I'll check the trash, that could be true, and if no success then try reformatting it.

---

### Post by bobbob1016 on 2007-01-02
It's most likely the trash.  Ubuntu, and Linux in general I think, keeps the things you throw out in a .Trash folder, and that folder stays on the drive it was deleted from.  I've had it numerous times where I've thrown something out from a thumb drive, and unplug it and have an empty trash can.  Then when I plug it in, the trash comes back.  You just have to empty the trash when you delete something off removable drives.

---

