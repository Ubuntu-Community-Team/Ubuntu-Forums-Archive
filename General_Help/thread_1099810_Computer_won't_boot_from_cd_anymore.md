---
title: "Computer won't boot from cd anymore"
date: 2009-03-18
forum: General Help
---

### Post by perpetualcacophany on 2009-03-18
Hello,

So, just a few days ago I loaded up the LiveCD on one of my old computers so that I could pull some pictures off of the hard drive. The computer does not have an operating system right now, so I was just pulling them off of the old hard drive in there. A few hours later, I tried to pull up the Ubuntu LiveCD again so that I could do an install, and it won't let me boot from it now. When I get to the decision of what to boot from, whatever I select it tries to boot from the hard drive.

I'm really not sure what the problem is. I went in to the BIOS and set it back to the defaults thinking that maybe it was just messed up somehow, but it didn't fix it.

So, do any of you have any ideas?

---

### Post by Therion on 2009-03-18
And the optical drive works correctly otherwise?

If so, it pretty much has to be one of two things:

[INDENT]1. The disc has become corrupt or unbootable for some reason.

2. The BIOS setting does not have the optical drive as being primary in the boot sequence. 
[/INDENT]
Setting the BIOS back to it's factory defaults may not accomplish what we need here.  We need the optical drive ahead of the hard-drive in the boot sequence.  I'd check that first.  If that's all good, and still no joy, I'd try a new LiveCD.

---

### Post by philinux on 2009-03-18
Option 3.

CD drive has bit the dust or needs cleaning.

---

### Post by perpetualcacophany on 2009-03-18
> **Therion said:**
> And the optical drive works correctly otherwise?

If so, it pretty much has to be one of two things:

[INDENT]1. The disc has become corrupt or unbootable for some reason.

2. The BIOS setting does not have the optical drive as being primary in the boot sequence. 
[/INDENT]
Setting the BIOS back to it's factory defaults may not accomplish what we need here.  We need the optical drive ahead of the hard-drive in the boot sequence.  I'd check that first.  If that's all good, and still no joy, I'd try a new LiveCD.

Alright, well I just tested the LiveCD on 2 other computers and it worked fine, so I'm pretty sure it must be something else. I'll try what you suggested and get back.

---

### Post by fieroboom on 2009-03-18
Option 4. You accidentally unplugged/loosened the IDE cable somehow. (Have you been inside the case lately?)
Option 5. Your power supply in that old beast has given up on providing power to that channel. (does the light come on/drive spin up when you start booting?)

:D
-Paul

---

