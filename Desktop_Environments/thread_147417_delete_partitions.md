---
title: "delete partitions"
date: 2006-03-20
forum: Desktop Environments
---

### Post by wfp on 2006-03-20
I have a old post back a page or so any way my linux install did not take, so i reinstalled windows but it ignored my linux partitons so im stuck with 20gigs space i can not use, i can not afford a program like partiton magic, but i found this program called partiton logic, was wondering if i go in and delete the linux partition and the swap partition, and reinstall windows again should it reformat the whole drive back to NTFS.wayne

---

### Post by Titus A Duxass on 2006-03-20
You could use fdisk or cfdisk they can be found on most distro CDs.

Alternatively google for "ultimate boot CD".  That is the most useful tool you can have in you box when it comes to messing around with partitions.

---

### Post by outofnicks on 2006-03-20
You have a free partition editing app on the install CD, called parted.
Boot the CD, find the option to exit to shell (can't remember for sure if the option is available at the beginning--if not, where ever there's a "Go Back" button you can get there) then type 
```
parted
```
then
```
 p 
```  (print)

if the Linux partition is still formatted, delete it:
```
rm 2
```
Replace "2" with the appropriate number seen in the print list. Do the same with the swap partiton.
The deleted partitions may merge on their own with your Windows one, not sure--or will remain a partition of free, unformatted space.

If the latter, just resize the Windows partition to the full disc size, from start to end. 

parted manual here, going to resize instructions:

[http://www.gnu.org/software/parted/manual/html_mono/parted.html#TOC25](http://www.gnu.org/software/parted/manual/html_mono/parted.html#TOC25)

Take my advice with a grain of salt, I'm a newbie--but this should work. I used parted to ***shrink*** my Windows partiton to make room for Linux, no problem. You are always advised to back up your data before using parted.

---

