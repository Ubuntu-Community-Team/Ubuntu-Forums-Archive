---
title: "[New User] littles questions,"
date: 2005-07-26
forum: Desktop Environments
---

### Post by d2_racing on 2005-07-26
Hello everybody, I'm a new guy in the world of Ubuntu and I installed Ubuntu Hoary 5.04 for my Father. Also I speak french, so sorry for my English.

Since, I used in the past, Mandrake,Fedora CORE 3, Debian Woody(little) and Gentoo.... I will ask straigth foward my questions.

First of all, I know that I can use KDE instead of Gnome. Also can I get it with apt-get.

Also, he uses only the official deposite, so I think that in Ubuntu, you use backports, is there any site or post that I can cut and paste de deposit that I need for this :

Because, I use Gentoo, and there is not deposite at all. So totally new for me (even when i was in Debian Woody).

My father will use this :

KDE 3.4.1 in french plz.
Open Office
Amule
Azureus
mplayer for the DVD Playback and Divx etc...
xmms (mp3)
amsn
gimp
firefox
thunderbird

The basic things has you can see.

So is there some who can help me.

Also, I can tell you that I read the Debian Sarge 3.1 Book in french and because of That I know the base of apt-get.

Thanks you in advance.
 \\:D/

---

### Post by SGC on 2005-07-26
Make sure you have the following repositories in your sources.list file (/etc/apt/sources.list):

```

deb http://fr.archive.ubuntu.com/ubuntu/ hoary-updates main restricted 
deb-src http://fr.archive.ubuntu.com/ubuntu/ hoary-updates main restricted 

deb http://fr.archive.ubuntu.com/ubuntu/ hoary main restricted 
deb-src http://fr.archive.ubuntu.com/ubuntu/ hoary main restricted 

deb http://security.ubuntu.com/ubuntu/ hoary-security main restricted 
deb-src http://security.ubuntu.com/ubuntu/ hoary-security main restricted

#### universe
deb http://fr.archive.ubuntu.com/ubuntu/ hoary universe 
deb-src http://fr.archive.ubuntu.com/ubuntu/ hoary universe 

#### multiverse
deb http://archive.ubuntu.com/ubuntu/ hoary multiverse 
deb-src http://archive.ubuntu.com/ubuntu/ hoary multiverse 

#### backports
deb http://ubuntu-backports.mirrormax.net/ hoary-backports main universe multiverse restricted 
deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted 
deb http://ubuntu-backports.mirrormax.net/ hoary-extras-staging main universe multiverse restricted 
deb http://ubuntu-backports.mirrormax.net/ hoary-backports-staging main universe multiverse restricted 

#### kubuntu.org
deb http://kubuntu.org/hoary-kde341/ hoary-updates main 
deb http://kubuntu.org/hoary-koffice14 hoary-updates main 

```

Then run this command to update the list of packages:
```

sudo apt-get update

```

To install kubuntu:
```

sudo apt-get install kubuntu-desktop

```

To install the rest of the programms:
```

sudo apt-get install kde-i18n-fr amule azureus mplayer-k6 xmms amsn gimp mozilla-firefox mozilla-thunderbird

```

* OpenOffice comes installed with both Ubuntu and Kubuntu

---

### Post by d2_racing on 2005-07-26
Thanks you very much, but I have 2-3 questions.

First of All, where are the deposit main, contrib and non-free from debian?

Also, does mplayer-k6 come with the libdvdcss for the DVD decryption ?
And what means k6....like P4 from pentium or something...

Also, can you explain what is 

main restricted 
universe
multiverse


And finally, is that what I think the source list means:

The original updates for ubuntu.
deb [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) hoary-updates main restricted 
deb-src [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) hoary-updates main restricted 

The original packages from ubuntu
deb [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) hoary main restricted 
deb-src [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) hoary main restricted 

The security update from ubuntu
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security main restricted 
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security main restricted

#### universe
A set of packages not supported by ubuntu
deb [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) hoary universe 
deb-src [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) hoary universe 

#### multiverse
I don't know 
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary multiverse 
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary multiverse 

#### backports
Theses deposits are there to install newer version or like testing in debian.
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted 
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted 
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras-staging main universe multiverse restricted 
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports-staging main universe multiverse restricted 

#### kubuntu.org
Theses deposite are there to installe KDE 3.4.1 and have the updates.
deb [http://kubuntu.org/hoary-kde341/](http://kubuntu.org/hoary-kde341/) hoary-updates main 
deb [http://kubuntu.org/hoary-koffice14](http://kubuntu.org/hoary-koffice14) hoary-updates main

---

### Post by jimcooncat on 2005-07-26
[QUOTE=d2_racing]
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras-staging main universe multiverse restricted 
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports-staging main universe multiverse restricted 
[/QUOTE]

I'd suggest not using these two lines for most setups. From [http://backports.ubuntuforums.org/](http://backports.ubuntuforums.org/):

BIG FAT WARNING: The staging area should be treated like Debian experimental -- it's NOT tested, NOT guaranteed in any way, shape or form to be stable!

---

### Post by SGC on 2005-07-26
Universe, multiverse and main restricted:
[http://www.ubuntulinux.org/ubuntu/components](http://www.ubuntulinux.org/ubuntu/components)

* both univrse and multiverse are offical repositories of ubuntu
* Backports has becomes an offical repository recently

jimcooncat is right about the above two line, I just copy my sources.list and posted here, although I never had a problem with any of the software in backprt staging area.

I don't know about mplayer since I used it once along time ago, but I remember mplayer-k6 is the the only package that works for me.

---

