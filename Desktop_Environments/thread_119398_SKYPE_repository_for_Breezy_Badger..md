---
title: "SKYPE repository for Breezy Badger."
date: 2006-01-19
forum: Desktop Environments
---

### Post by chris_andrew on 2006-01-19
Hi, all.

Just installed Breezy, and wondered if anybody knows of a good repository to add to my /etc/apt/sources.list  for the VoIP app Skype.

I tried apt-get.org, but it's search engine was down.

Many thanks,

Chris.

---

### Post by dalee on 2006-01-19
Hi,

There isn't a repository for Skype. You need to get it from Skype directly. Just don't use the Debian/Ubantu .deb. It won't work on Ubuntu. Instead, download the Fedora Core3 RPM. Then use Alien to turn it into a .deb.

If you don't have alien installed, you can get it from the univervse I believe.

dalee1002000

---

### Post by darth_vector on 2006-01-19
make sure you install libqt3c102-mt before you install the deb package or it will not work.

the following guide is quite helpfull: [http://www.ubuntuguide.org/#skype](http://www.ubuntuguide.org/#skype)

---

### Post by chris_andrew on 2006-01-19
Thanks, guys.

I found this:

deb [http://ftp.debian-unofficial.org/debian](http://ftp.debian-unofficial.org/debian) sarge main contrib non-free restricted

on apt.get.org, so will give it a go.

Cheers,

Chris.

PS:  It works :-)

---

### Post by flosofl on 2006-01-19
Do a search in this forum for "automatix".  It automates installs for a bunch of packages and skype is one of them.

---

### Post by ametade on 2006-01-19
Checkout the following site. They have repositories with skype for ubuntu.

[http://wiki.ubuntu-fr.org/doc/plf](http://wiki.ubuntu-fr.org/doc/plf)

---

### Post by ronmarley1 on 2006-01-19
[QUOTE=flosofl]Do a search in this forum for "automatix".  It automates installs for a bunch of packages and skype is one of them.[/QUOTE]

Here's the link to Automatix.
[http://www.ubuntuforums.org/showthread.php?t=66563&highlight=automatix](http://www.ubuntuforums.org/showthread.php?t=66563&highlight=automatix)

---

### Post by ffarcy@tntmax.com on 2006-01-24
We publish on our site TNTmax.com a step by steps howto Install SKYPE Debian Package on a Ubuntu distribution of Linux. The official package from SKYPE need some manual updating and you can follow the steps below.

[http://tntmax.com/content/view/176/60/](http://tntmax.com/content/view/176/60/)

---

