---
title: "How to resize drives"
date: 2005-08-31
forum: Desktop Environments
---

### Post by wadesmart on 2005-08-31
08312005 1424 GMT-5

I was saving some pictures on my hard drive and editing them with Gimp when gimp said there was no space to save. I deleted some non used pictures and that gave me only 85mg on my Home drive. 

How do I increase the size of the place where I store all my files - in the Home location?

wade

---

### Post by az on 2005-08-31
That is complicated.

How are your partitions laid out?  Why did you create more than one partition;  what needs do you have?

You will need to shrink another partitoin to make another ajacent partition grow.  You can do this with parted from the install cd (boot from it - a drive cannot be mounted when you partition it) or Qtparted or Gparted (knoppix)

---

### Post by Martin Witte on 2005-08-31
That is hard to tell without some more informationon how you have set up partitions on your darddisk(s). Start with the command 'sudo parted'. 'parted' Can resize - under certain conditions, see for an example [http://www.gnu.org/software/parted/manual/html_node/parted_32.html](http://www.gnu.org/software/parted/manual/html_node/parted_32.html)

---

### Post by wadesmart on 2005-08-31
08312005 1453 gmt-5

Well, when I set up Ubuntu I knew nothing of how things worked so I choose the default on everything. This is from fdisk ~l

Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1216     9767488+   7  HPFS/NTFS
/dev/hda2            1217        2432     9767520    5  Extended
/dev/hda5            1217        1824     4883728+  83  Linux
/dev/hda6            1825        1946      979933+  83  Linux
/dev/hda7            1947        2189     1951866   83  Linux
/dev/hda8            2190        2432     1951866   83  Linux

Disk /dev/hdd: 20.4 GB, 20480237568 bytes
255 heads, 63 sectors/track, 2489 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1               1        1117     8972271    7  HPFS/NTFS
/dev/hdd2               1           1           0    0  Empty

Since I just choose the default, those defaults are now full, well at least the one for home. 

wade

---

### Post by wadesmart on 2005-09-03
09032005 1347 GMt-5

This is the drive space now: 
Disk /dev/hdd: 20.4 GB, 20480237568 bytes
255 heads, 63 sectors/track, 2489 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1               1        1117     8972271    7  HPFS/NTFS
/dev/hdd2               1           1           0    0  Empty

wadesmart@wadesmart:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda5             4.6G  153M   4.3G   4% /
tmpfs                    375M     0     375M   0% /dev/shm
/dev/hda6             897M  827M  23M  98% /home
/dev/hda7             1.8G  1.7G     36M  98% /usr
/dev/hda8             1.8G  138M    1.6G   9% /var
/dev                      4.6G  153M    4.3G   4% /.dev
none                     5.0M  2.8M    2.3M  56% /dev
wadesmart@wadesmart:~$

So lets say I take 800mg from /var and 2.15gb from /.dev that would give me 2.95gb more to use. 

My question is, /.dev and / appear to be the same. They are both on /dev/hda5. Im a bit learly of doing anything until I know that taking space from one to give to another isnt a bad thing. 

Wade

---

