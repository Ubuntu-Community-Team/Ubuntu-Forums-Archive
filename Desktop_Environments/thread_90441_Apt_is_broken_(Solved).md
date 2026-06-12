---
title: "Apt is broken (Solved)"
date: 2005-11-15
forum: Desktop Environments
---

### Post by kris kincaid on 2005-11-15
Hello,

I tried searching on this forum and Google without much luck. If there is another thread on this, please point me that way. :)

Anyway, I cannot do an apt-get at all. I tried to do an apt-get update the other day, and this is what I get:

> 
kris@ubuntu:~$ sudo apt-get update
Password:
E: The method driver /usr/lib/apt/methods/cdrom could not be found.
E: The method driver /usr/lib/apt/methods/http could not be found.
E: The method driver /usr/lib/apt/methods/http could not be found.
E: The method driver /usr/lib/apt/methods/http could not be found.
kris@ubuntu:~$


As far as I know, I have not changed a thing. I haven't added any sources or deleted any. I thought maybe it broke during an upgrade, but it appears I am the only one having this problem. Any ideas? I figured somebody else must of had this happen before.

Thank you. :)

---

### Post by mikwig on 2005-11-15
[QUOTE=kris kincaid]Hello,

I tried searching on this forum and Google without much luck. If there is another thread on this, please point me that way. :)

Anyway, I cannot do an apt-get at all. I tried to do an apt-get update the other day, and this is what I get:



As far as I know, I have not changed a thing. I haven't added any sources or deleted any. I thought maybe it broke during an upgrade, but it appears I am the only one having this problem. Any ideas? I figured somebody else must of had this happen before.

Thank you. :)[/QUOTE]

Could you show us your /etc/apt/sources.list  anyway
cause you have me stumped

---

### Post by manicka on 2005-11-15
Does synaptic or aptitude work?

---

### Post by aysiu on 2005-11-15
According to Google, [it's not looking good for you](http://www.google.com/search?hl=en&q=E%3A+The+method+driver+%2Fusr%2Flib%2Fapt%2Fmethods%2Fcdrom+could+not+be+found.&btnG=Google+Search).

---

### Post by manicka on 2005-11-15
A search of some links on google indicates that it may be a problem with your sources.list. Could you post the contents.

---

### Post by manicka on 2005-11-15
another thought....

Find the apt package on the install cd or download it from packages.ubuntu.com and reinstall it with dpkg

---

### Post by kris kincaid on 2005-11-15
Synaptic complains of basically the same thing except this is thrown in:


> Could not download all repository indexes

The repository might be no longer available or could not be contacted because 
of network problems. If available an older version of the failed index will be 
used. Otherwise the repository will be ignored. Check your network connection 
and the correct writing of the repository address in the preferences.

My network appears to be fine and I have not made any changes to my router or any other settings. I have a quirky ISP, so maybe they are blocking something although I can't imagine what they could block that would also screw with Apt.

Anyway, here is my sources.list:

> #deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Preview i386 (20050908)]/ breezy main restricted

#deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
 deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
 deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) breezy multiverse universe main restricted
deb [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free
#deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) unstable main
deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/
deb-src [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) source/ 

Again, thanks. :)

---

### Post by kris kincaid on 2005-11-15
I love simple fixes, I just went to the CD and reinstalled apt and it works now!

This is by far the most useful forum I have ever seen. THANK YOU TO ALL! :p 


[QUOTE=manicka]another thought....

Find the apt package on the install cd or download it from packages.ubuntu.com and reinstall it with dpkg[/QUOTE]

---

### Post by uberlinux on 2005-11-15
This is probably a silly idea, but why not # out everything but the cdrom source, then apt-get apt all over again.
also, does dpkg -reconfigure apt do anything?

---

