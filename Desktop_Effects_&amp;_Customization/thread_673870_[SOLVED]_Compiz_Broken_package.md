---
title: "[SOLVED] Compiz Broken package?"
date: 2008-01-21
forum: Desktop Effects &amp; Customization
---

### Post by Janxeh on 2008-01-21
Hi there,
Im a complete linux nub and i have a fresh install of kubuntu gutsy installed as my first linux os :D
i have been following the link: [https://help.ubuntu.com/community/CompositeManager/CompizFusion#head-1447dbabe59744a63cad770f4d2143fb45cb4aad](https://help.ubuntu.com/community/CompositeManager/CompizFusion#head-1447dbabe59744a63cad770f4d2143fb45cb4aad)
to try and install compiz.
When i run the $ sudo apt-get install compiz-kde command or try and download it through Adept i get the following message.
"some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  compiz-kde: Depends: compiz-core (= 1:0.6.0+git20071008-0ubuntu1.1) but 1:0.6.0+git20071008-0ubuntu1 is to be installed
              Depends: compiz-plugins (= 1:0.6.0+git20071008-0ubuntu1.1) but 1:0.6.0+git20071008-0ubuntu1 is to be installed
E: Broken packages
janx@spawn:~$

So i ran sudo apt-get install compiz-core which ran ok so did " " Compiz-plugins, doing so did not even change the error message :(
Please help me :\

---

### Post by erfahren on 2008-01-21
post the output of
```

cat /etc/apt/sources.list

```

---

### Post by Janxeh on 2008-01-21
I added the repository that ubuntu guide has listed, they are at the bottom.

# deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
# Line commented out by installer because it failed to verify:
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main universe restricted multiverse
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb [http://ppa.launchpad.net/amaranth/ubuntu](http://ppa.launchpad.net/amaranth/ubuntu) feisty main universe
deb-src [http://ppa.launchpad.net/amaranth/ubuntu](http://ppa.launchpad.net/amaranth/ubuntu) feisty main universe

---

### Post by erfahren on 2008-01-21
ok try this ...
back up your current sources.list
```

cp /etc/apt/sources.list /etc/apt/sources.list_back

```
open it up in kate (isn't the KDE text editor called "kate"? I think so...)
```

gksudo kate /etc/apt/sources.list

```
Select all and paste the following overwiting what's in there with what's below and save it
```

## CD-ROM
## If you have a install CD you can add it to the reposity using 'apt-cdrom add'
## which will add a line similar to the following:
## deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

## Add comments (##) in front of any line to remove it from being checked.   
## Uncomment deb-src if you wish to download the source packages

deb http://au.archive.ubuntu.com/ubuntu/ gutsy main universe restricted multiverse
deb-src http://au.archive.ubuntu.com/ubuntu/ gutsy main universe restricted multiverse 
deb http://security.ubuntu.com/ubuntu/ gutsy-security universe main multiverse restricted
deb-src http://security.ubuntu.com/ubuntu/ gutsy-security universe main multiverse restricted 
deb http://au.archive.ubuntu.com/ubuntu/ gutsy-updates universe main multiverse restricted
deb-src http://au.archive.ubuntu.com/ubuntu/ gutsy-updates universe main multiverse restricted 
deb-src http://archive.ubuntu.com/ubuntu/ gutsy main restricted 

## START -- MANUALLY ADDED
##

## CANONICAL REPOSITORY
deb http://archive.canonical.com/ubuntu gutsy partner

## BACKPORTS REPOSITORY
deb http://archive.ubuntu.com/ubuntu gutsy-backports main restricted
deb http://archive.ubuntu.com/ubuntu gutsy-backports universe multiverse
deb-src http://archive.ubuntu.com/ubuntu gutsy-backports main restricted
deb-src http://archive.ubuntu.com/ubuntu gutsy-backports universe multiverse

## THIRD-PARTY REPOSITORIES
##
## MEDIBUNTU  
deb http://packages.medibuntu.org/ gutsy free non-free

```
then in the terminal add the key for Medibuntu (it has some "non-free" packages not available in the Ubuntu repos) - and update
```

wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update

```
check for software updates
```

sudo apt-get upgrade

```
try installing what you were before now

---

### Post by Janxeh on 2008-01-21
Wow that list is nice and neat :D yeah it was kate, i did as you said and everything installed :D your an absolute champion!
But one more problem i continued along my merry way through that install guide and now when i type compiz --replace in konsole or run... i get

janx@spawn:~$ compiz --replace
Checking for Xgl: not present.
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity
no /usr/bin/metacity found, exiting

Im guessing xgl is something to do with my graphics card. i have a nvidia 8800 gtx ultra, do i need different drivers to standard install ones?

---

### Post by Janxeh on 2008-01-21
Can someone please let me know how i fix xgl and install drivers?

Thanks :)

---

### Post by erfahren on 2008-01-21
what kind of video card do you have? you can see in the "VGA compatible controller"  line in the output of:
```

lspci

```
you also might need to enable a resticted driver for the card:
KMenu &#8594; System Settings, go to the Advanced tab and click Restricted Drivers. Then click the Administrator Mode button and check the box marked Enable to install the driver.

from: [https://help.ubuntu.com/community/Video](https://help.ubuntu.com/community/Video)

For an ATI card you would need to install the package "xserver-xgl" and log out/log back in before enabling desktop effects

[https://help.ubuntu.com/7.10/desktop-effects/C/](https://help.ubuntu.com/7.10/desktop-effects/C/)
[https://help.ubuntu.com/community/UbuntuEyeCandy](https://help.ubuntu.com/community/UbuntuEyeCandy)

---

### Post by Janxeh on 2008-01-21
Thanks, i will run though this as soon as i get home from work tonight and post the results.

---

### Post by Janxeh on 2008-01-22
Thanks for your help Erfahren.
All i had to do was activate the nvidia drivers in restricted drivers and compiz is up and running nice and smoothly.

---

