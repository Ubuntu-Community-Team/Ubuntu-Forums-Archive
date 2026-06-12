---
title: "Resizing partitions"
date: 2005-12-20
forum: General Help
---

### Post by ubuntuubuntu on 2005-12-20
I'd like to resize my HD partitions in order to set more free space for the Linux partition. My Linux partition has only a few MB free, so it's difficult to download a software to do it. What Windows software do you recommend for me to resize my HD partitions?

---

### Post by BathroomNinja on 2005-12-20
Have you tried Gparted?
Applications -> System Tools -> GParted

---

### Post by az on 2005-12-20
[QUOTE=ubuntuubuntu]What Windows software do you recommend for me to resize my HD partitions?[/QUOTE]

None that I know of work as well as parted.  The problem with parted or any partition software is that you cannot be using the drive while you partition it.

You can boot from the installer and use the installer's partitionner to resize your partitions.

You can use a live cd to use a graphical partition tool like gparted or qtpaerted to get the job done, too.

---

### Post by BathroomNinja on 2005-12-20
[QUOTE=azz]None that I know of work as well as parted.  The problem with parted or any partition software is that you cannot be using the drive while you partition it.

You can boot from the installer and use the installer's partitionner to resize your partitions.

You can use a live cd to use a graphical partition tool like gparted or qtpaerted to get the job done, too.[/QUOTE]


This man speaks truth.

---

### Post by Thunk on 2005-12-20
You can also do it very easily from Windows if you can get your hands on Partition Magic. It's really simple and it works like... well... magic. ;)

---

### Post by az on 2005-12-20
[QUOTE=Thunk]You can also do it very easily from Windows if you can get your hands on Partition Magic. It's really simple and it works like... well... magic. ;)[/QUOTE]

Most of the threads here which mention partition magic describe how it cannot reliably handle linux file systems.

---

### Post by briancurtin on 2005-12-21
[QUOTE=azz]You can boot from the installer and use the installer's partitionner to resize your partitions.[/QUOTE]
im looking to open up space in my current setup to install CentOS (i'm bored on christmas break and wanted to try it out now that i have the time), and my HD is currently setup with the default that breezy gave it which takes up every bit of the drive. since i'd like to shrink that big partition down to say half its size and make room to play with CentOS, are you saying that i can put the breezy CD in and run through the installer to get to the partition area, adjust the partition, then quit that install process somehow and now have room to install another OS? i have done some searching and found that parted is also a good method to resize the partion. which do you think is "easier?" rather, which do you recommend to someone who has never done this before?

i come from SuSE where there is a nice GUI partition tool that lets you drag little colored bars around and crap and its pretty simple.

---

### Post by Thunk on 2005-12-21
[QUOTE=azz]Most of the threads here which mention partition magic describe how it cannot reliably handle linux file systems.[/QUOTE]


I can only testify from my experience that it worked smoothly. I resized both my XP and Linux partitions using PM.

---

### Post by 11hjpphty76lkjj on 2005-12-21
I'd recommend booting from the Live CD and installing gparted, and using gparted.  It's easy, really.  Even I could do it!

I would never recommend someone use Windows for anything honestly, I haven't found anything that can't be done, as of yet, that's better and more stable, and just plain easier on Ubuntu.   

Except gaming. ](*,) 

Not to mention it's a good learning experience, if you are sticking with linux, learn to do whatever you want to do, the linux way.  The more you do it, the more you learn and the better you become.  Just my view.

---

### Post by ubuntuubuntu on 2005-12-21
[QUOTE=kalosaurusrex]I'd recommend booting from the Live CD and installing gparted, and using gparted.  It's easy, really.  Even I could do it!

I would never recommend someone use Windows for anything honestly, I haven't found anything that can't be done, as of yet, that's better and more stable, and just plain easier on Ubuntu.   

Except gaming. ](*,) 

Not to mention it's a good learning experience, if you are sticking with linux, learn to do whatever you want to do, the linux way.  The more you do it, the more you learn and the better you become.  Just my view.[/QUOTE]

It didn't work. I booted from the Live CD and used GParted. After resizing the partitions, I got the message "At least one operation was applied to a busy device. A busy device is a device with at least one mounted partition. Because making changes to a busy device may confuse kernel, you are advised to rebot your computer." I rebooted and the partitions had the same sizes as before.

