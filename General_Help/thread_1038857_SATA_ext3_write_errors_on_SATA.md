---
title: "SATA ext3 write errors on SATA"
date: 2009-01-14
forum: General Help
---

### Post by imaca on 2009-01-14
Hi,
 have recently installed a new 500GB disk.
I installed 8.04 at the same time (on existing disk) but have now noticed that when I copy files to an ext3 partition on the new disk file errors occur with many of the files. I only noticed because I copied over my photos and these are quite obviously corrupted.
Initially I thought it may be a problem with the sil3112A sata chip on my old nforce2 motherboard, but today I copied 10Gb of data to an ntfs partition on the same disk using winXP and there is NO apparent corruption of files whatsoever.
So... I am guessing that either
1  my ext3 patition on the new disk is corrupted (if so why does auto check not find it?)
2 there is some kind of driver bug in Ubuntu perhaps due to my old sata chip?
Does anyone have any help here?

Also forgot to mention -writting to original disk or dvd seems to be without problem, only writing to ext3 partitions on new disk seem to cause problem.

---

### Post by imaca on 2009-01-14
Hmm,
looks like I could be on my own here...
Anyway after a bit of research it seems that Seagate 7200.11 drives are dropping like flies (rumour is 30-40% failure rate) plus if you send it back you get another... so many users are getting 1 failure after another.
So my suspicion is now moving to the HDD, but doesn't explain why windows ntfs partitions seem to be working OK - are ntfs partitions more robust? is windows driver (shock horror) better than linux at error correction?
Please - any help on this??

---

### Post by Bucky Ball on 2009-01-14
A whole disk is usually not the problem. It is generally some bad sectors (or even one). An explanation could be the fried part of the disk is where you have put your ext3 partition. You could try reformatting and changing the positions of the partitions and seeing if the ntfs one then starts crashing.

If there is something intrinsically wrong with the mechanical side of the disk (not the platter(s)), that is another issue and ntfs may just crash a little further down the track losing you all your data. Ext3 could be telling you now there is a problem. I would swap the disk.

Another thing to remember is that ext3 organises data differently to ntfs (which bungs it all over and may just be missing the corrupt sectors on its bit, if there are any, which is why when it hits one, that partition will crash also).

Have you another ext3 partition on any of the other drives that may be sata? Linux is on an ext3 partition and you don't seem to be having any problems with that so this would definitely point to your new SATA drive, no matter how you think about it. Has a friend go an external sata drive with ext3 partition you could experiment putting data on?

---

### Post by imaca on 2009-01-15
Thanks for idea - I have an exteral sata HDD, which i connect using usb since i have only 2 sata plugs, so I will swap into this and see if it has same errors.

---

