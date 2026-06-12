---
title: "mssing space"
date: 2010-08-06
forum: Desktop Environments
---

### Post by illustrate38 on 2010-08-06
Major issues after working in wine yesterday I kept getting errors that disk is full.  I didn't bother looking to see if it was and figured it was an error on the WINE end.  It wasn't WINE but all of a sudden my system exploded in size and I can't figure out what has happened here.

After using "Disk Usage" and "File Lite" to see where the space is going nothing in size seems out of the ordinary.  The image adds up to be just around fifty gigs on a 225gb partition.  Gparted shows my disk has 9GB available.  I figure I must have a hard disk error that 175gb is missing.  I try several searches and still can't find any large hidden files, I don't even have a root trash directory.  I have a third hard drive of 500gb so I clean that off completely and reformat it.  I then boot off the Clone Zilla cd and clone a local to local and I can boot off the 500gb with out nay problems.  I reformat the original partition that is 225gb (sda1) and get ready to clone back over.  I then look at Gparted to check my 500gb to make sure all math was correct on my end for a 50gb image.  Nope on the 500gb I have 4.6gb available.

I decide to do a fresh 64bit install back onto the original drive and write over the files after with "cp -r" to get all my settings which sort of works.  After copying things over I have course ruined my MBR, but that is another issue, the total size of the image after copying is 11.9gb.

Medium to super experts tell me what the heck did I do and is all lost?

system is
Ubuntu lucid 64bit
(sda 1) 225gb ext3 partition for Ubuntu
(sda 2) 265gb ntfs partition for Windows7
(sda 3) 10gb swap

(sdb 1) 1TB NTFS back up

(sdc 1) 500GB ext 3 - cloned Ubuntu system

---

