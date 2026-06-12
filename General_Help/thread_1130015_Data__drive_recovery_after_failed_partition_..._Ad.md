---
title: "Data / drive recovery after failed partition ... Advice?"
date: 2009-04-19
forum: General Help
---

### Post by chrisgaffrey on 2009-04-19
Hi all, I'm a bit of a noob. Using Ubuntu Hardy 8.04 for about a year, first time using a linux os before. Dual booting with Vista.

I have a Trekstor 500GB external hd with fat32 I was trying to partition with Gparted and format the partition to Ext3. It failed. The shrink of the main partition worked but then I think I failed to properly set up the formating of the new unallocated space.

Getting out of Gparted I looked at my drive and noticed what appeared to be data loss. All my folders were there, but two of them were reading as empty (Music and Video files!). 

Lesson 1: back up first!

Figured it was my filesystem. Checked the forums (after getting smart) and saw that I needed to run chdsk in windows to try and see if it will correct errors in the filesystem. Tried that after rebooting into Vista with no obvious results other than a window briefly popping up and disappearing. I changed the the preferences of my External HD in Vista to allow it to examine it every time it mounts. 

Unmounted the external hd and mounted again with the result of the scan option coming up. Tried to have it look for and fix problems with the result that it said it could not do so but that I could schedule a scan. So I clicked the option and it disappeared. 

Assuming this meant it couldn't scan with it loaded up, I tried rebooting, hoping it would scan on reboot. As Grub loaded, I received an error message which I didn't understand saying that a certain file did not exist (first time and sorry I panicked and didn't read the error message thoroughly). 

I was relieved when I saw it say "press enter to continue" and that doing so brought me to the Windows boot loader. I was able to boot into Vista. Looked at my external drive and saw that there were now a bunch of files beginning with "fsck" followed by a sequence of 4 numbers with the suffix ".REC" along with the other unaffected folders. Thinking that more data was corrupting, I decided to reboot into Ubuntu to solve the problem from there, knowing that I would have more options of data recovery in Ubuntu and thinking that the problem started there so it could be fixed there.

Showing a friend the contents of the external hd in Ubuntu, we noticed that some of the "fsck*.rec" files were showing up as photos and as music files though their extensions were still ".rec" This gave me hope that my data was indeed still there! Way to go Ubuntu!

Looking up more forums I saw this:

[http://ubuntuforums.org/showthread.php?t=1031868&highlight=fsck+data+fat32](http://ubuntuforums.org/showthread.php?t=1031868&highlight=fsck+data+fat32)

But I'm not sure that dosfsck caused my problem as the initial data loss happened after I got out of Gparted. However, I did previously (as in a few days before attempting the partition) change the permissions in Ubuntu to allow my folders in my external fat32 hd to be read and written to... a no-no according to this post and the link it provides to a bug.

So did fsck cause the problem or fix it?

I plan on saving what I can from the "fsck*.rec" files, especially what I don't have backed up, and simply wiping the external hd and reformating with NTST or maybe even Ext 3. Any advice on which one would be better given my situation with Windows partitions and a Linux partition? My whole reason for wanting to partition my external hd and format 100GB as Ext3 was that fat32 was giving me problems when trying to save files bigger than 4GB in Ubuntu.

But before I format, anyone know if NTST drives have the same risk of possible corruption by fsck? Is it something to be concerned about since my other two partitions on my internal hd are NTST?

Thanks. I realize these are all noob questions. I appreciate any advice and replies.

---

### Post by cariboo on 2009-04-19
Fsck was trying to repair you drive, it moves repaired or misplaced files to lost & found. I would suggest you try [Testdisk]("http://www.cgsecurity.org/wiki/TestDisk") to repair your problems. Testdisk is in the repositories, and you can use Synaptic Package Manager to install it.

Jim

---

### Post by chrisgaffrey on 2009-04-19
> **cariboo907 said:**
> Fsck was trying to repair you drive, it moves repaired or misplaced files to lost & found. I would suggest you try [Testdisk]("http://www.cgsecurity.org/wiki/TestDisk") to repair your problems. Testdisk is in the repositories, and you can use Synaptic Package Manager to install it.

Jim

Thanks Jim, for clearing that up for me. At first I thought fsck was to blame, but then it hit me that the issue began after the partitioning and not after a boot.

I already tried testdisk, after downloading it using ```
sudo aptitude install testdisk
``` but I didn't try recovering my files with it. 

Instead I decided to go through the REC files in Ubuntu and rename the extensions, thus restoring and backing up only the data I didn't already have backed up (like most of my recent movies and music). Luckily the larger the number after "FSCK" in the file name, the newer the material, and I guessed from file sizes what were mp3's, wav's, mpegs, avi's etc, checking them, of course, before transferring them to my internal hdd. 

Once that was done I took the opportunity to reformat my external hard drive to NTFS, using a Gparted BootDisk. I picked NTFS over Ext3 so to not have to hassle with fs-driver for Ext3 in Vista, which I heard is a bear. 

If I understand correctly, reformating to NTFS, should now enable me to save files bigger than 4GB on my external HDD, something which was always a problem for me in Ubuntu when the drive was fat32.

The reformat worked, and I have most of my files restored to the drive. Only thing now is a bit of re-organization work on my part.

But for future reference, how would I command testdisk to recover my files?

Also, once I get everything back in order I would like to do a better backup job that will keep things together (My current back up disks have everything in pieces, thanks to iTunes backup of my music, which incidentally I no longer use). Any recommendations for a good open source backup program that will keep my data well organized?

Thanks again,
Chris

---

