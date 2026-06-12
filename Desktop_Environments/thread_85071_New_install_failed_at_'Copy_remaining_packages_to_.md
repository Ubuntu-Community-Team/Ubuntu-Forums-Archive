---
title: "New install failed at 'Copy remaining packages to hard disk'"
date: 2005-11-01
forum: Desktop Environments
---

### Post by geuis on 2005-11-01
Hey, I'm brand new to all this.

I burned the lastest kubuntu universal x86 iso the other night and I've spent the hour trying to install it.

It keeps failing at "Copy remaining packages to hard disk." I've repartioned the drive a couple times to see if that was the problem, no help.

As I've been looking through the forums some people have recommended using md5sum to verify the cd I burned, but I've not been able to find more info on exactly how to do that.

The error also is telling me to check /var/log/syslog or see virtual console 4 for details. I'm not sure where to find this information, since it cant write it to the cd.

I'm installing this onto a Dell 5100c with a 160gb HDD. I've wiped out windows on it, and set it all as 1 big partion. (I've since rebooted and let the installer run in its default mode so it should have created its own swap disk).


--update
I found the Check CD-ROM Integrity option. It says the language-pack-es-base_20051011_all.deb file failed MD5 checksum verification.

How can I verify the existing ISO file I have before I burn it again?
Thanks for any help! I'm looking forward to trying this distro out.

---

### Post by Princey on 2005-11-01
I'm going to take a long shot at this assuming you're using a Windows machine to download and burn your images. First, I'd suggest you don't use wellget (It's a great download manager and I love it, but just not the best for your job at the moment). I'd suggest you use BitTorrent to download the image and the checksum. Instead of listing the various ways as I'm not sure what cd burning software you have, you can find free file verifiers here [http://www.winappslist.com/utilities/file_verifiers.htm]("http://www.winappslist.com/utilities/file_verifiers.htm"). Some of the programmes are shareware but if you browse down that page, you'll find freeware versions that do a great job. Whether you want one with a GUI or using a commandline interface, it's all up to you. Good luck.

---

### Post by beefsprocket on 2005-11-01
I'm a fan of md5summer since it is free and opensource, and has seems to have a well configured GUI. 

[http://sourceforge.net/projects/md5summer](http://sourceforge.net/projects/md5summer)

---

