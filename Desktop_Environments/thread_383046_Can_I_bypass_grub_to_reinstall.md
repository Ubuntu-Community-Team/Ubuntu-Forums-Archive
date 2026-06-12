---
title: "Can I bypass grub to reinstall"
date: 2007-03-12
forum: Desktop Environments
---

### Post by GolfGeek on 2007-03-12
Hi all
I have a dual boot system and the second drive is running Dapper and I've been using GRUB to dual boot. I am now getting signs that there is a problem with the secondf drive. I would like to replace it with another but worry about GRUB not letting me access the windows drive for my work. I haven't done it yet, but what happens if I just yank the seconf drive. This is the third time I have had issues with the dependency on GRUB if there are errors on the Ubuntu drive. Is there a good alternative to GRUB that uses a different technique.

---

### Post by Herman on 2007-03-13
Hello GolfGeek
The [GAG Boot Manager]("http://gag.sourceforge.net/") is 'operating system independant'. GAG installs to the MBR and first track of the hard disk, which is normally empty and not formatted with any filesystem, and reserved by convention for this type of use. Or you can run GAG from a floppy disk very well, or even a CD in an emergency.

[                                GAG Boot Manager Page]("http://users.bigpond.net.au/hermanzone/p12.htm")

Or you could keep on using Grub and also use [Super Grub Disk]("http://supergrub.forjamari.linex.org/") 
 SuperGurbDisk isn't meant to be installed to hard disk. You can make an SGD floppy disk, CD or USBdisk to do almost anything you want easily, like re-install the Windows boot loader's IPL code to MBR, or re-install Grub again, and boot your operating systems for you when you have other booting problems.

Regards, Herman :)

---

### Post by GolfGeek on 2007-03-13
Herman
Thanks a ton.. I've had problems with GRUB on 3 different machines and if it has any type of problem, it leaves me hanging. I'll give this a try.

---

### Post by Herman on 2007-03-13
GolfGeek, 
Okay, GAG Boot Manager is quite a popular 'graphical' boot manager, it's a lot easier to configure because the configuring is all 'point and click'. 

GAG works by booting the operating system partition's first sector or 'boot sector', so GAG is always able to boot Windows for you because Windows has the boot-loader's IPL in the first sector on the partition by default.

However, I want to remind you that Ubuntu and most other Linuxes need you to  install Grub or Lilo to the operating system's  first sector or else GAG can't boot Linux. You just have to select that option when you are installing or you can do it any time later on from a terminal. There are links on that web page I already gave you that go into details about all that. Or you an do that with your [Super Grub Disk]("http://supergrub.forjamari.linex.org/") if you don't have time to learn the terminal commands right now.

Best of all GAG Boot Manager is 'open source'. That means the source code is available for other programmers to examine and see that it is okay for everyone and doesn't contain any malicious code. If it isn't open source you can't trust it.
I'm talking about software in general now.

Enjoy your dual booting,
Regards, Herman :)

---

### Post by salijackt on 2008-07-15
I have the same problem, but my second hard drive has already given out (the hard drive with Ubuntu on it).  Rebooting is also not an option for me, but I cannot start the computer because GRUB comes up with an error 21 (my second hard drive is not in the computer at all).  Please help me!

---

### Post by Herman on 2008-07-15
:) Hello salijackt,
You should use another computer to download yourself a copy of [Super Grub Disk]("http://www.supergrubdisk.org/").
You can get the .iso file of Super Grub Disk and burn it to a CD or DVD, (it's free and it's only a very small download, it doesn't even take up very much room on a CD).
There are floppy disk versions of Super Grub Disk or USB versions too in case you don't have a working CD Drive.
Super Grub Disk can chainload your Windows for you so it will boot until you get your new hard disk and install a new Ubuntu. Re-installing Ubuntu will fix GRUB automatically.
If it will be a long time before you'll be able to re-install Ubuntu, you can use Super Grub Disk to make your MBR boot Windows again for the meantime, as it may be more convenient for you.
Regards, Herman :)

---

### Post by Herman on 2008-07-15
If you happen to have a Windows XP 'Installation CD', you can boot it to a [Windows XP Recovery Console]("http://www.kellys-korner-xp.com/win_xp_rec.htm") and run the FIXMBR command, that might be quicker if you happen to have one of those CDs handy. Unfortunately not very many computer manufacturers include that kind of CD with new computers anymore these days.

Or, you can use GAG Boot Manager instead if you want, GAG Boot Manager is 'operating system independant', so you can uninstall operating systems or remove hard disks without losing your ability to boot.

---

