---
title: "Dual boot Install, Ubuntu says no HD space."
date: 2009-06-20
forum: General Help
---

### Post by Airmapper on 2009-06-20
Hello, I just installed Ubuntu after using Windows for 10+ years and no experience with any other OS. My apologies if there was a ready answer somewhere, I did run a few searches.

I can provide more details as needed, I'm going to try to be brief but still give what I hope is relevant info. 

I have a Dual boot install with Windows Vista, on a 160GB laptop HD. According to what information I can collect using Windows, I have ample space for both OS on here, most of my less used and large files are stored on an external HD, so even before I installed Ubuntu I was only using 30 or so percent of the drive.

There is an issue with hard drive space with Ubuntu. For exapmle the update window came up, and it seems I can't update since the space needed was 100% full and there is no room for more data. I need to identify what drive space (partition perhaps?) it is using and enlarge it. I'm aso having other related issues, it seems preferences, like my wallpaper and color scheme settings were forgoten after I shut down, as well as notices regarding storing anything. I'm not sure how Ubuntu uses the HD and how the file system works, it seems to be similar to windows in several ways, but different enough I can't identify what exactly is full so I can fix it.

I'd appriciate any help on this, I probably could figure it out in time, but a few nudges in the right direction will speed up the process. Given the advantages of Ubuntu I intend to use it as my main OS for general computer use. I'm very happy with it so far.

---

### Post by merlinus on 2009-06-20
Fire up gparted (System/Administration/Partition Editor)..  If not installed you can get it from Applications/Add/Remove.  Post a screenshot.

Also, how did you create space for ubuntu?  Did you use vista's disk management tool?  Did you defrag first?

Also, post results of:

```

sudo fdisk -l
df -h

```

---

### Post by pratiks19 on 2009-06-20
Please paste the output of the following:

> sudo fdisk -l
and
> df -h

> I'm not sure how Ubuntu uses the HD and how the file system works, it seems to be similar to windows in several ways, but different enough I can't identify what exactly is full so I can fix it.

