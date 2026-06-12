---
title: "Have to leave  Install CD in drive to have GUI"
date: 2008-07-15
forum: Desktop Environments
---

### Post by sprdave on 2008-07-15
I am sorry if this has been asked. I did a search and could not find anything.
I have only had Ubuntu for two days, so please be patient.
Question: "I have to leave the Ubuntu Desktop 8.04 CD in the drive in order to have a GUI desktop" I need that drive free in order to install things. How do I install the GUI so I do not have to keep the CD in the drive. Thanks, Dave

---

### Post by overdrank on 2008-07-15
> **sprdave said:**
> I am sorry if this has been asked. I did a search and could not find anything.
I have only had Ubuntu for two days, so please be patient.
Question: "I have to leave the Ubuntu Desktop 8.04 CD in the drive in order to have a GUI desktop" I need that drive free in order to install things. How do I install the GUI so I do not have to keep the CD in the drive. Thanks, Dave

HI and welcome, You have installed Ubuntu correct? Could you give us some system specs?
Did you check the cd for errors before installing?

---

### Post by sprdave on 2008-07-15
It is just an old Micron 733 Mhz P111. Nvidia 32MB video card. Nothing special... just trying to learn Linux on it.

I did have one problem when I was installing Ubuntu. I tried to partition like this:

/root 10GB
/home 25gb
/swap-file 1GB

Long story short... I got a GRUB 15 and 17 error. The only way my PC boots is if the HD is one big partition.

Not sure if related to my problem.

I did check the CD for errors.

Thanks

---

### Post by overdrank on 2008-07-15
> **sprdave said:**
> It is just an old Micron 733 Mhz P111. Nvidia 32MB video card. Nothing special... just trying to learn Linux on it.

I did have one problem when I was installing Ubuntu. I tried to partition like this:

/root 10GB
/home 25gb
/swap-file 1GB

Long story short... I got a GRUB 15 and 17 error. The only way my PC boots is if the HD is one big partition.

Not sure if related to my problem.

I did check the CD for errors.

Thanks

Well you forgot to mention the most important spec as for the amount of memory?

---

### Post by sprdave on 2008-07-15
512 MB of memory.

---

### Post by overdrank on 2008-07-15
> **sprdave said:**
> 512 MB of memory.

Ok if you remove the cd from the system what happens? Do you see the grub and can you select Ubuntu? 
Are you able to boot into recovery mode?

---

### Post by gnuvistawouldbecool on 2008-07-15
That should be enough, it needs more than 384MB and you have more.  You could try the alternate install CD if you aren't worried about how it looks while installing, since you know what it looks like now.

The GRUB Errors:

> 15 : File not found
    This error is returned if the specified file name cannot be found, but everything else (like the disk/partition info) is OK. 

> 17 : Cannot mount selected partition
    This error is returned if the partition requested exists, but the filesystem type cannot be recognized by GRUB. 

---

### Post by sprdave on 2008-07-15
The system will not let me open the CD drawer! If I reboot and take out the CD-ROM I get all kind of black screens with errors, and then it just goes to my login prompt. Looks just like Ubuntu server command line. No GUI..

I am trying to Install Dreamweaver tonight but "Wine" wants to browse C: drive and that is taken up by the install disk.

I can see the Dreamweaver.exe file, but it has an orange circle with an X. 

Thanks,

Dave

---

### Post by gnuvistawouldbecool on 2008-07-15
When you tell it to turn off the CD should prompt you to remove the disk, so do that then restart, and see what you get.  Otherwise you don't want it to start reading the disc as you remove it.  If then you get either GRUB error codes or horrible black screens with error codes, reinstall it.  But before using the disc you have to do that with you could check it for errors again.

Other than that, you could maybe try a different distro, if Ubuntu for some reason fails.

---

### Post by sprdave on 2008-07-15
UPDATE:  I just restarted my PC and opened the CD drawer and grabbed the install disk. When it booted back up I now have a GUI without the CD in the drive.

I swear before I installed WINE tonight I never had to have the CD in for GUI..

This is very weird... BTW  I only have 384 MB of RAM my other PC I am using for learning Ubuntu Server has the 512 MB.

I will get some more RAM for this one.. PC133 are cheap now.

Thanks,

Dave

---

### Post by sprdave on 2008-07-15
Okay enough frustration tonight.. thanks for all of your help. I do have 15 books my place of work bought me on Linux and Ubuntu. I will just have to start plowing through them and all the documentation on the Internet.

---

