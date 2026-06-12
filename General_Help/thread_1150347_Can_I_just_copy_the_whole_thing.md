---
title: "Can I just copy the whole thing?"
date: 2009-05-06
forum: General Help
---

### Post by jamesdcarroll on 2009-05-06
I really apologize if this is more detail than you need, but...

I have two physical hardrives in my system call them A and B. When I moved to Ubuntu I duel booted and put Ubuntu on B (one partition in Ext3) and left Windows on A (two legacy partitions both NTFS).  Once I decided that I was really going to make the move, I copied everything that I wanted to the Ubuntu drive and basically left the NTFS partitions there especially since one of them was marked *boot. 

Then things got bad. I decided to format the entire A drive ext3, lost the boot drive, but was able to install from the disk. But then during [the periodic fsck my]("http://ubuntuforums.org/showthread.php?t=1138503") B drive (which had everthing on it) threw some errors that I didn't understand and whatever I was supposed to do, I didn't and the drive (containing everything now) was unmountable.  So I ran out, got a myBook, ran a data recovery tool, and pulled as much as I could off and stuck it there. PHEW! At least as many of the kids' pictures were safe(r) as can be.

Turning back to my unmountable B drive, I researched and found TestDisk which gave me the alternate superblock locations and block size, ran  **sudo fsck.ext3 -b 1605632 -B 4096 /dev/sdb1** answering 'yes' everytime, and wonders of all wonders, I can see my drive and everything is there.

So now (and those who are still reading I appreciate it) I have basically two Ubuntu installs one on A that has nothing really and B that has everything. 

Can I just copy everything from B over A and have my old system back? I'm guessing I would have to change grub.lst, but would it be possible?

THANKS!!

PS: Did I mention my video card also decided to [give up the ghost]("http://ubuntuforums.org/showthread.php?t=1147784")?

---

### Post by exutable on 2009-05-06
I'm not sure if this is what you're thinking but you might want to use an imaging program like ghost or acronis true image.  Basically it just takes an exact image of a harddrive and put it on another harddrive.  If the harddrive is in the same computer the OS usually does pretty well because it's all the same hardware.

---

