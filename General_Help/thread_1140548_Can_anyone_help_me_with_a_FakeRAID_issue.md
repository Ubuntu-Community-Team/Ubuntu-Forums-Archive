---
title: "Can anyone help me with a FakeRAID issue?"
date: 2009-04-27
forum: General Help
---

### Post by moodah on 2009-04-27
Hi,

I posted my fake raid issue over in the newbie area here: [http://ubuntuforums.org/showthread.php?p=7163943#post7163943](http://ubuntuforums.org/showthread.php?p=7163943#post7163943)

Im not so sure if it was a good idea!

Cheers

---

### Post by moodah on 2009-04-27
Been trying to get DMRAID working with my raid0.

ubuntu 8.10 intrepid.

I have two 500 gig drives in stripe with XP running on them for performance. XP was working fine. I threw a new 160 gig drive in my pc to run ubuntu since i couldnt get it to detect the raid. I set the new hdd as the first recognised disk in bios so Ubuntu would install the mbr to the 160gig. However now when in the OS, since it cant detect the raid, it cant detect XP so im kinda screwed.. Been trying a few things though and followed the FakeRAID FAQ and ended up here: [https://help.ubuntu.com/community/FakeRaidDebug](https://help.ubuntu.com/community/FakeRaidDebug)

I have 4 partitions on the raid.  Here are some more details.

----------

terry@ubuntu-TEZ:~$ sudo fdisk -u -l /dev/sda

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x91979197

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   143364059    71681998+   7  HPFS/NTFS
/dev/sda2       143364060   552957299   204796620    7  HPFS/NTFS
/dev/sda3       552957300  1576956464   511999582+   7  HPFS/NTFS
/dev/sda4      1576956465  1781753084   102398310    7  HPFS/NTFS

---------------

terry@ubuntu-TEZ:~$ sudo fdisk -u -l /dev/sdb

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table

--------------

terry@ubuntu-TEZ:~$ sudo fdisk -u -l /dev/sdc

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x124b124a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63   300431564   150215751   83  Linux
/dev/sdc2       300431565   312576704     6072570    5  Extended
/dev/sdc5       300431628   312576704     6072538+  82  Linux swap / Solaris

---------------

also.

terry@ubuntu-TEZ:~$ sudo dmraid -r
No RAID disks
terry@ubuntu-TEZ:~$ sudo dmraid -rD
No RAID disks

terry@ubuntu-TEZ:~$ sudo dd if=/dev/sda of=outputfile skip=976771168
2000+0 records in
2000+0 records out
1024000 bytes (1.0 MB) copied, 0.0968202 s, 10.6 MB/s


Im attaching the outputfile so anyone can take a sneakpeek to see if anyone can find out how to fix this for me. (Im sure this happens alot since the debug page says to ask the community for help!)

Thanks in advance!

---

### Post by ronparent on 2009-04-27
I run a simular setup dual boot xp/ubuntu 8.10. If I read your post correctly, you can't find your windows partition while booted in ubuntu. I had the same problem.

Here is what you do. If dmraid is not installed, do** sudo apt-get install -y dmraid** in a terminal. After dmraid is installed you can verify your raid partitions by running **dmraid -s**. You will also find the 'sybolic links' to the raid array in /dev/mapper/. You use notations in fstab to automatically mount whichever partition you want to boot in /media/, or any aternative location in your filesystem.  The mounting instruction will be added to /etc/fstab and will take the form:

Example:
#/dev/sdb  nvidia_aebhdfib6  e:\PROGRAMS
/dev/mapper/nvidia_aebhdfib6	/media/WinXP-e-PROGRAMS	auto	relatime	0	1

Where /dev/mapper/your_raid_partition_here is substituted for my reference above. In the case above, you must create an empty directory ie /media/winXP_your_name to serve as the mount point. This last name is whateve you find meaningful. The /mapper/ name is the exact name you find in that directory for any particular partition you want to mount. Anything on a line after the # symbol is a comment. On reboot you will find your slected windows partion mounted.

---

### Post by moodah on 2009-04-27
Thanks for your reply.

The output shows.

terry@ubuntu-TEZ:~$ sudo dmraid -r
No RAID disks
terry@ubuntu-TEZ:~$ sudo dmraid -rD
No RAID disks
terry@ubuntu-TEZ:~$ sudo dmraid -s
[sudo] password for terry: 
No RAID disks

DMraid is installed - It just cant find any raid mapping data. I dont know how to get DMraid to find the correct data on the drive to discover it.

---

### Post by ronparent on 2009-04-28
Now that I have more thouroughly read you second post I see that you are already doing what you should be doing for a fakeraid. There are a couple of possibilities here. 1) That it is not truly a fakeraid but completely a software raid. In which case you could maybe use mdadm to assemble your array. 2) That it is actually a hardware raid requireing a proprietary linux driver and that you would have to acquire or assemble your own driver. 

So I guess the question is what is the hardware? Is it on the motherboard or a separate card? Is it set in your motherboard bios or its own secondary bios that appears on boot after the motherboard bios has loaded? I might not be familiar with your specific hardware if it has special requirements but someone else may be if they know what they are dealing with.

---

### Post by moodah on 2009-04-28
Hi,

