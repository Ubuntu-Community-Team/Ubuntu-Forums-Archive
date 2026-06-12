---
title: "Debian GNU/Linux 4.0r1 Released"
date: 2007-08-17
forum: Debian
---

### Post by Dark Star on 2007-08-17
[IMG]http://www.imgx.org/files/3409_5tsz0/324px-Debian-logo-notext.svg.png[/IMG]Debian GNU/Linux is a free operating system developed by more than a thousand volunteers from all over the world who collaborate via the Internet. Debian's dedication to Free Software, its non-profit nature, and its open development model make it unique among GNU/Linux distributions.
 
The Debian project's key strengths are its volunteer base, its dedication to the Debian Social Contract, and its commitment to provide the best operating system possible.
 
The Debian project is proud to announce the immediate availability of an updated version of their very popular distribution, Debian Etch 4.0r1. This release contains mainly security updates and some corrections to serious problems found in the first release of the Debian 4.0 distribution.
 
 [CENTER][[IMG]http://www.imgx.org/pthumbs/large/1475/Debian-GNU-Linux-4-0r1-Released-2.png[/IMG]]("http://www.imgx.org/public/view/full/1475")[/CENTER]

 **Highlights of this release include:**[LIST]
[*] kernels used in the installer have been updated to ABI 2.6.18-5; as a result, some "small" images (for example netboot and floppy images) included in the original Etch release will no longer work (but the new images included in the point release will work, as well as the full CD/DVD images from both the original release as well as from this point release)
[*] updated mirror list
[*] support added for certain USB CD drives that were not being detected
[*] incorrect setup of gksu fixed when the user chooses to install with the root account disabled; this prevented the execution of administrative tasks in GNOME
[*] important translation fixes in partman for Catalan and Romanian[/LIST]
While the ISO images will be available within the next week, you can update your current Debian installation via ftp mirrors. Usually, if you want to upgrade online, just point the aptitude package tool to one of Debian's HTTP or FTP mirrors. FTP Mirrors : [Getting Debian from the Internet]("http://www.debian.org/distrib/ftplist")
 
 **Other bugfixes include:**[LIST]
[*] Added debian volatile keyring
[*] Added support for lenny.
[*] Fix kde default wallpaper appearance between kdm to ksplash switch.
[*] Fix possible denial of service
[*] Fix CPU hog on 64 bits machines, dependencies of nscd, wrong assertion and unaligned memory access
[*] Added missing esp module to scsi modules list so it gets installed in the initroduction.[/LIST]
Source : [Official Announcement ]("http://times.debian.net/1161-etch-r1")
Home Page: [Debian -- The Universal Operating System]("http://www.debian.org/")

---

### Post by Bachstelze on 2007-08-17
And for those who already have Etch installed, you have nothing particular to do to apply those fixes, just upgrade your packages as usual :)

---

### Post by Pancetilla on 2007-08-18
Updated yesterday!

If anyone's having trouble updating the amd64 version...I run into a problem involving libc6 and nspluginwrapper (ouch!); libc6 would not upgrade, because some nspluginwrapper bug.

Just uninstall nspluginwrapper, apt-get update && apt-get upgrade, and then reinstall the nspluginwrapper deb. You'll have flash again.

---

