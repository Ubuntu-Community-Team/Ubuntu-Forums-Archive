---
title: "Ubuntu Breaks Again!!!!!"
date: 2009-01-23
forum: General Help
---

### Post by CaesarLike on 2009-01-23
Okay so its like this.

Yet again Ubuntu has broken itself when I try to do something that should be simple and straight forward. I wanted to add a hard drive to Ubuntu.  Under windows this is as easy as it gets, but under Ubuntu, well lets just say it make windows look good.

So, I followed this community tutorial.
[https://help.ubuntu.com/community/InstallingANewHardDrive]("https://help.ubuntu.com/community/InstallingANewHardDrive")

Everything went fine, until I had to mount the drive.  I formatted the drive as ext3, and I made the mount point directory owned and group owned by the main user's account.  
I put the drive to auto mount in fstab.  Acording to fdisk the drive is sda, so thats what I made it in fstab.  But when I reboot the pc, the drive suddenly becomes sdb, not sda, and I end up remounting my / partition on another drive to the mount point.  OK, so I change fstab to make the drive sdb, reboot, and ubuntu now makes the boot disk sdb, and the new disk sda!!  WTF????  So everytime I boot up I am remounting the / partition!

Ok, so I think, I shall just mount the drive manually. but no, this does not work either, as only root can mount it. And when the drive is mounted as root the owner and group owner are made as Root.  So clearly the drive is only useable to root, which is NOT what I want.

But wait, there's still more, as Ubuntu and linux have not yet finished messing things up - as usual.  Now when I boot up, I cannot access root at all.  Nor can I mount USB drives, access the network at all, and god knows what else.  Put simply Ubuntu has broken itself yet again. And it looks as if I will have to re-install it yet again. This now makes about the 5th or 6th time in under 6 months I have had to do this.  And people say windows is crap???  I have not had to reinstall windows in over 2 years now.  How folowing a simple tutorial, and making a few simple directory ownership changes can break a whole OS is totally beyond me. And why in 2009 installing a hard drive should be so hard is also beyond me.  While windows may be crap in some areas, at least it makes doing the basics easy.  And installing a HD is about as basic as it gets.  Make a partition or 2, format, then tell the OS where to mount it.  Why linux must make it so friggin difficult is totally lost on me.

So, the question to all this, is this, after I re-install this crap called linux - yet again -, how do I set up fstab and the mount point to allow me to have normal user (admin user) full access to the drive?  I am not going to bother about trying to fix unbuntu, some things are clearly outside the realm of the possible.  As I only want the install to gain some basic working knowedge of linux, and for torrents and such like, the time spent on trying to fix it could be better spent elsewhere.

Oh yes, and if anyone has missed it, I am so friggin fed up with ubuntu breaking all the time, I am just about ready to ditch linux altogether.  Or at least Ubuntu.  While it may be easy to use, when it works!, the fact it just keeps breaking itself is driving me crazy.  I mean its not hard to use mostly, and I know what not to do.  Suely there is a better linux OS out there?  One that is not so brittle, and so easy to stuff up when just doing things that should be simple.  At least things that are simple and easy under windows.  And while I am no windows lover, and I know its crap and unsecure, at least it does not break itself anywhere so readily as Ubuntu does.  At least in my experience that is.

---

### Post by steveneddy on 2009-01-23
First of all, Why are you complaining? You made the choice to run Linux.

This is a better tutorial for what you are trying to accomplish.

My Server still runs with this fstab edit.

I know it says Windows, but just follow the directions and name the other partition or hard drive /media or /storage instead of Windows.

[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)

BTW, this came from one of the links in my sig.

The links in my sig should get you a lot of answers for questions that you don't know that you need to ask yet.

Hope you get it fixed.

And remember, maybe you didn't make the choice to run Linux, maybe Linux chose you.

:-k

---

### Post by albinootje on 2009-01-23
> **CaesarLike said:**
>  I put the drive to auto mount in fstab.  Acording to fdisk the drive is sda, so thats what I made it in fstab.  But when I reboot the pc, the drive suddenly becomes sdb, not sda, and I end up remounting my / partition on another drive to the mount point. 

It makes sense to use UUID. That will prevent problems like this.
[http://www.unixtutorial.org/2008/05/ubuntu-uuid-how-to/](http://www.unixtutorial.org/2008/05/ubuntu-uuid-how-to/)
[https://help.ubuntu.com/community/UsingUUID](https://help.ubuntu.com/community/UsingUUID)

---

### Post by jrusso2 on 2009-01-23
You added a drive that should be sdb1 Which would be the second drive with Sda being the first hard drive.

---

### Post by Mud.Knee.Havoc on 2009-01-23
> **CaesarLike said:**
> But when I reboot the pc, the drive suddenly becomes sdb, not sda, and I end up remounting my / partition on another drive to the mount point.  OK, so I change fstab to make the drive sdb, reboot, and ubuntu now makes the boot disk sdb, and the new disk sda!!

Don't hard drives come with jumpers these days?

---

### Post by albinootje on 2009-01-23
The OP didn't mention whether it was about ATA or SATA.
With ATA it would be /dev/sda (before /dev/hda) for first hdd on the primary IDE interface etc.
But with adding another SATA disk I can imagine that things can get .. confusing.
Again.. using UUID is a good idea.

---

### Post by CaesarLike on 2009-01-23
Okay thanks for the reply everyone.

First, you are right, I did choose linux, and I am increasingly questioning why I did considering the amount of time I waste trying to make it do simple things.  And if it was linux that chose me, then clearly linux must be getting desperate for followers!

Second, the drive is an IDE drive.  The OS is on a SATA drive.  This is not a dual boot system.  The IDE I want for storing torrent downloads.  The drive is connected to the one and only IDE port on the motherboad, no other drives are attached to the IDE cable.  As far as I can tell the jumpers are correct, but as it has no actual markings on the jumpers, I am guessing they are correct based on the position of the jumpers on another and different brand of drive I have.

Also, as far as I can tell, many, but not all, of the directories and files for the OS have been chown to the main admin user account. As far as I can remember, most of these files should be owned by root?  Why most, but not all have been changed is a complete mystery to me.  If I had done a recursive chown in / then I assume all would have been changed.  The only cause for this that I can see was when I chown the mount directory for the drive.  Why it would chown so many other directories and folders I have no idea.

Anyway, its time for a re-install.  But I think maybe also time for a change of distros.  Ubuntu is good when it works, but I think maybe its time to try out some other distros.  Not that they will be fundamentally better.  But maybe they will be less problem prone for me, less brittle, and a bit more predictable in their actions.

Thanks again for the advice and links :)

---

### Post by albinootje on 2009-01-24
> **CaesarLike said:**
> 
Anyway, its time for a re-install.  But I think maybe also time for a change of distros.  Ubuntu is good when it works, but I think maybe its time to try out some other distros.  Not that they will be fundamentally better.  But maybe they will be less problem prone for me, less brittle, and a bit more predictable in their actions. 

If you want "easy" Linux distributions, try :
Fedora Linux
OpenSUSE Linux
PCLinuxOS
Mandriva Linux

---

