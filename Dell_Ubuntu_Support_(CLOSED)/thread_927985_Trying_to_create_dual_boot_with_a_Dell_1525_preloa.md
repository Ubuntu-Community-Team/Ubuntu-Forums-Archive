---
title: "Trying to create dual boot with a Dell 1525 preloaded with Ubuntu"
date: 2008-09-23
forum: Dell Ubuntu Support (CLOSED)
---

### Post by JlyGrnMigt on 2008-09-23
So I have here a new 1525 that came with Ubuntu that I need to turn into a dual-booting machine with XP.

I have the Ubuntu disk that came with the system (7.10) and a copy of XP.

I am finding a lot of information on how to create the dual boot when one is starting with a Windows installation (and that this is a preferred way to do it) but am having trouble getting Ubuntu off and Windows on in the first place.  Once I get past that, I'm confident that I can follow the tutorial to get the dual boot going, but I need a little help getting that far.

The Microsoft site ([http://support.microsoft.com/default.aspx?scid=kb;en-us;314458](http://support.microsoft.com/default.aspx?scid=kb;en-us;314458)) is unfortunately not helping, since it assumes that one knows more than I actually do, and it uses a floppy.  Seriously, who has a floppy anymore?

Thanks everyone...I hope I can get this working!

---

### Post by qstraza on 2008-09-23
well you can install windows after ubuntu, but than you have to re-enable grub boot loader, since win wont let you boot into ubuntu.

Why removing Linux is hard? Put win cd in, boot from it, and delete all unkown partitions, than install win.

---

### Post by qstraza on 2008-09-23
gr8.. i somehow double posted.. sorry

---

### Post by JlyGrnMigt on 2008-09-23
> **qstraza said:**
> 
Why removing Linux is hard? Put win cd in, boot from it, and delete all unkown partitions, than install win.

I guess I should have mentioned that when I tried to just stick in the Windows CD (assuming that it would trample over everything in its path) it couldn't find a hard drive and forced me to quit setup.

---

### Post by qstraza on 2008-09-23
oh that sucks. Im not sure what to do in this point, even tough, i dont think its ubuntus fault for windows not finding a hdd.

---

### Post by caljohnsmith on 2008-09-23
I would boot your Ubuntu Live CD, press ALT + F2 once your in Ubuntu, and type the following to run Ubuntu's partition editor:
```
gksudo gparted
```
And then you can wipe your HDD clean and create the partitions you need. I would highly recommend that you make the first primary partition at the beginning of the disk for Windows, and format it to NTFS. After that you'll need at least two partitions for Ubuntu, one for the main install and one for swap space. And you can create more partitions if you like, just remember you can have only 4 primary partitions, or 3 primary + 1 extended partition where the extended partition contains up to 63 logical partitions. Once you format the first primary partition to NTFS, probably your Windows Install CD will work. Let me know how it goes.

---

### Post by JlyGrnMigt on 2008-09-23
> **caljohnsmith said:**
> 
And then you can wipe your HDD clean and create the partitions you need. I would highly recommend that you make the first primary partition at the beginning of the disk for Windows, and format it to NTFS. After that you'll need at least two partitions for Ubuntu, one for the main install and one for swap space. And you can create more partitions if you like, just remember you can have only 4 primary partitions, or 3 primary + 1 extended partition where the extended partition contains up to 63 logical partitions. Once you format the first primary partition to NTFS, probably your Windows Install CD will work. Let me know how it goes.

Excellent.  Ok, so I am in GParted right now, and I have 5 partitions listed.  They are:
sda1, which is fat16, sized at 70.57 MiB, and cannot be resized.
sda2, which is apparently my cdrom
sda3, which is ext3, sized at 102.34 G, and flagged "boot"
sda4, which is extended, locked, sized at 4.38 G, and containing
sda5, which is linux-swap, locked, and also 4.38 G

So since the first one is non-resizeable, do I just leave it alone?

One of the instruction pages that I'm looking at gives approx. sizes for the wanted partitions as follows:
- 1st partition: 12-15 GB, NTFS file system For Win XP
- 2nd partition : Around 8- 10 GB, EXT3 file system for UBUNTU installation
- 3 rd around 2 GB , SWAP file system (assuming that your RAM is 1 GB, Normally it will be double the size of RAM)
- 4 th Partition, NTFS file system , remaining space for storage of normal files ,S/w ,documents etc (If NTFS it can be accesible from both Windows and linux environment)

The cdrom doesn't count in the limit of 4, right?  And that weird first one isn't nearly big enough to be used as my WinXP space, so how exactly do I deal with that since it's first and in the way.  Delete it?    Sorry to have so many questions...I really appreciate your help and hope I can someday be good enough to help others as well.

---

### Post by caljohnsmith on 2008-09-23
> **JlyGrnMigt said:**
> Excellent.  Ok, so I am in GParted right now, and I have 5 partitions listed.  They are:
sda1, which is fat16, sized at 70.57 MiB, and cannot be resized.
sda2, which is apparently my cdrom
sda3, which is ext3, sized at 102.34 G, and flagged "boot"
sda4, which is extended, locked, sized at 4.38 G, and containing
sda5, which is linux-swap, locked, and also 4.38 G

So since the first one is non-resizeable, do I just leave it alone?

If you click on the partition, say sda1, then right-click, there should be an option to delete the partition. I would do that will all of them so you can start clean. Just keep in mind that gparted doesn't actually do anything until you hit the "apply" button, so that is your insurance against mistakes. 

Also, sda2 can't be your CD-ROM, it is probably what is called an "extended" partition. An extended partition is merely a container for logical partitions, which in your case might be sda3, sda4, and/or sda5. Again, I would just delete all of them and start over since you aren't trying to save anything.
> **JlyGrnMigt said:**
> 
One of the instruction pages that I'm looking at gives approx. sizes for the wanted partitions as follows:
- 1st partition: 12-15 GB, NTFS file system For Win XP
- 2nd partition : Around 8- 10 GB, EXT3 file system for UBUNTU installation
- 3 rd around 2 GB , SWAP file system (assuming that your RAM is 1 GB, Normally it will be double the size of RAM)
- 4 th Partition, NTFS file system , remaining space for storage of normal files ,S/w ,documents etc (If NTFS it can be accesible from both Windows and linux environment)

Well you haven't really said yet how big your HDD is, but from the numbers you have above it looks like like it might be about 180 GB--is this about right? If that's true, those proposed partitions might be big enough for Windows and Ubuntu, but it depends on how many extra programs you install and things like that. I would give Windows maybe ~20 GB and Ubuntu ~15 GB; but again, if you don't tend to install a lot of extras, your numbers will probably be fine. And having the 4th storage partition as NTFS should work just fine since Linux now has good NTFS support. 

Anyway, let me know how it goes or if you need more details/info. :)

---

### Post by JlyGrnMigt on 2008-09-23
> **caljohnsmith said:**
> If you click on the partition, say sda1, then right-click, there should be an option to delete the partition. I would do that will all of them so you can start clean. 

Ok, that is only possible with sda1 and sda3.  The others are locked and I'm not sure how to unlock them. 

> 
Also, sda2 can't be your CD-ROM, it is probably what is called an "extended" partition. An extended partition is merely a container for logical partitions, which in your case might be sda3, sda4, and/or sda5. 


It says /cdrom in the column labeled "Mountpoint" and says fat32, not extended.  I'd happily delete it if I could...

> 
Well you haven't really said yet how big your HDD is, but from the numbers you have above it looks like like it might be about 180 GB--is this about right? 

I believe it's 120.  

I guess I should leave some room in the windows partition for ArcGIS since that's the main reason he needs windows on this machine.

> 
Anyway, let me know how it goes or if you need more details/info. :)

