---
title: "SCSI Drive?"
date: 2009-03-06
forum: General Help
---

### Post by RedSingularity on 2009-03-06
What is this SCSI drive i see in "my computer"?  I cant open it or anything.

[URL="http://img136.imageshack.us/my.php?image=screenshotg.png"][IMG]http://img136.imageshack.us/img136/4846/screenshotg.png[/IMG]
[/URL]

---

### Post by cariboo on 2009-03-06
It looks like you had a usb device or a CD that wasn't unmounted correctly. Check /etc/mtab to see if there is somethng mounted that shouldn't be.

Jim

---

### Post by RedSingularity on 2009-03-06
From what i can see that file looks fine.  It shows only the devices currently mounted.

---

### Post by RedSingularity on 2009-03-06
Nevermind, i got it.  Turns out it was just a HDD i had not formated yet.

---

