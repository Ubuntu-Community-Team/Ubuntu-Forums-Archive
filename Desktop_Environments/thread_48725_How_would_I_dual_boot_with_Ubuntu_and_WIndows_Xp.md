---
title: "How would I dual boot with Ubuntu and WIndows Xp"
date: 2005-07-13
forum: Desktop Environments
---

### Post by cheetahman on 2005-07-13
Could you help me do it the Windows Partition covers the whole drive

---

### Post by geearf on 2005-07-13
Hello,

you first need to resize the partition with some tool (i usually use Partition Magic for that but it ain't free, and it broke stuff some time so be carefull).

Then once the first partition is resized, you need to create one or more for ubuntu.

I have 3 :
one for ubuntu at /
one for the swap
and one for me at /home.

After that just roll in with the ubuntu cd install and it will be really easy :)

---

### Post by Xian on 2005-07-13
You need to read the [Official Install Guide](http://archive.ubuntulinux.org/ubuntu/dists/hoary/main/installer-i386/current/doc/manual/en), and view for specific information regarding your question the [Pre-Partitioning](http://archive.ubuntulinux.org/ubuntu/dists/hoary/main/installer-i386/current/doc/manual/en/ch03s05.html) and [Bootable System](http://archive.ubuntulinux.org/ubuntu/dists/hoary/main/installer-i386/current/doc/manual/en/ch06s03.html#di-make-bootable) instruction pages.

---

### Post by wjp.reg on 2005-07-13
In general terms, you need to make some free space - shrinking the windows partition(s). 

You are wise to defrag your windows part first.

Then using partition software (linux or windows) resize windows.

When finished, reboot.  Make sure your computer can boot from the CD (check your BIOS).

Pop in the ubuntu CD and auto-install.  Ubuntu will use all the free space by default and create a dual-boot loader for you.

good luck!  \\:D/

---

### Post by geearf on 2005-07-13
first  \\:D/

---

### Post by cheetahman on 2005-07-13
What is ubuntu's default bootloader Lilo or Grub

---

### Post by DancingSun on 2005-07-13
[QUOTE=Xian]You need to read the [Official Install Guide](http://archive.ubuntulinux.org/ubuntu/dists/hoary/main/installer-i386/current/doc/manual/en), and view for specific information regarding your question the [Pre-Partitioning](http://archive.ubuntulinux.org/ubuntu/dists/hoary/main/installer-i386/current/doc/manual/en/ch03s05.html) and [Bootable System](http://archive.ubuntulinux.org/ubuntu/dists/hoary/main/installer-i386/current/doc/manual/en/ch06s03.html#di-make-bootable) instruction pages.[/QUOTE]
Wow, I never knew there was an official install guide!  This should be located somewhere obvious on the official website!

---

### Post by mingster on 2005-07-13
personally, i'd recommend getting a second harddrive to install Ubunto onto. There's  less chance of anything going wrong during the install, plus, if one of your harddrives fails, you'll still have a usable operating system.

---

### Post by cheetahman on 2005-07-13
Couldn't I have SuSE resize my partitions for me then install Ubuntu which will delete the SuSE partitions and also keep my Windows partitions

---

### Post by jordanj1969 on 2005-07-13
I used Partition Magic 8 and partitioned 15gig of my 60gig drive for Ubuntu.... You do need to defrag before you begin the partition though.  Also, if you use GoBack (Norton) disable it prior to trying to partition your drive... Good Luck!

Need any further assistance just send me a message.

---

### Post by DancingSun on 2005-07-13
[QUOTE=cheetahman]What is ubuntu's default bootloader Lilo or Grub[/QUOTE]
Grub.

I just recently did a dual boot install of Ubuntu onto a HDD with an existing WinXP installation.

You just need to resize the Windows partition to make room for Ubuntu.  To resize, make sure you defrag your Windows partition first, so that you can free up some space at the end of the Windows partition.  This will allow the Windows partition to be resized without the lost of data, if done correctly.

To resize the Windows partition, if the partition is FAT32 or NTFS, the Ubuntu installer should be able to resize it for you (Ubuntu 5.04).  Just remember to use the manual partition option when prompt.  The default option is to wipe out the whole drive and install Ubuntu over it!  Once in the manual partition screen, select the Windows partition and choose to resize it.  Do not shrink it below the amount that is in use by your windows installation!  Normally, the partitioner will tell you that it cannot resize the partition, but just to be safe, make sure you are aware of the limits!  The partitioner should prompt you that it needs to write the changes to the disk, confirm and proceed.

After resizing the Windows partition, create the Ubuntu partition by consulting the Official Install Manual, the section on the parition schemes is really solid and I would use that as a reference if I knew about it earlier.

---

### Post by cheetahman on 2005-07-13
[QUOTE=DancingSun]Grub.

I just recently did a dual boot install of Ubuntu onto a HDD with an existing WinXP installation.

You just need to resize the Windows partition to make room for Ubuntu.  To resize, make sure you defrag your Windows partition first, so that you can free up some space at the end of the Windows partition.  This will allow the Windows partition to be resized without the lost of data, if done correctly.

To resize the Windows partition, if the partition is FAT32 or NTFS, the Ubuntu installer should be able to resize it for you (Ubuntu 5.04).  Just remember to use the manual partition option when prompt.  The default option is to wipe out the whole drive and install Ubuntu over it!  Once in the manual partition screen, select the Windows partition and choose to resize it.  Do not shrink it below the amount that is in use by your windows installation!  Normally, the partitioner will tell you that it cannot resize the partition, but just to be safe, make sure you are aware of the limits!  The partitioner should prompt you that it needs to write the changes to the disk, confirm and proceed.

After resizing the Windows partition, create the Ubuntu partition by consulting the Official Install Manual, the section on the parition schemes is really solid and I would use that as a reference if I knew about it earlier.[/QUOTE]
 Could you give me a link to the partition part of the offical install manual

---

### Post by cheetahman on 2005-07-13
So I have to partition it manually not automatically like SuSE does

---

### Post by cheetahman on 2005-07-13
Also how long would this install take

---

### Post by DancingSun on 2005-07-13
You could partition the Linux partitions automatically, but you need to resize the Windows partition manually.

After resizing the Windows partition, you can choose guided partition to setup the Linux partition (though I must've missed this, since I wasn't aware of this option), or have it automatically allocate the Linux partitions (which only includes "/" and "swap").

The install was blazingly fast when compared to the XP installation.  I don't know the exact numbers but after the partitioning, I went away for about 30 mins and when I came back it was ready to be rebooted.

---

### Post by DancingSun on 2005-07-13
[QUOTE=cheetahman]Could you give me a link to the partition part of the offical install manual[/QUOTE]

[http://archive.ubuntu.com/ubuntu/dists/hoary/main/installer-i386/current/doc/manual/en/ch06s03.html#partman](http://archive.ubuntu.com/ubuntu/dists/hoary/main/installer-i386/current/doc/manual/en/ch06s03.html#partman)

---

### Post by cheetahman on 2005-07-13
Is this install all done in text mode not gui

---

### Post by DancingSun on 2005-07-13
[QUOTE=cheetahman]Is this install all done in text mode not gui[/QUOTE]
Yes, it's in text mode.

---

### Post by cheetahman on 2005-07-13
[QUOTE=DancingSun]Yes, it's in text mode.[/QUOTE]
 What does the ubuntu partioner look like by the way

---

### Post by geearf on 2005-07-13
text mode asking question about the size, type ... of the partition.

---

### Post by cheetahman on 2005-07-13
[QUOTE=geearf]text mode asking question about the size, type ... of the partition.[/QUOTE]
 Found it at
[http://shots.osdir.com/slideshows/slideshow.php?release=305&slide=9](http://shots.osdir.com/slideshows/slideshow.php?release=305&slide=9)

---

### Post by geearf on 2005-07-13
that's it.

---

### Post by cheetahman on 2005-07-13
[http://shots.osdir.com/slideshows/slideshow.php?release=305&slide=9](http://shots.osdir.com/slideshows/slideshow.php?release=305&slide=9)

So I click the bottom one

---

### Post by cheetahman on 2005-07-13
[QUOTE=cheetahman][http://shots.osdir.com/slideshows/slideshow.php?release=305&slide=9](http://shots.osdir.com/slideshows/slideshow.php?release=305&slide=9)

So I click the bottom one[/QUOTE]
 Then what do I do

---

### Post by cheetahman on 2005-07-13
I get these 3 options in the partioner menu it probably isn't the first one.

Erase Entire disk:IDE1 master (hda) - 41.1 GB Maxtor 2F040L0
Use the largest continuous free space
Manually edit partition table

---

### Post by DancingSun on 2005-07-13
[QUOTE=cheetahman]What does the ubuntu partioner look like by the way[/QUOTE]
[http://ca.geocities.com/zachandloricox@rogers.com/ubuntu/windowsxp.html](http://ca.geocities.com/zachandloricox@rogers.com/ubuntu/windowsxp.html)

---

### Post by DancingSun on 2005-07-13
[QUOTE=cheetahman]I get these 3 options
Erase Entire disk:IDE1 master (hda) - 41.1 GB Maxtor 2F040L0
Use the largest continuous free space
Manually edit partition table[/QUOTE]
Oh yeah, when I was installed XP, XP some how left about 30Gb of diskspace alone....maybe that's where the continuous free space came from.

Anyway, if you haven't shrink the XP partition yet, then choose the last option to manually shrink it.  You should be able to do the following:

[list=1]
[*]When you see the XP partition on the list, highlight it, and press "enter".
[*]There should be a field that shows the size of the partition.  Highlight that field and press "enter".  
[*]Type in the new size and press "enter".
[*]The partitioner should ask you about writing to the disk at this point.  Confirm, and proceed.
[*]You should see your unpartitioned free disk space now.
[*]Create the Linux partitions.
[*]When you're done partitioning, there should be an option to write changes to disk on the partitioner's main screen.  Highlight it and press "enter".
[*]You should now be in another screen to confirm the changes.  Once you confirm and proceed, the installer will format the Linux partitions and install Ubuntu.
[/list]

Edit:
These are basically the steps that I went through to install Ubuntu (AMD64).

---

### Post by cheetahman on 2005-07-13
[QUOTE=DancingSun][http://ca.geocities.com/zachandloricox@rogers.com/ubuntu/windowsxp.html](http://ca.geocities.com/zachandloricox@rogers.com/ubuntu/windowsxp.html)[/QUOTE]

Great site but the system rescue hasn't been updated in a while and can't I use the knoppix cd also which can run the same exact program.I might use that and is it possible to change the login screen in grub to a fancy GUI like SuSE and this could also work on any other distro when dual booting.

---

### Post by DancingSun on 2005-07-13
[QUOTE=cheetahman]Great site but the system rescue hasn't been updated in a while and can't I use the knoppix cd also which can run the same exact program.I might use that and is it possible to change the login screen in grub to a fancy GUI like SuSE and this could also work on any other distro when dual booting.[/QUOTE]
 You don't need to use the SystemRescueDisc.  Like I said, the Ubuntu install disc is all you need.  The link and most of the Ubuntu install guides out there refer to the previous version of Ubuntu, which does not have the ability to resize NTFS partitions.  But with 5.04, you have the ability to resize NTFS partitions within the installer.

There is a project that could change the GRUB's appearance on this forum:
[http://ubuntuforums.org/forumdisplay.php?f=77](http://ubuntuforums.org/forumdisplay.php?f=77)

---

### Post by DancingSun on 2005-07-14
Just spot this cool link from another thread.  It gives you screen shots from the partitioner:

[http://www3.telus.net/linux4u/](http://www3.telus.net/linux4u/)

---

### Post by BeSerKa on 2005-07-14
Wow, if its as easy as it sounds to do a dual boot system with Ubuntu, I think I'll do that as soon as I get home.

Cheers everyone for the info.

---

### Post by DancingSun on 2005-07-14
[QUOTE=BeSerKa]Wow, if its as easy as it sounds to do a dual boot system with Ubuntu, I think I'll do that as soon as I get home.

Cheers everyone for the info.[/QUOTE]
Yeah, I was amazed how smoothly the install went.  The only problem I had was at the end of the install when the installer wanted to unmount something, it got stuck at 88 percent.  I'm guessing it's trying to unmount the CD drive.  So no worries, I just push the reset button, and I'm on my way to booting Ubuntu.

Just make sure you understand everything that you are doing, so that you won't "accidentally" choose something that messes up the system.

---

### Post by cheetahman on 2005-09-15
Thanks for the info

---

### Post by manis on 2005-09-15
Hello.
This is the step when I installed Xp and Ubuntu ( dual boot)

1. Make two partition - I m using Partition Magic 8.0. 
2. Install XP first in on the C partition.
3. Install ubuntu - make sure you boot from cdrom
4. ubuntu -(Partioner Program )will ask you whether you want to use 100% or all of your hardisk - select no and do your choice.
5. and the ubuntu ask you whether you want automatic partition on the other partiton (not xp partition)
6. select yes and ubuntu will be automate your partition with / (root partition ) and swap .
7. installing will continue and at the end grub will be configure automatic.
8. when finished take out your ubuntu cd and there is grub menu - select what do your want - ubuntu or win XP. ( I will say goodbye to wind..w)
9. for further information please seach at yahoo - type ubuntu stater guide - read this  valueable howto...
10. let me know ..ok
thank.

---

