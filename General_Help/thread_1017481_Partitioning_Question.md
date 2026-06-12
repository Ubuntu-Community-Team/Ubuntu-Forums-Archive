---
title: "Partitioning Question"
date: 2008-12-21
forum: General Help
---

### Post by elanning on 2008-12-21
Greetings,

I have a laptop running Ubuntu 8.10 i386, that I was dual booting with WinXP.  I have things all set now and want to delete the XP partition, and add that space to my /home partition.  

I installed GParted, and was able to delete the NTFS partition no problem, and able to create a new ext3 partition (called New) but as far as I can tell there is no option to add this space onto the existing /home partition, is this not doable?  Basically I want /New to get added to /home as usable space without having to format /home.

Any advice is appreciated, thanks!

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda7             6.1G  3.0G  2.8G  52% /
tmpfs                1012M     0 1012M   0% /lib/init/rw
varrun               1012M  304K 1012M   1% /var/run
varlock              1012M     0 1012M   0% /var/lock
udev                 1012M  2.8M 1009M   1% /dev
tmpfs                1012M  444K 1011M   1% /dev/shm
lrm                  1012M  2.0M 1010M   1% /lib/modules/2.6.27-9-generic/volatile
[COLOR="Red"]/dev/sda6              42G   21G   20G  52% /home[/COLOR]
[COLOR="Red"]/dev/sda1              43G  180M   41G   1% /media/New[/COLOR]

---

### Post by Elfy on 2008-12-21
If you added the new partition to fstab remove it.

Boot with the livecd or a partition editorlivecd - then you will be able to work with /home - while it's mounted you can't.

Once in the livecd - you need to delete the old ntfs partition and then move everything so that the unallocated space is next to the /home partition then you can add the space.

If /home is inside an extended partition - that has to be resized before you can add to /home.

You must also if swap is mounted unmount - you can do so by right clicking the swap partition.

Possibly you will need to check and change the UUID's for your partitions after you have finished, you can do that from within the livecd.

Good luck

Make sure you have backups and bear in mind that it can take a long time to do this.

You might be better of just using the new partition as data storage as it is already set to do so from the output you give.

---

