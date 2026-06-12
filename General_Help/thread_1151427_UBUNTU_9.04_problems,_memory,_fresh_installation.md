---
title: "UBUNTU 9.04 problems, memory, fresh installation"
date: 2009-05-06
forum: General Help
---

### Post by Costas100 on 2009-05-06
I have been using UBUBTU as a dual boot for over two years now (with win98, XP and Vista.
My last working system was a vista computer (Lenovo IdeaCentre K 500 GB HD ) from the manufacturer and Ubuntu 8.04 added on top with no problems for almost a year now, except lately Vista crashed completely for unknown reasons (possibly automatic updates).
So today I took the plunge to replace Vista with XP (I located the drivers) and at the same time, do a fresh install with Ubuntu 9.04.
I had my hard disk prepared with gparted (ntfs at the beginning, fat32 next for files, followed by ext3 for Ubuntu and finally some more fat32 for more files. Ubuntu was installed and appeared fine, until I started to use the system.
I was unable to save anything and upon update (security updates) I got the following message:
> E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

I did run the sudo command as shown above, it was accepted, went through a series of Setting up and ended as:
> Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 ttf-dejavu 

and the problem become worst.

So I started all over again: (XP was still working and left it as is), I did a second gparted, formated the partitions (except the XP) and reinstalled Ubuntu 9.04
Same problems again. Only a bit more strange: When I checked the partitions with gparted there were two extended partitions (one using 3.03 GB and the other using 2.11 GB and two linux swap partitions).

I am at a loss and I am not sure what is the next step.
It is getting late tonight, I may try tomorrow morning a fresh install of XP in the full 500 GB and then install 9.04 over it without pre-partitioning and if this does not work then try also only 9.04 alone, without XP.

Any help will be greatly appreciated
Costas

---

### Post by mb_webguy on 2009-05-06
Sounds like it might be a bad drive.  Boot up the LiveCD and run fsck using the command "fsck -F *file_system_type* /dev/*xxxn*", where *xxxn* is the device file associated with the partition.  You can find this out using the command "sudo fdisk -l".

---

### Post by Costas100 on 2009-05-07
Thank you mb_webguy, I just did the fsck and found the following:
> ubuntu@ubuntu:~$ fsck -/dev/sda4
fsck 1.41.4 (27-Jan-2009)
ubuntu@ubuntu:~$ fsck -/dev/sda5
fsck 1.41.4 (27-Jan-2009)
ubuntu@ubuntu:~$ fsck -/dev/sda6
fsck 1.41.4 (27-Jan-2009)
ubuntu@ubuntu:~$ fsck -/dev/sda7
fsck 1.41.4 (27-Jan-2009)
ubuntu@ubuntu:~$ fsck -/dev/sda8
fsck 1.41.4 (27-Jan-2009)
ubuntu@ubuntu:~$ 

In the mean time, although everything seams to work the problem is there and it amounts that I cannot save anything and in most programs I cannot even open them because:
1. gimp: cannot create folder "home/costas/.gimp-2.6" No space left on device
2. openoffice: could not save important information due to insufficient disk space at the following location  /home/costas/.openoffice.org/3/user/backup  - In fact it cannot save anything
3. text editor: opens but cannot save unde ext3 for example Documents but will save in the fat 32 partition
and so on
4. even the desktop does not have any room. Cannot save a screenshot for example with a similar comment as above.

I do have some suspicions:
The computer had Vista pre-installed and for sometime now I was unable to figure out the full contents of the drive. It appeared that there where areas with hidden files to both Vista and Ubuntu. Now after repartition, format ect there are still areas of mystery marked unallocated. At the end of the drive there is 7.8 MB unallocated. Also the total HD size was 500 GB now in gparted shows a total of 466 GB. The computer is fairly new and there were no indications of damaged HD. Is there a possibility that some old stuff is still there? Can I do a total HD clean up with some external tool? (I am not sure if gparted will do that).
Thank you very much, I am still an UBUNTU person, I am sure we will figure it out.
Costas

---

### Post by Costas100 on 2009-05-09
This is just an update on this problem which unfortunately was resolved only after a total wipe clean of the hard disk, partition, reformat or the HD and finally installing XP first and my old UBUNTU 8.04 over it.
I did not try again the 9.04 since I ended up spending so much time, maybe some other time.
Every thing now works fine except some minor problems that will be solved soon.
Thank you all, this topic should now be closed
Costas

---

### Post by epidenimus on 2009-08-15
Windows is finicky.  I have read a few treble booting how-to guides that:
a.)  Windows needs to be installed onto the first partition on the disk.
b.)  Windows should be installed first; Ubuntu second, as Ubuntu and GRUB are very intuitive about picking it up and adding it to the list of bootable partitions.

Have you since tried to update to 9.04?  I'm curious how this works on a K series box.

---

