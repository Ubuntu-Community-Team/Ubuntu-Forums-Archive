---
title: "backup vista through linux"
date: 2009-05-09
forum: General Help
---

### Post by damystics on 2009-05-09
My windows has died and I haven't made a backup using the software is there a way to make that backup so I can reinstall my windows thankyou

---

### Post by coffeecat on 2009-05-09
If you mean backing up the whole system, OS and apps, then no because you'd be backing up a dead system. But if you mean backing up your personal files that are on the C: partition, then yes. Or rather, yes if the partition itself is not corrupted.

Boot up with an Ubuntu live CD - versions 8.04, 8.10 or 9.04 should do. When you are in the live environment, go to Places in the main menu and find your C: partition. It will have the partition label or something like '80GB volume', depending on the size of the partition or whether there is a partition label. Click on it and a file manager window will open on the desktop. Now plug in a USB drive, let that be automounted and copy your personal files from the Windows partition to the USB drive.

**Edit:** I see you joined in November last, but this is your first post. Is that a dual Windows/Ubuntu system you've got there? In which case you'd be able to use your Ubuntu partition to rescue your personal files.

Might be a good idea to tell us exactly what your system consists of.

---

### Post by damystics on 2009-05-09
It has a corrupted driver so I wanted to reinstall windows but i didn't make a back up I have a dual boot ubuntu 9.04

---

