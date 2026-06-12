---
title: "Partition help"
date: 2005-09-19
forum: Desktop Environments
---

### Post by oofnik on 2005-09-19
Hey everyone, I have a quick question about partitioning. Ever since I've been using Ubuntu regularly, I'be been running out of space on the main partition. Right now I have a 160GB SATA drive, with the following partitions:
/dev/sda1 20GB NTFS
/dev/sda2 70GB FAT32
/dev/sda3 40GB NTFS
(unallocated) 10GB
/dev/sda4 12.3GB, extended
--/dev/sda5 11.7GB ext3 (boot)
--/dev/sda6 .5GB swap

I know, complicated. But anyway I was planning on booting with the Ubuntu live CD, starting up gparted and resizing the extended partition to include that 10GB unallocated space (which I just shaved off one of the NTFS partitions in PartitionMagic), then merge it with the ext3 partition. Will I have to make any changes to the GRUB config or anything? I just don't want to end up with an unbootable system... Thanks!

---

### Post by skoal on 2005-09-19
Where's your / (root) partition?  I only see a ~12GB (boot) and a .5GB (512MB ?) swap partition.

I would make the following changes, which should leave the original Windows stuff intact:

/dev/sda5 - 100 MB (/boot)
/dev/sda6 - 512 MB (swap)
/dev/sda7 - rest of drive = ~11.5 GB (/)

This is a fresh install of Ubuntu, right?  By doing it this way, you can mount your /dev/sda2 under Ubuntu and use that for all your goodies, like video, music, or whatever else you want to share between the two...

\\//_

---

### Post by Rufusz on 2005-09-19
Hi! I would like to divide my partition with GParted, but it's not working. I've got a 38Gg ext3 and a 750Mb swap partition, and I would like to create a 28Gb fat32 and leave 10 Gb ext3.
In Gparted, I can't change anything, becouse the icons are grey, so I can't use them. 
Is this problem becouse of the linux is running at the moment on the same partition that I want to modify?
Or I don't have the "right" to modify the partition?

Is it possible to create partitions during the installation? (I thought that I'll reinstall the system if it's necessary)

---

### Post by oofnik on 2005-09-19
Maybe this screenshot of GParted will help explain how I've got it set up.
/dev/sda5 is boot, and is where Ubuntu is installed. I want to expand it to include that unallocated space, bit I just want to make sure I don't need to do anything else beforehand so that GRUB still knows where the partition is.

---

### Post by skoal on 2005-09-19
oops. I completely overlooked that you were using gparted.  I thought you were going to do a fresh install of Ubuntu.  Yes, do not resize those partitions under the installation, since that will wipe out your current partitions.

I don't know enough about gparted to tell you why those partitions are grayed out.  If you are using the live CD then I would expect those linux partitions would not be mounted, and consequently, not grayed out.  It may be partition magic interfering with gparted.  I dunno.

From what I gather you are wanting to do, to keep your existing information on your root partition, while using a NON-contiguous partition _not_ next to your root partition already, you would need to create the new root partition first, copy over your old root partition to your new one using a drive imaging copy tool, then touch up your /etc/fstab and /boot/grub/menu.lst (from a live CD) to reflect those new changes.

* The easiest sol'n in your case might just be: Backup all your important information (on linux) off select partitions/paths to a CD (or another partition, like creating a temporary ext3 partition), and just recreate what partitions you want, then reinstall Ubuntu and restore that backup information.  *It might be a good idea to backup your linux stuff now anyways, since you are fiddling around with a rather "unique" partition scheme...*

/edit - ok. I see now from your pic.  Thanks.  I don't know enough about gparted but the fact that the "unallocated" partition is below your "extended" partition might be the problem.  I would think you could just append that "unallocated" partition to the ext3 (root).

\\//_

---

### Post by oofnik on 2005-09-19
Hah, thanks skoal. I'd really rather not do a reinstall now just for that. I just want my Ubuntu partition to be bigger. The way I've got it set up is that Ubuntu is installed on /dev/sda5, that extended ext3 partition at the end of the drive. I want to resize the extended partition to include that unallocated space, and then resize the ext3 partition to include that space, giving me an extra 10GB of space to install programs and whatnot. The whole system including /home is on this partition. I mounted the other partitions separately. I hope this isn't too confusing, and most of all I hope it's even possible! Otherwise I guess I can just format that unallocated 10GB as ext3 or something and mount it somewhere, but I'd really rather just merge it with the existing ext3 partition. I don't know if gparted has that kind of functionality and I'd be scared to mess up the partition tables...

edit:
[QUOTE=skoal]I don't know enough about gparted but the fact that the "unallocated" partition is below your "extended" partition might be the problem.  I would think you could just append that "unallocated" partition to the ext3 (root).

\\//_[/QUOTE]

The unallocated bit actually is outside the extended partition. But yeah, that's precisely what I want to do, append it to the ext3 partition there. I just need to know if I need to make any adjustments to the GRUB config or something. All the partition numbers should stay the same I think.

---

### Post by skoal on 2005-09-19
[QUOTE=oofnik]The unallocated bit actually is outside the extended partition. But yeah, that's precisely what I want to do, append it to the ext3 partition there. I just need to know if I need to make any adjustments to the GRUB config or something. All the partition numbers should stay the same I think.[/QUOTE]
Yes, sir.  The unallocated bit is the partition just below the extended one.  If you are able to just append that to the end of your ext3 partition, then you would _not_ need to modify your configs.  What basically gparted needs to do is shift the extended partition down one, and append the unallocated bit to the ext3 partition.  Boom! You got your bigger / (root) partiton now.

I don't know why it wouldn't be that simple in gparted.  I don't know enough about it to tell you why it's greyed out.  If you could just figure out that part, then it should be just that simple.  However, I would still backup a few select partitions/paths (like /home) to a CD before you proceed.  Gparted is pretty reliable, but you never know...

/edit - since it's unallocated, you would _not_ need to change any configs.

\\//_

---

### Post by oofnik on 2005-09-20
Thanks a lot, skoal. I appreciate your help on this. But before messing with my partitions, I want to just get a second opinion on here, so whoever wants to help is very welcome :D Thanks again!

---

