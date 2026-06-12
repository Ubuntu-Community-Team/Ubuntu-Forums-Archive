---
title: "Hard disk partitioning help please"
date: 2009-05-09
forum: General Help
---

### Post by jackbarnard on 2009-05-09
Hi, I want to install Ubuntu Linux on my Vista computer, so I went to the disk management tool and chose shrink volume on my C: primary partition (the only partition on that disk) to make room for it, however it says I only have around 20GB of space available for shrinking when my hard drive actually has about 170GB of free space on it.  Why could this be?

---

### Post by Tipped OuT on 2009-05-09
You should use Partition Magic for this kind of thing. I can give it to you for free, PM me if you'd like.

So yeah, I really don't know why that is, never dealt with Windows Disk Management before.

PS: If you have MSN Messenger, then click on the little butterfly below my avatar and add me if you'd like to discuss about obtaining Partition Magic, for free, any further.

---

### Post by jackbarnard on 2009-05-09
ok ive tried deleting old restore points created by vista but all thats done is give me 20gb more space in 'shrinkable' hard drive and 20gb more hard drive space if that makes any sense. so now i am allowed to shrink my partition by around 50gb but i have abour 200gb of free space in my hard drive! whats happened to 150gb of space?
help please lol.

---

### Post by ezsit on 2009-05-09
Have you run the defrag yet? This might get enough stuff moved toward the front of the drive and allow you to shrink the partition even more.

---

### Post by jackbarnard on 2009-05-09
yea i defragged about 6 hours ago, EDIT: should i do it again after now deleting the old restore points?

---

### Post by logos34 on 2009-05-09
you might try temporarily disabling hibernation file...maybe that's in the way.

Post a screenshot of disk manangement if you can

---

