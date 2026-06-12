---
title: "Uninstall Ubuntu"
date: 2009-05-18
forum: General Help
---

### Post by arsin225 on 2009-05-18
Running Vista 32bit, installed it  on a separate HDD, which happened to contain all of my music, I just a lot of free space compared to my main HDD's partitions. When I installed it asked how much space to use, and stupidly (I'm guessing) I clicked use the entire disk. Now my HDD is no longer accessible to Vista, nor can I even try to listen to music on Ubuntu.

So here's what I'd like to try to do, either uninstall it without wiping the hard drive, if it isin't already, or just modify the partition or whatever it is so that I can access the drive from Windows and also Linux.


Thanks. I know that the first message I'll get will be "Use the search button" but I'm just going insane here beacuse if I lose my 67GB of music I know it will be hard to retrieve.

Thanks again.

---

### Post by coffeecat on 2009-05-18
I'm really confused here trying to follow you. :) Could you please provide the following answers:

How many hard drives have you in the computer?
What is their capacities in GB?
How many partitions on each?
Which drive has your Ubuntu, Vista and music partitions?

Now, in Ubuntu, open a terminal, post the output of:

```
sudo fdisk -l
```Now confirm one last thing. Did you want to uninstall Ubuntu and have just Vista - hopefully accessing your music files? If so, have a read [of this]("http://www.users.bigpond.net.au/hermanzone/p18.htm") but **don't do anything** until someone has come in to help. :p

---

### Post by hangfire on 2009-05-18
> **arsin225 said:**
> Running Vista 32bit, installed it  on a separate HDD, which happened to contain all of my music, I just a lot of free space compared to my main HDD's partitions. When I installed it asked how much space to use, and stupidly (I'm guessing) I clicked use the entire disk. Now my HDD is no longer accessible to Vista, nor can I even try to listen to music on Ubuntu.

So here's what I'd like to try to do, either uninstall it without wiping the hard drive, if it isin't already, or just modify the partition or whatever it is so that I can access the drive from Windows and also Linux.

**STOP**- the more you use that disk, the more you will lose. Either boot Windows or a live CD.

**Recovery**- there is a program called TestDisk that has a component program PhotoRec that will search disks or partitions for files, including .mp3's and .mp4's. I suggest running this against your overwritten disk to recover your music. IF (big if) there is something there, it will find it. (You may need to install a Linux to an external drive, thumb drive, or find a Linux boot Cd with TestDisk installed in order to install and run this program without further writing to your problem disk.)

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

I have used this data recovery tool on disks with missing partition tables and it recovered massive amounts of data.

You won't recover all your music. During the install, whatever Ubuntu overwrote is gone. If you had 2 Gigs of Music and 3 Gig's of Ubuntu installed, chances are poor that anything survived. If the music happened to fall in a mostly unused Linux partition, you may be in luck.

Never overwrite a disk or partition unless you are ready to lose everything on it.

**Accessing from Windows**- There is a FOSS project to do this, but if your eventual goal is to uninstall Ubuntu, it isn't worth your time. And remember, STOP, the more you use Ubuntu and that disk before you run recover, the more you lose. On the other hand, a Windows-based data recovery program may do want you wish, but no better than TestDisk, and for a lot more money, too.

**Uninstall**- Uninstalling Ubuntu will not reverse any damage. You'd have to restore a backup to get back to where you were before.

Good luck, and tell us how it goes.

-HF

---

### Post by arsin225 on 2009-05-18
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0007a41c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18706   150255913+  83  Linux
/dev/sda2           18707       19457     6032407+   5  Extended
/dev/sda5           18707       19457     6032376   82  Linux swap / Solaris

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
240 heads, 63 sectors/track, 25841 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0x11202851

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        5419    40960000    7  HPFS/NTFS
/dev/sdb2            5419       18964   102400000    7  HPFS/NTFS
/dev/sdb3           18964       25842    51998716    7  HPFS/NTFS



Main drive w/ Vista - 200gb    3 Partitions 
Drive with Linux - 160gb   0 Partitions

I'd like to either, uninstall Ubuntu or make it so that I'll be able to access my music from both Ubuntu and Vista

Which ever is easier for the average person, but I'm not completely incompetent so please do tell me my options, thanks.

---

### Post by coffeecat on 2009-05-18
First of all, you haven't told us which of the two drives your music is/was on. It's not clear from your first post. If it was on the 160GB drive then that partition has been replaced by the Linux ones. If that is so, heed **hangfire**'s advice and **do not boot into Ubuntu**. If the music is on the 160GB drive, then some of it may be rescuable with testdisk/photorec.

If, however, the music is on one of the partitions on the 200GB drive, then I can't see why neither Vista nor Ubuntu is seeing it. If you add a NTFS partition to a machine with Vista and then boot into Vista, Vista will simply allocate it a drive letter like F:\ or whatever. Similarly, with Ubuntu, you just have a look in the Places menu and double-click on the icon corresponding to the partition.

According to a quick back-of-the-envelope calculation, your sdb partitions are:

1 - ~40GB
2 - ~98GB
3 - ~50GB

Partition 1 has the boot flag so that must be where Vista is, but that's rather a small partition for Vista. Not impossible, but small. Can you boot into Vista?

Last thing. Vista can't read a Linux ext3 partition (that's sda1) without special drivers, whereas Ubuntu can read NTFS partitions via the Places menu.

Before we go any further, you'd better confirm where those music files are. Any advice anyone gives is contingent on that.

---

### Post by arsin225 on 2009-05-18
It's on the drive with Linux

---

### Post by philcamlin on 2009-05-18
you formatted your drive windows is gone

---

### Post by coffeecat on 2009-05-18
> **arsin225 said:**
> It's on the drive with Linux

OK. Read through **hangfire**'s post very carefully. Don't boot into Ubuntu. You can run testdisk (which includes photorec which may be able to rescue some of your files) from a live CD (so long as you can connect to the internet to make a temporary installation of testdisk), but don't try this yourself until you're absolutely ready. You need to be comfortable in the terminal. Ideally you need an external drive to copy the rescued data onto, and you need a working knowledge of the Linux file layout to be able to navigate around in the spartan photorec user interface.

Have you got a friend with good experience of Linux to help you? Running testdisk is fairly daunting if you're not 100% comfortable with Linux.

---

### Post by arsin225 on 2009-05-18
Forget it. I'll just take everything off it, most of my stuff is on my Zune so I guess it wont be too bad. Can you just tell me how to get rid of it?

---

### Post by coffeecat on 2009-05-18
See link in my first post.

---

### Post by pricetech on 2009-05-18
If you're ready to start over, DBAN is good for wiping the drive.  A Zero Fill from the drive manufacturer is good too.

---

