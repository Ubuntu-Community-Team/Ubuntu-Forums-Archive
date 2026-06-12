---
title: "What version of Grub is Grub2"
date: 2015-07-10
forum: Fedora/RedHat and derivatives
---

### Post by tech291083 on 2015-07-10
Hi Friends,


What version of Grub is Grub2? Is it any version above and including 1.98 or 2.00? Is Grub2 version similar for all other Linux distros, particularly the ones listed below, which I often download to learn a few things about them? 


Thanks.


Ubuntu
Fedora
OpenSuse
Debian
CentOS Live CD
Gentoo
Sabayon
Arch
Chakra
Puppy Linux
Slackware
DSL
Knoppix

---

### Post by Skaperen on 2015-07-10
when the number is tied to the name like that it usually means a major version and the previous major version is depricated.   in the case of grub this is the case and "Grub2" has more than one release version.

---

### Post by sinisa1hr-z on 2015-07-10
grub is legacy and older version, now in use with all distribution,or version which can work with all distribution,even if is not shipped with that boot-loader, is so called grub2 ,so up to grub version 1.97 *generally with version number less then 2,is legacy and old ,depreciated version... newer version,modern and which can work with all kind of booting and all kind of partitioning is so called grub2, as far i know, now is  latest version in ubuntu repositories is 2.02~beta2-22ubuntu1.1...look for version number ,as now even grub-common and grub2-common are on 2.02 beta 22ubuntu1.1, and check and be sure when you are in grub menu,that  you can see version number..or to check in repositories of installed packages..so simple answer on your question is: 

grub2 is newer version of grub! ;)

 which will and are receiving updates and upgrades...and have active development, 
efi and uefi boot is not problem for grub2 !booting from msdos and gpt partiticong shema also..but also classic boot,without uefi ,with just msdos particionig shema.. that is what i know and see. And there is comprehensive manual shipped with explaining all...as have much more what grub2 can.(but what i still not use,and can not comment)

about distribution you mentioned, well some distro builder can choose to use other boot-loader ,and that choice sometimes is not grub2 at all. But you can configure grub2 to boot that ,too..
example: grub2 is sure is not shipped with windows ,but grub2 booting windows ,too..(in dual boot)
also ubuntu or other distro you can boot with many diff. boot-loaders ,...that is freedom of choice! like with all other things in open source and linux ecosystem. Just you will need to configure it(whatever capable boot-loader) to boot what you want by yourself..basically just to tell bootloader where is something bootable and how you want to handle it. ... well that is how nintendo can boot linux(full support), playstation3,some people,and some factories make some PDA,some smartphones,etc..well then we came to other topic,drivers...

---

### Post by QDR06VV9 on 2015-07-14
This is Trusty
```
 apt-cache policy Grub2
grub2:
  Installed: 2.02~beta2-9ubuntu1.3
  Candidate: 2.02~beta2-9ubuntu1.3
  Version table:
 *** 2.02~beta2-9ubuntu1.3 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/universe amd64 Packages
        100 /var/lib/dpkg/status
     2.02~beta2-9 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty/universe amd64 Packages

```
It is little more involved on fedora
```
rpm --queryformat="%{NAME}-%{VERSION}-%{RELEASE}.%{ARCH}: %{INSTALLTIME:date}\n" -qa
```
Hope that is what you meant.
Regards

---

### Post by tech291083 on 2015-07-17
> **sinisa1hr-z said:**
> 

grub is legacy and older version, now in use with all distribution,or version which can work with all distribution,even if is not shipped with that boot-loader, is so called grub2 ,so up to grub version 1.97 *generally with version number less then 2,is legacy and old ,depreciated version... newer version,modern and which can work with all kind of booting and all kind of partitioning is so called grub2, as far i know, now is  latest version in ubuntu repositories is 2.02~beta2-22ubuntu1.1...look for version number ,as now even grub-common and grub2-common are on 2.02 beta 22ubuntu1.1, and check and be sure when you are in grub menu,that  you can see version number..or to check in repositories of installed packages..so simple answer on your question is: 

grub2 is newer version of grub! ;)


Thanks, but I am a little confused here, particularly by the sheer no of times you have used a comma (,) in such a long, never ending one-line explanation.

What I understand is,

Any Grub version upto and including 1.97 is legacy Grub and any version above and including 1.98 is Grub2, am I right? Thanks.

---

### Post by coffeecat on 2015-07-18
> **tech291083 said:**
> Any Grub version upto and including 1.97 is legacy Grub and any version above and including 1.98 is Grub2, am I right? Thanks.

No.

Legacy grub never reached a version above 0.97. 

Anything above 1 is grub 2. From what I can remember, grub 2 started out as 1.97 because it was still considered beta. The first instance of grub 2 - actually 1.97 - with Ubuntu came with Ubuntu 9.10, Karmic Koala. Again, as far as I remember, grub 1.99 was the grub 2 release candidate. We're now comfortably above 2 with the grub version in the latest release of Ubuntu.

---

### Post by tech291083 on 2015-08-09
> **coffeecat said:**
> No.

Legacy grub never reached a version above 0.97. 

Anything above 1 is grub 2. From what I can remember, grub 2 started out as 1.97 because it was still considered beta. The first instance of grub 2 - actually 1.97 - 



Great clarification, thanks a lot.

---