Ubuntu mounts the drives or partitions to specified folders.
The contents of the partition are visible in the folder on which it is mounted.
For mounting windows partitions:
[http://www.psychocats.net/ubuntu/mountwindows]("http://www.psychocats.net/ubuntu/mountwindows")


> I'm aso having other related issues, it seems preferences, like my wallpaper and color scheme settings were forgoten after I shut down, as well as notices regarding storing anything.

I guess your wallpapers are stored on the windows partitions.
You will have to edit the /etc/fstab as indicated in the link above, this will ensure that the partitions are mounted during boot.

---

### Post by merlinus on 2009-06-20
If there is no space in the / partition, then no changes can be saved, as nothing can be written to disk.  That is why you cannot install updates, and is the problem with changing wallpaper, color schemes, etc., and it not being carried over to your next ubuntu session.

These things have zero to do with vista...

---

### Post by Airmapper on 2009-06-20
The results of the terminal commands you requested: (Added ***** to block out my account name)
```
*****-laptop:~$ sudo fdisk -l
[sudo] password for *******: 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0b41b817

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1019     8185086   27  Unknown
/dev/sda2   *        1020       19131   145484640    6  FAT16
/dev/sda3           19132       19457     2618595    5  Extended
/dev/sda5           19132       19435     2441848+  83  Linux
/dev/sda6           19436       19457      176683+  82  Linux swap / Solaris

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x469d60df

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121601   976760001    c  W95 FAT32 (LBA)
*************-laptop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5             2.3G  2.3G     0 100% /
tmpfs                 497M     0  497M   0% /lib/init/rw
varrun                497M  116K  497M   1% /var/run
varlock               497M     0  497M   0% /var/lock
udev                  497M  176K  497M   1% /dev
tmpfs                 497M   88K  497M   1% /dev/shm
lrm                   497M  2.4M  495M   1% /lib/modules/2.6.28-11-generic/volatile
overflow              1.0M   36K  988K   4% /tmp
/dev/sdb1             932G   36G  896G   4% /media/Elements
/dev/sda2             139G   47G   93G  34% /media/ACER
************-laptop:~$ 

```> Also, how did you create space for ubuntu?  Did you use vista's disk management tool?  Did you defrag first?Yes, I used Vista's disk management. I had defraged recently, and made a 60GB unformated space on the drive. It appears on installation Ubuntu found and used it. However, it seems the majority of the drive space was added to the partition Vista is on, and I think I need that space set aside to be used for Ubuntu.

dev/sda5 partition is the one that is "full." Fortunately is seems it did have a little space in it for me to install gparted. 48MB seems to be all the room I have now.

Screen shot of the Partition Editor:
[IMG]http://img524.imageshack.us/img524/2312/screenshotdevsdagparted.png[/IMG]

---

### Post by merlinus on 2009-06-20
If you do not have data nor lots of customization, it might be best to start over.

As things stand, you would need to still shrink the vista partition -- no space is designated as unused within it.  Then you would have to use gparted on the live ubuntu cd to first grow the extended partition (sda3) into the unused space, and then grow sda5 to use it.

---

### Post by Airmapper on 2009-06-20
I don't have anything done to Ubuntu yet, so I could start from scratch without loosing anything. Sounds like a bit of a pain though. I'll see what info I can find on un-installing Ubuntu. I do not want to bother the Windows instalation, and took a risk installing Ubuntu without access to adequate recovery CD's, so I don't want to goof around with the hard drive any more than necessary, especially since I'm less experienced when it comes to this kind of work.

Was there something I did during installation that possibly caused this? It had 60GB of free space to work with, yet added to the partition that Vista resides on, instead of using that free space for the sd5 partition, which if I'm correct is the main directory (/). I selected an option to import certain Windows elements (browser data and files) to Ubuntu, should I avoid that next time? I want to set aside that 60GB (Which I assume is ample room for Ubuntu + Applications and user data) and I want Ubuntu for the most part to have and use that 60GB for whatever it sees fit, and leave my other partitions alone.

Thanks for the assistance.

---

### Post by merlinus on 2009-06-20
My best guess is that you did not indicate how much of the free space ubuntu was to use.  You do not need to uninstall ubuntu, as a fresh install will overwite it.

But you do need to use vista's disk management tool to shrink its partition, and it would be best to defrag again beforehand.

Then at the partitioning screen, select Manual, and see what your options are.  As long as you leave sda1 and sda2 alone, vista will remain intact.

Use 10G for /, 1.5G for swap, and create a /home partition out of the rest of the 60 or so gigs.

---

### Post by Airmapper on 2009-06-23
Okay, here is my plan, might be a few days till I find a good time to start in on this, so if anyone sees that something is a bad idea I'd appreciate the heads up. I'm trying to start over and re-install Ubuntu entirely, this time with enought HD space I can use it.

In Vista, defrag my HD, then use the partition management tool to remove the Ubuntu partitions, and resize the partition Vista is on so that I have 60GB of free space on the drive. (I assume it will not harm anything to remove the Ubuntu created partitions? I'm thinking it will be easier later in the process if I have unpartitioned free space to direct Ubuntu to install on.)

I boot up from the Live CD, start installation, then at the partition setup step, select manual, assign use of free space per Merlin's suggested arrangement.

---

### Post by merlinus on 2009-06-23
Sounds good to me.  Using manual partitioning, you will need to specify the amount of space, filesystem and mountpoint for /, /home and swap.  The last can be 1.5G, and depending upon what apps and so on you are planning to install, a fair amount would be 10G / and the rest for /home.

IIRC you already have a partition for sharing data that is ntfs???

---

### Post by Airmapper on 2009-06-25
Okay, plan did not go very well.

Deleted the partitions, and now Vista will not boot since it appears GRUB is still active, ad gives me Error 22 when I turn on the computer. I'm not going to panic just yet since I know it's all there, Vista just won't boot.

I now have 2 partitions on the disk, the Vista partition is taking up all the space. I wanted to shrink it down to leave me the 60GB free but for some reason it would only let me have 2GB. I shut down to re-start, and can't get Vista to boot.  

I have the live CD running and can use Gparted to do my resize operation. I did defrag before this. It warns me about loosing data on my Vista partition when I apply the change, is this a concern? I do not have a restore disk, and the software in Vista to make one never worked correctly. (One reason for wanting a Linux OS, I'll never be without an OS as long as I back up my personal files.)

Here is Gparted screen, ready to apply changes but do not want to delete data:
[IMG]http://img341.imageshack.us/img341/2312/screenshotdevsdagparted.png[/IMG]

---

### Post by merlinus on 2009-06-26
Using anything to resize vista other than its disk management tool is a recipe for disaster.  Proceed at your own risk, but make damn sure you have all of your critical data backed up.

---

### Post by Airmapper on 2009-06-26
Thank you Merlin, you've been very helpful. This is one of the more friendly help fourms I've been to. I'll more than likely be back should I have any more issues with Ubuntu.

Right now I'm going to wait, I got my hands on a Vista recovery ISO, so I'll need to wait till I get to my work computer to burn it to a disk and use it to hopefully repair the Vista Bootloader, so I can keep what I have. I've decided as much as I'd like to use Ubuntu daily I can not fully convert this computer at this time, I got too much invested in Windows at the moment, which is really what M$ wants I'm sure. I may procede with the Ubuntu Dual boot once I get Vista stable again, and am more confident I can recover anything I loose.

I have 2 older computers to play with using light weight flavors of Linux, I'm gong to try DSL on an old Thinkpad I have, and maybe Puppy on an old desktop. I see great benifits to Linux / Ubuntu, hope to convert soon.

Thanks again, hopefully this issue is closed and I can use what I learned to have a smoother install next attempt.

---

### Post by merlinus on 2009-06-26
Wise choice.  Operating systems come and go, but critical data can be lost forever.

Good luck, and post back when you are ready to make the leap to dual-booting.

---

