---
title: "Unexpected Inconsistancy"
date: 2009-05-15
forum: General Help
---

### Post by OxentroT on 2009-05-15
Hello, 
  I have had this problem three times already and I have resorted to re-installation the first two and I am not wanting to do it again. I am thinking maybe the disk is somehow stuck in a "read-only state"?
  Three days ago it started doing a "routine disk check" while booting and I always canceled having not the patience. Until last night when I was busy upstairs while I let it boot, the routine check ran uninterrupted. As I approached my desk I saw this familiar disheartening screen.

[IMG]http://i730.photobucket.com/albums/ww309/oxentrot/DSCN0015.jpg[/IMG]

If there is no way to fix this problem without re-installation, however, I have some important data I would not like to lose. I am able to navigate folders through the line. Is it possible to move these files to USB data stick via command?

Thankyou all in advance for any light on this issue.

---

### Post by robin3 on 2009-05-15
Hello OxentroT,

I had the same problem.

I solved it by typing **fsck -p**, waiting and then typing **fsck** (without the p option)

Robin

---

### Post by OxentroT on 2009-05-15
ThankYou for you help Robin.

I have ran both command and unfortunately they seemed to not do much, except display a bunch of moan and groans such as:

-"Media Error"
-"{DRDY ERR}"
-"{UNC}"
-"I/O error"
-"short read" 

I do believe that I have ran those command the last two times this has occurred, and the same thing happened. I have tried to look for a solutiojn to those errors but I only find similar problems but with completely different scenarios. if that makes any sense.

---

