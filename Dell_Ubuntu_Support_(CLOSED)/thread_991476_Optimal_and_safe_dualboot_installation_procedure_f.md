---
title: "Optimal and safe dualboot installation procedure for XPS M1530?"
date: 2008-11-23
forum: Dell Ubuntu Support (CLOSED)
---

### Post by djdolber on 2008-11-23
Hello, im kinda a noob on this topic and i have searched and browsed this forum and the internet for a while now. I have a XPS M1530 and i want to dual-boot it with Ubuntu.

It has come to my attention that there is some serious issues with the MediaDirect button messing up partitions on the harddrive, and all the posts i have read on the internet has had different timestamps so im not really up to speed on that situation. Basically, the topic has been beaten to death already all over the internet, but, im having a hard time finding a final answer on the matter. One of the problems is that you cant trivially create a new primary partition since they are all taken up from the beginning, and if you mess with that to much, the media direct button will nuke your system or so i heard.

My question is, is there a safe way to dualboot a XPS M1530 with Vista and Ubuntu ? (If possible, without wiping the harddrive.) Has Dell made available a way to kill the MediaDirect button ?

Thank you in advance and sorry for posting such a noobish question :confused: :)

---

### Post by falcon61102 on 2008-11-24
Welcome to the forum.

Some people do experience trouble when deleting the media center partition because of how the media center button is tied into the system.  I don't know if you found this thread in your search, but it has some good information on what happens to the media button when messed with:

[http://ubuntuforums.org/showthread.php?t=794923](http://ubuntuforums.org/showthread.php?t=794923)

An option that you have besides completing deleting the media center partition and risking running into the above problems is using the media center button as a power button to start one of you OS's while the main power button starts the other OS.  So instead of relying on the GRUB to select the OS you want, you simply just press the button on your laptop.  Since I use Ubuntu as a primary, I set it up with Ubuntu coming on when I hit the main power button and Vista comes up when I hit the Media Center button.  The following is the walk-through I used to accomplish this:

[http://forum.notebookreview.com/showthread.php?t=231747](http://forum.notebookreview.com/showthread.php?t=231747)

If you have any questions or run into any problems, just post back here.

---

### Post by djdolber on 2008-11-24
Thank you for those links, before i go through with this, i would just like to ask another question... What i understand from theese two guides is basically that it will be impossible to do this operation without wiping my current installation.. 

My current system looks like this:
 - 118 MB
 - 10 GB "Recovery"
 - 154 GB "OS" (Shrunken)
 - 19,5 GB "unallocated space" (from shrinking the OS partition)
 - 2,5 GB "Media Direct"

Have i assumed right that it is impossible to merge "Recovery" with the "unallocated space" and use it to boot ubuntu ? I dont have any problem with not using the MD button to boot. But as i understood, these partitions are lined up physically on the disk the same way they are lined up visually in the vista disk manager, right ? If possible i would like to try this without wiping my current "OS" partition.

I saw somewhere that the ubuntu installation would be able to spot the unallocated space and create apartition there, is that a possibility ?

---

### Post by falcon61102 on 2008-11-24
I don't know about impossible but it would definitely make things more difficult to try to move all the partitions around.

As far as your current setup, you are correct.  The trick will be combining the Recovery and unallocated space.  If they are indeed seperated as you have them displayed, then you will need to move the partitions around a little bit for this to work.  It is an easy process, but a bit time consuming.

If you could, boot up from the LiveCD (installation disk) and open up a terminal window.  Then type the following code and copy it here:
```
sudo fdisk -l
```

This will list your partitions and give us a little more info to work with.  It will tell us for sure what order they are in.  If you can't access the web from the LiveCD, you can copy and paste the results of that command to a text file and save it on a USB drive so you can access it in Windows.

---

### Post by djdolber on 2008-11-24
Thanks for the tip, i tried that, this is the output i get:

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x50000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          15      120456   de  Dell Utility
/dev/sda2              16        1321    10485760    7  HPFS/NTFS
/dev/sda3   *        1321       21446   161651704    7  HPFS/NTFS
/dev/sda4           23995       24322     2621440    f  W95 Ext'd (LBA)
/dev/sda5           23995       24322     2620416   dd  Unknown
```

---

### Post by djdolber on 2008-11-24
So, i found this in a guide that says:

> Resizing partitions with Windows Vista
Windows Vista can shrink its own partition without the need to use third-party software. See this link. If you are running Windows Vista, shrink down your partition through that method, and then boot Ubuntu. The Ubuntu installer will use the free space you created.

Thats what i have done (shrinked the "OS" partition), however i already have three "primary" partitions on the disk, will this be a problem ? I have no problem with installing Ubuntu on my ~20GB unallocated area, as long as it doesnt make my MD button self destruct the computer...

---

### Post by djdolber on 2008-11-24
I went in and took a peek at the installation partitioning, selecting manual partitioning i saw the following info:

```
/dev/sda
    /dev/sda1    fat16    123 MB
    /dev/sda2    ntfs     10737 MB
    /dev/sda3    ntfs     165532 MB
free space       -        20972 MB
    /dev/sda5    fat32    2683 MB
dev/sdb
    /dev/sdb1    fat16    525 MB
```

Installing on the free space seems perfectly possible, i get the option to make a partiiton when i highlight it. So my only question now is basically will this mess up my computer by making the MD button a nuke-button ? Seems illogical considering the MD partition is left intact... So i guess i should carry on and install ?

---

### Post by csowm5je on 2008-11-24
I have a dell M1330 and installed Vista, Ubuntu and MediaDirect and these are the steps
1) Backup the restore partition to a DVD
2) Backup any other data
3) restart with MediaDirect DVD
4) select option no 2 and allocate partition size for Visa (125GB?)
5) install vista operating system
6) Log into Vista and install media direct
7) restart with Ubuntu Alternate CD (Not desktop)
8) create a boot partition (mine is 5GB) (I selected manual partition and note down the boot partition number)
9) create a logical partition for / (mine is 25GB)
10) create a logical partition for /home (mine is 50GB)
11) create a windows data partition (mine is 50GB)
12) install ubuntu 
13) install the grub in boot partition (Partition number on step 8)
14) copy the vista restore dvd to windows data partition
15) restart with the Vista operating system DVD
16) select repair and command prompt
17) issue this command "d:\dell\tools\imagex.exe /apply d:\dell\image\factory.win 1 c: (to install the dell factory image)
18) restart the computer again with Vista DVD and select repair andlet it fix the boot
19) boot back into Vista download and install easybcd boot manager and point to linux boot partition

This way you can mess with Linux without reinstalling Vista.

---

### Post by falcon61102 on 2008-11-25
If you are ok with installing into that 20gig unallocated space then you shouldn't have any troubles.  As long as you don't install over the media direct partition, you won't have to worry about that messing up anything.

If you want to combine the 10gig Recovery with the 20gig Unallocated Space like you mentioned earlier, than you will need to move the Vista partition to the front of the drive.  You can do this using the Ubuntu LiveCD and gparted.  Again, that won't affect you Media Center button at all.  

Bottom line, as long as you don't delete that Media Center partition, you won't have any affect on the Media Center button.

---

