---
title: "Duel boot problem"
date: 2011-03-03
forum: Desktop Environments
---

### Post by totocompany on 2011-03-03
hi friends.

I am new user of this forum. I am in a problem that this in my laptop i use in drive C windows 7 & drive E i use ubuntu. but some problem i need to setup my windows 7. When i complete the setup then i can boot the windows 7 but can not boot the ubuntu operating system. 

Now how i can boot in ubuntu in my laptop? 

please inform me & really sorry for my bad English. 

Thanks all

---

### Post by yusof125 on 2011-03-03
Hi Totocompany,

Don't worry, I'M just like you too.
Lot's to learn but it fun and new thing will you find here.

Let begin:

1. Try to read and learn this:
[https://help.ubuntu.com/community/DualBoot/Partitions](https://help.ubuntu.com/community/DualBoot/Partitions)
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

2. Solutions:
1.	Dual-Booting Ubuntu Linux and Windows 7/Windows Vista (with the Windows bootloader)
[http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)

2.	EasyBCD 2.0.2
[http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1)

3.	Adding Linux to the Vista Bootloader
[https://help.ubuntu.com/community/WindowsDualBoot#Manual%20partitioning](https://help.ubuntu.com/community/WindowsDualBoot#Manual%20partitioning)

---

### Post by yusof125 on 2011-03-03
The problem is same here if:

Problems:  DualBoot Ubuntu in Booting Screen
Kronology :
1.	PC  Installed with Ubuntu 10.10 (what ever desktop i386 or amd64) in directory C:\.
2.	Want to tryout Kubuntu 10.10 or Xubuntu 10.10 or Edubuntu 10.10 in same directory C:\.
3.	Used wubi.exe of Kubuntu 10.10.
4.	Install  Inside Windows. Must uninstall Ubuntu first.
5.	I don’t unistall but I’ve Deleted Ubuntu Folder in dir C:\.
6.	Used wubi.exe of Kubuntu 10.10.
7.	Install Inside Windows. Done.
8.	In boot screen have:
Windows Vista Home Premium
Ubuntu
Kubuntu
9.	Ubuntu boot is already corrupted, How to repair or remove the corrupted Ubuntu or  the Windows bootloader

The Solutions:
1.	Dual-Booting Ubuntu Linux and Windows 7/Windows Vista (with the Windows bootloader)
[http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)

2.	EasyBCD 2.0.2
[http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1)

3.	Adding Linux to the Vista Bootloader
[https://help.ubuntu.com/community/WindowsDualBoot#Manual%20partitioning](https://help.ubuntu.com/community/WindowsDualBoot#Manual%20partitioning) 

by yusof125

---

### Post by sanderd17 on 2011-03-03
Let me first explain what happened:

When you startup the computer, the BIOS looks at a predefined place (called the mbr) and runs the code on it. When you have a configuration win7 - Ubuntu, the mbr starts GRUB2 (GRand Unified Bootloader). Grub then lets you choose which OS you want to boot.

Now you installed Win7 again and windows overwrote the mbr and lets it point to the windows installation only.

Solution:

So what you need to do is overwrite the mbr again and let it point to grub.

You can do that by reinstalling GRUB2 using a live CD. See this thread: [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275) point 13

Please make sure that you understand every step before you continue. And do make a backup. When you make a mistake, chances are that you loose everything on your computer.

---

