---
title: "Install ubuntu ontop of redhat and have boot option for both"
date: 2009-04-22
forum: General Help
---

### Post by mythripk on 2009-04-22
**Install ubuntu when there is Red hat already installed**             
                                                                Hi All, 
I have posted this in installation forum no replies :( 

      In my PC i have Red hat installed and now in want to install ubuntu , I want both to co-exist.
Red hat is there in /dev/sda1 and /dev/sda2 , sda3 is the swap space. There are no mount points defined for either sda1 or 2. Hard disk space is 160GB and Red hat partition along with swap has taken up 20GB space
      My problem : 
1. I tried to create new primary partition with mount point as root with 15GB space it showed rest of the free space as unusable.But still i continued assuming that it can be partitioned later.But i did not see ubuntu as an option on boot up , but when added in the grub of redhat it showed the option but i said failed beacuse of some error (ext2fs does not match with partition 0x83) :sad:
2. I tried to create a new logical partition with mount point defined as root and it installed but again same problem seen above.

I am not sure as to how to go about it and am naivete with multiple linux installation on same machine.I need to do it asap.
Can anyone please help?:confused:

Thanks and regards

---

### Post by daniel014 on 2009-04-22
Hello mythripk, welcome to Ubuntu.

I'm no expert, but the simplest way I can see is to set up Red Hat to take up the 20GB.
Then boot into an Ubuntu live CD, choose manual partitioning and make your partitions on the 140GB space.
Ubuntu will recognise Red Hat and then add it to GRUB.

Hope this helps :).

---

### Post by mythripk on 2009-04-23
That is exactly what i did , in 140GB i tried to create those partitions as i mentioned in problem 1 and 2 .
And then added to grub , but may be the way i am adding to grub is the problem can you suggest that?


thanks and regards,
mythri.

---

### Post by uzi09 on 2009-06-11
Could you please also describe your problem a bit more clearly as well as what steps you took?

At the moment, it sounds as if you're not partitioning appropriately.

For the life of me, I can't seem to find a single install tutorial that shows pictures of how the partitioning bit works. I did, however, find a video of someone partitioning with Windows XP already installed. Red Hat should be similar.

[http://www.youtube.com/watch?v=JBfl3oViny8](http://www.youtube.com/watch?v=JBfl3oViny8)

Be sure you're doing this properly.

---

