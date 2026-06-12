---
title: "Amule install error"
date: 2005-07-16
forum: Desktop Environments
---

### Post by vedro on 2005-07-16
ellow

I`m trying to install amule 2.0.3. In my etc/apt/sources.list file I have added: deb [http://dude.gemil.de/](http://dude.gemil.de/) debian/
and deb [http://www.vollstreckernet.de/debian/](http://www.vollstreckernet.de/debian/) testing amule, deb [http://www.vollstreckernet.de/debian/](http://www.vollstreckernet.de/debian/) testing wx. From this page: [http://www.amule.org/wiki/index.php/HowTo_Compile_In_Debian](http://www.amule.org/wiki/index.php/HowTo_Compile_In_Debian)

I have also searched the forum and found: [http://www.ubuntuforums.org/showthread.php?t=48307&highlight=amule](http://www.ubuntuforums.org/showthread.php?t=48307&highlight=amule) and there was also one source: deb [http://www.vollstreckernet.de/debian/](http://www.vollstreckernet.de/debian/) testing amule wx

But I allways get this message in the console when I try the:  apt-get install amule

....
..
..
Some packages have undefined dependencies:
  amule: Depends of: libc6 (>= 2.3.2.ds1-21) but the package: 2.3.2.ds1-20ubuntu13 will be installed
         Depends on: libwxbase2.6 but it wont be installed
         Depends on: libwxgtk2.6 but it wont be installed
E: Damaged packages

(Since I have slovenian console, I have translated it into english)

What should I do?

have a nice day,
vedro

---

### Post by Feanor on 2005-07-16
I think is not a good idea to add all of that repositories in your sources.list. I've Amule 2.0.3 and I think (but I'm not sure of this) I take it from ubuntu backports repositories.

See here [http://www.ubuntuguide.org/#extrarepositories](http://www.ubuntuguide.org/#extrarepositories)

Anyway, if you want to install it from that repositories you must satisfy the dependence of the packet and search them from debian's archives. I don't think this is a good idea...  :? 

Sorry for the bad english  :-#

---

### Post by vedro on 2005-07-16
ellow...

[I]I think is not a good idea to add all of that repositories in your sources.list. I've Amule 2.0.3 and I think (but I'm not sure of this) I take it from ubuntu backports repositories.

See here [http://www.ubuntuguide.org/#extrarepositories](http://www.ubuntuguide.org/#extrarepositories)[/I] 

From that sources I can only install amule 2.0.0 and none other version

So what next?

have a nice day, 
vedro

---

### Post by vedro on 2005-07-17
anybody?..

 :smile:

---

### Post by Feanor on 2005-07-17
Try to search the dependent packets from [www.debian.org](www.debian.org) and install them by

sudo dpkg --install <packet>

I have to advise you that this can compromise other packets depending from previous version of libc6 packet. 

I repeat that I've amule 2.0.3 and I take it from repositories. 

Here is my sources.list, I hope this can help you, and try to uninstall and reinstall amule from this repositories.

```
#deb cdrom:[Kubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted


## Uncomment the following two lines to fetch updated software from the network
 deb http://it.archive.ubuntu.com/ubuntu hoary main restricted
 deb-src http://it.archive.ubuntu.com/ubuntu hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
 deb http://it.archive.ubuntu.com/ubuntu hoary-updates main restricted
 deb-src http://it.archive.ubuntu.com/ubuntu hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
 deb http://it.archive.ubuntu.com/ubuntu hoary universe
 deb-src http://it.archive.ubuntu.com/ubuntu hoary universe

 deb http://security.ubuntu.com/ubuntu hoary-security main restricted
 deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted

 deb http://security.ubuntu.com/ubuntu hoary-security universe
 deb-src http://security.ubuntu.com/ubuntu hoary-security universe

 deb http://archive.ubuntu.com/ubuntu hoary multiverse
 deb-src http://archive.ubuntu.com/ubuntu hoary multiverse

# deb ftp://ftp.nerim.net/debian-marillat stable main
# deb ftp://ftp.nerim.net/debian-marillat unstable main
# deb ftp://ftp.nerim.net/debian-marillat testing main

# repository da cui ho preso java sdk2
# deb http://backports.ubuntuforums.org/backports hoary-extras main universe multiverse restricted

 deb http://ubuntu.tower-net.de/ubuntu/ hoary java

# Ubuntu backports -> aggiornamento versioni dei pacchetti

# deb http://backports.ubuntuforums.org/ubp hoary-backports main universe multiverse restricted
# deb http://backports.ubuntuforums.org/ubp hoary-extras main universe multiverse restricted

 deb http://public.planetmirror.com/pub/ubuntu-backports/ hoary-backports main universe multiverse restricted
 deb http://public.planetmirror.com/pub/ubuntu-backports/ hoary-extras main universe multiverse restricted


## Backports

  deb http://ubuntu-backports.mirrormax.net/ hoary-backports main universe multiverse restricted
  deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted
  deb http://ubuntu-backports.mirrormax.net/ hoary-backports-staging main universe multiverse restricted
  deb http://ubuntu-backports.mirrormax.net/ hoary-extras-staging main universe multiverse restricted

## Kubuntu
  
  deb http://kubuntu.org/hoary-kde341 hoary-updates main
  deb http://kubuntu.org/hoary-koffice14 hoary-updates main
  # deb http://download.kde.org/stable/3.4.1/kubuntu hoary-updates main

## Altre repository per Kubuntu
## applicazioni non supportate dalle repositories ufficiali

  deb http://dinton.no-ip.org/ kubuntu main
  deb-src http://dinton.no-ip.org/ kubuntu main

```

---

### Post by vedro on 2005-07-17
ellow...

Tnx for your sources... From your sources I coul install Amile 2.0.3 without any problems!  :razz: 

From where did you get those sources? Is there some kind of www page where you can chose sources?

tnx again

have a nice day,
vedro

---

### Post by Feanor on 2005-07-17
I found this repos here on [www.ubuntuforums.org](www.ubuntuforums.org) randomly reading discussions ;-)

I think it should be a very good thing if will be available a thread with a collection of useful repositories

I'm glad you've now amule 2.0.3  see you soon  ;-)

---