Thanks a million.  I just gotta get those locks off of there...

---

### Post by caljohnsmith on 2008-09-23
So you are doing all this from the Live CD, right? And make sure none of your HDD partitions are mounted anywhere (they shouldn't be if you just boot the Live CD and immediately run gparted). And you ran gparted as root with "gksudo", correct? I've only had to use gparted a few times to do my own partitioning, so if it still says your partitions are locked, I don't know why. If you can't figure it out, you could always completely erase your HDD's partition table and then gparted will think the whole HDD is empty space. If you want to do that, just do the following from a terminal (applications > accessories > terminal):
```
sudo dd if=/dev/zero of=[COLOR="Red"]/dev/sda[/COLOR] bs=512 count=1
```
Make sure you use the correct HDD above (/dev/sda or whichever yours is), and not some other device. Let me know how it goes.

---

### Post by JlyGrnMigt on 2008-09-23
> **caljohnsmith said:**
> So you are doing all this from the Live CD, right? And make sure none of your HDD partitions are mounted anywhere (they shouldn't be if you just boot the Live CD and immediately run gparted). And you ran gparted as root with "gksudo", correct? I've only had to use gparted a few times to do my own partitioning, so if it still says your partitions are locked, I don't know why. If you can't figure it out, you could always completely erase your HDD's partition table and then gparted will think the whole HDD is empty space. If you want to do that, just do the following from a terminal (applications > accessories > terminal):
```
sudo dd if=/dev/zero of=[COLOR="Red"]/dev/sda[/COLOR] bs=512 count=1
```
Make sure you use the correct HDD above (/dev/sda or whichever yours is), and not some other device. Let me know how it goes.

It says "live session user" so yep, using the live cd, and I typed the code just as you typed above.  I will cancel out and try again, and use this other code if all else fails.  Thanks!

---

### Post by JlyGrnMigt on 2008-09-23
Ok, so the one that says the mount point is /cdrom has an option to unmount, which gives an error saying it's busy then crashes GParted.  So I guess I'll use that other line of code you gave :)

---

### Post by JlyGrnMigt on 2008-09-23
Ok, so I used that code and set up the new partitions from scratch, hit apply, and it threw an error immediately.

The first time I started Gparted after using that code though, it created a dos...thing...sorry I forget what it called it and said it would erase everything, which was fine, then it apparently did that and closed Gparted.  So I opened it again to set the partitions and now this.

So I open Gparted again, and now it shows the area of my first partition marked off, but with an unknown file system.  The other three were not even roped off.  Will it help to post the saved details?

---

### Post by caljohnsmith on 2008-09-23
Sounds strange. Yes, go ahead and post the saved details, and can you post a screen shot of what you are seeing with gparted? That would also help.

---

### Post by JlyGrnMigt on 2008-09-23
GParted 0.3.3

Libparted 1.7.1

Format /dev/sda1 as ntfs  00:00    ( ERROR )
     	
calibrate /dev/sda1  00:00    ( SUCCES )
     	
path: /dev/sda1
start: 63
end: 52050599
size: 52050537 (24.82 GiB)
set partitiontype on /dev/sda1  00:00    ( SUCCES )
     	
new partitiontype: ntfs
create new ntfs filesystem  00:00    ( ERROR )
     	
mkntfs -Q -vv /dev/sda1
     	
The device doesn't exist; did you specify it correctly?
libparted messages    ( INFO )
     	
Error informing the kernel about modifications to partition /dev/sda1 -- Device or resource busy. This means Linux won't know about any changes you made to /dev/sda1 until you reboot -- so you shouldn't mount it or use it in any way before rebooting.
The kernel was unable to re-read the partition table on /dev/sda (Device or resource busy). This means Linux won't know anything about the modifications you made until you reboot. You should reboot your computer before doing anything with /dev/sda.

========================================

---

### Post by JlyGrnMigt on 2008-09-23
[IMG]http://i7.photobucket.com/albums/y274/jlygrnmigt/gpartedshot.png[/IMG]

---

### Post by JlyGrnMigt on 2008-09-23
Then after I close and re-open GParted (always with the gksudo command), it looks like this:
[IMG]http://i7.photobucket.com/albums/y274/jlygrnmigt/gpartedshot2.png[/IMG]

---

### Post by JlyGrnMigt on 2008-09-29
Ok, here's what I finally ended up doing:

Using my non-doorstop computer, I dled nLite and created a custom XP installation starting with my SP2 installation CD, and adding SP3 and the proper drivers for my HDD since even the SP3 installation alone was having issues detecting it correctly.  With SP3 plus the driver, XP installed without a hitch on the 30 gigs I gave it.  I got all the drivers set, defragged, and moved onto the Ubuntu installation

I decided on a fresh install of Hardy since Dell sent the Gutsy CD and we lost our sound when we upgraded to Hardy.  Sound seems to work with this...go figure. Everything was simple once I figured out how to get ol' XP recognize fancy new technology.  Frustrating, but I feel much better now that I've been through it.

---

