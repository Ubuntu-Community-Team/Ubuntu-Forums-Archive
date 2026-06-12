---
title: "CRC error after upgrading to Ubuntu 9.04"
date: 2009-04-25
forum: General Help
---

### Post by jonathannevins on 2009-04-25
Yesterday I upgraded from Ubuntu 8.04 to 9.04 (via 8.10).  Now, sometimes when my computer tries to boot Ubuntu I get a black screen that says "CRC error. System halted."  Can anyone help me fix this?  I searched a bit and found out that CRC errors can result from loose hardware cables, so I double-checked all of my connections and everything looks good, but I'm still getting the problem.  I also read that CRC errors may result from a hard drive that's going bad, but it seems too coincidental that the first time this ever happened was directly after upgrading to Ubuntu 9.04.  I haven't had any other problems that would indicate a bad drive.  Is there a way that I can determine if a drive is going bad?  Any other suggestions?

---

### Post by LouisFlorian on 2009-05-07
I did exactly the same, I download the upgrade from 8.10 to 9.4 and installed flawless but today when I start the system and choose ubuntu the system froze so I re-started the system but I finished having the crc error. I have dual boot ( Windows XP with ubuntu partition ).
After the crash system never recovery and had leave me without any OS. 8.10  never gave me any trouble but after the update to ubuntu 9.04 crashed and since then the Computer does not boot on any system after the error and leave me without any OS. 

Any advise?  Any Clue? Any Tip?

---

### Post by LouisFlorian on 2009-05-08
Since CRC Errors are mostly related to hardware.

I went to the easy one first (Memory) I try removing the second Memory card and reboot,  I did not help, they I try the first card been replaced it by the second card.  and that was the problem.  somehow the memory was faulty and as soon as I removed it.  I reboot the system and it work as it was before.

In this case my issue has been solved.  I hope the previous issue posted is somehow easy to resolve.

---

### Post by geraldvillorente on 2009-05-09
There so many reason why CRC occur as the following:

Cause:

  * Software problem
    * Corrupted file(s)
  * Hardware problems
    * HDD bad sector
    * Defective memory module
    * Faulty IDE/SATA cable
    * Faulty motherboard bus
Solution:
  * perform filesystem check
  * check/replace IDE/SATA cable
  * clean the memory bank 
  * clean the memory module terminal using eraser
  * also check the power supply cable terminal(sometimes it
    can cause power fluctuation due to loose connection and ruin
    your hdd)

HTH,

---

### Post by LouisFlorian on 2009-05-09
Thank You Gerald, 

As I explain in my previous posted message I did my first shot with the memory, one of them was faulty and I was lucky that I do not have to deal the rest of the list that you posted.

I hope that when other see your posted message this can give them a amplitude spectrum of all the possibilities of what they have to deal with. 

Thanks Again.

---

### Post by geraldvillorente on 2009-05-11
Welcome Sir....Happy to help

---

