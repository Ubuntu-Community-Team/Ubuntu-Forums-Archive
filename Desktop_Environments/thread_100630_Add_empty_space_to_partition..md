---
title: "Add empty space to partition."
date: 2005-12-08
forum: Desktop Environments
---

### Post by dartakaum on 2005-12-08
Hy, i have some unloucated space i'd like to "append" to my reseirFs partition.

How can i do it?

and how can i change from reseirfs to ext2 without losing data?

---

### Post by RAOF on 2005-12-08
How to add extra space depends on what sort of setup you have.

You probably don't have an LVM setup, so what you'd need to do is to run "gparted", probably from a live cd.  That does all the partitioning stuff - moving, resizing, etc.

If you **are** using LVM (and you can tell because there will be something under the /dev/mapper/ directory) ask & I'll work out how to do it.

As for converting reiserfs to ext2, I think you're out of luck.  You'll have to copy all the data off, reformat it to ext3, and then copy the data back on.  Why do you want to change to ext2 anyway?  (I **assume** you mean ext3 - it's just the same as ext2 (and can be read by anything that reads ext2 partitions), but recovers more gracefully from problems)

---

### Post by dartakaum on 2005-12-08
ext2/3 was just to access it under windows, but probrably won't be necessay.

:) moving all the way to linux.

i'll try gparted and say something later.

thank u.

---

### Post by dartakaum on 2005-12-08
well.... i was checking if i got LVM..
and i got one control in /dev/mapper/control
:\ so, what can i do?
gparted won't do?

---

### Post by RAOF on 2005-12-08
If there's **only** "control" in the /dev/mapper directory, I don't think you're using LVM.  You'd have other devices in there, one for each virtual partition.  So go ahead and use gparted.

Oh, and you can also get a reiserfs reader for windows, too.  I forget the link.  Perhaps ask Dr Google?

---

### Post by dartakaum on 2005-12-08
haaa, LVM, is virtual machine. No i'm not using one. :)

going to gparted from live cd. 

thanks.

---

### Post by RAOF on 2005-12-08
LVM is actually Logical Volume Manager.  Sorry, I could have spelt that out earlier ;)  It's basically a way to treat a whole bunch of discs/partitions as one virtual drive, then make nicely-resizeable partitions on it.

---

### Post by aqk on 2006-01-04
Well after using Ubuntu BB 5.10 for a couple of months, I noticed my linux  data in its partition getting bigger and bigger, and my Windows partn data getting smaller and smaller (after I deleted a few win apps).
  You can see where this is going... ;-) 
  Hmmnn.. how to increase the linux partn? 
  I easily reduced the size of the Win partion with GPARTED, but of course, it would not let me un-mount my Linux partition to make it bigger.
 So I finally joined this forum, did a brief search and BINGO! 
  The obvious:  BOOT FROM THE LIVE CD and run GPARTED.  !
  It pays to lurk.

  Thanx, guys... haven't tried the LIVE gparted yet, but I hope it works.

   Incidentally, my trustworthy old Partiitionn Maggic 8.0 diskette which I have
used for years on Windows partitions, shows the Linux hard disk as one
bigg error on drive, and will not do anything with the disk,  so that's why I'm using GPARTED.  Any know why partttition majik show the boot sector as being in error? 

   Will come back here once I increase my  linux partition - I'm getting that sign-in error at boot time necessitating  a periodic  'sudu apt-get clear' which releases at best about half a meg...  

    -  Tony      [www.tonyking.tk]("http://www.tonyking.tk")

---

### Post by dartakaum on 2006-01-04
the last time i did that i ended up formating my entire drive! :)

and i still left 10gb to win, but now i'm wondering if it is worth... after u format and add your partition say how it went. :)

---

### Post by aqk on 2006-01-06
The GPARTED on the LiveCD worked like a charm. :p 

 I simply booted from the LiveCD, mounted the hard disk partition, beyond which was about 10 gig of empty space, and increased my partition size by 10 gig.

  Worked just like Windows' Partition Magic, except the boot was extremely slow,considering it had to install and copy stuff to a RAMdisk (I assume).

  The disk resizing was actually faster than the boot and login process.

   :confused: Now, all I need to do is figure out how to make a boot diskette with GParted on it, similar to the PartitionMagic diskette.  
    Actually, a boot from a USB flash drive would be even better!

   **- Tony (aqk)    [www.tonyking.tk]("http://www.tonyking.tk")**

---

