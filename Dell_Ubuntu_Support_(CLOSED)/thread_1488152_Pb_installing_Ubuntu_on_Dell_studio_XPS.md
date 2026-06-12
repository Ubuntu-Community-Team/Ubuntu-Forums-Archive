---
title: "Pb installing Ubuntu on Dell studio XPS"
date: 2010-05-19
forum: Dell Ubuntu Support (CLOSED)
---

### Post by The Faba on 2010-05-19
Hi,
  I just bought a Dell studio xps 8100 (i7 870, 1TO 2 hard drives of 500Go set in raid 0, Nvidia 240) and I want to install Ubuntu (10.04) in dual boot with the pre-install windows 7.
  When partitioning, I'm facing a few problems :
  - the installer refuses to resized the window partition to free memory for Ubuntu without erasing the entire disk. 
  - I tried to do the partitioning within the live CD:
                  -> Gparted sees the two hard drive as free of space 
                  -> The disk analyser (I don't remember the exact name) sees the various partitions that are existing in within the 2 disks. I think it sees it as it is supposed to because there are 2 disk in raid 0.
  - Even if I accepted at the first place to completely erase the only disk it sees to install Ubuntu, the installer refuses.
  Does one of you have an idea on how I should proceed to install Ubuntu on dual boot with window 7 within this configuration ?
   
  Thanks for your help,

---

### Post by mellowtothemax on 2010-05-19
I recommend you install Linux on a third disk.  It will save you a lot of possible data loss problems and time.

Or erase both disks and install each os on its own drive from the two you have.

Do you really need raid?

---