---

### Post by az on 2005-12-21
The live cd uses your swap.  That is why your drive was busy.  Gparted does nothing until you tell it to go.

swapoff it.

---

### Post by ubuntuubuntu on 2005-12-22
[QUOTE=azz]The live cd uses your swap.  That is why your drive was busy.  Gparted does nothing until you tell it to go.

swapoff it.[/QUOTE]

What do you mean by swapoff it?

---

### Post by aamukahvi on 2005-12-22
Enter the command ```
sudo swapoff
```

---

### Post by az on 2005-12-22
sudo swapoff /dev/hda2
or actually just

sudo swapoff -a

---

### Post by sigma2805 on 2005-12-22
hi Azz,
thanks for the advice. I also needed to resize my partition on my laptop and the swapoff command was exactly what i was looking for. Hopefully, the developers incorporate swapoff as a boot time command. Anyway, I have a problem though when resizing the partitions. Basically, i can resize my NTFS partition(hda1) to make it smaller and then take the unallocated space and make my ext3(hda2) partition bigger. The problem is that once the entire hda2 partition is bigger, i can't resize the individual extended partitions under it. Here is the partition scheme i have...

/dev/hda1 Windows Partition

/dev/hda2 Extended

[INDENT]/dev/hda5       /boot           reiserfs
/dev/hda6       none            swap 
dev/hda7       /home           reiserfs 
/dev/hda8       /               reiserfs[/INDENT]
 
As you can see, hda2 is an extended partition and the rest of the partitions fall under it.

Thanks!

---

### Post by ubuntuubuntu on 2005-12-23
[QUOTE=azz]
You can boot from the installer and use the installer's partitionner to resize your partitions.

[/QUOTE]

Would I have to defrag the Windows partition?

---

### Post by az on 2005-12-23
[QUOTE=ubuntuubuntu]Would I have to defrag the Windows partition?[/QUOTE]
I think parted and ntfs tools can move things around, but I am not sure.  You do not have to defragment VFAT filesystes, parted does that for you.  If parted refuses to do it, that would be the first thing I would try to do to get it to work.

---

### Post by sunset_studies on 2005-12-24
[QUOTE=sigma2805]hi Azz,
thanks for the advice. I also needed to resize my partition on my laptop and the swapoff command was exactly what i was looking for. Hopefully, the developers incorporate swapoff as a boot time command. Anyway, I have a problem though when resizing the partitions. Basically, i can resize my NTFS partition(hda1) to make it smaller and then take the unallocated space and make my ext3(hda2) partition bigger. The problem is that once the entire hda2 partition is bigger, i can't resize the individual extended partitions under it. Here is the partition scheme i have...

/dev/hda1 Windows Partition

/dev/hda2 Extended

[INDENT]/dev/hda5       /boot           reiserfs
/dev/hda6       none            swap 
dev/hda7       /home           reiserfs 
/dev/hda8       /               reiserfs[/INDENT]
 
As you can see, hda2 is an extended partition and the rest of the partitions fall under it.

Thanks![/QUOTE]



I have exactly the same problem, i.e. I was able to reduce the size of the Windows partition, but I can't distribute the free space amongst the Linux partitions. 

It seems that you can only increase the size of a partition if there is free  space available *after* it appears in the partition table. Is this true?

Here's my setup as it currently exists:

Disk geometry for /dev/hda: 0.000-38166.679 megabytes
Disk label type: msdos
Minor    Start       End     Type      Filesystem  Flags
1          0.031  20606.813  primary   fat32       boot, lba
2      28607.937  31290.666  primary   ext3 (/)
3      31290.667  38162.219  extended              lba
5      31290.697  37824.917  logical   ext3 (/home)
6      37824.948  38162.219  logical   linux-swap


... All I want to do is make (2) start from where (1) ends. Any suggestions?

---

### Post by dragonfyre13 on 2005-12-24
[QUOTE=azz]Most of the threads here which mention partition magic describe how it cannot reliably handle linux file systems.[/QUOTE]
Yes, that's quite true. The best commercial Partition editor/resizer/whatever is acronis disk director. It creates a boot disk on installation that is just amazing. It handles pretty much every file system I've seen, does it well, and does it fast.

---

