---
title: "I messed up installing Breezy..."
date: 2005-12-18
forum: Desktop Environments
---

### Post by overclockedkarma on 2005-12-18
Being extremely careful not to lose data, I made the partitions myself with a morbis live cd. I made a 29 gig ext3 partition (I'm a noob at linux, literally, my first encounter. If someone could explain exactly what gets saved where, that'd be lovely), and mounted it / in the ubuntu instalation process. I also made a 2.8 gig swap portion. This is on a 180 GB harddrive that's set to slave (another thing I'm unsure about is wheter or not I can even dual boot from a slave). 
Now I've used almost all the space I want to for linux, but I didn't make a fat32 portion. So I went back into the morbis disk and tried to remove both the swap and the ext3, but it says it can't. I can't format those portions from Windows now, so am I supposed to change the formats back to ntfs and hope formating them will let me remove them to remake them?

---

### Post by Rackerz on 2005-12-18
Putting them into NTFS in Windows should be the safer thing to do. After that you should be able to change them back and forth to ext2,3 etc. I had a similar problem to this by anychance did you change any settings for the drives? Or did you JUST partition and format them?

---

### Post by overclockedkarma on 2005-12-18
Okay, I had 70 GB left on my primary slave. I went into morbis and partitioned it into a 30 GB NTFS section and a 2.8 GB NTFS section. Then in the Breezy installer I changed the 30 into EXT3 and monuted it "/", and I changed the 2.8 into SWAP and it mounted itself "swap". That's all I changed about it...I didn't format the new partitions before I changed them, should I have? They were supposed to me made of free space...

---

