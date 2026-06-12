---
title: "&quot;No Boot Device Found&quot;"
date: 2011-06-28
forum: Desktop Environments
---

### Post by mrbison on 2011-06-28
So I encountered this problem after I'd been using 10.10 for maybe 4 months: all of a sudden, after the computer had been powered down it wouldn't load my OS (ubuntu alone, no partitions)... I'd get the message "No Boot Device Found, press enter to retry." The weird thing is that I can then put in my live CD or bootable USB and it will load linux fine and THEN I can restart the computer which will allow me to get back into my OS with all my files. 

Restarting is ok, but if the computer looses power like in a shut down, then it won't boot without a recovery CD...

To try and solve this mysterious problem, I recently completely erased ubuntu and installed linux mint. Same problem still there.

About an hour ago I completely erased and reinstalled GRUB2... same problem! 

Anybody have any ideas about what this could be???

Thanks!

---

### Post by mcduck on 2011-06-28
Sounds like a hardware problem, for example a bad soldering in some place on your motherboard could cause the computer to fail to boot (or recognize some device) ion the first try, only working after the components have warmed a bit.

Of course simply making sure all the cables are properly connected would be a good start... You could also try switching the hard drive to another connector in case that would help. 

Whatever it is, it definitely isn't a software problem.

---

### Post by mrbison on 2011-06-28
Thanks for your input. I hadn't even considered the possibility that it wasn't a software problem. 
One thing I've noticed is that it doesn't seem to matter how long the computer has been running. As far as I can tell it's this simple:

"Restart" = successful loading of installed OS
"Shut Down" or "Hibernate" = unsuccessful loading of OS with error message

Maybe I should dig around in the tower and see if there is anything obviously wrong. 

Otherwise... ???

At least I learned some things about GRUB in the process of trying to fix this thing...

Thanks!

---

### Post by Maheriano on 2011-06-28
This happens to me when I plug in external storage. Do you have another USB drive or a phone/camera plugged in? It'll try booting from that sometimes.

---

### Post by mrbison on 2011-06-28
> **Maheriano said:**
> This happens to me when I plug in external storage. Do you have another USB drive or a phone/camera plugged in? It'll try booting from that sometimes.


No, I thought about that too. I've been careful to make sure that nothing is plugged in or in the drive that might confuse the boot loader (or do I mean the BIOS?). Anyway, this doesn't appear to be it, but thanks.

---

