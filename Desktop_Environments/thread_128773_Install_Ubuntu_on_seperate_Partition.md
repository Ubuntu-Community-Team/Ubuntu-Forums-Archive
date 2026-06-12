---
title: "Install Ubuntu on seperate Partition"
date: 2006-02-12
forum: Desktop Environments
---

### Post by LaserLight on 2006-02-12
Hi,

On mij new PC was XP preinstalled on a 80Gb HD / NFTS.

I've installed Ubuntu with help from this site:

[http://users.bigpond.net.au/hermanzone/p3.htm](http://users.bigpond.net.au/hermanzone/p3.htm)

I've made a screen picture, hopefuly it is correct added:

/dev/hda    76324MB           
/dev/hda1  NTFS  9535 MB  (lock)
/dev/hda3  EXT3  9099 MB  (lock)
/dev/hda2  Extended  55365  (lock)
/dev/hda6  Linux/Swap 424 MB  (lock)
vrij                                 8 MB
/dev/hda5   FAT32   54933 MB  (lock)
/dev/hda4   FAT32   2322

Mijintention is that Ubuntu 5.10 stays on
/dev/hda3 so if I want to Upgrade I can do it there.

 /dev/hda5 was ment to hold :
- to install all the aded Ubuntu/Linux programs
- to save al the documents (oo.o.org) so I can work there with XP and Ubuntu
- to save al the savings from Ubuntu
-  to save all the email and saved sites from the browsers.


How can I install or rearange the Ubuntu maps to get this working ?

Cheers.

---

### Post by alfotis on 2006-02-12
Files needed for the ubuntu settings, must have certain permissions like -rwxr-xr-x or something.
 This can't be done under a FAT32 filesystem. How about storing all your documents (I mean documents that YOU create, and not the system) in a separate partition. At least, that's what I do.

Also, you can see [Paragon Mount Everything]("http://www.mount-everything.com/"), but my advise is to mount your linux partition as read only (at least for start, just to make sure that the program works fine - remember, it runs on Windoze... ;) )

---

