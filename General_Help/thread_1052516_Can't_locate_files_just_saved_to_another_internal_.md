---
title: "Can't locate files just saved to another internal harddrive"
date: 2009-01-27
forum: General Help
---

### Post by Logan 1229 on 2009-01-27
I'm two weeks new to Ubuntu, using forums to learn.  But I've now gotten stuck & can't find the answer!
  
  Intrepid installed on main harddrive, with 3 additional separate storage harddrives.  Have figured out how to mount them as needed, used Gparted to partition (one single large partion) & label all 3, & Nautilus to give myself ownership permissions to all so I could save/delete files (THANK YOU TO ALL PREVIOUS POSTERS).  Now the problem:

  I just transferred all my old media, etc files to them (from old XP computer)...all seemed well.  Few days pass, then I go to access... nothing on drives.  All I see is the "lost&found" file.  According to "properties" & Gparted, the files are still there but I just can't find/locate/access them!

  Please keep in mind I'm a newbie to this (I love what I see so far but wow, there's tons to learn!).  Any help would be greatly appreciated!

---

### Post by dcstar on 2009-01-27
> **Logan 1229 said:**
> 
........
  I just transferred all my old media, etc files to them (from old XP computer)...all seemed well.  Few days pass, then I go to access... nothing on drives.  All I see is the "lost&found" file.  According to "properties" & Gparted, the files are still there but I just can't find/locate/access them!

  Please keep in mind I'm a newbie to this (I love what I see so far but wow, there's tons to learn!).  Any help would be greatly appreciated!

If a root-privileges program like gparted reports file use, but you cannot access them then it is a user rights problem - you do not have read access. Do this in a terminal and then see if you can see them (and then change their ownership):

```
gksudo nautilus
```

---

### Post by Logan 1229 on 2009-01-28
[QUOTE=dcstar;6629624]If a root-privileges program like gparted reports file use, but you cannot access them then it is a user rights problem - you do not have read access. Do this in a terminal and then see if you can see them (and then change their ownership):

Thanks for fast response David. However, gksudo nautilus didn't show me anything else. I have also tried changing ownership/permission to read/write &/or access files with no luck. Any other suggestions?

---

### Post by Wayne_V on 2009-01-28
Can you send:

$ df -hT

and tell us under what mount point the lost files are supposed to be?

---

### Post by Logan 1229 on 2009-01-29
> **Wayne_V said:**
> Can you send:

$ df -hT

and tell us under what mount point the lost files are supposed to be?

  Wayne, thank you for your help. Below is what I found:

Filesystem    Type    Size  Used Avail Use% Mounted on
/dev/sda1     ext3    453G  133G  298G  31% /
tmpfs        tmpfs    1.7G     0  1.7G   0% /lib/init/rw
varrun       tmpfs    1.7G  344K  1.7G   1% /var/run
varlock      tmpfs    1.7G     0  1.7G   0% /var/lock
udev         tmpfs    1.7G  2.8M  1.7G   1% /dev
tmpfs        tmpfs    1.7G  492K  1.7G   1% /dev/shm
lrm          tmpfs    1.7G  2.0M  1.7G   1% /lib/modules/2.6.27-9-generic/volatile
/dev/sdb1     ext2    459G   70M  436G   1% /media/Music
/dev/sdc1     ext2    459G   70M  436G   1% /media/Files

  (Not sure why I partitioned ext2 vs ext3 but shouldn't matter, correct?)

  This allowed me to see all my drives at once.  Alas, I made an amatuer's mistake... during my excitement to convert my old computer to Ubuntu, I did not verify the data transfer & it appears the data never transferred.  To test this theory, I copied a file to one drive then rebooted... file was present & I had full access.  Fortunately, data was backed up elsewhere.  (At this point, Wayne, thank you as df was great info to learn)

  The drive allocations of "used" simply appear to be allocations lost to partitioning...but 23GBs??  I understand 500GB is usually @ 465GB but considering sdb1 & sbc1 don't have an OS on them, seems like a lot was "used" to partition for storage.  Would there be a reason for this?

---

### Post by Wayne_V on 2009-01-30
/dev/sdb1     ext2    459G   70M  436G   1% /media/Music
/dev/sdc1     ext2    459G   70M  436G   1% /media/Files

You should be able to add journaling to the two disks (making them ext3) as follows:

$ sudo -s   (switch to root)

# umount /media/Music
# tune2fs -j /dev/sdb1
# mount /media/Music

# umount /media/Files
# tune2fs -j /dev/sdc1
# mount /media/Files

Some commands to analyze the disk usage:

# parted /dev/sdb print
# parted /dev/sdc print
# cd /media/Music ; du -sk *    .*   (note, thats star, space, dot, star)
# cd /media/Files ; du -sk *    .*
# find /media/Music -ls | more
# find /media/Files -ls | more
# exit
$ (back to user mode)

---

### Post by Logan 1229 on 2009-01-30
> **Wayne_V said:**
> 
You should be able to add journaling to the two disks 

Thanks for the help! Changed all drives to ext3 easily & all are working now.  You have been pointed me in a great direction...lots of reading/learning to do now!



Issue SOLVED



as a side note: 
  any knowledge of --> The drive allocations of "used" simply appear to be allocations lost to partitioning...but 23GBs?? I understand 500GB is usually @ 465GB but considering sdb1 & sbc1 don't have an OS on them, seems like a lot was "used" to partition for storage. Would there be a reason for this?

---

### Post by Wayne_V on 2009-01-31
df just displays a rough usage value.  See the following link for some explanation.  There is also space for inodes, privileged users, journaling, etc.  You can use 'dumpe2fs  /dev/sdX' to give some more detailed information.

[http://linuxshellaccount.blogspot.com/2008/12/why-du-and-df-display-different-values.html](http://linuxshellaccount.blogspot.com/2008/12/why-du-and-df-display-different-values.html)

---

### Post by Logan 1229 on 2009-02-01
Thanks Wayne_V; makes sense!

---

