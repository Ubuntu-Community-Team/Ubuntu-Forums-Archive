---
title: "DUMMY: Deleted Ubuntu partition (XP) Now Grub = error 17"
date: 2009-05-22
forum: General Help
---

### Post by fpuhan on 2009-05-22
I knew I'd screwed up the moment I hit the "OK" button. Now I'm paying for it (baring my back for flagellation...)

My "sandbox" laptop (IBM ThinkPad R40) was a dual-boot Windows XP/Ubuntu 8.04 system. I also had Wubi (Kubuntu 8.04) installed on the XP partition.

I decided to go to an all-Wubi (9.04) solution, and so I used Windows Disk Manager to reformat the Ubuntu partition (I would have liked to have just expanded my primary back to the whole disk, but I couldn't find a way to do so without erasing everything on the disk -- something I want to avoid doing). I then installed Wubi onto the "new" E: drive. And rebooted.

Oops. The Grub bootloader starts up and immediately throws an "error 17" and locks up.  Oh, boy.

I've been told I can simply repair the Master Boot Record, but I am unsure how.  I do not have my XP recovery disk, but I do have a copy of Hiren's BootCD.  Not being a disk geek, these things baffle me (not to mention some of them are pretty old...).

So, now I can boot from a Knoppix CD, Hiren's CD, or my Jaunty CD.  But not from my hard disk.  Any suggestions?

---

### Post by hexanol on 2009-05-22
If you have no more Linux OS on your hard drive, the best solution would be to fix the MBR with the Recovery Console utility that you can find on Windows install CD.

This is as simple as: putting the Windows CD in your drive, boot from the CD, tell it you want to enter the Recovery Console, and then once you are in the Recovery Console, you type "fixmbr". After that, it should boot just fine.

EDIT: you can find more information about the XP Recovery Console [here]("http://support.microsoft.com/kb/314058").

---

### Post by coffeecat on 2009-05-22
There are several ways of repairing the Windows mbr listed [here](http://www.users.bigpond.net.au/hermanzone/p18.htm). The simplest and easiest is with SuperGrubDisk - the link is on that page. The menu in SGD is poor, but if you can find the right choice it works quickly and easily. I've tried it myself - it does work.

---

### Post by Bender2k14 on 2009-05-22
I also recommend SuperGrubDisk.  I used it to fix this exact problem.

You can also put SGD on a USB, so I didn't even need to waste a CD :) (as long as your computer supports booting from USB that is).

---

### Post by fpuhan on 2009-05-22
> **coffeecat said:**
> There are several ways of repairing the Windows mbr listed [here](http://www.users.bigpond.net.au/hermanzone/p18.htm). The simplest and easiest is with SuperGrubDisk - the link is on that page. The menu in SGD is poor, but if you can find the right choice it works quickly and easily. I've tried it myself - it does work.

Yep, that's exactly what I did! After I posted the original message, I did some searching and found SuperGrubDisk. I burned a CD, booted from it, booted into it and simply followed the instructions I found in the docs on the SuperGrubDisk web site. Piece of cake!

I simply logged in to close this thread. I'm delighted to see people have responded as quickly as they did, as I only opened it about 90 minutes ago!

:)

---

### Post by 73ckn797 on 2009-05-22
Quick responses are directly relevant to descriptive thread titles. You did well Luke!!

---

### Post by BLTicklemonster on 2009-05-22
I had to do some work to get a laptop working and hooked the drive up to my box here, but for some reason that escapes me, I never got anything done with it, put it back in the laptop and finally got it going right. BUT, I could not boot to ubuntu any more. Trying to reset grub using a live disk and find /boot/grub/stage1 wouldn't even work. So I downloaded and burned super grub disk finally, and booted from it thinking perhaps my mrb on the windows partition was goofing things up. Well, not only would SGD not do anything for my mbr. Yes, I forget what it said, but it was basically, "dude, this windows isn't supported. It's XP64 bit. I thought the newest version of SGD would work on a 64 bit XP install... Oh well. Then after that, guess what? And remember, I never actually got SGD to do anything, so it never actually performed any tasks... Windows wouldn't boot any more either. No Ubuntu, no windows. Great giggly wiggly. 

I just went to the live cd, opened gparted, removed the boot flag from the xp partition, and installed Ubuntu fresh on a spare blank partition I was going to use for fotos later on. It works, but I can't boot to the old Ubuntu at all.

Not seeking advise, just ranting on how SGD, in obviously the wrong hands, can mess things up even worse!

---

### Post by s3nsiu on 2009-05-23
i think that this is ur solution
[http://ubuntuforums.org/showthread.php?t=1162263](http://ubuntuforums.org/showthread.php?t=1162263)
make the steps with the commands with win cd...cause i think that u cant enter win so first 4 steps are useless to u

---

