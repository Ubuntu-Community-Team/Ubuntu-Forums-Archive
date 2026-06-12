---
title: "Installing beryl with svn"
date: 2007-03-12
forum: Desktop Environments
---

### Post by Razer on 2007-03-12
I wanted to install beryl with trevino's repo and this guide [http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_from_the_SVN_snapshots_repository](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_from_the_SVN_snapshots_repository) 
but when it says to add the lines to the sources list I added the lines but when I did the sudo dist upgrade nothing happened. I think that I added the lines in the list wrong but I'm not sure. Please help me out.

---

### Post by Razer on 2007-03-12
Right now my sources.list looks like this
```

  GNU nano 1.3.12                                   File: /etc/apt/sources.list                                                                              

## Major bug fix updates produced after the final release of the
## distribution.

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb http://us.archive.ubuntu.com/ubuntu/ edgy universe
# deb-src http://us.archive.ubuntu.com/ubuntu/ edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse

# deb http://security.ubuntu.com/ubuntu edgy-security universe
deb http://archive.ubuntu.com/ubuntu/ edgy universe main multiverse restricted
deb-src http://archive.ubuntu.com/ubuntu/ edgy universe main multiverse restricted #Added by software-properties
# deb-src http://security.ubuntu.com/ubuntu edgy-security universe

#AUTOMATIX REPOS START

deb http://www.getautomatix.com/apt edgy main

deb http://archive.canonical.com/ubuntu edgy-commercial main

deb http://archive.ubuntu.com/ubuntu edgy-backports main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu edgy-updates main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu edgy-security main restricted universe multiverse
#AUTOMATIX REPOS END

# Treviño's Beryl-SVN Ubuntu Repository
# GPG key: 81836EBF
deb http://download.tuxfamily.org/3v1deb edgy beryl-svn
deb-src http://download.tuxfamily.org/3v1deb edgy beryl-svn




```

---

### Post by roon on 2007-03-12
Hi,      
       There's nothing wrong with your repo.But **sudo apt-get dist-upgrade** will not install beryl on your PC.This command is to make sure that your Edgy distro is up to date before you try to install Beryl.
     Now if you want to install beryl then you must specify your graphics card so we suggest an appropriate guide for installing beryl on your system.

---

### Post by Razer on 2007-03-12
I just installed beryl and aiglx using this guide [http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_AIGLX](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_AIGLX).
Beryl is enabled but when I do enable it, the title bar is gone on every window and the terminal is pure white. Can you all help me fix this.

---

### Post by roon on 2007-03-13
This [thread]("http://forum.beryl-project.org/viewtopic.php?f=36&t=4046")  at the beryl project forums might help.

---

