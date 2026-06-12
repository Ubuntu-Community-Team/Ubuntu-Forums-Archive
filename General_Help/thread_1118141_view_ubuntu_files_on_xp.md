---
title: "view ubuntu files on xp?"
date: 2009-04-06
forum: General Help
---

### Post by kristen89 on 2009-04-06
hi again, i am on xp right now and am trying to figure out how to access my ubuntu files to load the music from it onto mediamonkey :)  

my xp is ntfs if that is needed and 20 gig partion =P

---

### Post by wrose51106 on 2009-04-06
[http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by kristen89 on 2009-04-06
last time i tried that i double clicked the hd i set it to and it asked me to format it.... >.>

---

### Post by dacorr on 2009-04-06
What is the file System on your drive, EXT3, EXT4, Resier etc ..

Dac

---

### Post by kristen89 on 2009-04-06
ubuntu is ext3   xp is ntfs

---

### Post by tr33m4n on 2009-04-06
Ive experienced this problem as well... I found that I could access external hds formatted as ext3, yet not internal... hmmmm

---

### Post by kristen89 on 2009-04-06
hmm... i guess i can go google till i find somthing =P

---

### Post by kristen89 on 2009-04-07
so i searched google and the htings i tried did not work...

fs driver asked me to format the drive which was ubuntu so i did somthing wrong im guessing >.>

---

### Post by callie510 on 2009-04-07
I had so much trouble with this - the ext2ifs driver, that everyone suggests and googling usually shows, didn't work for me at all!

I finally diagnosed my problem and I bet it's yours too. Check the inode size of your filesystem with this command:

> sudo tune2fs -l /dev/sda1 
(change location to reflect any of your ext3 partitions)

My bet is that your "inode size" is 256. ext2ifs only supports an inode size of 128. 
I don't really understand inodes, but I believe the inode of a file has something to do with how Linux/Ubuntu locates items (files, directories, etc) on the hard disk. When I installed with the 8.10 Live CD, I formatted to ext3, and it formatted with an inode size of 256. ext2ifs doesn't support this. 

I didn't want to reformat the whole drive - especially since I had an inkling that larger inode size = better and more future proof. Fortunately, I found a driver that works!!

[http://sourceforge.net/projects/ext2fsd](http://sourceforge.net/projects/ext2fsd)

After installing this, I was finally able to mount and see my ext3 volumes. :) Finally my windows and linux can share music!

Hope this helps you (or others) out! It took me a long time to find a solution to this problem, so I don't think I'm the only one who has had trouble with ext2ifs :)

---

### Post by kristen89 on 2009-04-07
> **callie510 said:**
> I had so much trouble with this - the ext2ifs driver, that everyone suggests and googling usually shows, didn't work for me at all!

I finally diagnosed my problem and I bet it's yours too. Check the inode size of your filesystem with this command:



My bet is that your "inode size" is 256. ext2ifs only supports an inode size of 128. 
I don't really understand inodes, but I believe the inode of a file has something to do with how Linux/Ubuntu locates items (files, directories, etc) on the hard disk. When I installed with the 8.10 Live CD, I formatted to ext3, and it formatted with an inode size of 256. ext2ifs doesn't support this. 

I didn't want to reformat the whole drive - especially since I had an inkling that larger inode size = better and more future proof. Fortunately, I found a driver that works!!

[http://sourceforge.net/projects/ext2fsd](http://sourceforge.net/projects/ext2fsd)

After installing this, I was finally able to mount and see my ext3 volumes. :) Finally my windows and Linux can share music!

Hope this helps you (or others) out! It took me a long time to find a solution to this problem, so I don't think I'm the only one who has had trouble with ext2ifs :)


thank you so much!!! you just made my day ha ha :D now i can load my music from ubuntu and listen to it while i play games on xp :) 

too all who cant get that fs driver thing to work like me, this will most likely work :D 

just add the  drive to a letter and restart..fairly simple ^.^

thanks again callie!

---

### Post by callie510 on 2009-04-07
glad i could help :) this problem took me too long to solve, since it is very unclear from most of the internet that ext2ifs doesn't work on systems formatted in ext3 with (at least in my experience) the ubuntu live CD of 8.10.

enjoy shared files!!

---

### Post by phreaknite on 2009-04-08
> **callie510 said:**
> I had so much trouble with this - the ext2ifs driver, that everyone suggests and googling usually shows, didn't work for me at all!

I finally diagnosed my problem and I bet it's yours too. Check the inode size of your filesystem with this command:



My bet is that your "inode size" is 256. ext2ifs only supports an inode size of 128. 
I don't really understand inodes, but I believe the inode of a file has something to do with how Linux/Ubuntu locates items (files, directories, etc) on the hard disk. When I installed with the 8.10 Live CD, I formatted to ext3, and it formatted with an inode size of 256. ext2ifs doesn't support this. 

I didn't want to reformat the whole drive - especially since I had an inkling that larger inode size = better and more future proof. Fortunately, I found a driver that works!!

[http://sourceforge.net/projects/ext2fsd](http://sourceforge.net/projects/ext2fsd)

After installing this, I was finally able to mount and see my ext3 volumes. :) Finally my windows and linux can share music!

Hope this helps you (or others) out! It took me a long time to find a solution to this problem, so I don't think I'm the only one who has had trouble with ext2ifs :)

This works great with XP...but Vista is a bit trickier...

Would Ubuntu 8.10 run just as well with an inode of 128 as it does with 256?  Are there any drawbacks because I think I will just reformat my ext3 partition for 128 inodes if it will make my Vista more seamless...

---

