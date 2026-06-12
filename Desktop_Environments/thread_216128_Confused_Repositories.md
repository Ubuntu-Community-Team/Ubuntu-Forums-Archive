---
title: "Confused Repositories"
date: 2006-07-15
forum: Desktop Environments
---

### Post by DanMan_7 on 2006-07-15
Greetings,
   I was hoping someone could share their repositories list, mine is screwed up and I didn't want to reinstall just for that.  I'm not smart enough to figure out where the glitch is.  Perhaps if someone has a working repositories list, with universe and multiverse activated, they could paste the "Sources.list" file.     Thanks a lot, Dan

---

### Post by DanMan_7 on 2006-07-15
OH, and if you have an idea of where my problem is this is the contents of my sources.list file.  
> 

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
> 

---

### Post by struess on 2006-07-15
hey Dan,
check out the repository support page.. there are some stickies worth looking at:

[http://ubuntuforums.org/forumdisplay.php?f=41](http://ubuntuforums.org/forumdisplay.php?f=41)

good luck!

---

### Post by struess on 2006-07-15
a note real quick -- in your sources.list, try taking out the #'s in front of the six lines that start with "# deb ...".  with those commented out, you might be missing something. 

in any event, check out the link above.  for a clean re-start, try:
[http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)

---

### Post by Ramses de Norre on 2006-07-15
I've got a few more repos, I don't know how legal they are and most of them are unsupported so only use them if you need them.
```
## Penguin Liberation Front (PLF)
##deb http://theli.free.fr/packages/dapper/ ./

## Dapper PLF repository
deb http://packages.freecontrib.org/ubuntu/plf/ dapper free non-free
deb-src http://packages.freecontrib.org/ubuntu/plf/ dapper free non-free

##
## Use the following repos only if you need them.
## To use one remove the "##"  from the line that starts with "## deb".
##

## Skype
##deb http://seveas.theplayboymansion.net/seveas breezy-seveas extras
##deb http://download.skype.com/linux/repos/debian/ stable non-free

## wine
deb http://wine.budgetdedicated.com/apt dapper main
deb-src http://wine.budgetdedicated.com/apt dapper main

## opera web browser
##deb http://deb.opera.com/opera/ etch non-free

## Oo2 final - you can optionally use this one until OOo2 final arrives in backports
##deb http://people.ubuntu.com/~doko/OOo2 ./

## kubuntu.org packages for the latest KDE version (GPG key: DD4D5088)
##deb http://kubuntu.org/packages/kde-latest dapper main

## kubuntu.org packages for the latest Koffice version (GPG key: DD4D5088)
##deb http://kubuntu.org/packages/koffice-latest dapper main

## kubuntu.org packages for the latest amaroK version (GPG key: DD4D5088)
##deb http://kubuntu.org/packages/amarok-14 dapper main

## Cipherfunk multimedia (GPG key: 33BAC1B3)
deb ftp://cipherfunk.org/pub/packages/ubuntu/ dapper main
deb-src ftp://cipherfunk.org/pub/packages/ubuntu dapper main

## Seveas repo
##deb http://seveas.ubuntulinux.nl dapper-seveas all
##deb-src http://seveas.ubuntulinux.nl dapper-seveas all

## Canonical commercial repo
deb http://archive.canonical.com/ubuntu dapper-commercial main

```

---

### Post by T700 on 2006-07-15
Below is mine:

```
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse
deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free
deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/
deb [http://deb.opera.com/opera](http://deb.opera.com/opera) etch non-free
# The above lines were generated automatically by EasyUbuntu 3.0 Beta Release
# The rest of your sources.list follows
# I just added this line to see if anyone really reads the comments

# sudo gedit /etc/apt/sources.list
#deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper main restricted
## MAJOR BUG usX UPDATES produced after the usnal release
#deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper-updates main restricted
## UBUNTU SECURITY UPDATES
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
## UNIVERSE AND MULTIVERSE REPOSITORY
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse
## BACKPORTS REPOSITORY
##deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper-backports main restricted
##deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper-backports universe multiverse
##deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper-backports main restricted
##deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper-backports universe multiverse
# PLF REPOSITORY
deb [http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf) breezy free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf) breezy free non-free
# WINE
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main
deb-src [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main
deb [http://www.beerorkid.com/automatix/apt](http://www.beerorkid.com/automatix/apt) dapper main

deb [http://kubuntu.org/packages/kde-353](http://kubuntu.org/packages/kde-353) dapper main
deb [ftp://bolugftp.uni-bonn.de/pub/kde/stable/3.5.3/kubuntu](ftp://bolugftp.uni-bonn.de/pub/kde/stable/3.5.3/kubuntu) dapper main
deb [http://www.mirrorservice.org/sites/ftp.kde.org/pub/kde/stable/3.5.3/kubuntu](http://www.mirrorservice.org/sites/ftp.kde.org/pub/kde/stable/3.5.3/kubuntu) dapper main
# mirror.cc.columbia.edu not responding as of July 3 2006
#deb [http://mirror.cc.columbia.edu/pub/software/kde/stable/3.5.3/kubuntu](http://mirror.cc.columbia.edu/pub/software/kde/stable/3.5.3/kubuntu) dapper main

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main
deb [http://kubuntu.org/packages/amarok-141](http://kubuntu.org/packages/amarok-141) dapper main
```

Paul

---

### Post by Ramses de Norre on 2006-07-15
Why do you have breezy versions of things like the PLF repo? And you've got a lot of duplicates in fact (but that doesn't do no harm I think).

