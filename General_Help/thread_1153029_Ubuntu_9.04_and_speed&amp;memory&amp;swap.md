---
title: "Ubuntu 9.04 and speed&amp;memory&amp;swap"
date: 2009-05-08
forum: General Help
---

### Post by ypeskov on 2009-05-08
Hi,

i have some strange problem:

When i am loging in system everything is OK. but in some period of time (about after 1 hour of work) especially when i start a lot of heavy applications speed of system is getting extremely down. When i take a look of usage of memory and swap i see next:

from 1gb of total memory about 500mb are used
at the same time from total about 3gb of swap about 800mb are used

well, it's normal because i use heavy applications. 
But after closing everything some memory is freed and swap is left at the same level and even starting to grow. Sometimes it grows up to 1.2-1.4 Gb
And all time hard disk is working very much (as  i understand it is changing info with swap).

After 3-4 hours i have to reload system to be able to work normaly, no just to be able to work.

Where coud bethe problem? in 8.10 everything was ok.

Yuriy

---

### Post by dabl on 2009-05-08
> **ypeskov said:**
> Hi,

Where coud bethe problem? in 8.10 everything was ok.




The only way to find out is to monitor the processes and figure out which one(s) are using the disk.  I would open "top" or "htop" and leave it open the entire time you use the computer, and notice which process is working when you close all your other packages.

For example, if it is a new system, maybe strigi daemon or nepomuk are making an index of your disk?

---

