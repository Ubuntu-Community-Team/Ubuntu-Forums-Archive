---
title: "How do I install on second drive?"
date: 2011-09-24
forum: Desktop Environments
---

### Post by xSyNisTeRx on 2011-09-24
Hello, 
Currently I'm running Ubuntu 11.04 on a multi-boot through the windows installer. I have 2 separate physical HDDs. My objective is to keep the multiboot option, but to install Ubuntu onto its own physical drive capable of using all space. Now when I installed initially through the windows installer I selected the second drive, but it still limited my install size to 30gb and its still running as a program I can delete in windows. I want a FULL install on my second drive with the multiboot feature. Is this possible, if so, does anyone know how it's done? 
THANKS!

---

### Post by ajgreeny on 2011-09-24
Add your second drive to the machine, run the live CD/USB of ubuntu and when you get to the disk preparation, or partitioning stage choose "Something Else".  I know, it's a stupid way to describe it, but it means you can choose the disk or partitions that are already on the machine to install to.

In your case it will probably be sdb, as sda will be your Windows disk.  There is a point where you can choose where to put the bootloader files, ie grub, but I can not remember where exactly that is.  Just keep a wary eye open for it, or look for an **Advanced** button and see if it is there.

If you are keeping the two OSs separate on the disks I suggest you put grub on /dev/sdb and have the second disk (sdb) as your first boot device in the computer BIOS.  Note that there must be no partition number, such as /dev/sdb1, put grub on the root of the disk /dev/sdb.  That will leave the Windows bootloader untouched on the root of sda, so if you have a problem with booting ubuntu you can simply choose to boot to sda as first boot device.

---

### Post by oldfred on 2011-09-24
+1 on ajgreeny suggestions.

An example with screen shots:
Installing Ubuntu in Hard Disk Two (or more) internal or external 
Maverick screens shown, other versions have slight difference in screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html]("http://members.iinet.net.au/%7Eherman546/p24.html")
p24/041.png Shows combo box to select where to install the grub2 boot loader.
Where Do You Want To Install GNU/GRUB?
[http://members.iinet.net.au/~herman546/p24/041.png]("http://members.iinet.net.au/%7Eherman546/p24/041.png")

Install with separate /home from aysiu
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

Even though installing to a separate drive is is best to have a Windows repair CD/USB and good backups
Make your own Windows recoveryCD/repair:
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

---

