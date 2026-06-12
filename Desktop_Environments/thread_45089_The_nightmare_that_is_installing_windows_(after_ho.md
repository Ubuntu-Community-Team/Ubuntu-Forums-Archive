---
title: "The nightmare that is installing windows (after hoary)"
date: 2005-06-28
forum: Desktop Environments
---

### Post by Steel3 on 2005-06-28
I apologize if this is the wrong forum; wasn't really sure where to put this.

Anyway, for various reasons I need to start running the Windows OS again after almost an entire year of having ditched it completely.  I'm a total newb when it comes to all of this GRUB/dual-booting/partition table type stuff.  Since my computer is currently nonfunctional (more on that later), I wrote down my most recent fdisk -l output from a Live CD (in case that is helpful):

Device		Boot	Start	End	Id	System
/dev/hda1		1	7786	83	Linux
/dev/hda2		7787	19457	f	W95 Ext’d (LBA)
/dev/hda3	*	13385	19457	c	W95 FAT32 (LBA)
/dev/hda5		7787	13322	c	W95 FAT32 (LBA)
/dev/hda6		13323	13384	82	Linux swap

The FAT partitions are a throwback from when I used to dual boot so I could access and modify my Windows storage space from my real OS.  I initially tried Qemu, and it seemed to work out pretty nicely, except I couldn't manage to get network/internet access or sound working, which are essential to the applications that I need Windows for (cedega/crossover office/wine just don't do the trick, unfortunately).

