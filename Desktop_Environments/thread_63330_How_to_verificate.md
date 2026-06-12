---
title: "How to verificate?"
date: 2005-09-07
forum: Desktop Environments
---

### Post by acim on 2005-09-07
Hello,
I am using Kubunutu 5.04. You are going to see my **sources.list** is below.

# deb cdrom:[Kubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted

deb [http://tr.archive.ubuntu.com/ubuntu](http://tr.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://tr.archive.ubuntu.com/ubuntu](http://tr.archive.ubuntu.com/ubuntu) hoary main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://tr.archive.ubuntu.com/ubuntu](http://tr.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://tr.archive.ubuntu.com/ubuntu](http://tr.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://tr.archive.ubuntu.com/ubuntu](http://tr.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://tr.archive.ubuntu.com/ubuntu](http://tr.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

#### backports
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted

deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted

deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras-staging main universe multiverse restricted

deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports-staging main universe multiverse restricted

##Kubuntu
deb [http://kubuntu.org/hoary-kde342/](http://kubuntu.org/hoary-kde342/) hoary-updates main
deb-src [http://kubuntu.org/hoary-kde342/](http://kubuntu.org/hoary-kde342/) hoary-updates main



The problem is:
After giving the "apt-get update" command, there is no problem. But when I write down "apt-get upgrade", it displays:


root@AcimKubuntuLinux:/home/sacim # apt-get upgrade kde
Reading package lists... Done
Building dependency tree... Done
The following packages will be upgraded:
  acroread acroread-plugins amarok amarok-arts firefox foomatic-db-hpijs foomatic-filters-ppds gimp gimp-data gimp-svg gtk2-engines-clearlooks hpijs k3b
  k3blibs kappfinder kate kcontrol kdebase kdebase-bin kdebase-data kdebase-kio-plugins kdepasswd kdeprint kdesktop kdm kfind khelpcenter kicker klipper
  kmenuedit konqueror konqueror-nsplugins konsole konversation kpager kpersonalizer ksmserver ksplash ksysguard ksysguardd ktip kwin libgcc1 libgimp2.0
  libkonq4 libsmbclient mozilla-acroread mozilla-firefox powernowd python-xdg python2.4-samba samba-common smbclient w32codecs
54 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 28.6MB/133MB of archives.
After unpacking 262MB disk space will be freed.
Do you want to continue [Y/n]?
WARNING: The following packages cannot be authenticated!
  libgcc1 acroread acroread-plugins amarok-arts amarok mozilla-firefox firefox hpijs foomatic-db-hpijs gimp-data libgimp2.0 gimp gimp-svg
  gtk2-engines-clearlooks k3blibs kdebase-bin kdebase-data kcontrol k3b kappfinder kate libsmbclient kdebase-kio-plugins libkonq4 kdepasswd kdeprint
  kdesktop kfind khelpcenter kicker klipper kmenuedit konqueror-nsplugins konqueror konsole kpager kpersonalizer ksmserver ksplash ksysguard ksysguardd
  ktip kwin kdebase kdm konversation mozilla-acroread powernowd python-xdg python2.4-samba samba-common smbclient w32codecs foomatic-filters-ppds
Install these packages without verification [y/N]?
E: Some packages could not be authenticated

What do I have to do or what should I do for verification to upgrade without a problem?

Can you help me?

Thank you. :roll:

---

### Post by mlomker on 2005-09-07
> What do I have to do or what should I do for verification to upgrade without a problem?


That's a common problem.  Just press 'Y' at that prompt and you should be fine.

---

