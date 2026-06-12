---
title: "Can't upgrade to KDE 3.5.2"
date: 2006-05-17
forum: Desktop Environments
---

### Post by ModusOperandi on 2006-05-17
This is a problem I just can't explain. I have added in the repository, but when i go to do apt-get dist-upgrade, it says that 68 packages will be held back (practically all KDE applications/components) and that 3 packages will be removed, including ksysguard and Kubuntu-desktop. Attempting to use Adept to upgrade one of the 68 packages being held back results in the action from keep to BREAK (upgrade) with Commit failing because packages will be broken.

Here's the kicker: This is a fresh install from a disc that cleanly upgraded to 3.5.1. I have tried going to 3.5 and to 3.5.2.

Thanks in advance. I was looking forward to using an ACID2 compliant browser, but this is definitely a setback.

---

### Post by zhoux on 2006-05-17
[QUOTE=ModusOperandi]This is a problem I just can't explain. I have added in the repository, but when i go to do apt-get dist-upgrade, it says that 68 packages will be held back (practically all KDE applications/components) and that 3 packages will be removed, including ksysguard and Kubuntu-desktop. Attempting to use Adept to upgrade one of the 68 packages being held back results in the action from keep to BREAK (upgrade) with Commit failing because packages will be broken.

Here's the kicker: This is a fresh install from a disc that cleanly upgraded to 3.5.1. I have tried going to 3.5 and to 3.5.2.

Thanks in advance. I was looking forward to using an ACID2 compliant browser, but this is definitely a setback.[/QUOTE]

Just wondering, are you using Dapper or Breezy. And i would suggest to do:

sudo apt-get clean

then:

sudo apt-get update

then:

sudo apt-get upgrade

and make sure that your repos are up to date

Hope that helps

---

### Post by ModusOperandi on 2006-05-17
I'm using Breezy. 

Unfortunately, nothing has changed.

I forgot to post my sources.list:

```
# deb cdrom:[Kubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted 


deb http://us.archive.ubuntu.com/ubuntu breezy main restricted 
deb-src http://us.archive.ubuntu.com/ubuntu breezy main restricted 

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted 
deb-src http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted 

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb http://us.archive.ubuntu.com/ubuntu breezy universe 
# deb-src http://us.archive.ubuntu.com/ubuntu breezy universe 

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse 
# deb-src http://us.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse 

deb http://security.ubuntu.com/ubuntu breezy-security main restricted 
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted 

# deb http://security.ubuntu.com/ubuntu breezy-security universe 
# deb-src http://security.ubuntu.com/ubuntu breezy-security universe 
deb http://kubuntu.org/packages/kde35 breezy main 
deb http://kubuntu.org/packages/kde351 breezy main 
deb http://kubuntu.org/packages/kde352 breezy main 
```

---

### Post by link141 on 2006-05-17
Just wondering, did you originally have Ubuntu (GTK) installed and decide to install KDE.  This caused a huge problem upgrading for some other guy I was helping the other day.  If so, this may explain it trying to remove KDE, though it shouldn't.

---

### Post by link141 on 2006-05-17
One other thing I forgot to ask, do you at any point download software from the universe repositories, I notice you have them commented, and this may explain some broken packages.

---

### Post by ModusOperandi on 2006-05-18
I don't know if this downloads stuff from the universe, but I don't see why it would. 

This is a clean install after a format, so I shouldn't be having to deal with GNOME.

Thanks guys.

---

