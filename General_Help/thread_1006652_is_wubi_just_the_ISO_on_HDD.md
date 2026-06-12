---
title: "is wubi just the ISO on HDD?"
date: 2008-12-09
forum: General Help
---

### Post by nood1e on 2008-12-09
it seems that when you install via wubi all it does is create a partition for the ISO image so it can load off the HDD instead of the CD. is this what its doing? if so can i do a full install through this wubi install? if i can this will solve a huge issue im having, which i created another post begging for a solution to that. 

the problem came from installing via wubi and uninstalling. now my computer wont boot from the CD. but my drive is completely recognized in bios and running prefectly. 

just wondering.

---

### Post by Jammanuser on 2008-12-09
> **nood1e said:**
> [COLOR="Red"]it seems that when you install via wubi all it does is create a partition for the ISO image [/COLOR]so it can load off the HDD instead of the CD. is this what its doing? if so can i do a full install through this wubi install? if i can this will solve a huge issue im having, which i created another post begging for a solution to that. 

the problem came from installing via wubi and uninstalling. now my computer wont boot from the CD. but my drive is completely recognized in bios and running prefectly. 

just wondering.

that is incorrect...the red text, that is! Wubi does NOT create a partition for the ISO image...or at least not in the conventional sense! what Wubi does is simple install Ubuntu 8.10 on **top** of ur Windows OS, in a folder named "ubuntu"! it doesn't create a partition...it operates on a virtual disk, called a "root.disk", which allows it to run Ubuntu, as **if ** it was on a partition, which it is not, from a ext3 filesystem type from within the virtual disk itself!

to create a full install from a Wubi install, see the sticky thread on Wubi forums, which describes how to migrate a Wubi install to a dedicated partition...i.e. moving all ur data, settings, and programs to a partition which u create with a partitioning program!

Hope this helps! :guitar:

Cheers! :D

-jammanuser

):P

---

### Post by magmon on 2008-12-09
Good luck and be careful while following that guide. My results where... Less than favorable, but it works for most people.

---

### Post by nood1e on 2008-12-10
problem sort of solved. i got the disk to boot normally. the wubi is a cool idea, but really its a pain in the butt. a person should just test on the virtual OS disk, decide if they like it, then do a full install if they do. its like lying to them saying "here is ubuntu in windows!" its not the read deal.

---

