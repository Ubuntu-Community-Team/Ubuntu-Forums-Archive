---
title: "Wubi works"
date: 2007-04-17
forum: Connecticut Team
---

### Post by Razzl on 2007-04-17
If you're double-booting Windows and you don't really like having to boot through GRUB or have Windows be second fiddle (the instructions on the Wiki for changing boot-order works but requires a little bit of terminal editing), I experimented with Wubi on the Feisty beta in Windows XP Media Center edition and it worked well.  Wubi is the program that lets you install Feisty inside of Windows with the Windows installer (no cd to burn) and boots from the Windows bootloader with Windows as top dog.  I found Ubuntu seemed to work properly and fast enough, and the only problem I had was not understanding why Ubuntu took up so much space when seen in Windows Explorer (it carved out 30gb of my 100gb hard drive).  Ubuntu normally only takes about 3gb of space for the program; I couldn't tell if Wubi does a messy job of using space when the program is unzipped or whether it was empty space appropriated by Wubi from what it found.  It's kind of a rush to open Windows Explorer and see your Ubuntu folders in the drive list...:cool: 

[http://www.cutlersoftware.com/ubuntusetup/wubi/en-US/index.html](http://www.cutlersoftware.com/ubuntusetup/wubi/en-US/index.html)

---

### Post by Dragonbite on 2007-04-18
Another alternative is running VMWare and have a virtual client of Linux.

I'm looking at going the other way.. set up Linux as the primary, and virtualize Windows with the Windows-only programs necessary (Visual Studio Express, IE, Pain.NET, IIS, SQL Server Express, Web Developer Express, Cisco VPN Client, etc.)

---

### Post by Razzl on 2007-04-18
I'm one of the many who got my Windows as an oem install on the machine without a complete Windows disk, so Wubi was the only option.  Like everything else Ubuntu, though, it was free, and when I decided to uninstall (because I already had Ubuntu running elsewhere on its own partition) it uninstalled cleanly using the Windows uninstaller.

I'll bet anyone who's got a complete boxed copy of WinXP is going to make some money at the flea market this Summer...

---

### Post by spesheled1 on 2011-02-19
I have been a fan of Ubuntu for years and have always set up my Windows PCs to dual boot Windows and Ubuntu. I purchased a Compaq Presario CQ62 laptop with Windows 7 a few months ago. It wouldn't have been my first choice for a laptop, but it was really cheap and I'm a poor college student. It's actually a very nice laptop, but it didn't come with any Windows 7 disks. All installation files are placed on different "recovery" partitions on the HDD. In Windows 7 you do get the option to make actual recovery disks, but that would mean a complete reinstall.

This caused a problem when I went to install Ubuntu because there were several partitions that had been created for the purpose of making recovery much easier. I could have decided to wipe everything, but having to reinstall Windows 7 when you don't really have too seemed like too much of a hassle in this situation.

Then I found the Wubi installer when I was checking out the 10.10 release of Ubuntu. I decided to give it a shot and it's working perfectly. It seems just as stable as my other Ubuntu PCs that were installed in the traditional manner. This seems like a very good option for those who are new to linux and hope Ubuntu continues to make this option available.

---

### Post by Rubi1200 on 2011-02-19
I know I have nothing to do with the  Connecticut Team, but I just wanted everyone to know about the GRUB updates breaking Wubi installs.

See here for more information as well as solutions:
[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

Greetings :-)

---

