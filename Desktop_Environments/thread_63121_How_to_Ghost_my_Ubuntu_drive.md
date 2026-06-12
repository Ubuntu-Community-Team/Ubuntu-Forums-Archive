---
title: "How to Ghost my Ubuntu drive?"
date: 2005-09-07
forum: Desktop Environments
---

### Post by ry_ry on 2005-09-07
I've been looking everywhere and can't seem to find a good step by step "How to" for ghosting a Linux drive. I have Norton Ghost 2003 for my Windows systems, but from its own documentation it only states that it is only sort-of supports Linux and this seems to be questionable. I need a good, fast, reliable, easy to use, hard drive imaging software to either back up my Ubuntu Linux install to a spare hard drive, or maybe even to blank bootable DVD's. I've heard about partimage, but that has to be run from a LiveCD and I can't find any easy step-by-step directions for using it. Any suggestions? I'm still a Linux newb in training so I will need step-by-step directions or a good recommendation?

I've heard about a "dd" command but how can I  use it to make an exact drive copy with Grub or MBR included too? Do you run this from a terminal window in Gnome? There needs to be a good "How to" full backup guide.

I have Ubuntu installed on a 80GB drive, and I have a spare 80GB that I could install in my PC on the secondary IDE channel. Could I use this "dd" command to clone the Ubuntu drive to the second drive? How would I do this, and does it take a long time? Would it copy everything, basically making an exact copy of the original drive that's bootable just like the original?

Any help would be great. Thanks. :)

---

