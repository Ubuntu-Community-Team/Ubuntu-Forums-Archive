---
title: "Ubuntu Vs. Fedora 10, Trouble installing Fedora 10"
date: 2009-04-19
forum: General Help
---

### Post by boarder428 on 2009-04-19
I recently started a "Fundamentals of Unix" class in school I have a few weeks experience with Ubuntu 8.10 and that is the extent of my Linux usage to date. Our text book is using the Live cd for Fedora 10.  I have Ubuntu installed on 1 pc and the others I am using it in VMPlayer. My first question, Can/should I use Ubuntu over Fedora or should I use Fedora since it is what the book is using? (Guide to Unix Using Linux 4th Edition by Michael Palmer)

Today I just fired up the Fedora 10 Live cd and decided to install a copy of it on a 3rd HD that I added to this computer speciffically to run Linux distros on. I had some difficulties getting install to begin and I'm not sure if it is due to the fact that the HD has not been partitioned or formatted yet or what!

When I choose the drive to install it on I am presented with a Formatting Error: Partitioning failed: Could not allocate partitions as primary partitions.
Not enough space left to create partition for /boot

---

### Post by Simian Man on 2009-04-19
Most of your text book should apply to all Linux systems.  What I'd really suggest is setting up Fedora in a virtual machine so that you can use both.  Besides that's a great way to learn Linux since you don't have to worry about hardware issues or screwing your system over.

As for your problem, I'm not sure what your partitioning problem could be.  It shouldn't matter what's on the drive if you tell Fedora to use the whole drive.  You could try deleting all partitions on your extra drive with gparted though.

---

### Post by meierfra. on 2009-04-19
> When I choose the drive to install it on I am presented with a Formatting Error: Partitioning failed: Could not allocate partitions as primary partitions.

Please post the output of 

```
sudo fdisk -lu
```

---

