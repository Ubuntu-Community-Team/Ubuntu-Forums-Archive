---
title: "Dell Vostro 1500 Duel-boot help?"
date: 2007-09-16
forum: Dell  Ubuntu Support
---

### Post by gpilkay on 2007-09-16
I've been looking at the forums, and I'm about to try to duel boot my Dell Vosto 1500 laptop with Gutsy come October.  I have Feisty running on my desktop but that's with two Hard Drives, one for each OS.  Last time, this forum was great for my first setup, now I'm going to try a more complex one!

To try to make this easier for myself, I ordered it from dell with the hard drive pre-partitioned into two equal halves.  I'm hoping that makes things simpler.  The partitions are supposed to be 60 gig each.

Does anyone know how I would make sure it loads properly into the pre-made partition?  I want to have an idea of what I;m doing BEFORE I do it, which is why I'm taking notes in advance.

Thanks again!

---

### Post by notwen on 2007-09-16
You're wanting to dual-boot Ubuntu with what other OS? =]  This shouldn't be too difficult, I'm currently dual-booting my Inspiron 1420n with the pre-installed Ubuntu along with WinXP.

---

### Post by gpilkay on 2007-09-16
Sorry!  I guess that would be important info...the laptop will come with Windows XP Home, the 120 gig drive pre-partitioned down the middle at the factory.

---

### Post by elyk on 2007-09-16
Just boot off the live CD, run the installer, and choose the second 60 gig partition when it asks you how you want to set up your disk. The installer should handle the rest of the partitioning automatically.

---

### Post by notwen on 2007-09-17
Yes, I'd recommend installing from one of the [new Ubuntu images]("http://linux.dell.com/wiki/index.php/Ubuntu_7.04#Download_Dell_Ubuntu_Image") released by Dell which use the basic Feisty Fawn install, [http://linux.dell.com/wiki/index.php/Ubuntu_7.04/Add-on_Packages](http://linux.dell.com/wiki/index.php/Ubuntu_7.04/Add-on_Packages) for some hardware issues in Dell PCs.  As elyk posted above, just use the Ubuntu installer and install to the 2nd partition and Grub should automatically pick up your WindowsXP install and your dual-boot should be good to go.  Post back with any updates. =]

---EDIT---
Here's a [thread]("http://ubuntuforums.org/showthread.php?t=515275") specifically for the Vostro 1400, not sure on the common hardware, but this may give you an idea of how to remedy some issues if they relate to same hardware.
Here is a Vostro 1700 How-to, seems to have alot of Vostro1400 users attempting his how-to, you may want to browse it should you find some of the info useful.

---

### Post by gpilkay on 2007-09-26
I got my laptop in, and tried out the Dell Remastered 7.04 CD.  It was useless, but when I tested out the Gutsy Tribe 5 disk on the 1500 tonight, it actually works just fine.  I even considered installing it right there, but I ran into trouble and didn’t want to destroy anything.  I guess I will wait till the stable release is out, now that I know 7.10 will work with this system, but I’m trying to get an idea of how to do this before I need to.

When I run the disk partitioner, I see several partitions already there.  I know that /media/sda1
/media/sda2 (windows)
/media/sda6 

Are all used by something.

/media/sda5 is largely clear, it shows up as D: in windows and is blank.  There is about 75 Mg of something there, though, when I see it in Linux.  

Given that this partition does not seem to have anything important on the Windows side, I’m assuming that it’s my safest option to install to. It’s an NFTS type file system.

How exactly do I tell the computer to leave whatever’s there with maybe 2-4 gig extra just in case (I can use that as a music file dump or something in Windows) and use the rest?  I tried several options but I just don’t really know what I’m doing.  I did look at the ‘resize whole disk’ thing, but it was going to write over the entire 120 gig volume.  There are several options for ‘don’t use’, but I didn’t want to potentially not create a GRUB record.

I’m VERY new at this…sorry if I sound really out of it.

---

