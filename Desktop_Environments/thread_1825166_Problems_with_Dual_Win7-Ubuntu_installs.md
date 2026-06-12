---
title: "Problems with Dual Win7-Ubuntu installs"
date: 2011-08-14
forum: Desktop Environments
---

### Post by jwbasham on 2011-08-14
I have made attempts to install Ubuntu on two systems now with the same results.  Both systems eventually crashed after a month.  The crash was so bad I had to reinstall both systems from the original operating CDs.  Has anyone else had this same problem or something similar?  I know I would like to have more info before ever making the attempt to do another dual boot system.

Thanks.

---

### Post by elgordodude on 2011-08-14
Sorry to hear about that, it's not uncommon for sytems to crash, but it is weird for them to crash that hard that often. Since you seem to be expressing frustration more than looking for help here's a couple of things I can tell you from my experience.

First, it's weird to crash ubuntu and win at the same time as the OSes don't interact. This points toward a hardware failure, an old drive an overheating processor, some bad memory, outdated bios, who knows but realistically win won't accidentally kill ubuntu and vice versa, and to do it twice, in a month?

Second, have you experimented with any of the flavors in Linux? If you have an older system Lubuntu might be a better fit, maybe unity is conflicting with some of your drivers and 10.04 would be a better place to start, heck maybe you'll just like Mint better. And if you burned from the same cd or .iso image it could be as simple as a corrupt install. Good luck in the future,

---

### Post by jwbasham on 2011-08-15
The system I am using is a brand new system.  450gb HDD, 4gb RAM, and i5 pentium processor.  It is not a hardware failure.  Yes I have tried different flavors of Linux with the same results.  I am currently experimenting with Ubuntu because I have an upcoming class in the fall that will require it.  Plus I installed it using Wubi.exe and downloading the install files right there and then.  That takes out the corrupt install.

Thanks.

---

### Post by tlcstat on 2011-08-15
Greetings,

> It is not a hardware failure.

Having built hundreds of systems over ten years I would say that it could most definitely be a hardware problem. I'll admit that current technology is very dependable but still has a failure rate. Could be that you have a bad bit in high ram that you seldom access. Also you don't say what file systems are being used. Windows will install in fat32 which is easy to crash. Ubuntu will install in a EXT2 file system which could also crash. Also, is is possible that nothing crashed but grub. I will usually plug my drive in to a usb adapter and check the data. If the data is good you probably have a grub problem. If you don't have a extra computer to check the drive with an adapter then use a Live disk like Puppy linux or even the Ubuntu install disk and check it. Not enough data.
tlcstat

---

