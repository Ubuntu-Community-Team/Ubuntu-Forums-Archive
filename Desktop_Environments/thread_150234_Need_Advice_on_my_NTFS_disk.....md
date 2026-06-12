---
title: "Need Advice on my NTFS disk...."
date: 2006-03-25
forum: Desktop Environments
---

### Post by tidy_boy on 2006-03-25
Hey guys I only have one problem with linux is that i cant right to my ntfs external caddy which is 250gig.

I do not really want to format the disk to ext3 as i sometimes take the disk around to my friends house on his windows pc.

I have been told to create a fat32 partition but the partition can only be a certain size. Is this correct or could i create say a 100gig fat32 partition?

Any input would be great.


Thanks

---

### Post by twopeak on 2006-03-25
I've heard once that the microsoft tools put a cap on the size you can format them in FAT to make you switch over to NTFS. 
In other operating systems you should be able to go over that limit.

I'm not really sure of what i'm saying... i'm a newbie myself

---

### Post by Hairy_Palms on 2006-03-25
yeah you should make a fat32 partiton with gparted under linux or partition magic under windows linux cant yet write to ntfs safely as microsoft wont release their specifications.

---

### Post by fatsamurai on 2006-03-25
The partition size limit for fat32 is two terrabytes. The maximum individual file size is 4gb.

---