Anyway, first I tried using GParted and QTParted (had all of the necessary libraries that I needed) to just get rid of the two FAT partitions (they're empty now), resize the ReiserFS partition to take up most of the space and leave 8-10 gigs of FAT for Windows.  Unfortunately, neither program could read the partition table on hda and spit out a slew of errors at me.

Finally I decided to just take the plunge and install Windows XP on one of the now-empty FAT partitions (I picked what it thought was the "D" drive, hda3).  After going through the initial install process where it copies the setup files onto the drive before rebooting to run the actual installation, the computer... wouldn't reboot.  Now normally (and in Qemu) the computer just booted without the CD, asked for the CD, and continued with the installation.  This time it gave some error about not being able to find a disk, so I was just like "screw it," popped in a Warty LiveCD that I had lying around, and followed the instructions in [this thread](http://ubuntuforums.org/showpost.php?p=215131&postcount=4) and wrote GRUB to (hd0) (the MBR?).  Anyway, after I tried to add a entry to Windows in GRUB when I try to load it it still went "disk error" or "disk not found" or something like that.

So a few days later I decide to try it again, figure maybe I'll do things differently.  I tell Windows to install on that same partition, and everything craps out on me again.  I get the same error and I've got to use a LiveCD to boot up, except this time the LiveCD encounters some fatal error when its trying to load up and I've got to load it in failsafe mode to even boot up.  Rescuing the computer is not going to be a difficulty now that I've got internet access someplace else and printed out what to do, but I've got a few questions about this situation:

What am I doing correctly in the installation of Windows, and is there a process I can follow to install it correctly?

Is there any way I can get parted to "see" all of the partitions on my drive?  I've got all the necessary programs and I'm not exactly sure what to do so I can repartition my computer correctly.

I can supply you guys with any other information as necessary.  Sorry for the trouble and thanks in advance!

---

### Post by Steel3 on 2005-06-28
UPDATE:  So I tried to run parted from a LiveCD.  Does this message mean that my MBR is screwed up or something, or is it related to me not being able to partition properly?

warty@ubuntu:~ $ sudo parted
GNU Parted 1.6.9
Copyright (C) 1998, 1999, 2000, 2001, 2002, 2003 Free Software Foundation, Inc.
This program is free software, covered by the GNU General Public License.

This program is distributed in the hope that it will be useful, but WITHOUT ANY
WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS FOR A
PARTICULAR PURPOSE.  See the GNU General Public License for more details.

Using /dev/hda
Warning: Unable to align partition properly.  This probably means that another
partitioning tool generated an incorrect partition table, because it didn't havethe correct BIOS geometry.  It is safe to ignore,but ignoring may cause
(fixable) problems with some boot loaders.

---

### Post by Steel3 on 2005-06-28
Sorry for yet another update, but this is really bothering me and I can't seem to figure it out.

Anyway, I downloaded and burned the Breezy Live CD, booted it up, added all of the repositories, updated and installed various programs related to reiserfs and parted.  This is my fdisk output.

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        7786    62541013+  83  Linux
/dev/hda2            7787       19457    93747307+   f  W95 Ext'd (LBA)
/dev/hda3   *       13385       19457    48781341    c  W95 FAT32 (LBA)
/dev/hda5            7787       13322    44467857    c  W95 FAT32 (LBA)
/dev/hda6           13323       13384      497952   82  Linux swap / Solaris

I figured since everything was unmounted and hda wasn't being used I'd give it another shot.  With parted, I get the error message "Error: Unable to satisfy all constraints on the partition." when I try to do something.  Other programs see the hard drive, but see it as completely unallocated space.  With QTParted I get the error message "Critical error during ped_disk_new"

What gives?  Is there any information out there about how to fix something like this?

Thanks!

---

### Post by DancingSun on 2005-06-29
Ok...while I'm no dual boot expert (actually I was about to try that myself), I do know that windows likes to be on the 1st partition in the beginning of the HDD.  If you have already installed Ubuntu first, it looks like you'll need to create an empty partition at the beginning of the drive somehow, if that is even possible.  Otherwise, you may need to wipe out the drive and install Windows first, then Ubuntu.

---

### Post by Steel3 on 2005-06-29
[QUOTE=DancingSun]Ok...while I'm no dual boot expert (actually I was about to try that myself), I do know that windows likes to be on the 1st partition in the beginning of the HDD.  If you have already installed Ubuntu first, it looks like you'll need to create an empty partition at the beginning of the drive somehow, if that is even possible.  Otherwise, you may need to wipe out the drive and install Windows first, then Ubuntu.[/QUOTE]

Hmm, let me know how it goes.  I've wiped out the other partitions completely and I'm close to getting ReiserFS to take up the entire space on the drive.  From there I need to figure out how to back up my data (I've got a hell of a lot of it!) so I can either wipe everything and reinstall windows, then install Hoary or figure something else out.

Is there any way to create a new partition, move everything over and back it all up in that, and then wipe everything out but that partition so I could successfully install windows and Ubuntu, and then reassimilate all of that data back into an Ubuntu partition?

---

### Post by DancingSun on 2005-06-29
I just happen to find this wiki article while searching for "safe" ways to install Ubuntu after WinXP.  I've been hearing horrer stories with GRUB installing on the MBR and not being able to boot into Windows afterwards.

While this article isn't what I'm looking for, it might be helpful to your situation:
[Recovering Ubuntu After Installing Windows](http://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows)

---

### Post by Steel3 on 2005-06-29
[QUOTE=DancingSun]I just happen to find this wiki article while searching for "safe" ways to install Ubuntu after WinXP.  I've been hearing horrer stories with GRUB installing on the MBR and not being able to boot into Windows afterwards.

While this article isn't what I'm looking for, it might be helpful to your situation:
[Recovering Ubuntu After Installing Windows](http://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows)[/QUOTE]

Thanks!  I have no idea how this stuff works, but if I modify the GRUB menu to point to a partition that's got Windows on it, hopefully I can load the partition through GRUB and continue with the installation.  Does anybody know if that would work?

---

### Post by DancingSun on 2005-06-29
Another idea, if you have anther Ubuntu computer or bootable HDD, you can attach your current HDD as a slave drive, and try to boot into another Ubuntu instance and attempt to backup your data that way.

Edit:
I just found an article about a horrer story that's worst than messing up the MBR when installing XP **after** Linux, it will wipe out the Linux parition!.
[http://www.newsforge.com/os/02/05/27/0334227.shtml](http://www.newsforge.com/os/02/05/27/0334227.shtml)
I'm not sure if this happens consistently, since some dual boot install guides recommend partitioning the HDD first, then install Windows, then install Linux.  According to their guide, the Linux partition still exists after the Windows installation.

---

### Post by jr0 on 2005-06-30
I have a problem along the same lines. After awhile of using both windoze and Kubuntu dual boot, I had to reinstall windows. Now my Grub doesn't start and I get forced to windows instead. I didn't reformat or repartition, so I know my linux is still on the drive.  Is there an easy way to get Grub back without messing things up?  :-|

EDIT: I'm a moron! The solution is posted above.  [http://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows](http://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows)
After following the instructions, I'm back on Linux. It even saved my custom Grub settings.  Ubuntu's LiveCD is a handy thing to have in times like this!

---

### Post by mingus on 2005-07-01
You likely have a problem with the MBR, but that is easily fixed.  The much more serious problem is with the partition table, and this likely cannot be fixed without repartitioning.  This is the source of the errors in Parted and W$ setup.  You also are not installing W$ correctly.

We could get into a lot of technical detail about how different OS's calculate geometries and diff algorithms for writing to the table.  What is important is that you mixed OS's and partitioning utilities on the same table, and most importantly, that one of them was DOS, which is primitive, inaccurate, and hostile to anything else being in its sandbox.  Bottom line, the table is corrupted and neither Parted nor W$ setup can handle it.

Give cfdisk a try at deleting hda2-6.  And then fdisk (which is not the same as DOS fdisk).  A PartitionMagic rescue CD might also work.  To resize, because it's ReiserFS you'll have to use Parted, which should work once the table is cleared.

However, you still have the W$ install problem.  W$ expects to be installed on the first partition, which must be an active primary.  Here XP is diff than prev vsns.  It actually only needs its "system partition" to be there, and that literally is 3 files (ntldr, ntdetect.com, boot.ini).  The rest of XP can be on any other primary partition.  Therefore you must backup Ubuntu (use tar, there is a HowTo), delete hda1, create a new hda1 for W$, a new hda2 and restore Ubuntu to it.

There may be one workaround, if you can boot from floppy.  You just put those 3 system partition files on the floppy, and when you boot it will find XP on the new partition you install it on, after the Ubuntu partition.  You just have to modify the boot.ini file to make this work.

Finally, installing grub is fairly simple. First you need to get into Ubuntu with either the Live-CD or install CD; the methods are a bit diff but with either you must mount hda1 and chroot to that mount point.  Then from the shell you do:
#grub
grub> device (hd0) /dev/hda
grub> root (hd0,0)
grub> setup (hd0)
grub> quit
that will put grub on your MBR.  It's also a very good idea while you're there to create a grub boot floppy.  If for some reason the grub install above doesn't work, this will get you in and can be used to get that right.

Do not confuse fixing the boot loader problem with the partition table problem.  The former is easy, as jr0 has found.  Not so the latter, which is complicated by your need to install XP.

*EDIT:  You might check [http://ubuntuforums.org/showthread.php?t=45719](http://ubuntuforums.org/showthread.php?t=45719) for a somewhat similar (but not exactly the same) problem.  In post #6 are instructions on how to manually edit the partition table.  The section about DiskProbe does not work for you because your partitions are FAT32.*

---

