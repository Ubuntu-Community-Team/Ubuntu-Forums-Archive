---
title: "Software RAID 5 hard drive space usage?"
date: 2006-09-30
forum: Desktop Environments
---

### Post by Adrayic on 2006-09-30
I just successfully created a software raid 5 partition consisting of 3 250gb diamondmax 10 drives.  I have a quick question regarding drive space.  I mounted the new partition but its showing up as 436GB free space available.  The partition is empty and it seems like this number is a little low.  I am well aware of the binary / decimal representations of hard drive space and the discrepencies between the two but it still seems like I'm missing 30Gb or so.  Both 250gb drives are read as 233gb within linux (and windows).  So it seems like I should have 233gb x 2 = 466gb free space available on an empty array (given that one of the drives is used for parity).  I had two of these on a raid 0 array running Win XP and the stripe showed up as 467gb within windows.  Is there something I'm missing?  Why am I seeing 436 Gb free space instead of 467Gb?

Running df -h gives the following line for the Raid array:

Filesystem            Size  Used Avail Use% Mounted on
                      
/dev/md0              461G  129M  437G   1% /media/RAID

---

### Post by lha on 2006-09-30
You have formatted your md0 as ext3, haven't you? As a default, partitions formatted as ext3 reserve 5% of total space for super user. 1 - 436/466 = 0.064377682, so most of the "lost" space is in fact reserved for root. You can set the reserved space to 0% if you want to get the most of your drives.

---

### Post by Adrayic on 2006-09-30
Ahh, ok, that makes sense.  A few questions though... during the Ubuntu install I created an EXT3 partition on my OS drive for the home directory.  Running df -h gives:

Filesystem            Size  Used Avail Use% Mounted on

/dev/sda6             201G   16G  175G   9% /home
/dev/sda3              37G  2.7G   33G   8% /


Since this is and EXT3 partition, why have I not lost 5%?  IE (why isn't it showing available space at 165 Gb.  Shouldn't 10gb or so have been allocated for root?  Interestingly, the root drive is showing about a 5% loss as well, which makes sense since this is also an EXT3 partition.  

Second question -- 

Would there be any disadvantage to setting the reserved space % to 0%? (IE -- why is 5% set aside for root?).  Does this only happen with EXT3 partitions?  Should / could I use a different filing system?  I am only using this array as a media storage device for a home media server so I dont need stellar performance.  I would like to get the most out of these drives though.... and 30gb of wasted space is quite a lot :)

---

### Post by lha on 2006-09-30
201 - 16 = 185! So there's something missing, too. 201*0.95 - 16 = 174.95, so there's the 5% again.

The reserved space reduces defragmentation and allows root-owned processes to run even if drive becomes "full" (= you run out of non-reserved space). You might be interested in the former reason to have some space reserved to root. The latter is not valid on a drive that is used like your md0 is. I'd definitely reduce the amount of reserved space. I'm not an expert in filesystems, so I don't know the effects of setting reserved space to 0%. If you have the time, it might not be a bad idea to read a little bit of ext3 and other filesystems.

---

### Post by Adrayic on 2006-09-30
My bad... to early to do math properly :) --  Thanks a lot Iha, you have been a great help.  I'll read more about filing systems and see if I can reduce the space reserved for root.  Thanks again.

---

