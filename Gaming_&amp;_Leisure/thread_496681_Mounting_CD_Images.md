---
title: "Mounting CD Images"
date: 2007-07-09
forum: Gaming &amp; Leisure
---

### Post by eljoeb on 2007-07-09
Buenas dias,

I'm trying to install Call of Duty and I was having an issue switching CD's.  I tried wine eject, and it won't pick up the 2nd CD. In a desperate effort to play games in Ubuntu I decided to make images of the disks and mount them.  That wasn't very hard. I can't quite say mounting them has been easy.

I tried  sudo mount -o loop COD1.iso /mnt/iso . This seemed to work fine.  The disc's contents appear in the /mnt/iso folder I already made.  Dandy.  But when I tell wine to run it, it says "General failure" (which is weird, because I thought my wife was the only one to call me that.)

So can anyone help me out?  Please tell me what kind of information you would need to help me.

Thank you in advance,

Joe

---

### Post by Liolikas on 2007-07-09
Try more complex way:
mount myiso.iso /mnt/iso/ -t iso9660 -o ro,loop=/dev/loop0

---

### Post by eljoeb on 2007-07-09
That didn't seem to work.  Has anyone else installed Call of Duty?  I know there is already a thread on this, but none of those fixes helped.

Thanks

---

### Post by wounded on 2007-07-09
Probably has nothing to do with it but why did you mount it to /mnt/iso? When I tried to get Diablo 2 on Ubuntu I mounted the images  to /media/cdrom0 and the install program picked up on it fine and when I unmounted one image and mounted the next it worked fine. I don't know if that has anything to do with the issue you're having, just curious.

---

### Post by eljoeb on 2007-07-09
Hmm... didn't know.  I figured I would want to differentiate between the two.  I'll check that out.

---

