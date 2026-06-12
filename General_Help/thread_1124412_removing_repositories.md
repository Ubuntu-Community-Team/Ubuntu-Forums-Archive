---
title: "removing repositories"
date: 2009-04-13
forum: General Help
---

### Post by anarchoprole on 2009-04-13
Hi all,

I have only had umbuntu for two days so really am a newbies here. I tried to add a repository through adpet and thought everything had gone ok but now when i try to start adept up i get the following error message:

E: Type ‘[http://www.medibuntu.org/sources.list.d/intrepid.list’](http://www.medibuntu.org/sources.list.d/intrepid.list’) is not known online 55 in source list /etc/apt/sources.list
E: The list of sources could not be read.

I was running KDE so tried it again through GNOME but i still get the same error message

I have tried using the terminal and typed:

sudo apt-get remove [http://www.medibuntu.org/sources.list.d.inrepid.list](http://www.medibuntu.org/sources.list.d.inrepid.list)

but get the same error

I can't install or remove any software, please help!!

Ferdi

---

### Post by memories on 2009-04-13
check /etc/apt/sources.list (text file)

Make sure to back it up by copying it somewhere before editing it.. just in case.

Here's mine for Feisty (I upgraded Hardy) but DO NOT use this. It's only an example. Your system might be different.

> 
# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release amd64]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid restricted main
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid restricted

deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid universe


deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid multiverse


deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security restricted main
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) intrepid-backports main restricted universe multiverse



Edit sources.list and then run 
sudo apt-get update

---

### Post by anarchoprole on 2009-04-14
thanx for that :-)

---

