---
title: "External Harddisk Mounting Problem"
date: 2008-05-17
forum: Dell Ubuntu Support (CLOSED)
---

### Post by bme on 2008-05-17
I have a toshiba 40 gb portable usb harddisk which was working perfectly on ubuntu gutsy(7.10).It has 2 partitions 15gb 1st partition and 25gb for the rest.
On 8.04 the second partition will not mount.It gives an error that the drive was not safely removed in windows and furthermore instructed me to "force mount" via command line or add a line to fstab with the second partition.
There is nothing wrong with the portable hd in windows nor have I safely uninstalled it. 
Is this a hardware issue with 8.04?

---

### Post by pytheas22 on 2008-05-17
I think I've seen errors like this in the past.  They're generated because Linux thinks that the NTFS partition that you're trying to mount is not clean, which could indeed be the case (run chkdsk in Windows to find out), or it could be a mistake on the part of the Linux ntfs driver.

The error message should tell you which command to use to force-mount the partition.  Open a terminal and try it.  This has always worked for me without a problem, although you should keep in mind that if something goes wrong you could lose data, so just make sure any important files are backed up.

If the error message doesn't tell you how to force-mount, please post a screenshot of it here.

---

### Post by bme on 2008-05-18
Yes I've tried the "forcemount" option and it does work. But why should I do this on 8.04 when I am not having this problem in Linux mint(7.10 ubuntu based)? both partitions mount automatically when I insert the usb drive on linuxmint.
Yes I also did the checkdisk in vista with no problems found....
I think this is a 8.04 problem.

---

