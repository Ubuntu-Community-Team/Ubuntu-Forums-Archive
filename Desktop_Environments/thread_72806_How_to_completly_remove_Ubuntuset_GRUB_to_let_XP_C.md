---
title: "How to completly remove Ubuntu/set GRUB to let XP CD to boot?"
date: 2005-10-07
forum: Desktop Environments
---

### Post by balazs on 2005-10-07
Hi guys,


i am selling away my notebook, and i have to install the original OEM Windows XP back on it before i give it to it's new owner.

Is there a nice way to do this?

It seems that GRUB does not let me boot from the OEM Hewlet Packard XP CD. How can i set grub properly? I searched with google and on the forums here too, and could not find a proper official documentation on how to say good-bye to ubuntu.

I've already tried to delete the partitions, but that screwed GRUB, it stuck with an error code "22", so right now i am reinstalling ubuntu just to remove it :-(

Pls. let me know a hassle free way to say good bye, my experience was nice all along while i was using the system. I do not want to be disappointed at the very end.

Thanx,

Balazs

---

### Post by 11hjpphty76lkjj on 2005-10-07
I could be incorrect, but you should be able to just boot from the winxp cd, delete the hd partitions, remake them which xp should auto like set the primary partition to active and then install as such.  Although if the OEM cd's wont let you do that you may need to boot from a win9x boot disk, repartition with fdisk and set the primary partition to active.  And actually you should be able to do this with during the ubuntu install, where as make the primary parition set the boot flag on, format it as fat 32, commit the changes, then reboot with the oem cd.  Although you may need to boot from the ubuntu cd with the expert option.  Just some ideas.

Aaron

---

### Post by Irony on 2005-10-07
*Boot from XP installation disc > press any key on prompt to boot from CD > after some time options appear, press R for recovery console > press 1 to select Windows > admin password, enter if no password > at the command prompt type fixmbr > warning given, hit y for yes, hit enter > at prompt type exit > eject disc*

You can then delete the ubuntu partitions by going;

*Start > All Programs > Administrative Tools > Computer Management > Disk Management*

Right click on the partition and delete it or format it as NTFS, it will then pop up in windows as a D partition in My Computer. I think you can merge the partitions, but you can't merge it to the C partition.

---

### Post by balazs on 2005-10-07
Thanx for the suggestions, but my HP NC6000 does not have a floppy drive.

So to summerize the suggestions:

Load the Install CD, format the drive to Fat32, save changes. That sounds nice, but why would this delete GRUB from the MBR?

As i said, i tried already to simply remove the partitions, but grub stayed on the MBR, and simply hung. I do not see any difference between deleting the partitions, or having an empty FAT32 partition, as it still does not allow me to boot from the OEM disk.

Once more, thanx for your replies.

---

### Post by balazs on 2005-10-07
To make my question more precize?

How do i set grub to allow booting the OEM CD?

Is there a command which load the CD instead of loading the default option?

---

### Post by 11hjpphty76lkjj on 2005-10-07
From my experience grub doesn't  disallow booting from the cd-rom, in your BIOS, in the boot sequence, is the cd-rom listed before the hard drive?  I've installed ubuntu, and booted to a windows xp cd fine, and it didn't involve grub.  grub is started after the BIOS says, "oh hey there is a hard drive I'm going to boot from it".  so make sure that the cd-rom is listed first in the boot sequence in your BIOS.

ie the BIOS boot seqence should be something like this:

1. USB (optional)
2. CDROM
3. HARD DRIVE

So if the BIOS doesn't see the USB or CDROM is boots the HARD DRIVE using Grub.  But booting from the cd-rom will not be effected if grub is on the hard drive.  It's a bios thing.

Aaron

---

### Post by balazs on 2005-10-07
I have added the "chainloading" thingy as a new option to my GRUB menu, but it does not help.

Right now what happens is that i choose at the bios prompt to "boot from CD", hit enter, but GRUB loads immidiatly, and nothing starts to load from the CD itself.

Any clues why is this?

---

### Post by 11hjpphty76lkjj on 2005-10-07
hmm odd.  I can't say for sure. :( Anyone else with ideas?

Sorry!

Aaron

---

### Post by 11hjpphty76lkjj on 2005-10-07
Wait a sec, during POST you are hitting the option for boot from cd.  Lets still verify the boot sequence, else can you boot from the disk at another pc?

Aaron

---

### Post by balazs on 2005-10-07
Hi Aaron,

thanx for the answers. The boot order is OK. The CD spins up fine. Still, instead of starting to boot from the CD, GRUB loads the default setting. I can see the contents of the CD in Gnome, and it mounts properly, so it is not a damaged CD. It is the original HP cd, and it worked many times before fine.

I also understand what u are explaining. If the CD would be bootable, the BIOS would boot that first, and the harddrive only afterwards. Which would mean that the CD is not bootable. But this is not the case. I used it several times without a glitch. 

This is frustrating.

---

### Post by 11hjpphty76lkjj on 2005-10-07
Maybe something in this thread will help?

[http://www.ntcompatible.com/How_to_remove_GRUB_loader_t28242.html](http://www.ntcompatible.com/How_to_remove_GRUB_loader_t28242.html)

Aaron

---

### Post by balazs on 2005-10-07
Hi guys,

after thinking about this whole issue, i think the problem is with the boot cd. I can not think about something else.

It is getting late here in India, so i will try tomorrow again.

Thanx for the ideas  until now.

---

