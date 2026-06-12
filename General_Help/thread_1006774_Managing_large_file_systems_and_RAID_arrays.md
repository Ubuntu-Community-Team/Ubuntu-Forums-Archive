---
title: "Managing large file systems and RAID arrays"
date: 2008-12-09
forum: General Help
---

### Post by batfastad on 2008-12-09
Hi everyone

About 6 months ago our shared files system died (an old Lacie Ethernet Disk) so I decided to build a new one from scratch. All fairly easy, 3Ware 9690SA card 8 port multilane with 5 x 500GB drives in a RAID 6 configuration with another drive as a hot-spare.
Then 2 drive bays free in the backplanes for future capacity expansion.
Got it configured exactly how I wanted it using Samba and Netatalk and it was my first real dive into Ubuntu, and Linux admin in general... apart from PS2 Linux and some old Red Hat/Mandrake experience, and remote admin of web servers through SSH.
The 3Ware card has been working excellently with Ubuntu.

Our RAID drive is basically shared out as a single share of 1.4TB, and we still have 800GB free.
The file system is ext3.

When I add new drives into the array, the 3Ware card will rebuild the array onto the new drives and the system should detect the extra capacity on the drive (although it's actually an array of drives).
However the OS won't be able to use that new space since our existing ext3 partition with all the data will still be 1.4TB

So I can add another partition onto the RAID drive, which I doon't really want to do as the idea of our shared files is to have 1 massive share.
Or I could resize the existing ext3 partition. It seems pretty straight forward according to this guide: [http://www.howtoforge.com/linux_resizing_ext3_partitions_p2](http://www.howtoforge.com/linux_resizing_ext3_partitions_p2)
I've tried this method on Ubuntu Server 8.04 with a few different external HDDs and it seems to work fine.
Before doing this live I will obviously run full backups. But eventually I'll be doing this on an amount of data where it will require a whole load of spare drives to fit the backup!

Am I missing something here?
Is there another way I should be managing this?
Surely Amazon don't have to do this with their S3 service everytime they add capacity :lol:

Is there a file/partitioning system that would allow me to just add the new drives to the RAID card, rebuild the array, dismount/reboot the server and use the capacity straight away?

Or will I always have the problem of having to resize a partition/file system to fill the newly added space on the array?

Any comments/suggestions/ideas?

Cheers, B

---

### Post by psusi on 2008-12-10
Resizing is pretty straight forward using gparted on the livecd.

---

### Post by fjgaude on 2008-12-10
Resizing with gparted should work for a hardware raid array. Try it and see what it looks like.

As for backup, have it, no matter what! Many use three levels, one online, another near-line, and finally, off-line. Sooner or later such will be needed, doesn't matter what it takes, do it. Tape, another array, whatever!

---

### Post by insane_alien on 2008-12-10
resizing shouldn't be an issue(it hasn't been for me) but as always, have full backups.

although i question i should ask you is, why don't you have full backups already?

---

