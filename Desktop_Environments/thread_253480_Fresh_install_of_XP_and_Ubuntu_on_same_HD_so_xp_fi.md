---
title: "Fresh install of XP and Ubuntu on same HD so xp files are RW!!!"
date: 2006-09-08
forum: Desktop Environments
---

### Post by BLTicklemonster on 2006-09-08
Okay, I finally got it figured out. I keep trying to get XP and Ubuntu set up on the same hard drive, an 80 gig equal partitions, and XP will not format the windows partition any other way than NTFS. Which means, as we all know, that Ubuntu will not be able to Write to this drive at any given time unless you use some extra software and or steps.

I just found out the way one would get around this. It seems that Windows will not format FAT32 on anything larger than 32 gigs. 


[SIZE="5"][COLOR="Red"]THEREFORE, IF YOU ARE WANTING TO SET UP XP AND UBUNTU ON THE SAME HARD DRIVE AND WRITE TO THE XP PARTITION, SET THE PARTITION FOR XP TO LESS THAN 32 GIGS, AND FORMAT IT FAT32 AND LEAVE THE REST FOR UBUNTU.[/COLOR][/SIZE] It's that simple. ](*,) 



Now how many of you already knew this? Show of hands! Well, here's a post with it out in plain site to go along with all your other posts telling us. (which I am sure you posted this info, but with my limited search skillzorz, I never found the answer)

THEREFORE, I just put in a request for the afternoon off, and I'm going home and redoing a hard drive now. I think a woot woot is in order here. G'Day.

---

### Post by Wolki on 2006-09-08
I've heard something like that... But I definitely know that FAT32 Partitions can be larger than 32 gb (have an external hdd with a 80gb FAT partition). I've never installed XP, so I don't know whether it's possible, but maybe it'll work if you format the partition with Ubuntu/gparted as FAT before installing windows?

---

### Post by BLTicklemonster on 2006-09-08
I looked it up at microsoft, and didn't see anything other than "it won't do it". Not a single "but if you really want to: " anywhere. 

Thanks for the tips.

---

