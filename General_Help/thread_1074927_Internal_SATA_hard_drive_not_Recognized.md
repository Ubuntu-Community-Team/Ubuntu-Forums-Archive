---
title: "Internal SATA hard drive not Recognized"
date: 2009-02-19
forum: General Help
---

### Post by pingiscoolest on 2009-02-19
I have a system running ubuntu 8.10 Intrepid Ibex, I have 3 Hard Drives installed, 2 SATA II, a 30GB SSD and a 1.5 TB spinning drive, and a 500 GB spinning IDE drive. I installed Ubutnu on the solid state drive with no partitions. When I run Ubuntu it only recognizes the 30GB SSD. The BIOS recognizes all three drives, and when I installed ubuntu it recognized both SATA drives (i didn't have the IDE drive plugged in at the time.). I am new to Ubuntu so if there is something you have to do to set up a hard drive for use I haven't done it. What am I doing wrong? Why won't Ubuntu recognize my drives? It recognizes my CD drive if that helps. Thanks in Advance

---

### Post by dcstar on 2009-02-19
> **pingiscoolest said:**
> I have a system running ubuntu 8.10 Intrepid Ibex, I have 3 Hard Drives installed, 2 SATA II, a 30GB SSD and a 1.5 TB spinning drive, and a 500 GB spinning IDE drive. I installed Ubutnu on the solid state drive with no partitions. When I run Ubuntu it only recognizes the 30GB SSD. The BIOS recognizes all three drives, and when I installed ubuntu it recognized both SATA drives (i didn't have the IDE drive plugged in at the time.). I am new to Ubuntu so if there is something you have to do to set up a hard drive for use I haven't done it. What am I doing wrong? Why won't Ubuntu recognize my drives? It recognizes my CD drive if that helps. Thanks in Advance

What does the Partition Editor show?

---

### Post by pingiscoolest on 2009-02-19
> **dcstar said:**
> What does the Partition Editor show?

it shows 3 partitions, dev/sda1 , dev/sda2 , and dev,sda3 . It show 2.86GB used in the first partition and none in the other 2. Sorry if I didn't give you what you asked for Ill be happy to provide more info.:D

---

### Post by Yellow Pasque on 2009-02-19
Can you post output of:
```
sudo fdisk -l
```

---

### Post by pingiscoolest on 2009-02-19
Heres a screenshot of the partition manager.



[http://www.flickr.com/photos/35566332@N07/3294612850/](http://www.flickr.com/photos/35566332@N07/3294612850/)

---

### Post by pingiscoolest on 2009-02-19
It asked me for my administrater password and after I entered that I got this







E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
david@davids-PC:~$  sudo apt-get install gparted
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
david@davids-PC:~$ sudo fdisk -l
[sudo] password for david: 

Disk /dev/sda: 32.0 GB, 32044482560 bytes
255 heads, 63 sectors/track, 3895 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xec8c65a6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3730    29961193+  83  Linux
/dev/sda2            3731        3895     1325362+   5  Extended
/dev/sda5            3731        3895     1325331   82  Linux swap / Solaris

Disk /dev/sdb: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table




I will admit I dont know what all that means but I see 1.5 TB in the last paragraph that seems good :)

---

### Post by Yellow Pasque on 2009-02-19
It looks like your 1.5 TB drive is unpartitioned/formatted. Correct?
> E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
You probably have Synaptic or Update Manager open. Close them before trying to run an apt command. Anyway.. you already have gparted installed.

You need to create partitions on your 1.5TB drive before you can use it. To do that, go into the Partiton editor and choose /dev/sdb/ (pull-down menu in upper-right of screen).

---

### Post by pingiscoolest on 2009-02-20
Well that was correct until about 10 minuites ago when I partitioned/formatted it :) Now I think I need to mount it is that correct? Sorry about the simple questions I just started using Ubuntu 2 days ago :)

---

### Post by Yellow Pasque on 2009-02-20
> Now I think I need to mount it is that correct?
Yes, I recommend right-clicking on one of your panels/taskbars, selecting "Add to Panel" and adding the disk mounter applet.

---

### Post by pingiscoolest on 2009-02-20
I tried to do that and for some reason I can add just about all the applets except the disk mounter Ill try again in the morning

---

### Post by Yellow Pasque on 2009-02-20
You probably added the disk mounter, but it has no partitions to show because you need to reboot.

---

### Post by pingiscoolest on 2009-02-20
Hey it works! I rebooted and there they were 30 disk mounting applets! I mounted my drive and now it works!

Thanks Guys!!

---

