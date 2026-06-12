---
title: "Dual Booting XP Home with Ubuntu."
date: 2007-07-14
forum: Dell  Ubuntu Support
---

### Post by amitpop on 2007-07-14
I have a couple questions about dual booting XP home with Ubuntu:

I have a Dell Dimension 2400 with a p4 2.53ghZ
250gb HD
first of all, is dual booting compatible with this anyway?

Second, if i dual boot Xp home and Ubuntu, does it wipe my main hard drive with XP on it? If so, is there any way i can dual boot without wiping my hard drive?

Finally, Where can i get a good tutorial online for dual booting?

Thank You!

---

### Post by lisati on 2007-07-14
There are a variety of options for setting up dual=boot. When installing Ubuntu from the "LiveCD" or the "alternate" CD you will be asked whether you want to use the whole disk or only part of it for Ubuntu

---

### Post by johnnydough69 on 2007-07-14
Hi Amitpop,

Have been working on a dual boot Dell for some time. XP Pro SP2 and previously Debian "Etch".  Presently trying Ubuntu Feisty because it is based on Debian, the community is so strong, and they leave out the kitchen sink to keep it simple.  Works good for a new guy.

Get your partioning right (lots of information available on that). If your entire drive is given over to Windows you will have to try to resize your partitions prior to install.  The live cd can help, I think.  Better research that prior to trying it. Then, as lisati said, use the live cd or alt cd.  Don't be afraid to do it several times.

As Ms Frizzle says: "Take chances, make mistakes, and get messy."

---

### Post by strabes on 2007-07-15
You shouldn't want the default XP install that comes with dells because it's full of crapware. The first thing I did after I got my dell laptop a year ago was format it with a new windows install.

Anyway, here's how my partitions are set up, in case you were looking for a good way to set up your dual boot system:

20gb: Windows XP Pro (ntfs)
15gb: Kubuntu 7.04 feisty (ext3)
1gb: Swap (n/a)
60gb: Shared Data partition (ext3)

Now let me explain a few things. First, if you **don't** want to get rid of the crippled windows install that comes with new dells and install a new copy, you'll have to resize the existing NTFS windows partition to around 20gb. I'm not sure if the feisty live CD is able to resize NTFS partitions, but I **am** sure that the [Gparted Live CD](http://gparted.sourceforge.net/livecd.php) does this. You'll have to boot up from the gparted live CD to resize the ntfs partition to around 20gb. This will probably take awhile. Also, make sure it's the first partition, at the beginning of the hard drive.

Once the ntfs partition is resized & at the beginning of the drive, you can go ahead and boot up the feisty live CD. When you get to the part of the install about partitioning the disk make sure you click "Manual" so that you can set up the partitions how you would like. Next to the windows partition, make a 15-20gb partition for ubuntu, a 1gb partition for swap, and the rest of your hard drive's free space for a shared data partition. Set the mount point of the data partition to /media/data or something similar.

Now go ahead with the install. After it's done, reboot and you should be greeted with the GRUB screen which allows you to select your operating system. Windows doesn't read or write to ntfs by default so you'll need to install [this driver](http://www.fs-driver.org/) to enable read/write of the data partition. If you have any questions, message me or post them in this thread.

I remember how confusing it was the first time I went through this process but once you have it set up it's pretty nice.

Hope this helps

---

### Post by dndzz on 2007-07-15
I've just started with Ubuntu (10 days) and being "chicken" about Dual Booting, I went the Wubi route. (Google it).
Eventually I'll go the regular dual boot but so far so good!

---

### Post by tabs on 2007-07-15
First of all I'm relatively new to Linux.

My first attempt at Dual boot XP/Linux failed with a grub error.To get the XP side of things working again 
I had to use the XP disc and run MBR.(This is a Dell pc btw.)

I won't go into details of what I did  for the next week but basically the Ubuntu Live cd didn't work for 
me.After much googling and forum browsing I manually partitioned the hard drive with  Ext3, Swap and 
mount point.This worked.

My advice, take it or leave it, is don't put dual boot XP/Linux on a pc thats IMPORTANT to you.

No doubt folks will say "I installed Ubuntu as a dual boot with XP and had no problem"  and thats fine but 
my pc met the Linux requirements by a long way and I had a ton of problems.

---

### Post by johnnydough69 on 2007-07-15
Must agree with strabes.  His partitioning is identical to mine, except that he was smart enough to keep the data partition non ntfs.  Thanks for the tip on "ext2 ifs" strabes.

---

### Post by strabes on 2007-07-15
It's so easy. You install windows on a 20 gb partition at the beginning of your hard drive. You make 3 partitions with the ubuntu live CD. You install ubuntu. That's it. If you get a grub error you use the ubuntu install CD or a grub superdisk to reinstall grub.

I have a dell e1705 laptop and I haven't had any hardware problems at all.

---

### Post by HermanAB on 2007-07-15
Modern PCs are so fast, that dual booting doesn't make much sense anymore.  The only good reason for dual booting is to play games in Windows.  If you are not a gamer, then you may be better served by installing VMware, Virtualbox or Qemu and running WinXP in that.  Doing so, you can run Windows in a window, concurrently - no annoying rebooting and interrupting what you are doing anymore.

---

### Post by strabes on 2007-07-15
That's really the only reason I have a dual boot. I play a bit of CS 1.6 and that's basically all.

---

