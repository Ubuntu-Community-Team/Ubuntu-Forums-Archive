---
title: "Help Needed installing Ubuntu"
date: 2011-12-28
forum: Desktop Environments
---

### Post by Handvoodoo on 2011-12-28
Unfortunately I've been a Windows guy since Win 95..the extent of my linux knowledge was on a terminal in college some years ago..
I'd really like to get up and running with Ubuntu as my main environment, but I'v hit a hurdle that I cant get over.

First I'd like to say that I have successfully installed Ubuntu and Mint before..All within a week actually.

Heres my issue.
I have a 3TB drive that I migrated all the data off of to other drives.
So the 3TB HDD is clean.
I launched the liveCD..formatted some partitions in GParted..mapped the partition with the installer and installed 'fine'. I removed the disc, restarted..and my computer hangs after the BIOS Post with a blinking cursor.
Went back to the liveCD, reformatted the drive, and used Ubuntu's "just do everything for me option", installer runs for a bit than hangs with an error about going past sector xxxxxxxxxx. 
I'm assuming its b/c its trying to make my drive one large MS-DOS partition.
So I read around a little and went back to GParted, formatted again, Changed the partition to GPT and did the process over. Still hangs after the reboot. No errors, just hangs.
Went back into the liveCD, installed Boot-Repair, updated it and the first thing I get is a warning prompt telling me Im using and EFI boot and I need to create an EFI partition (fat16, <20mb, boot, efi flags).
I've got a partition, first one on the disk labeled EFI, formatted as fat16, its 20mb with the boot flag..For the life of me I cant find anywhere to set an 'EFI flag'

I've been attacking this for the past 3 days without any luck. I finally decided to give up and see if any one more knowledgeable can help me through it.

Ideally what I would like to do is set up a few partitions on this disk to get the OS up and running. I'd like to have separate partitions for "/" - 40GB, "/home" - 250GB, and a large 1TB partition for windows/linux sharing..a fat32 dump or something where i can store docs/movies/what have you between windows and linux..The latter I'm not all to concerned about.
Right now I'd settle at just having a / partition and a /home partition (and a swap partition - I have 16gb of ram).

Any one able to give me any pointers? I'm kind of at my wits end.

TL:DR Cant seem to get Ubuntu installed (and booted) on a 3TB drive. Mobo does support EFI (double checked and its set to 'auto' in bios, i also tried it as enabled (default is auto)).
Any tips? Pointers? Guides? Anything?
Right now the drive is formatted (again) so I'm starting clean. 2.73TB of unformatted space

Sorry about the wall of text

---

### Post by ManualSparrow on 2011-12-29
Maybe you got it figured out by now, but if not, I'd try using Gparted again and redoing the partitioning _scheme_, not just the partitions. Select "Master Boot Record" and create the shared partition with NTFS.  Use ext4 for the Linux partitions. At install you should be able to use the advanced partitioning option to select mount points (/home) for them. Note that you can only have 4 primary partitions under MBR, but you can make the fourth an extended partition and put any additional ones in there.

I also find the gnome disk utility more useful than Gparted in the situations, you may want to give it a go and run disk diagnostics, etc. (I think the package might actually be called palimpset). And defrag with Windows if you can.

Edit: assumed you are ok with not using EFI.

---