### Post by frodon on 2005-09-07
There is a good [thread](http://www.ubuntuforums.org/showthread.php?t=35087) about that. Personally I use the latest version of norton ghost which is able to see ext2,ext3 format so I can ghost my ubuntu drive with it. I already did a restore of my drive and it worked perfectly.

---

### Post by earther on 2005-09-07
You can try this script which I discovered through a local LUG - [http://www.io.com/~treeflyr/mkbkup/](http://www.io.com/~treeflyr/mkbkup/)  I haven't figured out how to run it yet but have heard that it works quite well.

---

### Post by ry_ry on 2005-09-07
[QUOTE=frodon]There is a good [thread](http://www.ubuntuforums.org/showthread.php?t=35087) about that. Personally I use the latest version of norton ghost which is able to see ext2,ext3 format so I can ghost my ubuntu drive with it. I already did a restore of my drive and it worked perfectly.[/QUOTE]

Yeah, I already read that thread but I don't think that it is a good idea to tar an active drive that you're using. This method of backup seems kind-of iffy to me and it doesn't backup GRUB either. Also that thread states:

> In fact; using Ghost might be a very bad idea if you are using anything but ext2. Ext3, the default Ubuntu partition, is seen by Ghost as a damaged ext2 partition and does a very good job at screwing up your data. 

And even my Ghost manual states that it doesn't support GRUB.

I'm going to continue to research about cloning my Ubuntu Linux drive and will post my solution if I find one.

Thank you for your input.  :)

---

### Post by ry_ry on 2005-09-07
[QUOTE=earther]You can try this script which I discovered through a local LUG - [http://www.io.com/~treeflyr/mkbkup/](http://www.io.com/~treeflyr/mkbkup/)  I haven't figured out how to run it yet but have heard that it works quite well.[/QUOTE]

It only mentions being used with only Redhat 8.0 and Suse 9.2 and it still appears to be under development.

Thank you anyway.  :)

---

### Post by valnar on 2005-09-07
If you want a retail program, Acronis True Image is the best there is.  I gave up Ghost a long time ago.  Acronis will backup & restore anything.

Robert

---

### Post by earther on 2005-09-07
[QUOTE=ry_ry]It only mentions being used with only Redhat 8.0 and Suse 9.2 and it still appears to be under development.

Thank you anyway.  :)[/QUOTE]I'm going to take my box to the local LUG and have the experts give it a try.  I'll let you know how it goes.  I have been using  Acronis on my Windoze box and it's great!

---

### Post by frodon on 2005-09-07
The latest version of norton ghost offer a full support of ext3 partitions and I can confirm that it works really well because i often restore my ubuntu partition and I never got any problems.
I don't hnow why you think that GRUB is such a big problem, it's really easy to re-install, in addition restoring my ubuntu partition never destroyed my GRUB.

If you still looking for another way (norton ghost is not a good way because you have to pay for it  :-? ) you could have a look to [mondo](http://www.mondorescue.org/about/about.html)  which allow you to create a bootable backup CD/DVD of your partition with a GUI if you like.

Hope you will find a tool which will fit to your need  ;-)

---

### Post by jeremy on 2005-09-07
I regularly backup using partimage from a knoppix live CD, works beautifully, and is FOSS.

---

### Post by John.Michael.Kane on 2005-09-07
[http://www.pcquest.com/content/linux/2005/105041202.asp](http://www.pcquest.com/content/linux/2005/105041202.asp)
[http://www.feyrer.de/g4u/](http://www.feyrer.de/g4u/)
[http://freshmeat.net/projects/g4l/](http://freshmeat.net/projects/g4l/)

Hope this helps

---

### Post by bdamon on 2005-09-07
[QUOTE=valnar]If you want a retail program, Acronis True Image is the best there is.  I gave up Ghost a long time ago.  Acronis will backup & restore anything.

Robert[/QUOTE]

I'll second this. True Image is a great.

---

### Post by ry_ry on 2005-09-07
Well, so far nothing has worked.
Using the "dd" command will take around 22 hours to complete.
I tried using "Clone Maxx" but it gave the overall time at 1000+ hours!
I went ahead and tried my Norton Ghost 2003 but it did not work, it messed up the target partitions.
I spent several hours downloading g4l (Ghost for Linux) and that didn't work either, started giving errors something about losing ticks?, and was just as slow as "dd" command.

I have to have at least kernel 2.6.11 to enable DMA on my system and that is why I had to compile a custom 2.6.10 Ubuntu kernel for my install.

I guess the only two options would be to buy a new Linux LiveCD with at least kernel 2.6.11 on it and hope that, that kernel will enable DMA so I could just use "dd" command.

Or just go ahead and buy that TrueImage software. Man this sucks. :(

---

### Post by ry_ry on 2005-09-08
If I buy the TrueImage software, do you have to install this in Windows? Is there a disc already in the box that I can just boot with and do the Linux hard drive cloning without installing TrueImage in Windows?

---

### Post by earther on 2005-09-08
[QUOTE=ry_ry]If I buy the TrueImage software, do you have to install this in Windows? Is there a disc already in the box that I can just boot with and do the Linux hard drive cloning without installing TrueImage in Windows?[/QUOTE]You can get excellent answers on the [Acronis True Image Forum](http://www.wilderssecurity.com/forumdisplay.php?f=65).   I have TI installed on XP but I always create my images via the TI boot disk.

---

### Post by frodon on 2005-09-08
[QUOTE=ry_ry]If I buy the TrueImage software, do you have to install this in Windows? Is there a disc already in the box that I can just boot with and do the Linux hard drive cloning without installing TrueImage in Windows?[/QUOTE]If you have norton ghost 2003, maybe be you could update it to norton ghost 2005 (which support ext3). Don't forget mondo it's easy to use, with a GUI and it make a bootable cd/DVD (and it's free !), I don't use it but if you want some help i know someone who use it with success in this forum.

---

### Post by manicka on 2005-09-08
[QUOTE=jeremy]I regularly backup using partimage from a knoppix live CD, works beautifully, and is FOSS.[/QUOTE]
 I'll second this one. Partimage does a great job (backs up Windows and Linux) and most importantly is open source.

---

### Post by ry_ry on 2005-09-08
Well I have a Knoppix 3.7 CD and tried the partimage, but I'm having alot of problems. The online documentation at the Partimage website is not very good. I might have even messed up my source drive and have to do everything all over again. :(

1. I don't understand how to backup the partition tables or how to make images of the extended and logicial partitions? Partimage will not let me backup the extended and the logicial partitions. Don't you need to backup these too?

2.Also is the MBR with GRUB, backed up in the image file or not? And does this MBR also contain the extended and logicial partitions table information as well?

3.They show how to use a "dd" command and "sfdisk" command to backup the partition tables but do you have to boot back into Ubuntu and do this there in a terminal window or do you backup the partition tables from the booted Knoppix CD and how?

4.Can you save the partition tables backup files on the same backup hard drive and how do you access them to restore them?

5.Why can't I format my second hard drive, I'm using to store the image file, in the ext3 file system? "Parted" only will let me format using ext2 file system.

I did manage to backup my primary partition onto my second hard drive, or at least I think I did. Is there any way to check the integrity of the image file?

---

### Post by ry_ry on 2005-09-09
ok, my bad.
I think I didn't hurt my source drive and I did backup my primary partition to hdd using partimage. And I did some more research and this is what I got:

Running from Knoppix 3.7 LiveCD:
To backup my MBR:
mount -t ext2 /dev/hdd /mnt  (this is the drive I'm writing to)
dd if=/dev/hda of=/mnt/backup-hda.mbr count=1 bs=512
sfdisk -d /dev/hda > /mnt/backup-hda.sf

To restore my MBR from a running LiveCD:
mount -t ext2 /dev/hdd /mnt (this is the drive I'm reading from)
dd if=/mnt/backup-hda.mbr of=/dev/hda count=1 bs=512
sfdisk /dev/hda < /mnt/backup-hda.sf

Does the above look right?

And if I want to ever format my hdd drive in ext3 format I would use Parted and issue this command:
mkfs.ext3 /dev/hdd

Does this sound right?

And I only need to backup Ubuntu's primary partition because the extended partition just contains the swap logicial partition and that doesn't need to be backed up with partimage correct?

Any suggestions or corrections to the above would be great. Have I got the right information above?

---

