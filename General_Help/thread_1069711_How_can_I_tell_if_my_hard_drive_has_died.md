---
title: "How can I tell if my hard drive has died?"
date: 2009-02-14
forum: General Help
---

### Post by Jeztastic on 2009-02-14
I am using a 2 hard drive setup with an 8.10 desktop install. I upgraded from 8.04 to 8.10, leaving the second hard drive mounted at /home. Now I get an error message - fsck died with exit status 8. I have used a live CD to try and work out what is happening, but the live CD will not recognise the second HDD. Does this mean it has died?

---

### Post by fragos on 2009-02-14
"man fsck" lists 8 as an operational error. Not quite sure what that means. There is "e2fsck" which is described as interactive fsck. That may provide more insite. You might run "blkid" to see the UUIDs of the devices and insure that /etc/fstab has the correct ones.

---

### Post by Matsukaze on 2009-02-14
The disk manufacturers have diagnostic programs which will determine if the disk hardware has failed. You can download and burn a live CD from the manufacturer's website, if you don't have a CD that came with the disk when you bought it.

---

### Post by Jeztastic on 2009-02-15
The hard disk drive had become loose when I moved the PC. Reconnecting it to the IDE cable sorted it. Really should start looking for the simple answers first...

---

