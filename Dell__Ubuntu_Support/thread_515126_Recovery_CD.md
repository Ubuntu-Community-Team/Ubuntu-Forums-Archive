---
title: "Recovery CD?"
date: 2007-08-01
forum: Dell  Ubuntu Support
---

### Post by perryrt on 2007-08-01
Ok, I just purchased an inspiron 1420n, with Feisty preinstalled. I've been using Linspire (and Lindows before it) for years, but I'm still fairly new to Ubuntu.

I'm thinking it will probably take me a week or so to really "move in" - you know, set preferences, browser shortcuts, email, etc. etc. The little things.

I also noted that the system came just with a "stock" Ubuntu DVD. Presumably this disc doesn't have the special drivers for this machine, and certainly won't have my "specializations", etc etc.

So...what I'd like to do is to create what Dell provides with MS-based machines - a "recovery disc"...but with my choices.

The idea is to have a DVD that I can, when it all goes horribly wrong, drop into my drive and be able to start over...*sans* data, of course, but at least from a stable starting point.

So, my question is - what's the best way/program/set of commands to do this? I have seen lots of ways to backup my system, but what I want to do is more along the lines of creating an install/live CD.

---

### Post by Rocket2DMn on 2007-08-01
Ubuntu has a LiveCD, it is the preferred method of trying out Ubuntu and installing
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)
Your DVD may function as one, pop it in, boot from it, and find out.

---

### Post by kuja on 2007-08-01
Ubuntu (and derivatives) also have DVD isos available. I always use the dvd to install and use it as a repository as well.

---

### Post by dragonwings on 2007-08-02
dont wast your time i ve been trying to do it for the last 2 weeks
no one here really knows or cant be botherd helping?

i managed to make a live cd with remastersys but it only worked as a live cd when i installed it to hard drive grub booted and went to loading bar and frezed .

i have tried over 6 other applications but they didnt work or had crap instructions
unless you are some sort of super nerd or get help from one your buggerd

---

### Post by rickyjones on 2007-08-02
My advice would be to use a hard drive ghosting program. Set up all your settings, ghost it, and if you need to restore you can pop in that cd and restore it. If you keep your /home on a different partition then you might be able to just ghost the other partitions.

-Richard

---

### Post by Dellfan on 2007-08-02
Dell machines with a factory install of Ubuntu have a recovery partition on the disk. You can recover from this partition, the same way as on the Windows based machines. This will return the machine to an "as shipped" configuration (ie. no user data). The re-installation process is invoked from the GRUB menu at boot time. Just select "Reinstall Operating System". 

NOTE: If you reformat the drive, and blow away this partition, the recovery option will obviously be lost. The CD shipped with the system is just a stock 7.04 LiveCD. It is close to what is installed on the system but does not have all the required patches and tweaks.

More information on the as shipped OS is available at:

[http://linux.dell.com/wiki/index.php/Ubuntu_7.04#Factory_Installation_Details](http://linux.dell.com/wiki/index.php/Ubuntu_7.04#Factory_Installation_Details)

---

### Post by perryrt on 2007-08-02
[quote=Delfan]Dell machines with a factory install of Ubuntu have a recovery partition on the disk. You can recover from this partition, the same way as on the Windows based machines. This will return the machine to an "as shipped" configuration (ie. no user data). The re-installation process is invoked from the GRUB menu at boot time. Just select "Reinstall Operating System". [/quote]

I actually didn't know that. I saw the GRUB menu "hit ESC" thing for about 2 seconds when I booted up - I was kinda wondering what else was in the menu, but hadn't gotten far enough into the machine to look there yet. That's a reasonable start, althought it won't have my "personalizations" on it.

[quote=rickyjones]My advice would be to use a hard drive ghosting program. Set up all your settings, ghost it, and if you need to restore you can pop in that cd and restore it. If you keep your /home on a different partition then you might be able to just ghost the other partitions. [/quote]

This seems more like a good long term solution. I think I'll investigate that. Rickyjones - can you suggest any Ubuntu-based ghosting programs?

[quote=dragonwings]dont wast your time i ve been trying to do it for the last 2 weeks
no one here really knows or cant be botherd helping? [/quote]

Well - the reason I got interested in Linux in the first place was because I like figuring it all out for myself :) Tell you what, though - when I get this working, I'll repost on this thread what I came up with. Hopefully that will work for you too. Hang in there - it's been my experience that usually you can find someone somewhere who knows the right answer.

