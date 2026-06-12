---
title: "Can't boot without liveCD"
date: 2006-07-04
forum: Desktop Environments
---

### Post by veloxdraco on 2006-07-04
I have 2 HDs, one with Ubuntu, and one with XP. Whenever I restart the computer, it always boots into XP. I found the easiest way around this was using the liveCD and selecting the option to boot from the first HD, which makes grub come up, and all is well. This got anoying after a couple of weeks of switching back and forth (I need to spend a little bit of time getting some games working on wine so I won't need to switch so much), so I reinstalled Ubuntu figuring I did something wrong the first time. It didn't fix anything. I searched the forums here, and googled various queries, and I couldn't find anything, so I am asking here now. Can someone help me?

And if anyone can help with the problem in the following thread, that would be great, too.
[http://ubuntuforums.org/showthread.php?t=191060](http://ubuntuforums.org/showthread.php?t=191060)

---

### Post by tonyr1988 on 2006-07-05
I have the 2 HD setup as well (Ubuntu + XP). Which HD did you set as master and which one as slave?

If you have XP as master, that's probably why it's not loading GRUB. Of course, the LiveCD gets first priority above all HDDs.

I'd check that first. If you don't know how to check master / slave, Google for info about jumpers.

---

### Post by veloxdraco on 2006-07-05
Yes, the HD with Ubuntu is master.

---

### Post by PandorsBox on 2006-07-06
[QUOTE=veloxdraco]Yes, the HD with Ubuntu is master.[/QUOTE]

Did you install WinXP after Ubuntu?  That would explain it...  

I would try running grub again and set it up that way.  It's not for the faint of heart, however :D  Can you show us your partition tables for each drive? (use fdisk on the devices; p, then q to quit)  That would help us figure out what's going on.

---

### Post by veloxdraco on 2006-07-06
I've had XP for a while, I stuck in the other HD to play with linux until I understand it enough to use it full time. I had breezy installed, then updated to dapper, and it would boot correctly, but I had a bunch of other problems, so I reinstalled straight to dapper, fixing most of my problems, but creating this one.
I'll post my partition table in just a minute, I need to reboot into ubuntu.

Ok, here it is:
   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1          13      104391   83  Linux
/dev/hda2              14         274     2096482+  82  Linux swap / Solaris
/dev/hda3             275        5495    41937682+  83  Linux

---

### Post by veloxdraco on 2006-07-08
Nevermind, I just realized my problem. Somehow, I forgot you could choose the boot order for the hard drives on my motherboards bios, I have absolutely no idea how it got changed, but it wasn't booting the master, it was going directly to the slave. I feel incredibly stupid now.
Thank you both for trying to help, and if anyone could help me with the post I linked before, that would be good, too.

---

