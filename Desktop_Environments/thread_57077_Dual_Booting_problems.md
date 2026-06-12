---
title: "Dual Booting problems"
date: 2005-08-15
forum: Desktop Environments
---

### Post by tiggerliam on 2005-08-15
Right firstly i'm a bit of a n00b when it comes to Linux and dual booting!

I had windows xp on my laptop and created another partition on the same physical drive. I installed KDE on this drive and it detected XP and installed the GRUB boot loader and it all worked fine for many months. Then I had to reinstall windows due to completely separate reasons and now rather predictably the MBR has been rewritten so I can't boot into my KDE install. I've tried a lot of things and have messed up my MBR twice, so i've reinstalled windows effectively 3 times this week.

I've also recently tried the UBUNTU disk but it seems to me that to install and use grub I have to delete my linux partition first? Well I don't really want to start the linux again from scratch i'd much prefer to continue with my current install.

Is there any easy way of doing this? If so can someone point me in the right direction or just give a step by step fool proof idiot guide. KDE is much better than windows, i've tried a DVD writter on many different installs and versions of windows in various machines and never got my drive to write quicker than 1 speed. It writes in 8 speed in Ubuntu without the need to install any specific drivers !!!

---

### Post by Martin Witte on 2005-08-15
This is covered on this page, [http://ubuntuguide.org/#restoregrubmenuafterwindowsinstallation](http://ubuntuguide.org/#restoregrubmenuafterwindowsinstallation). Also read paragraph  'How to use Ubuntu Installation CD, to gain root user access?' on this page!

---

### Post by tonysathre on 2005-08-15
you dont need to reinstall the OS to reinstall grub. to do this boot to the cd and hit enter until you get to the partition part of the install where it ask where you want to install ubuntu then go back, this should take you to the main menu, go down til you see install grub and go through the steps. ive done this many times myself and it had worked everytime

---

### Post by tiggerliam on 2005-08-15
Firstly thank you both very much for your replies. 

Tonysathre i'll try it again but I think that method doesn't work as it won't install it because the drive isnt mounted (or some similar error).

Also I had a glance at the guide about how to edit the bootloader to include XP but I can't log into Linux at all so I can't see how i can do that. However i'll read that link more thoroughly later as i'm sure it might be able to help me some how. I'm surprised that i'm finding this so hard!

---

### Post by Martin Witte on 2005-08-16
If you still got the installation cd follow this link: [http://ubuntuguide.org/#gainrootinstallcd](http://ubuntuguide.org/#gainrootinstallcd) to boot into linux.

---

