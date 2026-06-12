---
title: "Cannot install Vista."
date: 2011-04-29
forum: Dell Ubuntu Support (CLOSED)
---

### Post by CIMMajor on 2011-04-29
My brother wants to re-install Windows Vista over his installation of Ubuntu because Linux does not get as much software support as Windows does. I suggested and even tried to install WINE on his computer but he would not have it, he insisted he wants Vista back. 

Now, the problem I am having when trying to get Vista installed back on his hard drive is that the main partition(the local hard disk) is not of NTFS type and therefore will not let me install Windows over Ubuntu. I have tried the command prompt convert trick but the only drive I can access is drive "X:" and it claims that it is already an NTFS drive. 

My brother's computer is a Dell XPS 400.

---

### Post by oldfred on 2011-04-29
Windows will install to unallocated space if you have a primary partition left or to a NTFS partition with the boot flag set.

You will have to use gparted from a liveCD to erase the existing partitions and create the NTFS partition as a primary sda1 thru sda4 partition. Then right click and manage flags to add boot flag.

You could make it dual boot?

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

---

