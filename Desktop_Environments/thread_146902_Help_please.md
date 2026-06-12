---
title: "Help please"
date: 2006-03-19
forum: Desktop Environments
---

### Post by wfp on 2006-03-19
Tonight i tried installing ubuntu to dual boot with xp, the install crashed about three quarters of the way through, I was finally able to use my xp restore disk and choose the option to completley reformat my hardrive and start with xp from scratch.Everthing went good untill xp booted up, and it gave me a C:drive with ntfs, but it also gave me D:drive with 30gigs of free space fat 32, thats exactley:cry:  the amount i used when i was partioning my drives in the linux install. Is there any way to get that free space back on to my C:drive. any help would be appreciated.

---

### Post by dermotti on 2006-03-19
When you install Windows XP from scratch you have the option to remove partitions. You should have just removed them all and created a new windows xp partition that uses the whole disk. 

You can reclaim the space within windows XP too, but it will still be a seperate partition.

goto controlpanel -> administrative tools -> computer management -> disk maangement

you should see that fat 32 partition in there somewhere. right click it and DELETE partition. Once thats done, right click the free space and Create partition. Once yer done right click format it as ntfs.

---

### Post by wfp on 2006-03-19
Thank you allready done wayne.

---

### Post by wfp on 2006-03-19
This is what it looks like now Partition	Partition Type	Drive	Start Offset	Partition Length
#1 (Active)	NTFS	C:	4314 MB	36052 MB
Partition	Partition Type	Drive	Start Offset	Partition Length
#2	FAT32	E: (RECOVERY)	0 MB	4314 MB
Partition	Partition Type	Drive	Start Offset	Partition Length
#3	Linux		40366 MB	18269 MB
Partition	Partition Type	Drive	Start Offset	Partition Length
#4	NTFS	D:	59451 MB	19077 MB
Partition	Partition Type	Drive	Start Offset	Partition Length
#5	Linux swap		58635 MB	807 MB
During the install of linux to dual boot I kept getting this window can not finish installing applications check to make sure you have enough space, could not get it to finish, so after a couple hrs. I threw my xp recoverey cd. and positive i choose the option to completley reformat hardrive, becasue i got another window that said you will loose all data that you have stored, and will install all aplications that came with this compter i choose yes, xp is working great now but is there any way to get those lixux partitions off my hard drive can not understand why it left those on my hardrive any help would be appreciated. also windows is not even showing those linux drive anywhere, i use everest hom edition and thats how i found out about the linux drives still being on my hard drive becasue i noticed there were about 20Gigs not being accounted for.

---

