---
title: "Ubuntu can see some of my external disk but cannot see some of them"
date: 2012-06-21
forum: Dell Ubuntu Support (CLOSED)
---

### Post by fairyoflinux on 2012-06-21
I have  Dell XPS X15Z-7502ELS laptop and I installed ubuntu 12.04. 
I didn't have any problem in installation stage and I did an installation in flash disk in USB drive. After installation I tried some of my external disks. 
Than the weird things happened. Ubuntu can see some of my external disks but cannot see some of them. I contolled the laptop usb  entrance and there is no problem . I also checked  thise external disk in windows 7. There is no problem in windows. 
Can anybody help me in this issue. I don't want to use windows 7 for only usb issue.
Thanks

Note: Although my laptop is 64, ubuntu installation for 64 bits didn't work and I installed for 32 instead

---

### Post by Lee_Bo on 2012-06-22
A little more information might help.  What make, model and size is working, and what make, model and size is not working?  Are all formatted the same way?

---

### Post by LiamOS on 2012-06-22
With everything connected, could you post the output of 
```
$ sudo fdisk -l
```I don't think architecture should have any bearing on this, but it may be due to the partitions or problems with mounting.


Edit: I'd also highly recommend installing a 64-bit system on a 64-bit machine, if it's at all possible. You may simply have had a problem with the download or burn resulting in some corruption.

---

### Post by fairyoflinux on 2012-06-23
when I run the command sudo fdisk -l the following are shwon :
  Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63      208844      104391   de  Dell Utility
Partition 1 does not start on physical sector boundary.
/dev/sda2   *      212992    41172991    20480000    7  HPFS/NTFS/exFAT
/dev/sda3        41172992   506192084   232509546+   7  HPFS/NTFS/exFAT
/dev/sda4       506193918   976771071   235288577    5  Extended
Partition 4 does not start on physical sector boundary.
/dev/sda5       506193920   964407295   229106688   83  Linux
/dev/sda6       964409344   976771071     6180864   82  Linux swap / Solaris

when I tried to install 64 bit it gives the following messages and installation just frozen . So I install 32 bits
[5.896735][Firmware Bug](ACPI)(PEGP) defines _DOD but not _DOS

The external hard disk which ubuntu doesn't see make is Philips. Actually it was seen perfectly my previous laptop (which was ubuntu installed in it) and it is also working with windows. But Right now it doesn't work on my new laptop and ubuntu.

---

