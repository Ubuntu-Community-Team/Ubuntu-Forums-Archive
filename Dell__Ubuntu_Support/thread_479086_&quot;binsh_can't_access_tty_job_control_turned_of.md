---
title: "&quot;/bin/sh: can't access tty: job control turned off&quot; - lo tech solution"
date: 2007-06-20
forum: Dell  Ubuntu Support
---

### Post by mluster on 2007-06-20
So like many I encountered the dreaded "/bin/sh: can't access tty: job control turned off" message during the initial boot up. Frustrating as this was, it was made even more so by the fact I had an identical system and the Ubuntu Desktop 7.04 installed first time without a hitch. So.. what to do?

Well my trusty old Dell OptiPlex GX150 (P-III, 512MB RAM, 80GB HD) seemed to put up a little fight but here is how I got around the error:

Insert a floppy into the 3.5" floppy drive and then boot from the CD. Yeah, I know that sounds fishy but if you are tired of seeing the initfs prompt, tired of looking at casper.log, then throw a floppy in. The search for FD0 works and install continues. Nuff said on that quirk.

Good luck !

---

### Post by angryfirelord on 2007-06-20
(I think) on some machines, the kernel in Ubuntu tries to look for a nonexistent floppy drive, which when it fails, it gives you that message.

[https://bugs.launchpad.net/ubuntu/+source/casper/+bug/97306]("https://bugs.launchpad.net/ubuntu/+source/casper/+bug/97306")

---

### Post by magisbladius on 2007-06-21
I have tried booting with and without a floppy drive or disc, and it does not fix anything.

---

### Post by daynah on 2007-06-21
I have no floppy drive. USB?

---

### Post by onemustfall on 2007-06-27
Doesn't work for me. Looks like I'll be sticking to Windows...

---

