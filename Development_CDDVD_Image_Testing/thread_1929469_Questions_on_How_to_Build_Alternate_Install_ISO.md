---
title: "Questions on How to Build Alternate Install ISO"
date: 2012-02-22
forum: Development CD/DVD Image Testing
---

### Post by sephthir on 2012-02-22
As part of a project, I need to be able to rebuild the Ubuntu alternate install ISO due to some of the requirements of the packages that need to be installed on the system. I've found the common pages about how to add packages to the alternate install discs ([InstallCDCustomization]("https://help.ubuntu.com/community/InstallCDCustomization")), which I have managed to get to work, but it is becoming increasingly apparent that I may need to do more to the install image.

Because of this, what I really would like to find is documentation on how the alternate install image is created. Based on the research I've done, it appears to be based on the Ubuntu variant of the "debian-installer" package (instructions for building under Debian are  [here]("http://wiki.debian.org/DebianInstaller/Build"), and are roughly equivalent for Ubuntu after fetching the "debian-installer" source package), and... then I can't seem to find anything useful. I assume the process is similar to that of building a Debian install disc (instructions [here]("http://wiki.debian.org/DebianCustomCD")), but I'm not entirely sure where the packages are pulled from, etc.

If anyone has any knowledge on this subject, even vague pointers would be appreciated, as I seem to have run into a blank wall of a lack of information. Thanks in advance!

Sephthir

---

### Post by skellat on 2012-07-12
At this point I'd suggest looking at simple-cdd and considering the e-mail archive here: [http://lists.alioth.debian.org/pipermail/simple-cdd-devel/](http://lists.alioth.debian.org/pipermail/simple-cdd-devel/)

---

### Post by Cheesehead on 2012-07-12
Duplicating all that work to reconstruct the Ubuntu Alternate Image seems unusual.

Have you looked into a [preseed file]("https://help.ubuntu.com/8.04/installation-guide/hppa/preseed-using.html")? Adding that to an install media is much easier than reconfiguring (and updating) it. Preseed files are used in most specialty (like UbuntuStudio) and OEM installers. 

Another oft-overlooked tool is [AptUrl]("https://wiki.ubuntu.com/AptUrl"), a handy way of installing from a web page. Useful when a whole class or group needs to install packages but you don't have admin access to all the systems.

My understanding (from a couple years ago) is that the Alternate CD consists of three elements:
1) The isolinux bootloader, linux kernel, and menus (compiled into initrd)
2) The debian installer with Ubuntu customization file
3) The packages, most of which are right out of the 'main' repository

---

### Post by johnmatthews920 on 2012-09-05
I completely agree with the thoughts.

---

