---
title: "Grub Error 18. Out of the blue. Then Error 15. Come on now..."
date: 2009-05-17
forum: General Help
---

### Post by Roasted on 2009-05-17
I have 4 hard drives. 500/500/250/250. 

The first 500 is Vista/Ubuntu 9.04 dual booting. The other 3 drives are simply backup drives with no operating systems.

Half of the time I boot up, I get error 18 selected cylinder exceeds maximum supported by bios. Press any key to continue.

Typically rebooting solves this. But other times I reboot and I get it again. Last time I got it about 4 times in a row.

I checked the BIOS and it appears as if my main 500gb hard drive with the OS's is indeed the first in the boot priority. 

Then just now when I booted up and I selected Ubuntu, I got error 15: no file found. I hit enter again and it booted up. Hm, interesting.

What's up with Grub? This is getting kinda old...

EDIT - I'm reading that having a separate boot partition seems to be the best. But I've never had a separate boot partition.

-How big does the boot partition have to be?
-Can I resize my existing partitions and drop in a boot partition after windows/before linux? Or do I have to format the whole thing and start over?

---

### Post by mancimailman on 2009-05-17
Try using a boot cd called "super grub", this fixed my grub error 22

---

### Post by Roasted on 2009-05-17
I use super grub very often at work. Why would super grub fix this problem when the error itself directly indicates it's a BIOS issue?

I also checked ASUS's BIOS updates for my board (P5QL Pro) and the versions I found had a section that says what they updated - and nothing seemed relevant to my issue.

It's weird because on the grub web site I read that this was a problem when hard drives exceeded the 8.45gb barrier. Well, I've been beyond this barrier ever since I started using computers. It specifically noted "Even computers as late as 2001 may have this issue." This computer was built in November of 2008!! :confused::confused::confused::confused::confused:

---

