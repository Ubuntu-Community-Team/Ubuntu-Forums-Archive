---
title: "Disc boot failure"
date: 2009-06-12
forum: General Help
---

### Post by Uubnewb on 2009-06-12
Hi,

I just installed Ubuntu 9.04 64-bit.  When I restarted after the installation process Ubuntu wouldn't load up; instead I got a "Disc boot failure" message asking me to put in the boot disk.

At first it was the Windows installation I have on another partition that is causing the problem, so I deleted the Windows partition and re-installed Ubuntu.  Unfortunately that did nothing to fix the problem.  I still get the same message even though I now only have one operating system, namely Ubuntu 9.04, on my computer.

I am currently using the install disc as a live CD (thank goodness for that option), but I'm sure you'll agree that I cannot continue using this method indefinitely.

Your help will be greatly appreciated.

---

### Post by jerrrys on 2009-06-12
how did you install? manual, guided or use entire disk? do you want to dual boot?

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by Uubnewb on 2009-06-13
I selected the partition manually.

At first I wanted to dual boot, but when I received the "disk boot failure" message the first time, I deleted my Windows partition.  At the moment I am not trying to dual boot, I only have one operating system on my computer: Ubuntu 9.04.

In the meantime I followed [these]("http://ubuntuforums.org/showthread.php?t=224351") instructions to install Grub but that, unfortunately, changed nothing, I still get the same message.  I also tried changing the disc boot priorities before startup (by pressing delete when the first splash screen appears).

For more clarity, and in hope that it will help to determine the problem, the full message that is displayed is: "DISK BOOT FAILURE, INSERT SYSTEM DISK AND PRESS ENTER ...".  When I then insert the Ubuntu CD and press enter the system loads from the CD like it would normally do.  I get this message directly after the first splash screen (the one that informs me to press the "Delete" button to enter the Bios).

---

### Post by jerrrys on 2009-06-13
since you will only be running ubuntu, the easy  fix would be to reinstall and use the entire disk option.

also have you successfully ran the live cd without installing it? 

and last is some good reading...

