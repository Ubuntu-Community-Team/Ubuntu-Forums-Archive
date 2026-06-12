---
title: "Why ubuntu installer don't create user on my own distribution?"
date: 2016-04-16
forum: Development CD/DVD Image Testing
---

### Post by hardrp220 on 2016-04-16
Hello :)

I added new user (user1) to my own distribution. In live mode this user works normally but when I install system and fill data to new user (user2), new user (user2) don't create. I think in /usr/share/ubiquity I must change adduser line but how ?


User(user1) I add to visudo but it not help.

---

### Post by ian-weisser on 2016-04-16
How confusing. Please add a bit more detail.

The live environment is for testing before agreeing to install.
The installer ignores the presence or absence of the live environment entirely, any changes made to the live environment will not be installed to disk.

---

### Post by hardrp220 on 2016-04-18
how to set up user live? I did it by command adduser maybe this is the problem?

---

### Post by lisati on 2016-04-18
> **hardrp220 said:**
> how to set up user live?
By "live", do you mean you are running Ubuntu from CD/DVD/USB?

> I did it by command adduser maybe this is the problem?
"Adduser" is a common and perfectly valid way of adding a new user once you have actually installed Ubuntu on your system.

---

### Post by hardrp220 on 2016-04-18
> **lisati said:**
> By "live", do you mean you are running Ubuntu from CD/DVD/USB?
Yes
> **lisati said:**
> 
"Adduser" is a common and perfectly valid way of adding a new user once you have actually installed Ubuntu on your system.

that is, I mean that in a bad way I added the user live? And how to add so that the installation has been removed?

---

### Post by lisati on 2016-04-18
As someone else has said, the "live" environment is good for testing an [operating system]("https://en.wikipedia.org/wiki/Operating_system")[*] before you install it, so you can get an idea of what's going to work, and what might not work so well for you. If you install Ubuntu on your computer, add users, and then remove Ubuntu, then any users you have added to the installed copy will be removed as well.

[*]An operating system is what manages your computer, lets you run programs, lets you access files, and a whole lot of other things. Ubuntu is an example of an operating system. Windows is another, MAC OSX is another.

---

### Post by hardrp220 on 2016-04-18
We do not understand probably :)

I know how all this works only when the ubuntu firing in test mode with USB (live mode ) 
[IMG]http://www.howtogeek.com/wp-content/uploads/2010/10/539x209ximage173.png.pagespeed.gp+jp+jw+pj+js+rj+rp+rw+ri+cp+md.ic.14sF8f2pTa.png[/IMG]
we can install distributions.

 During the installation complement field users and run the system with the disk already installed on the user is added.
[IMG]http://news.softpedia.com/images/extra/LINUX/large/ubuntu1010installer-large_005.jpg[/IMG]


My distribution of fires normally with USB and can be installed normally. The only problem is that the user is not added when you will fill these fields. After installation of the system is you added earlier by:
```

chroot mydistro/
adduser liveuser
```

*pictures from google so a little different

---

### Post by ian-weisser on 2016-04-18
The way you seem to be doing it, you must add user2 AFTER the installation is complete and you have rebooted into the new system.
All changes you make before the installation is complete are lost and ignored.

There are better ways to customize an install, if that's what you need.

---

### Post by hardrp220 on 2016-04-18
> **ian-weisser said:**
> The way you seem to be doing it, you must add user2 AFTER the installation is complete and you have rebooted into the new system.
All changes you make before the installation is complete are lost and ignored.

There are better ways to customize an install, if that's what you need.
so in this manner it is planning to do just what way?

---

### Post by sudodus on 2016-04-18
The screenshots in post #7 look very old. Please tell us which version of Ubuntu you are using. You should use a current version, a version that is supported with updates/upgrades (security updates, bug fixes, improved features), Ubuntu 12.04 LTS, 14.04 LTS, 15.10. Soon there will be 16.04 LTS. The digits represent year and month, so now it is **April** 20**16**, which makes the version number 16.04. We recommend LTS versions (long time support).

-o-

There is a way to keep the live system, to have a ***persistent live system***, when the modifications you make are stored in a casper-rw file or partition. But still, those modifications will ***not*** be ported to an installed system.

Most people run ***installed systems*** with Ubuntu and the Ubuntu family flavours, Kubuntu, Lubuntu ... Xubuntu. And you set up the installed system after installing it (and rebooting without the install media, DVD or USB drive).

See this link and links from it: [Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it](http://ubuntuforums.org/showthread.php?t=2230389)

[hr][/hr]
***Edit:*** When you run the live session, you can install, either from the boot menu 'Install Ubuntu', or from the desktop icon in the live session. This way you are typically installing Ubuntu into an internal drive, either as the only operating system or alongside Windows.

Remember that installing operating systems is risky, so ***backup*** all important files and create recovery disks for Windows ***before*** starting the installation.

---

