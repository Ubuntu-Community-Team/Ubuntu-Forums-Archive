---
title: "Free flight simulator games for ubuntu"
date: 2006-01-11
forum: Gaming &amp; Leisure
---

### Post by Dark Damo on 2006-01-11
does anyone know any free flight simulator games for linux? 

Thank you :)

---

### Post by briguy on 2006-01-11
Flight Gear is like MS Flight Sim - really good program.  There is also GL-117 which is a dated fighter game, but kinda fun.  There are a few space flight simulators as well like vegastrike.  All these are in the repositories

---

### Post by Dark Damo on 2006-01-11
Thank you but my synaptic package manager has gone all funny :(

Anyway i'm looking at flight gear but on the debian site it is down :( 

How do i acsess the repositories?

---

### Post by Perfect Storm on 2006-01-11
[http://www.flightgear.org/Downloads/binary.shtml#linux](http://www.flightgear.org/Downloads/binary.shtml#linux)

But you might run into dependency problems if your repo is down. ( [http://doc.gwos.org/index.php/Flight_Gear](http://doc.gwos.org/index.php/Flight_Gear) )

---

### Post by Dark Damo on 2006-01-11
Thank you i am trying out the links now ;)

Which one do i get? i cant get the debian one because the site is down :(

---

### Post by Perfect Storm on 2006-01-11
If you have universe enable in your source list, you can apt-get it. Though if you can live with it's v0.9.7 and not not v0.9.9

---

### Post by Dark Damo on 2006-01-11
Thats ok but i only have the stock sources.list

Where can i get the upgraded one?

Thanks :)

---

### Post by Perfect Storm on 2006-01-11
You can use the one I'm using

```
sudo gedit /etc/apt/sources.list
```

Wipe out what you see and add this instead then you have all what you need and more:

> 
deb [http://dk.archive.ubuntu.com/ubuntu](http://dk.archive.ubuntu.com/ubuntu) breezy main restricted
#deb-src [http://dk.archive.ubuntu.com/ubuntu](http://dk.archive.ubuntu.com/ubuntu) breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://dk.archive.ubuntu.com/ubuntu](http://dk.archive.ubuntu.com/ubuntu) breezy-updates main restricted
#deb-src [http://dk.archive.ubuntu.com/ubuntu](http://dk.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://dk.archive.ubuntu.com/ubuntu](http://dk.archive.ubuntu.com/ubuntu) breezy universe
#deb-src [http://dk.archive.ubuntu.com/ubuntu](http://dk.archive.ubuntu.com/ubuntu) breezy universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

## Multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse
#deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse

## Skype
deb [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free

## Wine
deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/
#deb-src [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) source/

## Penguin Liberation Front
deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free
#deb-src [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free

## Backports
deb [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) breezy-backports main universe multiverse restricted
deb-src [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
#deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) breezy-backports-staging main universe multiverse restricted

#backports-extras
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) breezy-extras main universe multiverse restricted
#deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) breezy-extras-staging main universe multiverse restricted

# Open Office 2 final
deb [http://people.ubuntu.com/~doko/OOo2](http://people.ubuntu.com/~doko/OOo2) ./

# Opera web browser
deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) etch non-free


```

sudo apt-get update
sudo apt-get install flightgear

```

---

### Post by Dark Damo on 2006-01-11
Thank you very much. I allso have a tar.gz file. How can i install that? Its from some game called ysflight simulator or something.

Ok the other game works good appart when the plane starts moving it really badly lags!

I have a Celeron 320 with a Radeon 9800 pro 128mb 1024mb DDR400. Am i under the specs? I have the ATI drivers installed allso

---