[http://www.howtoforge.com/the-perfect-desktop-ubuntu-9.04](http://www.howtoforge.com/the-perfect-desktop-ubuntu-9.04)

---

### Post by Uubnewb on 2009-06-13
How does the "entire disk option" work?  I have another hard drive with all my files on, and I would hate to see Ubuntu automatically choose that hard drive.  I also might want to install windows on another partition (on the same hard drive) later on, so I would prefer to install Ubuntu on only part of the hard drive in stead of the entire disk.

The Live CD works perfectly.  As a matter of fact, the only operating system I am using at the moment is the live CD.  I also used the "Check disk for errors" on the CD (an option given before you boot or install from the CD) and found no problems.

By the way, would you mind posting that link again, it gives a "The requested page does not exist." message.

Thank you for your patience.

---

### Post by jerrrys on 2009-06-13
how does the use entire disk option work? it all pertty much automatic and should get you going for the moment and in the case of two drives, it will give you the option.   or.......

use guided install and tell it how much of the hdd to use.

the link i posted works for me, but heres another one.

[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

[http://ubuntuforums.org/showthread.php?t=282018](http://ubuntuforums.org/showthread.php?t=282018)

[http://aplawrence.com/Linux/linux_partitioning.html](http://aplawrence.com/Linux/linux_partitioning.html)

[http://ubuntuforums.org/showthread.php?t=1044768](http://ubuntuforums.org/showthread.php?t=1044768)

---

### Post by Uubnewb on 2009-06-13
Thanks, the link is working now.  I will try this install option and then report back.

---

### Post by keplerspeed on 2009-06-13
Double post from here:

[http://ubuntuforums.org/showthread.php?t=1186145](http://ubuntuforums.org/showthread.php?t=1186145)

Uubnewb, please check your BIOS settings as I have explained in the above link.

As you can see double posting makes a mess. Just bump your thread (but not too often!)

---

### Post by jerrrys on 2009-06-13
maybe a mod will come along and combine them...

---

### Post by Uubnewb on 2009-06-13
Like I said: Sorry for the double post, but I was rather desperate.  What do you mean by "bumping" the thread?

---

### Post by jerrrys on 2009-06-13
you just bumped your thread to the top of the list with your post.

---

### Post by Uubnewb on 2009-06-13
> you just bumped your thread to the top of the list with your post. 

Oh, okay.  Thanks for that.

So here is what I did now:

I installed Ubuntu again, this time using the guided installation option (using the entire disc).  When I restarted after the installation, I still received the same message.

So I checked the BIOS again to make sure everything was correct and it all looked fine to me:

```
Under the "Main" tab:

Primary IDE Master > DVDW
Primary IDE Slave > None
Secondary IDE Master > HDD1
Secondary IDE Slave > None
SATA1 > HDD2
SATA2 > None
SATA3 > None
SATA4 > None
HDD SMART Monitoring [enabled]
```

```

Under the "Boot" tab:

Boot Device Priority:
1st Boot Device [Hard Disk]
2nd Boot Device [CD ROM]
3rd Boot Device [Removable]
4th Boot Device [Disabled]
```

What should I do next?

---

### Post by zeroseven0183 on 2009-06-13
How about setting the HDD1 as the Primary IDE Master instead of the DVDW?

But... On which partition/HD did you install Ubuntu?

Since you have to hard drives, I believe it's booting on the wrong drive (HDD2) and not on HDD1. If you can find a setting on your BIOS to set the IDE first then the SATA (which, I think would be difficult).

---

### Post by jerrrys on 2009-06-13
looks like its booting to hdd1 in bios and you need to boot to hdd2. what is the make and model of your computer?

good question 'z'. im thinking hdd2 is where ubuntu is at, is this right?

---

### Post by Uubnewb on 2009-06-13
And the plot thickens...

No, unfortunately the solution is not that simple; Ubuntu is installed on HDD1 (160GB IDE), HDD2 (500GB SATA) is where I keep all my files and Removable (1TB external HDD) is where I keep my backups.  What I want to do is install Ubuntu and Windows on HDD1 on different partitions.

As for the Primary IDE Master: I tried to do that, but only my DVD ROM was available as an option.  I then set the Primary IDE Master to "none" hoping that if the computer do not "see" the DVD ROM, the hard drive will boot first.  Unfortunately that did not work either.

As a temporary solution I installed Windows again (on a partition on HDD1), and although this is hardly an ideal solution, I can at least now boot my computer without using a live CD.

The thing is, I really like Ubuntu and don't want to use Windows as my only OS.

My computer is a self-made AMD Athlon 64 X2 Dual Core 4200+ with an ASUS M2NPV-VM motherboard and a NVIDIA 9800GT GPU.

---

### Post by presence1960 on 2009-06-13
> **Uubnewb said:**
> And the plot thickens...

No, unfortunately the solution is not that simple; Ubuntu is installed on HDD1 (160GB IDE), HDD2 (500GB SATA) is where I keep all my files and Removable (1TB external HDD) is where I keep my backups.  What I want to do is install Ubuntu and Windows on HDD1 on different partitions.

As for the Primary IDE Master: I tried to do that, but only my DVD ROM was available as an option.  I then set the Primary IDE Master to "none" hoping that if the computer do not "see" the DVD ROM, the hard drive will boot first.  Unfortunately that did not work either.

As a temporary solution I installed Windows again (on a partition on HDD1), and although this is hardly an ideal solution, I can at least now boot my computer without using a live CD.

The thing is, I really like Ubuntu and don't want to use Windows as my only OS.

My computer is a self-made AMD Athlon 64 X2 Dual Core 4200+ with an ASUS M2NPV-VM motherboard and a NVIDIA 9800GT GPU.

Do you have a single IDE cable with primary/master connecting the DVD & hard disk to the motherboard? if so make sure the hard disk is plugged into the master and the DVD is plugged into the slave fitting. Check the jumpers on the drives too.

---

### Post by Uubnewb on 2009-06-13
No, the cables connecting my hard drive and my DVD ROM to my motherboard are two different ones.

---

### Post by presence1960 on 2009-06-13
> **Uubnewb said:**
> No, the cables connecting my hard drive and my DVD ROM to my motherboard are two different ones.

I saw an older HP with a motherboard that had the IDE inputs on the board labeled master & slave. Did you try switching the cables at the mobo?

---

### Post by Uubnewb on 2009-06-13
No, but I checked the user manual to make sure, and the cables seem to be connected in the right order.  Aside from that, if it was the cables, wouldn't Windows give the same problem?

---

### Post by jerrrys on 2009-06-13
good morning. see you made progress while i was snoozing.  got windows up and running, thats good.  did you use entire disk for windows?  if so, please to do the guided install and when you will get to a part where it will give you an option to free up x amount of disk space, just type in how much. this process can take several minutes up to several hours.  depends on how much it tries to free up.  after that, ubuntu will figure it out.  let windows be on the first partition. i dont recall if it will give you a grub option, but if it does, use ubuntu grub. also use ext3 file system, ext4 is still a bit unstable in my opinion...if you have any questions now a good time to ask. if not,go for it and good luck...jerry

---

### Post by Uubnewb on 2009-06-13
I only used a part of the partition to install Windows (30GB).  I'm quite used to Windows messing up my system, so I never use a large hard drive when installing it as it is only a matter of time before I have to re-install Windows.

---

### Post by jerrrys on 2009-06-13
let us know how it goes

---

### Post by Uubnewb on 2009-06-13
Okay, I guess it's time for a status report:

Since my problems started when I installed Ubuntu 9.04 I decided to install Ubuntu 8.10 instead.  The good news is that it worked:  I am now, once more happily using Ubuntu.  Unfortunately I now have to download and install all the drivers and updates again.

I suppose this means that the "Disk boot error" is a bug in Ubuntu 9.04.  Can you maybe tell me where I should report the bug?

I will however appreciate it if someone can still come up with a solution.  I would rather much like to use Ubuntu 9.04, especially since there are some minor bugs in 8.10 that I hope will be fixed in 9.04.

Thanks for all your help, you have all been very helpful so far.  Special thanks to you, Jerry, for your continues support.

PS: Later on, when I feel up to it again, I am going to try and install Ubuntu 9.04 again.  First I am going to try using the "guided resize" option as suggested.  If that fails I will attempt to install it in Windows (using the Wubi installer).  I will let you know how it went afterwards.

---