### Post by jackbarnard on 2009-05-09
heres a pic of my disk management:
[[IMG]http://img4.imageshack.us/img4/2314/diskmanagementm.jpg[/IMG]](http://img4.imageshack.us/my.php?image=diskmanagementm.jpg)

---

### Post by -kg- on 2009-05-09
> **Tipped OuT said:**
> You should use Partition Magic for this kind of thing. I can give it to you for free, PM me if you'd like.

So yeah, I really don't know why that is, never dealt with Windows Disk Management before.

PS: If you have MSN Messenger, then click on the little butterfly below my avatar and add me if you'd like to discuss about obtaining Partition Magic, for free, any further.

Partition Magic doesn't run under Vista.

I notice that Vista is installed on Disk One in your Disk Manager view.  What is on the Disk 0 partition?  If it isn't another OS (like Windows 7) then you could shrink it and install there.  If you do so, just make sure to install GRUB in the root of Disk 1, which is where your Vista installation seems to be booting from (or is it?).

Actually, if you can get 50 GB of free space, that should be plenty in which to do an installation, unless you plan on having multi-GB of files that you want to store on the ext3/4 partitions.  Otherwise, you can store the majority of your files in the free space on the ntfs/FAT partitions you have, then 50 GB would be more than enough.

---

### Post by jackbarnard on 2009-05-09
my disk 0 is a backup drive and yea i suppose i could put linux on there.  yea 50gb would def be enough for me its just the principle that 150gb of my hard drive is inaccessable to anything but vista.  im currently looking at a possible solution ill post again soon

---

### Post by -kg- on 2009-05-10
I know what you mean.

It used to be that I would partition a drive down because of the issue of cluster size.  Then I saw the advantage of not doing so, so I quit doing it so much.  Now, however, there's another reason to do it again; to resolve the issue you're having.

I'm back to, especially when installing Vista, installing the OS itself in pretty much as small a partition as I can create for it, then creating another partition to install software and store data in.  Then, if I need to create some space on my hard drive, I won't have to deal with trying to shrink the OS partition.  Other partitions used by Vista seem to shrink correctly.

Another aspect of separate partitions is that you can keep them defragged much easier.  Generally, I've found that it is the OS partition that will fragment more than the others, with the exception of some software with very dynamic data.

I just had a thought...how is your paging file set up?  You might want to consider setting up a static paging file on your spare partition only.  Once you reboot into Vista, any paging file will not exist on your OS partition...only your backup partition...and that will take yet another file off of your OS partition, perhaps giving you the ability to shrink it even further.

I do that as a matter of course with all my Windows OSes.  It minimizes paging file fragmentation and, since the paging file is on another physical hard drive, makes Windows run a bit faster, since it can access both the OS and the paging file virtually instantaneously.  It might be something else to try.

---

### Post by jackbarnard on 2009-05-10
ok ive managed to shrink my partition by quite a bit more using perfect disk 10, but now I have another question, I went to install Linux and at the partitioning screen it asks where you want to install it.  I freed up 50gb of space in the vista disk management tool, and this came up on the bar at the top with the other space on the disk occupied by the vista partitionas expected.  But which option do I choose?  If I choose 'largest continuous free space' or whatever it is then the bar at the bottom changes and says Linux will take 2.5gb with the rest left to Vista but this doesnt make any sense surely coz windows can only occupy the space i gave it (which is the whole disk minus 50gb) or does this bar at the bottom not mean anything? I obviously dont want to choose erase disk either, and I cant remember the other options now but which do I choose?
Thanks

---

### Post by -kg- on 2009-05-11
If you're sure that you freed up 50 GB and it shows only 2.9 GB when you select Largest Contiguous, then something is definitely wrong.  Actually, I don't even know that Ubuntu will install in that small of space.

The only thing I can think of that might be going on is the installer is trying to install to the wrong physical hard drive.  Do you have around 2.9 GB of free space on one of your other hard drives?  I'm thinking you can select which hard drive you want to install to at that stage of the menu.  Let me go see...OK, you're going to have to select "Choose Partitions Manually.

Choose Manual Partitioning and go to the next screen.  The drive that you freed space up on should show up there with all the free space indicated, and you can make your partitions from there.

I am assuming that you are installing Jaunty.  In the manual partitioning window, you will see a representation of your hard drives, with lines below it indicating the partitions and free space on each of your drives.  You will want to select the line that represents the 50 GB of free space you created.

First thing will be to create a swap partition at the end of the partition (you'll see a couple of radio buttons. The default is at the beginning...click the one for "end").  Make your swap partition approximately 1 1/2 X the amount of the memory you have installed and make sure you format it as swap in the "File System" drop down box.

Next, make your root partition.  This will be at the beginning of free space, so you can leave this as default.  Make this partition around 10 GB (or 15 GB, if you anticipate installing a lot of software). You can format this as ext3, or ext4 if you want to experiment with the newer file system. There are a few issues with it.  At the bottom of the screen, you want to mark this as "/" (which is root)

Next you want to create another ext3 (or ext4) partition in the remaining free space and mark this as /home.

As you're doing this, notice which drive you are making these operations on.  If this drive is not the first drive (hd0) and is instead on the second drive (hd1), then if you are actually booting to the 2nd drive (as it seems from your screen shots), you will need to make another adjustment.

When you are sure you have your partitions set up correctly, click forward to the next screen.  This will show you the operations that will be performed, and to the right you will see an "Advanced" button.  If you are sure that you are booting from the second hard drive, click this button.

This window allows you to change where to install GRUB's bootloader.  The default is hd0.  You will want to select hd1 (or sd1, depending) if you are booting from your second hard drive.

If you forget to perform this step, when you reboot from installing you will boot directly into Windows without going through GRUB, since GRUB will be installed in the MBR of the other drive.  All is not lost, though.  All you have to do is go into BIOS and change the setting to boot from the first hard drive.  GRUB will be there and should boot to either OS from that point.

If you are unsure whether you are actually booting from hd0 or hd1, you will need to check which drive you're booting to in BIOS.  Go into BIOS and check whether you are set to boot from the 150 GB or the 300 GB drive.

Hope this helps.

---

