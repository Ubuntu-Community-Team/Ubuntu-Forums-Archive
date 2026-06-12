---
title: "Partition Help"
date: 2005-09-14
forum: Desktop Environments
---

### Post by awtomlinson on 2005-09-14
i have made my / partition way too big (19 gb) & want to cut off some of this (around 10 gb or so) & merge it with my /home partition.  can i do this in linux (with either gparted or qtparted or command line) without destroying each affected partition?  i don't mind so much if the / partition is gone, i could just reinstall when breezy is officially released, but i do not currently have the means to backup my massive /home partition.  step by step instructions would be greatly appreciated.  also, what is the recommended / file size?  out of my 19 gb partition, barely over 3 gb is used, & i have a ton of programs & all updates installed.  my total hard drive size is 250 gb.  i have 1 gb of ram, so my swap partition is currently 512 mb.  should i resize the swap to make it 1 or 2 gb?  all of the rest of the 250 gb goes to the /home partition.

---

### Post by Hairy_Palms on 2005-09-14
you should be able to do it but not fro inside ubuntu, i recommend using a liveCD and using gparted from there, i did this before with a live mandrake CD

---

### Post by awtomlinson on 2005-09-15
i just want to make sure.  so, if i use a live cd & gparted or qtparted, i can resize these partitions without destroying them?  again, not that big of a deal if the / partition is destroyed, but i ABSOLUTELY CANNOT lose my /home partition.

---

### Post by az on 2005-09-15
[QUOTE=awtomlinson]i just want to make sure.  so, if i use a live cd & gparted or qtparted, i can resize these partitions without destroying them?  again, not that big of a deal if the / partition is destroyed, but i ABSOLUTELY CANNOT lose my /home partition.[/QUOTE]

Do not do it if you cannot back up any data.


Also, you cannot relocate another partition onto itself.  For example, you cannot make a partition start a few gigs before itself.  This is hard to explain:

If you have a partition that is ten gigs big and is on your disk from 10g to 20g, you cannot move it to start at 8g and finish at 18 gigs because the move would require the data to be placed onto a partition that does not yet exist.

In that case, if you have sufficient space elsewhere, you can move the 10g-20g partition elsewhere( say 30g-40g (were have a 40 gig hard drive, here)), then shrink whatever partition comes before it (to free up space at 8g where you want to put it, and then copy the data back to 8g-18g.


Does that make sense?

---

