---
title: "Boot error"
date: 2011-04-19
forum: Dell Ubuntu Support (CLOSED)
---

### Post by ohadgo on 2011-04-19
Hi,
 
I used to have ububtu (9.04 i think) last year.
During the period i used ubuntu i encountered 2 times the same error:
 
error:file not found.
Grub rescue>
 
I didn't succeded with finding how to boot nor to save the data.
 
----
 
Now i have win7 (for the last 10 month,i don't know how it was installed - wasn't done by me) 
and i had the problem again.
This time, i tried to use win7 original disk **("repair --> boot.. ")**
 
Therefore,
I see the next message instead :
 
[COLOR=black]**"Missing operating system"**[/COLOR]
 
(without possibility to write anything)
 
Maybe grub was removed by win repair?
I hope someone can advise me how to boot to win7.
 
Thanks,
Ohad
 
Results:
-----------------------------------------------------------
                Boot Info Script 0.55    dated February 15th,
2010                    

============================= Boot Info Summary: 
==============================

 
=> Windows is installed in the MBR of /dev/sda
 
=> No boot loader is installed in the MBR of /dev/sdb
 
sda1:
_________________________________________________________________________
    
 
 File system:       ext4
    
 Boot sector type:  -
    
 Boot sector info:  
    
 Mounting failed:
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
 

sda2:
_________________________________________________________________________
    
 File system:       Extended Partition
    
 Boot sector type:  -
    
 Boot sector info:  
 
sdb1: 
_________________________________________________________________________
    
 File system:       vfat
    
 Boot sector type:  Fat16
    
 Boot sector info:  No errors found in the Boot Parameter Block.
    
 Operating System:  
    
 Boot files/dirs:  
 
=========================== Drive/Partition Info:
 =============================
 

Drive: sda ___________________
 _____________________________________________________
 
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
 
Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   300,560,084   300,560,022  83 Linux
/dev/sda2         300,560,085   312,576,704    12,016,620   5 Extended
Empty Partition
 
 

Drive: sdb ___________________
_____________________________________________________
 
Disk /dev/sdb: 1992 MB, 1992294400 bytes
6 heads, 5 sectors/track, 129706 cylinders, total 3891200 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
 
Partition  Boot         Start           End          Size  Id System

/dev/sdb1                 256     3,891,199     3,890,944   6 FAT16
 
 
blkid -c /dev/null:
____________________________________________________________
 
Device           UUID                                   TYPE
LABEL                         

/dev/loop0                                             
squashfs
/dev/sda1        3a1f16dd-b379-4f5c-99a2-df622a6f7551   
ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda: PTTYPE="dos" 
/dev/sdb1        78EC-984C                              
vfat                                     
/dev/sdb: PTTYPE="dos" 
 
============================ "mount | grep ^/dev  output: 
===========================
 
Device           Mount_Point              Type       Options
 
aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /media/78EC-984C         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec,flush)

---

### Post by ajgreeny on 2011-04-19
Oh dear!!

I am uncertain from your post exactly what you mean or what you have done, but it is certain that you do not have a windows partition on disk at all.

Did you install 10.10 and try and put it alongside your Windows 7 install?

If so, I think you may have fallen foul of the trap in the 10.10 installer, which, if you try to install side by side on the "whole partition" installs to the "whole disk" and wipes out whatever was already on the disk.

I am not sure if you can do anything to get back your files etc, and I sincerely hope you have some backups.  If not it may be possible to use testdisk on a liver CD to restore at least some of the files that have gone.
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by ohadgo on 2011-04-19
thanks for your reply,
 
I didn't installed the 10.10,
 
I had old ubuntu version.
 
now i have win7 (untill today),** i do not have linux at all**
i've just use the live cd to create the Result file (try ubuntu)
 
currently i see **"Missing operating system".**
 
:(

---

### Post by ajgreeny on 2011-04-19
So tell us exactly what you did, one move at a time, because it appears that you have no windows installation on the machine, and according to what you now are saying, no Ubuntu either.

Currently you have the following, with my questions to you in [COLOR=Red]red[/COLOR]:-

/dev/sda1    *             63   300,560,084   300,560,022  83 Linux  [COLOR=Red]your old ubuntu partition?[/COLOR]
/dev/sda2         300,560,085   312,576,704    12,016,620   5 Extended  [COLOR=Red]an empty extended partition; previously swap?[/COLOR]
/dev/sdb1                 256     3,891,199     3,890,944   6 FAT16  [COLOR=Red]a USB disk?[/COLOR]

There is no ntfs partition, as you can see, so you seem to have lost your windows completely.

---

### Post by ohadgo on 2011-04-20
I shouldn't have linux partition,
Before it happened i could fill my whole HD in Win7.
Maybe thats what the live CD allocate?

sdb1-Fat16 : is the USB.

For some reason it doesn't show the NTFS :(
2 days ago i worked normally on my win7 untill **someone unplugged the electricity cable when the computer was without the battery** 

now i get the next error:

**"error loading operating system" **

I guess there is some problem with the first sector in the HD. 

Thanks

---

### Post by ajgreeny on 2011-04-20
I presume that you can not mount the windows 7 ntfs partition if you boot again to a live ubuntu system, but just to be doubly sure, can ubuntu live see that win7 partition at all, or is it totally either hidden or gone from the disk?  The results file suggests it is gone.

Things don't look too good to me, but I admit that I have no idea where to point you now to try to sort out the problem.

---

