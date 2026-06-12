---
title: "My raid 0 has died! Noooooo!"
date: 2009-05-19
forum: General Help
---

### Post by Vigh on 2009-05-19
hey guys,
       I was running a RAID 0, 2 500GB SATA drives running windows vista OS, and thought I would install Ubuntu 9.04 within windows, rebooted the system got to the partitioner and noticed something was wrong, it was not detecting the RAID 0, I specified 30GB installation for Ubuntu 9.04 to run within windows, as soon as I saw something strange, I exited the installer without making any changes, no formatting, no partitioning, nothing, to my dismay the computer came up with an error notification- MISSING OPERATING SYSTEM and the 2 disks were no longer in raid, is there any way of recovering my data? or is it lost forever, I am a big fan of ubuntu but its really frustrating that I lost all that data, I didnt format anything, it seems either windows destroys your raid when you attempt to install ubuntu within windows, or the ubuntu installer automatically destroys your raid, me sad now =-( thankfully my university work is backed up onto another machine.

On the bright-side getting a new machine soon- its going to be shiny and dedicated to Ubuntu, AMD X2 2.7Ghz microATX system

---

### Post by LoneWolfJack on 2009-05-19
chances are, just your MBR has been corrupted.

I'd boot into ubuntu using the live disc and create an image of both drives, then use the bios to reestablish the raid and then use a windows disk to try to reset the MBR.

note (perhaps I should make this my signature *sigh*):
NEVER EVER mess with raid or partitions without a full backup of your data

---

### Post by dcstar on 2009-05-20
"RAID 0" is a total misnomer as there is absolutely no "Redundancy" whatsover is striping disks, in fact you double you chances of losing data because if either one of the drives has a problem - you lose the lot.

"RAID 0" is in fact a "Risky Array of Inexpensive Drives".

---