---

### Post by T700 on 2006-07-15
> **Ramses de Norre said:**
> Why do you have breezy versions of things like the PLF repo? And you've got a lot of duplicates in fact (but that doesn't do no harm I think).

Feh...lazy...careless.  Guess it's time to pay a visit to source-o-matic.  Maybe I should have cleaned house after the last upgrade, before posting my dirty laundry for the world.  Thanks for the reminder.

Edit:

```
# Automatically generated sources.list
# http://www.ubuntulinux.nl/source-o-matic
#
# If you get errors about missing keys, lookup the key in this file
# and run these commands (replace KEY with the key number)
#
# gpg --keyserver subkeys.pgp.net --recv KEY
# gpg --export --armor KEY | sudo apt-key add -

# Ubuntu supported packages (packages, GPG key: 437D05B5)
deb http://us.archive.ubuntu.com/ubuntu dapper main restricted
deb http://us.archive.ubuntu.com/ubuntu dapper-updates main restricted
deb http://security.ubuntu.com/ubuntu dapper-security main restricted

# Ubuntu community supported packages (packages, GPG key: 437D05B5)
deb http://us.archive.ubuntu.com/ubuntu dapper universe multiverse
deb http://us.archive.ubuntu.com/ubuntu dapper-updates universe multiverse
deb http://security.ubuntu.com/ubuntu dapper-security universe multiverse

# Cipherfunk multimedia packages (packages, GPG key: 33BAC1B3)
deb ftp://cipherfunk.org/pub/packages/ubuntu/ dapper main

# kubuntu.org packages for the latest KDE version (packages, GPG key: DD4D5088)
deb http://kubuntu.org/packages/kde-latest dapper main

# kubuntu.org packages for the latest Koffice version (packages, GPG key: DD4D5088)
deb http://kubuntu.org/packages/koffice-latest dapper main

# kubuntu.org packages for the latest amaroK version (packages, GPG key: DD4D5088)
deb http://kubuntu.org/packages/amarok-latest dapper main

# Penguin Liberation Front (packages)
deb ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/ dapper free non-free

# Bleeding edge wine packages (packages)
deb http://wine.budgetdedicated.com/apt dapper main

# The Opera browser (packages)
deb http://deb.opera.com/opera etch non-free


``` 
Paul

---

### Post by DanMan_7 on 2006-07-15
> **Ramses de Norre said:**
> Why do you have breezy versions of things like the PLF repo? And you've got a lot of duplicates in fact (but that doesn't do no harm I think).

Well that is my problem i think.  I haven't altered my repositories outside of easy ubuntu, yet It takes 20min of failed attempts to get through a list of repositories it says are not available.  I have no idea how they got there.   
     Thanks everyone.

---

