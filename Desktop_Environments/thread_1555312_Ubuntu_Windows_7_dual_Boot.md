---
title: "Ubuntu Windows 7 dual Boot"
date: 2010-08-17
forum: Desktop Environments
---

### Post by yanceypd on 2010-08-17
I have a new desktop and it runs Win7.  On my old pc ran Vista and Ubuntu 10.04 no problem in dual boot config.  Looks like Win 7 does a registry check because after a good boot up in Ubuntu and Win 7 does a check then boots ok but when I try to boot back into Ubuntu it say something about a target not found.  Any Ideas?  Also may haveto repost later as old printer not compatable with Win 7.

---

### Post by oldfred on 2010-08-17
I do not have win7 but saved these links:

Writes to MBR-----------------------------------
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR)
[http://www.supergrubdisk.org/wiki/WindowsErasesGrub](http://www.supergrubdisk.org/wiki/WindowsErasesGrub)
In Windows 7, I had to remove Windows 7 DataSafe.
HP ProtectTools, Dell Recovery, and a few others write into MBR meierfra.
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941)
[https://bugs.edge.launchpad.net/ubuntu/+source/grub2/+bug/441941?comments=all](https://bugs.edge.launchpad.net/ubuntu/+source/grub2/+bug/441941?comments=all)
Dell Media direct or Uninstall Dell DataSafe issues with MBR
[http://ubuntuforums.org/showpost.php?p=9330849&postcount=9](http://ubuntuforums.org/showpost.php?p=9330849&postcount=9)

---

### Post by The Fold on 2010-08-18
I had to set up an Ubuntu/Windows 7 dual boot not that long ago. It seems Windows 7 messes around with the MBR and I had to get a beta version of the program EasyBCD to be able to set things up correctly.

I ended up with the Windows loader coming up, selecting Ubuntu, then getting GRUB. A mild annoyance, but it worked.

[http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1) - EasyBCD

---

### Post by jamessimo on 2010-08-18
I currently run a win7 64bit and Ubuntu 10.04 32bit dual boot and I have had no problems to report of sorry.

---

### Post by jimbop99 on 2010-08-18
> **jamessimo said:**
> I currently run a win7 64bit and Ubuntu 10.04 32bit dual boot and I have had no problems to report of sorry.

Same here. Except Ubuntu 64.

---

### Post by wilee-nilee on 2010-08-18
> **oldfred said:**
> I do not have win7 but saved these links:

Writes to MBR-----------------------------------
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR)
[http://www.supergrubdisk.org/wiki/WindowsErasesGrub](http://www.supergrubdisk.org/wiki/WindowsErasesGrub)
In Windows 7, I had to remove Windows 7 DataSafe.
HP ProtectTools, Dell Recovery, and a few others write into MBR meierfra.
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941)
[https://bugs.edge.launchpad.net/ubuntu/+source/grub2/+bug/441941?comments=all](https://bugs.edge.launchpad.net/ubuntu/+source/grub2/+bug/441941?comments=all)
Dell Media direct or Uninstall Dell DataSafe issues with MBR
[http://ubuntuforums.org/showpost.php?p=9330849&postcount=9](http://ubuntuforums.org/showpost.php?p=9330849&postcount=9)

+1 this is the most likely candidate, I wasn't sure as this computer had vista first, with a running system dualbooted.

---

### Post by yanceypd on 2010-08-19
Thanks for the replies and ideas.  Kinda miss my Ubuntu it's so versatile.  This win7 is fair though.  It's only locked up once in the first week.  Thank again.

---