---

### Post by rickyjones on 2007-08-02
> **perryrt said:**
> 
This seems more like a good long term solution. I think I'll investigate that. Rickyjones - can you suggest any Ubuntu-based ghosting programs?


I haven't actually used any Ubuntu-based ghosting programs. However I have heard that one good way to accomplish this is to create a TAR archive of the mount points that you need and burn that image to a CD or DVD. To restore back to the way it was (with all your drivers) you could boot to a live CD of some sort and restore the archive image.

It would accomplish the same thing, just not a block-by-block image like Ghost.

So, Step One would be to create a .tar.gz of the filesystems that you wish to backup. Step Two would be to burn that to media. Step Three would be to restore the backup with a live CD of some sort.

I hope this points you in a good direction!

-Richard

---

### Post by kuja on 2007-08-02
How about partimage?

---

### Post by deserthowler on 2007-08-03
> **Dellfan said:**
> Dell machines with a factory install of Ubuntu have a recovery partition on the disk. You can recover from this partition, the same way as on the Windows based machines. This will return the machine to an "as shipped" configuration (ie. no user data). The re-installation process is invoked from the GRUB menu at boot time. Just select "Reinstall Operating System". 

NOTE: If you reformat the drive, and blow away this partition, the recovery option will obviously be lost. The CD shipped with the system is just a stock 7.04 LiveCD. It is close to what is installed on the system but does not have all the required patches and tweaks.

More information on the as shipped OS is available at:

[http://linux.dell.com/wiki/index.php/Ubuntu_7.04#Factory_Installation_Details](http://linux.dell.com/wiki/index.php/Ubuntu_7.04#Factory_Installation_Details)

If I use this recovery, am I able to repartition the drive with it?  

I want a separate home partition.  I can save my /home partition and a few of my configuration files on the network on another machine.  I haven't done a lot of customizing.  I use dpkg -l > installedprograms to get a list of the programs already installed in a file on my /home partition.  This allows me to duplicate my installation.

I've had enough Linux experience I'm hesitant to dork up something that works.

Earl

---

### Post by rickyjones on 2007-08-03
I'm assuming that the recovery option will blow away all the data on the drive (all mount points, including /home) and will put the original install back exactly as it was when you first powered on the computer. I doubt it will let you play with the partition scheme.

-Richard

---

### Post by deserthowler on 2007-08-21
> **rickyjones said:**
> I'm assuming that the recovery option will blow away all the data on the drive (all mount points, including /home) and will put the original install back exactly as it was when you first powered on the computer. I doubt it will let you play with the partition scheme.

-Richard

I'm trying to find that out too. :confused: If it reinstalls Ubuntu (and lets you partition) :) or just is an image that rewrites the whole hard drive. :mad: I looked at the recovery partition and can't really tell for sure.:confused:  

I would like to install another distro on the hard drive.  Maybe I'll just do it and see what happens.  Good project for next week after my Linux SIG meets and sees my 1420n.

Earl

---

### Post by perryrt on 2007-09-06
> I'm trying to find that out too.  If it reinstalls Ubuntu (and lets you partition)  or just is an image that rewrites the whole hard drive.  I looked at the recovery partition and can't really tell for sure. 

Did you ever find out an answer to this?

---

### Post by gbrainin on 2007-09-07
Unfortunately, the recovery partition has no options, and it repartitions the drive as it was on shipment.  So if, like me, you've messed with your partitioning, you'll lose that if you use the recovery function.

---

