---
title: "Preinstalled Windows and Ubuntu dual boot"
date: 2012-09-21
forum: Dell Ubuntu Support (CLOSED)
---

### Post by resander on 2012-09-21
I am thinking about getting a Dell Vostro 470 with a 3rd generation Intel processor. This is shipped with Windows 7 (64-bit) pre-installed and I believe there is a recovery CD too.
 
What are the implications of Windows being pre-installed for dual booting with Ubuntu?

-  can gparted on the Ubuntu Live CD be used for shrinking the Windows  partition(s) to make room on disk for Ubuntu? Or would I have to use some partition editor that comes with Windows? 

- I hardly ever use Windows but still want to keep it and give it a very small portion (10GB say) of the disk and let Ubuntu 12.04 have the rest.  Is that possible?

- I assume the install image/recovery disk is bound to the hardware and would not work on another PC or same PC if the hardware is changed. Is that so?

- Anything else that is frustrating, irritating or awkward with having a pre-installed Windows?

- Can I request a normal install CD when buying a Dell?  

Ken

---

### Post by ajgreeny on 2012-09-21
All will depend on the how Dell partition their Windows 7 installation.  Some OEMs seem to insist on using all of the 4 partitions that are available if the system has the now old style BIOS, with an msdos partition table.  If so you will probably have to decide which partition to remove/delete before you can add any more for the ubuntu installation.

You can easily see what Dell have done before you buy;  you will need to ask the salesman to tell you, or ask him to start the disk management utility in Win 7 and see how many partitions there are already.

---

### Post by black veils on 2012-09-21
> would I have to use some partition editor that comes with Windows?  yes, use the windows partition editor to shrink the partition, leave the space as unallocated, no need to format. then restart to make sure there are no errors. proceed with gparted for linux-y things.

> I hardly ever use Windows but still want to keep it and give it a very small portion (10GB say) of the disk and let Ubuntu 12.04 have the rest.  Is that possible? [http://windows.microsoft.com/en-us/windows7/products/system-requirements](http://windows.microsoft.com/en-us/windows7/products/system-requirements)  so maybe 35 to be safe? depends on if you will have games/media on there.

---

### Post by oldfred on 2012-09-21
If it is real new, it might be UEFI. Then you do not have 4 partition limit, but have to use 64 bit version of Ubuntu and from install disk boot into UEFI mode.  If it is UEFI come back and ask for more details. Even with UEFI it may still have Windows in BIOS mode.

---

### Post by JKyleOKC on 2012-09-21
> **resander said:**
> - I hardly ever use Windows but still want to keep it and give it a very small portion (10GB say) of the disk and let Ubuntu 12.04 have the rest.  Is that possible?When you use the Win7 Disk Management tool to shrink the Windows partition, it will decide how far you can reduce it. The NTFS file system that Microsoft uses is built around what they call the Master File Table and for some reason this seems to be placed about the middle of the partition and cannot be moved, so you won't be able to reduce Windows as much as you want. On my recent dual-boot installation with an HP machine, I could only get a bit less than half of the 500 GB disk freed up for installing Linux. Fortunately that was plenty for my needs and I still have well over 100 GB free in Linux, but it sorta burns me that I have more than 200 GB "wasted" on a Win7 installation that I may never use at all...

---

### Post by over_my_head on 2012-09-22
i'm also trying to dual boot Win7 and Ubuntu. I used the Windows disk management utility to shrink the Windows partition and I left the space as unallocated but when i try to install Ubuntu it says the space is unusable.


my hard drive had Win7 preinstalled and is using 4 primary partitions, i've attached a screen shot of gparted (running off the ubuntu 12.04 live CD on the laptop i'm trying to dual boot).


so do i need to delete one of the 4 existing primary partitions and if so which one should i delete?

---

