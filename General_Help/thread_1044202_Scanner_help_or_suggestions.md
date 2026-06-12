---
title: "Scanner help or suggestions"
date: 2009-01-19
forum: General Help
---

### Post by Indyviews on 2009-01-19
Hello, I really like linux and Ubuntu but have two major problems, one is in getting my scanner to work. I have tens of hours googleling and searching forums on this and having other work to do...this is beginning to literally make me sick. I need an opinion as to if I should pursue this or go the route of reinstalling windows 2000 (only to use the scanner) with Ubuntu or having Ubuntu with another linux distro on the same hard drive...or my extra hard drive.

After downloading all the needed files and backends I could find for my Epson Perfection 3170 scanner, I realized last night that I am not going to have my original scanner controls etc. This morning I realized also that after turning the scanner on....that Sane came on with all of the various panels and perhaps it was going to work and I thought perhaps I can live with this. However....when trying to scan, I get the: Failed to start scanner- invalid augument.

Also when inserting my Epson CD, it actually came up on the screen this time and I thought perhaps it would do something but no....it  eventually came up with: cannot find the Autorun Program. There is an Auto Run.inf but it is just a small text file. I saw in one thread that someone game a command line to force the running of such a disk.

My question first is: Is there such a command line so perhaps I can get what is needed off of the disk. Here is the thread that gave such a command...it is for a different Epson scanner though.  [http://ubuntuforums.org/showthread.php?t=825264&highlight=scanner+invalid+argument](http://ubuntuforums.org/showthread.php?t=825264&highlight=scanner+invalid+argument)

Second question: If I find a distro (such as SuSE) that might work better with my scanner....is it possible to repartition my hard drive without starting all over and losing what I have entered and customized in Ubuntu so far?  Also I suppose that if I attempted to reinstall Windows 2000, I would need to do it first and then reinstall Ubuntu. (Ugh)

Final question: I have a second hard drive which Ubuntu recognized when I installed it. I can't figure out how to access it. If I could....perhaps someone could tell me: can I install another distro on it in order to run my scanner and then perhaps I could find a program similar to “Syncback” that I could transfer files back and forth between the two disks.

Any help or suggestions would be greatly appreciated.

---

### Post by albinootje on 2009-01-19
> **Indyviews said:**
>  After downloading all the needed files and backends I could find for my Epson Perfection 3170 scanner
-- cut --
However....when trying to scan, I get the: Failed to start scanner- invalid augument.


Your scanner is not listed here :
[http://www.sane-project.org/sane-mfgs.html#Z-EPSON](http://www.sane-project.org/sane-mfgs.html#Z-EPSON)

Here's someone having the same scanner running on Fedora Linux :
[http://www.usenet-forums.com/linux-general/370432-solved-epson-perfection-3170-fedora-8-x86_64-a.html](http://www.usenet-forums.com/linux-general/370432-solved-epson-perfection-3170-fedora-8-x86_64-a.html)

[http://ubuntuforums.org/showthread.php?t=393882](http://ubuntuforums.org/showthread.php?t=393882)

Is your user in the group scanner ?
Check with these commands :
```

id
groups

```

The cdrom that came with your scanner is *only* for MS-Windows, and *perhaps* also for MacOSX, but it's unlikely that there's some "autorun" software for Linux on it.

One other option is to use MS-Windows as a guest VM inside VirtualBox in Ubuntu, and see whether your usb scanner is working with that, it worked for me at work with some HP scanner a few weeks ago.
For that you will need the VirtualBox version from the virtualbox website, and you need to make usb work, and install the Guest Additions.

---

### Post by albinootje on 2009-01-19
> **Indyviews said:**
> 
Second question: If I find a distro (such as SuSE) that might work better with my scanner....is it possible to repartition my hard drive without starting all over and losing what I have entered and customized in Ubuntu so far?  Also I suppose that if I attempted to reinstall Windows 2000, I would need to do it first and then reinstall Ubuntu. (Ugh)

If you make backups first, you can easily work with gparted to resize your partitions.
And remember, if you install MS-Windows after installing Linux, you will have to fix your boot-loader. 
(MS has a trademark on overwriting bootloaders without asking or without informing the user since more than 20 years)
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
> 
Final question: I have a second hard drive which Ubuntu recognized when I installed it. I can't figure out how to access it. If I could....perhaps someone could tell me: can I install another distro on it in order to run my scanner and then perhaps I could find a program similar to “Syncback” that I could transfer files back and forth between the two disks.

It should be no problem to install another Linux distribution on it.

---

### Post by Indyviews on 2009-01-19
Thanks albinootje...I will check into your suggestions.

---

