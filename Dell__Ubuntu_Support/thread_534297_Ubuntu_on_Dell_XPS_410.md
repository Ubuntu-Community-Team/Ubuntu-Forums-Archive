---
title: "Ubuntu on Dell XPS 410"
date: 2007-08-25
forum: Dell  Ubuntu Support
---

### Post by dateg on 2007-08-25
Hello, I am trying to duel boot Ubuntu 7.04 and windows XP on my newly purchased XPS 410.  I would also like to have a partition for shared media (fat32 format).  I have been reading a lot in these and other forms, but I still have a few questions that I was hoping someone could help me with.

My thought process for how I would like to partition my hardrive is as follows (Please let me know if you disagree of have suggestions):

100 GB for Windows XP (NTSF format) on a primary partition
100 GB for Ubuntu (Ext3 format) on a primary partition
Note: I am hoping this will include both / and /home, but I am unsure if I should put the /home partition on another extended partition or not. 

8 GB for Linux Swap (linux-swap format) on an extended partition
Note: I have read that it is a good idea to make your linux swap twice the size of your ram.  I upgraded to 4 GB of ram, so I am not sure if I should still follow this advice and go with 8 GB in my linux swap partition)

Finally
112 GB for shared media (fat32 format) on an extended partition

The hardrive is 320 GB and already has 3 primary partitions.  One for the Dell Restore (3 GB), one for the Dell Utility (55 MB), and the other for windows with the rest of the hardrive.  I have read that it is necessary to remove these partitions because I am allowed no more than 4 primary partitions.  As I understand the situation, I will first need to burn the Dell restore and Dell utility to disks and then remove the partitions from my hardrive.  This should allow me to create the partitions I will need.  I have the standard desktop distribution of Ubuntu 7.04, which includes Gnome Partition Editor.  I have been playing with this a little, but haven't changed anything on my hardrive yet. 

Basically I am just looking for someone to let me know if I am on the right track here, or if I have gone totally wrong.  I have some experience using linux, but this is the first time I have attempted an install by myself, not to mention a dual boot.  I would really appreciate any advice anyone out there could give me.

Thanks,
John

---

### Post by ridgeland on 2007-08-25
I kinda went that route the first time.
I had fat32 for a shared data space.
It caused lots of annoyances.  There is no file owner with fat32.  Fat32 may be limited to file size of 4GB max.  There can be no links with files in Fat32.  I could not install downloads that were saved to fat32, I had to first copy them to a ext3 partition.

My PC I used fat32 for WinXP because ntfs caused problems when I installed SP2, a couple of years ago.  My wife's PC has Ubuntu 7.04 with WinXP on NTFS with ntfs3g and it works fine.  She keeps "shared" things on the NFTS partition.  My new PC is a Dell-Ubuntu and has no MS-Win.  I would reinstall WinXP to NTFS on the old one, but why waste the time.

Overtime you are likely to drift further and further from the MS-owned world.  I would backoff a little on the 100GB for WinXP.  Maybe 20GB for WinXP and a D: drive of 40GB NTFS for Data.  Then later you can change the D: drive without a major reinstall of WinXP.  

My philosophy is small OS partitions, several of 8-10GB and large Data partitions, 100GB.  All the OS share the Data partitions (ext3), even Firefox bookmarks are shared.  This makes new OSs easy, like trying SuSE 10.3 and Fedora8. It's also easy to keep Ubuntu 7.04 when I install Ubuntu 7.10.

You are allowed more than 4 partitions, 16 I think.  The last is called "extended" and hold the others.  i.e. P1, P2, P3, P4(extended holds P5-P16).  P5 in extended space works just like P3.

---