Its definitely a fakeraid and not a software raid. My motherboard is a GA-N680SLI-DQ6 revision.1. [http://www.gigabyte.com.tw/Products/Motherboard/Products_Overview.aspx?ProductID=2460](http://www.gigabyte.com.tw/Products/Motherboard/Products_Overview.aspx?ProductID=2460)    There are 3 Raid controllers on board.. first is a 6 port NVraid controller. And the second two controllers I am pretty sure are JMIcron controllers, 2 ports on each one.   I have the 2 500gigs attached to a JMIcron controller.

All the raid controllers have their own bios they boot after the main motherboard bios.

This is what Ubuntu documentation says about my problem.

[https://help.ubuntu.com/community/FakeRaidDebug](https://help.ubuntu.com/community/FakeRaidDebug)

(copy + paste)
-----------------------------
**"dmraid -r" just returns "No RAID disks."**

 If you get this error message, this page is the place for you. 
1. First run the comand "dmraid -ay -vvv -d". If errors show up here, that probably indicates that other problems outside of dmraid exist with your disk. 
2. Run the command "dmraid -b" and make sure that dmraid can see your block devices. 
3. Run the command "dmraid -rD" and look for the three output files: ( .dat, .offset, .size ). If it generates these files, pack them up, post them and ask for help. Use the command "tar jcvf yourfilename.tar.bz2 *.{dat,size,offset}" 
You're done!  
**"dmraid -rD" generates no files**

 Run the command "fdisk -u -l /dev/sda" (if sda is not your disk, change it) You'll get something like this: 
Disk /dev/sda: 160.0 GB, 160000000000 bytes 255 heads, 63 sectors/track, 19452 cylinders, total 312500000 sectors Units = sectors of 1 * 512 = 512 bytes 
Subtract 2000 from the number of total sectors. For example, 312500000 minus 2000 = 312498000 
Run the command "dd if=/dev/sda of=outputfile skip=312498000" (changing sda and skip= to your values) Pack up the outputfile using the tar command above, post it and ask for help. ALSO include the output from the fdisk command above. 
NOW you're done! 
--------------------------------

---

### Post by ronparent on 2009-04-28
I presume then that you have properly configured your array in the JMIcron raid bios since you have been running winXP on them. The instructions you cited in your post look appropriate. If worse comes to worse and you get no success you can try removing and purging dmraid and reinstalling it with sudo apt-get install -y dmraid. Once that command is run sucessfully the symbolic links for your raid partitions (volumes) should appear in /dev/mapper/. Once that happens you can edit /etc/fstab so the partions you want to see are mounted on boot.

---

### Post by moodah on 2009-04-28
Gday.

Ive removed and added DMraid multiple times on two installs.. Its not the problem. 

As above though, ive pasted an excerpt for this actual problem written in a Ubuntu support page. (see above).  Youll see that Im exactly up to the part where the documentation says: "package the output and ask for help".  :(

---

### Post by ronparent on 2009-04-28
That's your best bet. JMIcron is supposedly supported (dmraid -l) so this appears to be a bug. Good luck.

---

### Post by moodah on 2009-04-28
Ahhh.. Yes but the problem is I have no idea where I should be asking for help! The fakeraiddebug page says "package the file and ask for help"...

but wheeere?

---

### Post by ronparent on 2009-04-29
You could go to the fakeraidDebug link in your prior post where you will find another link near the bottom of the page to a launchpad thread. That may give you more info on the problem. Also you could post a bug report in launch pad.

I wouldn't have believed that a chip  maker would use a deviant method to write the partition table section for the array, but, that appears to be the case. Their driver for windows takes care of that. But, unless they have released a linux version you are pretty much dependent on someone having written a linux patch for that problem.

Alternatively you could make a backup image of your complete windows installation, plug your drives into two of the nVidia ports, reconfigure your raid in the nVidia bios, and restore your windows to the array. That may be like the choice between a sharp stick to the eyes or a sharp knife to your gonads [http://ubuntuforums.org/images/smilies/smiley-faces-75.gif:lolflag::lolflag::lolflag:](http://ubuntuforums.org/images/smilies/smiley-faces-75.gif:lolflag::lolflag::lolflag:). Good luck in either case! I'm sorry I can't be more help.

---

### Post by moodah on 2009-04-29
Well.. Good thing for me theres not data on there I need. Maybe I will just swap them to the NVidia raid..

I hate defeat.

:P



Thanks for your help!

---

### Post by AzT3K on 2009-05-06
Hey out of interest version of dmraid are you using?

type "dmraid --version" at the console

if it says you have rc15 you are screwed anyway.  You need to get rc14 from the intrepid package repository and install it manually with dpkg - rc15 would not recognise my nvidia fake raid setup so my system died on upgrade to jaunty.

even with a fresh install it still didn't work and i had to boot from the live cd and chroot to the old install after i had installed dmraid in the live session. then i had to install dmraid on the chrooted session by calling dkpkg -i packagename.deb to install the packages i had manually downloaded from the intrepid package repository. then ran update-initramfs and update-grub and the system was then able to recognise my raid arrays - although i still have to call dmraid -ay then exit when i get thrown out to the busybox, but hey at least i can use my computer again now.

---

### Post by flamsmark on 2009-05-17
> **AzT3K said:**
> if it says you have rc15 you are screwed anyway.  You need to get rc14 from the intrepid package repository and install it manually with dpkg - rc15 would not recognise my nvidia fake raid setup so my system died on upgrade to jaunty.

Your comments are interesting. Are you saying that the default dmraid package on jaunty (unlike previous releases) does not work with nvidia fakeraid arrays?

I have an nvidia fakeraid (3 disks in a raid5) on the same N680 chipset as the OP. I just did a fresh jaunty install alongside xp, and 'dmraid -ay' detects my array, but doesn't activate it. Do you think that your problem and solution are applicable here?

---