### Post by JKyleOKC on 2012-09-22
Read this before going any farther: [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

It's essential that you know which of the two types of bootloaders your Win 7 installation is using, since the Ubuntu installation must use the same type and at the moment, the installer doesn't always make the right decision. The four-partition limit applies only to one of them, not both. Therefore you may not need to make any more change to the partitioning, but rather may need to change the bootloader type. The link above tells you how to tell which is in use, and how to force the proper setup.

---

### Post by black veils on 2012-09-22
> **over_my_head said:**
> 
so do i need to delete one of the 4 existing primary partitions and if so which one should i delete?

yes, and people with hp computers, with the same issue, say its ok to remove hp-tools. 

i dont know about the rules for shifting your partitions around though, in terms of moving the large unallocated space to the end, or if it even matters. i have never needed to know that stuff.

---

### Post by oldfred on 2012-09-22
If you have Windows and the first partition is efi formated FAT32, and drive is partitioned gpt not MBR then you have UEFI. 
If first partition is just the 100MB boot partition (hidden in Windows and NTFS)  and partitioned with MBR then you have the four partition limit. If Vendor recovery is first partition then the 100MB may be second partition. HP usually puts recovery & tools last.

Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Be sure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)
For a complete blow-by-blow on dealing with HP's four partitions, see Full Circle Magazine, issue 41, page 36. 
[http://fullcirclemagazine.org/](http://fullcirclemagazine.org/)
Shrinking a Windows 7 partition is best done in Windows. But do not create new partitions with Windows.
[http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/](http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/)

---

### Post by over_my_head on 2012-09-23
thanks for the information!

---

### Post by resander on 2012-10-06
OldFred:
Many thanks for the links.

These and other links referred to helped me to reduce the size of Windows 7. 
Luckily it turned out to be very easy.  I  

- downloaded and installed the free disk frag program (aus) from [www.auslogics.com](www.auslogics.com) (very good and shows allocation diagram)
- first ran the W7 defrag function and this reported 8% fragmentation (but no diagram). 
- ran aus 'analysis' function which showed space allocated at the end of the w7 partition stopping any reduction in size.
- defragged by aus. No effect. There were still blocks allocated at the end of W7 partition.
- defragged by w7 again and then defragged by aus. This time I managed to reduce the W7 size! Don't understand why it did not work the first time.

I could have reduced the size a bit more, but stopped and installed Ubuntu 12.04 and restored my data and programs from backup dvds. Ubuntu ran extremelly well. 

I don't know if I could have repeated the procedure reducing the size of w7 a bit each time. Anyone knows or willing to try? Of course before adding Ubuntu in case W7 would suddenly hang and need a restore.

W7 disk management only allowed a reduction of size to about 50%.  Would it insist on having 50% of 1TB or 2TB disks too? That would be intolerable if you only need a small W7.

Ken
P.S. attaching the gparted display after the Ubuntu 12.04 install.

---

### Post by oldfred on 2012-10-06
If installing from scratch you can get Windows into 30GB or smaller. And then have a separate shared NTFS for any data you may want to use from both systems.

This was for Vista but I think the same applies to 7.
Windows Vista - partition your hard drive using Disk Management, if XP use Gparted
25GB at an absolute minimum 
[http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/](http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/)

Some of the third party tools work better at shrinking Windows. Some have used gparted and it has worked, but some have reported issues so we usually suggest Windows tools for Windows & Linux tools for Linux. After a resize Windows will need chkdsk or other repairs, sometimes it will do that itself and sometimes you need the repairCD or USB.

---

### Post by resander on 2012-10-06
Some threads are pointing the finger at the MFT refusing to leave the end of the Windows partition and therefore stopping the partition to become smaller. I did not observe this for W7. Maybe that is for Vista only.

When preinstalled the MFT was on the first row reported by the auslogics defragger. After shrinking the w7 partition and installing Firefox the MFT had moved to the center. See attached screenshot. 

So for w7 the MFT does not appear to be the culprit. There is other information that appears at the end following shutdown and reboot. Do not know why and what it is. If I were to redo the Ubuntu install I would try using auslogics and w7 defraggers only:

1.  defrag with w7; defrag with auslogics
2.  repeat from 1 until target size reached or the w7 partition not getting any smaller

and see how it goes.

If anyone tries this for W7 please post the outcome, OR what happened if you tried something else.

Ken

---

### Post by JKyleOKC on 2012-10-06
The MFT (Master File Table) is a key part of the ntfs structure and has been around since WinXP. Once it's in place, defraggers consider it to be unmovable -- but Windows itself can and does move it from time to time.

My best guess is that on a clean install of Windows, the MFT gets put close to the front of the disk area because that allows installation on smaller drives, but after the first few times you store large files (such as by installing FireFox) it moves to the center. Every time I've run the Auslogics defragger (on XP; I've not run it on W7) the MFT has been approximately in the center of the disk.

As for putting stuff near the end of the disk, most defraggers seem to use that as a temporary storage area while doing their job. They usually clean it out, but sometimes leave a few clusters there. Your approach of using two different programs, alternately, is a good idea -- each may do things that the other doesn't notice. And my observation is that none of them for ntfs do as good a job of packing down the data as the old vfat system could do. I always have chunks of free space scattered through the "defragged" data.

Finally, I'd steer clear of the "defraggler" program. My favorite repairman recommended it to me, but when I used it on my wife's WinXP system the data got totally scrambled and could not be recovered. Fortunately I had backed things up to an external drive and could reinstall XP from scratch, then restore the backup, but I no longer trust that program. I've found Auslogics to be quite reliable, and now recommend it exclusively.

EDIT: You might try defragging W7 again, after shrinking it. Windows just **might** move it to the center of the smaller area, allowing additional shrinking. If that works, you can then expand the Ubuntu partitions into the resulting unallocated area **without** having to re-install -- although as always good backups should be available in case anything goes wrong, as it did for my use of defraggler...

---

