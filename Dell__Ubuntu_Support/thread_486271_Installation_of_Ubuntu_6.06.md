---
title: "Installation of Ubuntu 6.06"
date: 2007-06-27
forum: Dell  Ubuntu Support
---

### Post by DigitalHighway on 2007-06-27
I am trying to install Ubuntu 6.06 on my Dell Inspiron 6000.  Running into problems with partitioning portion of the install.  Right now, I have four partitions 

/dev/sda1  fat16
/dev/sda2  ntfs
/dev/sda4  linux-swap
/dev/sda3 fat32

I need to add another partition for the /root directory.  Any suggestions on how to install, fix or repair this installation.  Any suggestions would be greatly appreciated?

---

### Post by Scunizi on 2007-06-27
ok.. the NTFS partition looks like it has Windows installed on it.  Is that right?  As for the other partitions, is there data on them that you need to save or did you create them for the install.  For the rest of this I'm going to assume that there's nothing on them.

1st.. I noticed you have SATA drives.. you might have some problems installing like I did.  Here's a clip from the release notes on Dapper.  Do what they say before installing even if you don't have raid setp.  It helps.

> If you are installing from the Desktop CD on a system that already has one or more RAID arrays or LVM volume groups set up, you must disable the arrays (sudo /etc/init.d/mdadm stop; sudo mdadm --stop --scan) and volume groups (sudo vgchange -a n) before starting the installer.

Now on to the other issues.  You really don't need fat16 or 32 partitions.  If those were ment for the install and data sharing, delete them both.  You can use one large partition for both home and root if you want or seperate root into another partition.  If you seperate root give it 8-12 gigs to play with and leave the remaining to /home. 

Format your root to reiserFS and your /home to ext3.  ext3 is read and write compatible with windows as long as you install the widows driver for it.  It makes it much easier to swap data from one side to the other.

You already have a swap so you're ok there.

By the way,  why are you using Dapper?  I do because I like the stability and it's a production machine. (of course I have other partitions with the newer stuff just to play until the problems get sifted out.):D

---

### Post by DigitalHighway on 2007-06-27
ok.. the NTFS partition looks like it has Windows installed on it. 

Yes. I have windows XP home as my primary operating system.

As for the other partitions, is there data on them that you need to save or did you create them for the install.

This is where my problem is.  I don't know what my fat16 partition and fat32 is used for? system restore? Dell recovery?  I don't want to delete these because as of right now I dont know what they are used for.  Did some searches on google, but have not found any answers to partitioning on a dell 6000.  Any suggestions?

By the way, why are you using Dapper? I do because I like the stability and it's a production machine. (of course I have other partitions with the newer stuff just to play until the problems get sifted out.)

I am totally new to this linux thing. :) I thought I should start somewhere since Dell is now providing end users with ubuntu on new dell machines.  I know 7.04 and 6.10 are out there, but I thought I could upgrade later, once I get familar with linux.  Do you know of any good linux books you could recommend  for beginners??

---

### Post by Scunizi on 2007-06-28
Dapper is solid.  Fiesty seems to be ok right now too.  A good book is one that I own, Beginning Ubuntu Linux from Novice to Professional by Keir Thomas.  It really clued me into a lot of things.  

So if you want to leave the fat partitions alone, you're going to have to resize the NTFS partition.  Make it smaller and take the newly created blank portion and split it into your root and /home partitions.  By creating a seperate home it will make it easier to upgrade or simply reinstall an upgraded version.

---

### Post by DigitalHighway on 2007-06-28
You can have only four partitions, correct?

How do I create a root and /home partition with the partitions I already have ???

---

### Post by Scunizi on 2007-06-28
True to the 4 "PRIMARY" partitions.  So what you have to do is resize the NTFS partition, delete the swap partition, with the freed space, use all of it and create a new "primary" partition.  Inside of that you'll create 3 logical partitions "/" root, "/home", and "/swap".

---

### Post by DigitalHighway on 2007-06-28
How do I create one Primary Partition and 3 Logical Partitions.

Do I need Partition Magic?  

Is there a website with directions on how to do this step by step?

Thanks for all the help so far.

---

### Post by Scunizi on 2007-06-28
No need for partition magic.  If you're going to leave the 2 fat files systems and the NTFS then you'll actually have three primary partitions.  The last partition you want to make "extended" which is the same as LVM.  Once that is made it isn't really formatted, just designated differently.  Inside of that partition you want to make a /home partition, a "/" (root) partition and a /swap partition.  These will all be logical instead of primary and be listed below the "extended" partition.  Ubuntu has a partitioner built in that's as good as partition magic.  During the install you'll get to a point where it will enter the partitioner and you'll be presented with some choices.

Choose "Manual" partition.  This is where you will create the extended, root, swap and home partitions.  I can't tell from your original post how much space you currently have allocated for the created "swap" partition but a general rule of thumb for the allocation is 1.5x your Ram for swap. So if you have a gig of ram allocate 1.5 gigs for swap.  Root can be anywhere from 8 to 12 gigs and use the remainder for /home.  To change what kind of partition it is, double click on the partition and click on the mount point.  That will bring up a box to change the  "label" on the partition ie swap, root (known as /) and home.  

Personally if you're just testing things out and want to avoid upgrade headaches later, download Ubuntu Fiesty Desktop and install that.  Don't mess with Dapper.  When I first installed Ubuntu over a year ago I didn't have a clue about linux.  I needed to mess around with it. Screw things up and try to fix it .. etc.. I'm still learning tons but my Ubuntu install is now "production" for work at home.  I have other partitions on other drives I'm playing with for the newer stuff.

Enjoy!

---

### Post by DigitalHighway on 2007-06-29
I have created the three logical partitions.  Which "file system" do I set each logical partiton to?  ext3?

---

### Post by Scunizi on 2007-06-29
Swap is Swap and won't format to anything but "swap".  Use ext3 for the rest and you'll be fine..

---

### Post by DigitalHighway on 2007-06-29
This is driving me nuts.  I created the three logical partitions but now I get an error message:

Unable to detect filesystem?Possible reasons are:
The filesystem is damaged
The filesystem is unknown to libparted
There is no filesystem available (unformatted)

any suggestion before I throw this laptop against the wall.  Scary part is:

It might help!

Installation from Hell!

---

### Post by Scunizi on 2007-06-29
When did you get this error?  After installation on reboot? or during installation?

---

### Post by Scunizi on 2007-06-29
One more question.  Can you get into the Fat partitions from windows? or are they hidden?.. If you can get into them, is there anything there?

---

### Post by DigitalHighway on 2007-06-29
Installation is finally complete.  Ubuntu is installed.

I performed a restart and logged into windows XP pro.  Windows detected "new hardware". Then I did a system restart and booted up using Ubuntu Live cd.  Started the install again.  All logical drives were detected and I was able to complete the install.

I guess windows xp needed to detect the new partitons.

I might have more gray hairs now then before.

Scunizi, I appreciate all your help. This installation would not have been completed without your help.  Thanks again.

---

### Post by Scunizi on 2007-06-29
Welcome to Ubuntu land...  the next thing you should do is install xChat from Synaptic.  Then figure out how to log onto chat.freenode.net port 8001 (even though the referances are for irc.freenode.net).  Once on, type /join #ubuntu    you'll now be live with lots of Ubuntu users in real time.  Ask questions get answers.  Although things like this install would not have been possible on IRC.:popcorn:

---

