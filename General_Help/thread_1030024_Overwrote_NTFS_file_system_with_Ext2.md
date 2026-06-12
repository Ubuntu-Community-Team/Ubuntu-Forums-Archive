---
title: "Overwrote NTFS file system with Ext2"
date: 2009-01-04
forum: General Help
---

### Post by scrapnad on 2009-01-04
I have recently installed Ubuntu.  When windows did not show the drive it was installed on in My Computer I changed the file system on the drive with a program to Ext2.  I thought I was only doing the partition with Ubuntu on it but I changed the whole drive.  Now the drive shows up in my compiuter but it is completely empty.  Is there any way to reverse it back to NTFS and retrieve my files?

---

### Post by semi_fiction on 2009-01-04
When you say "shows up in my computer but is completely empty," do you mean shows up in Ubuntu? Because if it shows up empty mounted in Ubuntu, you have formatted your drive and unfortunately cannot get your data back.

Any ext2 or ext3 partition will not show up in "My Computer" under Windows. It simply doesn't recognize it.

---

### Post by Sef on 2009-01-04
If you did reformat your Windows partition, then check out [Test Disk]("http://www.cgsecurity.org/wiki/TestDisk").  It can restore deleted partitions.

---

### Post by HermanAB on 2009-01-04
I don't want to totally discourage you, but the probability of recovering your data is somewhat less than a snowball's chance in hell because Linux always writes to the disk when you start your system up - log files and such - and recovering data only works if nothing has been written to disk since the mistake was made and even then it is not so good.

So, enjoy your nice clean Linux system!

Cheers,

Herman

---

### Post by scrapnad on 2009-01-04
Well when I was installing it got to 20% and then said it couldn't be installed...the only time I started it back up I chose the option to run it from the CD.  I thought that there might be something wrong with the CD.  

I suppose I will try the test disk.  I'm running the 'Recover my Files' program right now.  I'll see how that goes...

---

