---
title: "adding a second hard disk drive to the system?"
date: 2005-05-29
forum: Desktop Environments
---

### Post by sal on 2005-05-29
sorry if i'm posting this in the wrong section of the forums.
what i am wounder is this:

1 - to add a second hard drive to the system, what tool or command would i use or issue to format the hard drive after installing it into the case?

2 - if i wanted to use that hard drive to store personal data on that i would create or download (documents, iso's, mp3's and the like) would it be as simple as formating it and then adding a shortcut to it  in  /media with my read/write ownership only so the drive only shows up for me?

here is what i'm trying to do:

my currnet windows system setup: 

C:\ My hard drive for the O/S that i install

D:\ My hard drive i use to save all personal data to so it's away from the O/S and safe if the need for a reformat/reinstall has to be done. 
simple set up, reinstall os, boot into it and in My Computer is the second hard drive with all personal data intact.

what i need to know how to do in Ubuntu is this so i can have O/S and personal files on seperate hard disks at all times.

  i am asking this because i'm somewhat new to the linux side. i have used windows all my life untill about six months ago. for the past six months i have been playing around with a few diferant distros on a dual-boot, nothing sirus though. Until now, that is. for about the last 3 weeks i have been listening to lug radio on the internet and have herd them talk about Ubuntu. so the other day i downloaded the live edition and let me just say, this disro rocks! as someone who within windows 2k/xp is (or should i say was because after i figure this HDD issue out it will be by by windows) a power user, i find Ubuntu just what is needed to convert the masses.

tahnks in advance.

---

### Post by YaAqoB on 2005-05-29
I'm a fresh convert from Windows XP aswell. I still have dual boot setup.
I just got a second Hard Drive partition and formatted it to ext3.
I then mounted it via the terminal and then created a link onto my desktop.
Now I have a separate hard drive for my music, downlaods and docs etc.
To do this I just did the following.

sudo mkdir /mnt/chosenname

sudo gedit /etc/fstab

I then added the following line to this file

/dev/device  /mnt/chosenname  ext3  defaults 0 0 

---------

Hope this helps. Feel free to get more advice & I'm sorry if I havn't remembered so well as I'm still new to this.  :)

---

### Post by KmL on 2005-05-29
[QUOTE=sal]sorry if i'm posting this in the wrong section of the forums.
what i am wounder is this:

1 - to add a second hard drive to the system, what tool or command would i use or issue to format the hard drive after installing it into the case?

2 - if i wanted to use that hard drive to store personal data on that i would create or download (documents, iso's, mp3's and the like) would it be as simple as formating it and then adding a shortcut to it  in  /media with my read/write ownership only so the drive only shows up for me?

here is what i'm trying to do:

my currnet windows system setup: 

C:\ My hard drive for the O/S that i install

D:\ My hard drive i use to save all personal data to so it's away from the O/S and safe if the need for a reformat/reinstall has to be done. 
simple set up, reinstall os, boot into it and in My Computer is the second hard drive with all personal data intact.

what i need to know how to do in Ubuntu is this so i can have O/S and personal files on seperate hard disks at all times.

  i am asking this because i'm somewhat new to the linux side. i have used windows all my life untill about six months ago. for the past six months i have been playing around with a few diferant distros on a dual-boot, nothing sirus though. Until now, that is. for about the last 3 weeks i have been listening to lug radio on the internet and have herd them talk about Ubuntu. so the other day i downloaded the live edition and let me just say, this disro rocks! as someone who within windows 2k/xp is (or should i say was because after i figure this HDD issue out it will be by by windows) a power user, i find Ubuntu just what is needed to convert the masses.

tahnks in advance.[/QUOTE]

Hi,

q1: I recommend GParted ([http://ubuntuguide.org/#gparted)](http://ubuntuguide.org/#gparted)). Easy tool to partition and format hard disk.

q2: It is simpler than that. Only mount your new hdd as /home partition. Let's say that your system have two harddisks, hda and hdb with one partition each one, so, you have two 'file' /dev/hda1 and /dev/hdb1. In /dev/hda1 you have Ubuntu SO and in hdb1 you will have /home. In home, there are all the users account stuff, e.g. user kml have a directory in home named kml (/home/kml) and it's only accesible by you or the root. It's easy to configure that when you install Ubuntu, but if it is already installed, just edit /etc/fstab and add this line 

/dev/hdb1       /home           ext3    defaults        0       2

(replace hdb1 with whatever you have as second partition)

the next time you boot your ubuntu, when you go to /home/something, you will be in your second hard disk (very transparent behaviour or not?)

hope I helped, if not, I didn't understand your post...

sonoma  :razz:

---

### Post by sal on 2005-05-30
thanks for the reply. i will try this.
just to let you know, just now, when creating this message i hit the wrong button and reported you by acksadent. soory about that.

---

### Post by pieniaszek on 2007-10-06
I installed Ubuntu on the slave, with XP on the primary and am undertaking that complicated partitioning task.

I have Gparted installed and found web sources for explanation but I encountered the dilemma of not finding information on what I was seeing, Specifically, under Partition, none of the following were actionable (not bold): new,delete, Resize/Move, copy, paste, format to.
Unmount was bold, but I couldn't undestand why I would unmount when I just installed.
The GParted sources I went to seemed too fragmented and non-sequential (for me, a newbie), so I used the Acronis Disk Director 10.0 Partition Expert.  I honestly guessed on file types and sizes, but am asking for opinions on what is wrong and should be changed with this partitioning:
/dev/sdb1  52.40 GB		/dev/sdb6  15.11 GB	/dev/sdb7 25.14 GB			/dev/sdb10 30.55 GB
						
						
						
Partition 	Filesystem	Mountpoint	Size	Used	Unused	Flags
						
/dev/sdb1	ext3	/	52.40 GiB	3.23 GiB	49.17 GiB	boot
/dev/sdb2	extended		94.64 GiB	…	…	lba
/dev/sdb5	linux-swap		4.34 GiB	…	…	
/dev/sdb6	fat32	/media/home	15.11 Gib	15.12 MiB	15.09 GiB	
/dev/sdb7	ntfs	/media/tmp	25.14 GiB	65.22 MiB	25.08 GiB	
/dev/sdb8	ntfs	/media/usr	10.79 GiB	58.00 MiB	10.73 GiB	
/dev/sdb9	fat32	/media/var	10.72 GiB	10.73 MiB	10.71 GiB	
/dev/sdb10	fat32	/media/data	30.55 GiB	15.31 MiB	30.53 GiB

---

### Post by brallan on 2008-06-13
> **YaAqoB said:**
> /dev/device  /mnt/chosenname  ext3  defaults 0 0 


I followed that advice with my fstab file, but then found that I had lots of permissions problems with the new drive, until I changed defaults in the fstab line to read 

```
/dev/device	/mnt/chosenname	ext3	rw,user,exec		0	0
```

thanks to the folks [in this thread]("http://ubuntuforums.org/showthread.php?t=826305") who helped out.

---

