---
title: "Dual Boot Problem Between Linux and Windows 7"
date: 2010-10-14
forum: Dell Ubuntu Support (CLOSED)
---

### Post by xenon401 on 2010-10-14
Hello! I have been on these forums a while back ago and I believe I have previously discussed this issue but cannot seem to find a fix to it...

First things first. I am runing a copy of Ubuntu 10.04 Lucid Lynx and I dual boot with Windows 7 x64 version.  My computer is a Dell 1555 srs premium sound with a 4GB RAM. If you need to know more specific information such as processors, memory, communications, etc., please, leave a comment and I will give it! =)

Moving on... When I boot up my computer, "Dell" loads like usual. Then, the GRUB loader appears and it loads my backups, Windows 7 boots, and my previous Linux kernels. I almost always select the newest kernel version of Linux.... Then I have the option to log into which OS. I can go into WIndows 7 then. So once Windows 7 boot is complete, I can sign in, do all my stuff I want to on Windows 7, then shut down. But here comes the trouble. Once I boot up my computer again, Dell loads but the GRUB won't. I do not recall the error message that pops up but all I can do is enter the BIOS or put in my Live CD .iso of Linux, etc., which is how I get back into Ubuntu and then I have to reinstall everything and all my linux data gets eraseed..

Basically, I want to be able to get back into Windows 7 without having to reinstall everything the next boot up..

Any additional information, please, comment!

Thanks so much in advance!

---

### Post by rMatey on 2010-10-14
Here's how to remove Linux, which might be something you want to do..
[http://www.sevenforums.com/installation-setup/62209-remove-grub-restore-windows-7-a.html]("http://www.sevenforums.com/installation-setup/62209-remove-grub-restore-windows-7-a.html")

  You can use WUBI to run a linux under Windows just like any other program, and can even uninstall it with the built-in Windows Uninstaller Program.  Most people don't see a performance hit.
  As for your startup you can use UbuntuTweak to remove those pesky old kernels.

---

### Post by bcbc on 2010-10-14
Some windows software write to what is supposed to be free space in the MBR to track things they don't want you finding. e.g. the date you started trialling some software. Or suchlike.
This screws up the grub2 bootloader which is using more space than its predecessor grub-legacy. 

First, you should only have to reinstall the grub bootloader, not reinstall ubuntu.
Second, you should be able to use easyBCD to boot ubuntu. Don't ask me how. 
Third, find and remove the software causing the problem.
Fourth, yes wubi will solve it too.

There is also something you can do to help grub2 get around this problem in the future. [http://www.chiark.greenend.org.uk/ucgi/~cjwatson/blosxom/debian/2010-08-28-windows-applications-making-grub2-unbootable.html](http://www.chiark.greenend.org.uk/ucgi/~cjwatson/blosxom/debian/2010-08-28-windows-applications-making-grub2-unbootable.html)

---

### Post by oldfred on 2010-10-14
As bcbc suggests you should help solve the problem by saving the boot sector.

Some windows 7 software is well know to cause issues:

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR)
[http://www.supergrubdisk.org/wiki/WindowsErasesGrub](http://www.supergrubdisk.org/wiki/WindowsErasesGrub)
[http://linux.slashdot.org/story/10/08/28/2112208/Some-Windows-Apps-Make-GRUB-2-Unbootable](http://linux.slashdot.org/story/10/08/28/2112208/Some-Windows-Apps-Make-GRUB-2-Unbootable)
In Windows 7, I had to remove Windows 7 DataSafe.
HP ProtectTools, Dell Recovery, and a few others write into MBR meierfra.
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941)
[https://bugs.edge.launchpad.net/ubuntu/+source/grub2/+bug/441941?comments=all](https://bugs.edge.launchpad.net/ubuntu/+source/grub2/+bug/441941?comments=all)
Dell Media direct or Uninstall Dell DataSafe issues with MBR
[http://ubuntuforums.org/showpost.php?p=9330849&postcount=9](http://ubuntuforums.org/showpost.php?p=9330849&postcount=9)

To reinstall grub2:
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by ktoepke on 2010-11-06
I had the same problem for a while...after I uninstalled all of the Dell utilities in Win7, it stopped happening.

---

