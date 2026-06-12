---
title: "Update Error Questions"
date: 2010-07-18
forum: Desktop Environments
---

### Post by OxentroT on 2010-07-18
I have been having, for some time, every time I run 

```
sudo apt-get update
```

I am returned at the end of the process numerous error messages as follows:

```

W: GPG error: http://packages.medibuntu.org karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: GPG error: http://packages.medibuntu.org lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: Failed to fetch cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)/dists/jaunty/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)/dists/jaunty/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

E: Some index files failed to download, they have been ignored, or old ones used instead.
```

I was just wondering how I can or should address these errors and resolve them. As for the "Jaunty" errors I was wondering if it were somehow I have obsolete entries in my repositories?

---

### Post by Cavsfan on 2010-07-18
Here is a link on how to work with repositories.

You probably just need to change the jaunty to lucid.

_[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)_

---

### Post by CoolJohnB on 2010-07-18
I had the same problem, the solution at: [http://ubuntuforums.org/showthread.php?t=1532984](http://ubuntuforums.org/showthread.php?t=1532984)

Worked for most of them, maybe it can work for you?

---

### Post by Cavsfan on 2010-07-18
Aldo here is a copy of my [COLOR=Red]Lucid 64 bit[/COLOR] sources list

gksu gedit /etc/apt/sources.list

```
# deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release amd64 (20100429)]/ lucid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ lucid main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ lucid universe
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid universe
deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ lucid multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid multiverse
deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu lucid partner
# deb-src http://archive.canonical.com/ubuntu lucid partner

deb http://security.ubuntu.com/ubuntu lucid-security main restricted
deb-src http://security.ubuntu.com/ubuntu lucid-security main restricted
deb http://security.ubuntu.com/ubuntu lucid-security universe
deb-src http://security.ubuntu.com/ubuntu lucid-security universe
deb http://security.ubuntu.com/ubuntu lucid-security multiverse
deb http://archive.canonical.com/ lucid partner
deb-src http://security.ubuntu.com/ubuntu lucid-security multiverse
#added 2 lines below 07-02-10 for mediainfo
deb http://ppa.launchpad.net/shiki/mediainfo/ubuntu lucid main
deb-src http://ppa.launchpad.net/shiki/mediainfo/ubuntu lucid main

```I hope this helps! 
I also do not use update manager.

Only 
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

It's nice to see what is going on before it happens.

---

### Post by miminom on 2010-07-18
After the upgrade version of Ubuntu, having huge problems with the keyboard. It works, but wrong ... Keyboard layout simply mixed,
some are English letters, then suddenly the letters of my language ... I tested not only on your keyboard effect is the same. He tried:( to dig into the settings, but it did not help. What do I do with this?:)

__________________________
my site: [pharmacy affiliate]("http://pharmacyaffiliate.biz")

---

### Post by Cavsfan on 2010-07-18
> **miminom said:**
> After the upgrade version of Ubuntu, having huge problems with the keyboard. It works, but wrong ... Keyboard layout simply mixed,
some are English letters, then suddenly the letters of my language ... I tested not only on your keyboard effect is the same. He tried:( to dig into the settings, but it did not help. What do I do with this?:)

__________________________
my site: [pharmacy affiliate]("http://pharmacyaffiliate.biz")

This is not related to the OP's issue, but have you looked at System > Preferences > Keyboard and the Layouts tab?

---

### Post by ajgreeny on 2010-07-18
To the OP.

Use ```
gksudo gedit /etc/apt/sources.list
``` and comment out any lines that have **karmic** or **jaunty** or **cdrom** in them (type # at the start of the line) save the file.

The medibuntu lines that are probably in a separate file will need ```
gksudo gedit  /etc/apt/sources.list.d/medibuntu.list
``` and again comment out the lines with karmic in them, then run 
```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```and you should get your medibuntu repos back again.



Now try updating again.

---

### Post by OxentroT on 2010-07-19
> 
ajgreeny     Re: Update Error Questions

To the OP.

Use
Code:

gksudo gedit /etc/apt/sources.list

and comment out any lines that have karmic or jaunty or cdrom in them (type # at the start of the line) save the file.

The medibuntu lines that are probably in a separate file will need
Code:

gksudo gedit  /etc/apt/sources.list.d/medibuntu.list

and again comment out the lines with karmic in them, then run
Code:

sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update

and you should get your medibuntu repos back again.



Now try updating again.
Last edited by ajgreeny; 1 Day Ago at 02:53 PM..
ajgreeny is offline   	Reply With Quote

Thanks mate! I think that takes care of theses errors for the most part, however, there seems to be some problem with authenticating my keyring.

The errors within the results of my latest update through terminal is as follows:
```
Fetched 7,051B in 7s (943B/s)                                                       
Reading package lists... Done
W: GPG error: http://packages.medibuntu.org lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
drdoak@nOvUm:~$ 

```


Not quite as bad, but what has me for a sort of loss is that when I open the medibuntu.list with gedit, the file is completely empty.

---

### Post by Cavsfan on 2010-07-20
To the OP:

The contents of /etc/apt/sources.list.d/medibuntu.list

```
## Please report any bug on https://bugs.launchpad.net/medibuntu/
deb http://packages.medibuntu.org/ lucid free non-free #Medibuntu - Ubuntu 10.04 "lucid lynx"
# deb-src http://packages.medibuntu.org/ lucid free non-free #Medibuntu (source) - Ubuntu 10.04 "lucid lynx"
```Add the medibuntu key

```
wget --quiet http://packages.medibuntu.org/medibuntu-key.gpg -O - | sudo apt-key add -
```

---

### Post by OxentroT on 2010-07-21
> Cavsfan  	
Re: Update Error Questions
To the OP:

The contents of /etc/apt/sources.list.d/medibuntu.list

Code:

## Please report any bug on [https://bugs.launchpad.net/medibuntu/](https://bugs.launchpad.net/medibuntu/)
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) lucid free non-free #Medibuntu - Ubuntu 10.04 "lucid lynx"
# deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) lucid free non-free #Medibuntu (source) - Ubuntu 10.04 "lucid lynx"

Add the medibuntu key

Code:

wget --quiet [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O - | sudo apt-key add -



AhAh! Worked like a charm, however I am un sure as to weather or not that mattered a whole lot? I am now beginning to wonder if my OCD was making a bigger deal than it may be.

Thank You!

:guitar:

---

### Post by Mixphonics on 2010-07-29
Thank you for this thread!  I was looking everywhere on how to find and add this key, couldn't find it any place else.  

Much appreciated!

-Mixphonics

---

### Post by OxentroT on 2010-08-01
Thankyou all for help. The issue has been gracefully resolved.

-Rock 0n!
:guitar:

---

