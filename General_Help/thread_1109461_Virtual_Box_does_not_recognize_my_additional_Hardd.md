---
title: "Virtual Box does not recognize my additional Harddrive"
date: 2009-03-28
forum: General Help
---

### Post by steffenklug on 2009-03-28
Hi,
I am new to Ubuntu. I am very familiar with MS.
My current setup: Ubuntu 8.10
I loaded VirtualBox and it runs.
Unfortunately my hard drive is too small so I added another one, which I can access and read files from. It is FAT32.

When I goto VirtualBox (2.04) and Preferences and try to pick the new hard drive.
it is not there, (I just see Computer and my original drive) but
If I go to the Ubuntu Menu: Places - Computer - It is listed as "70.0 GB Media" and it is labeled removable.
Note: I can not rename it.

Thanks for your help

---

### Post by ene_dene on 2009-03-28
Your hard disk is probably mounted in directory /media/some_dirname.
That is the location you need to find in virtualbox.

---

### Post by steffenklug on 2009-03-28
Thank you 
I did not realize that was a choice and additionally 
it did not represent the correct name.
(The name is 70 G... [which I can not change])
and the entry was /media/disk
but it is all good now thank you

---