### Post by phubai on 2009-04-19
Fedora has a few peculiarities which make it a little different than Ubuntu. I doubt that would give you too much difficulty in class however. Regarding the 3rd HD, if you don't have anything on there that you need, I'd format it. Depending upon how many distros I wanted to have on it and how large the drive is, I might want to make a primary for /boot (if you're so inclined) and the rest an extended partition so that you would only be limited by drive space. If you create primary partitions, which is fine if you're only going to have two or three distros on the HD, you are limited to a max of 4 primary partitions. I think that's one of the errors you were seeing when you tried to install. Format what you want to use for Fedora, and show the installer where you want it installed and you should be good.

---

### Post by boarder428 on 2009-04-19
> **meierfra. said:**
> Please post the output of 

```
sudo fdisk -lu
```

liveuser is not in the sudoers file.  This incident will be reported.

---

### Post by meierfra. on 2009-04-19
> liveuser is not in the sudoers file. This incident will be reported. 

Sorry, in Fedora use

```
su -
fdisk -lu
```

---

### Post by boarder428 on 2009-04-19
> **Simian Man said:**
> Most of your text book should apply to all Linux systems.  What I'd really suggest is setting up Fedora in a virtual machine so that you can use both.  Besides that's a great way to learn Linux since you don't have to worry about hardware issues or screwing your system over.

As for your problem, I'm not sure what your partitioning problem could be.  It shouldn't matter what's on the drive if you tell Fedora to use the whole drive.  You could try deleting all partitions on your extra drive with gparted though.

Ty, I have considered this option although I'm studying to be a repair tech. I seem to always run into problems actually installing so I have found the best way to learn is to deal with the problems.  I do have a VM of Fedora! Thanks for the input!
Corey

---

### Post by boarder428 on 2009-04-19
> **meierfra. said:**
> Sorry, in Fedora use

```
su -
fdisk -lu
```

```
Disk /dev/sda: 40.0 GB, 40016019456 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78156288 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x63889742

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    78153727    39075840    7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x267a267a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   312560639   156280288+   7  HPFS/NTFS

Disk /dev/sdc: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x52452ea7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *        2048  1465145343   732571648    7  HPFS/NTFS

Disk /dev/sdd: 2083 MB, 2083520512 bytes
64 heads, 32 sectors/track, 1987 cylinders, total 4069376 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd2d7b3e8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *          32     4069374     2034671+   6  FAT16

```

---

### Post by boarder428 on 2009-04-19
> **phubai said:**
> Fedora has a few peculiarities which make it a little different than Ubuntu. I doubt that would give you too much difficulty in class however. Regarding the 3rd HD, if you don't have anything on there that you need, I'd format it. Depending upon how many distros I wanted to have on it and how large the drive is, I might want to make a primary for /boot (if you're so inclined) and the rest an extended partition so that you would only be limited by drive space. If you create primary partitions, which is fine if you're only going to have two or three distros on the HD, you are limited to a max of 4 primary partitions. I think that's one of the errors you were seeing when you tried to install. Format what you want to use for Fedora, and show the installer where you want it installed and you should be good.

The drive I want to put Fedora on is 40gigs, I may want to put 2 or 3 linux distros on it, the computer already has Windows Vista and Windows Xp on the other 2 drives and they are probably primary partitions as well, so I assume the rule of 4 primaries includes the other drives as well or is that per drive? I need to learn how to use GParted Efficiently!!  I have been using Disk Management in windows to do the majority of my formatting and partitioning due to my lack of experience with GParted and Linux!

---

### Post by meierfra. on 2009-04-19
> The drive I want to put Fedora on is 40gigs,

I'm not familiar enough with the fedora installation process, to give you any qualified advice. But does  fedora give you an option  to delete or resize the "ntfs" partion on the 40gig drive?  If not you should use gparted beforehand  to partition that drive.  Is where any data on that drive which you would like to save?  If not,  you can just freely experiment with gparted  until you figure out how to use it correctly. Also keep in mind that gparted does not   change anything on your hard drive until you choose "apply".

> I need to learn how to use GParted Efficiently!!
There isn't really that much to learn about gparted. Just try it out. An empty hard drive and/or  VM give you a perfect opportunity  to practice.

---

### Post by boarder428 on 2009-04-20
> **meierfra. said:**
> I'm not familiar enough with the fedora installation process, to give you any qualified advice. But does  fedora give you an option  to delete or resize the "ntfs" partion on the 40gig drive?  If not you should use gparted beforehand  to partition that drive.  Is where any data on that drive which you would like to save?  If not,  you can just freely experiment with gparted  until you figure out how to use it correctly. Also keep in mind that gparted does not   change anything on your hard drive until you choose "apply".


There isn't really that much to learn about gparted. Just try it out. An empty hard drive and/or  VM give you a perfect opportunity  to practice.

Fedora does not seem to give me an option to delete or resize except there is a tick in the bottom left for Reviewing and modifying partition layout but I got the same error with it ticked!
[IMG]http://img03.picoodle.com/img/img03/3/4/19/cjb428/f_FedoraInstam_04cf454.jpg[/IMG]

Thanks for the advice!  I'll play with GParted, I don't have anything I need to save on that HD

---

### Post by meierfra. on 2009-04-20
What happens if you check the box next to:

   Review and modify partitioning layout

in the screen you posted?  That  should give you the opportunity to edit the partitions.

---

### Post by boarder428 on 2009-04-20
> **meierfra. said:**
> What happens if you check the box next to:

   Review and modify partitioning layout

in the screen you posted?  That  should give you the opportunity to edit the partitions.

It gave me the same error, I'm running it in VM right now, I'll probably play with it some more over the weekend!  I have got to study for the time being.
Thanks,
Corey

---

### Post by boarder428 on 2009-04-30
Well I somewhat figured it out, I got fedora to install but now I seem to have lost the ability to boot to windows XP now.  Still can boot to vista but not xp!

VM is becomming my best friend, now I just need to figure out how to undo my Fedora install!  I don"t want to waste anybody's time here so I'll post this issue in the Fedora or UNIX forum.

Thanks for the replies!
Corey

---

