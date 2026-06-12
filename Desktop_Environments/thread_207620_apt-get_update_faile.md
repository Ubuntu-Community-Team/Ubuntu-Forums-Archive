---
title: "apt-get update faile"
date: 2006-07-02
forum: Desktop Environments
---

### Post by snowdogdb on 2006-07-02
Please help!  I just installed Ubuntu (server install), and when I do an "apt-get update" I get "Connection failed" errors.
Interesting thing is... if I reinstall Ubuntu (desktop install), then apt-get update works fine.
So, with the server install I tried running with debug options:
apt-get -o Debug::Acquire::Http="true" update
...and below is sample of what I got.  
These are good working URLs and I can get to them fine with lynx.  Why is apt telling me connection failed?

=====================
GET [http://archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-i386/Packages.gz) HTTP/1.1
Host: archive.ubuntu.com
Cache-Control: max-age=0
User-Agent: Debian APT-HTTP/1.3


Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
  Connection failed [IP: 85.133.25.7 80]
56% [Working]GET [http://archive.ubuntu.com/ubuntu/dists/dapper/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/dapper/main/source/Sources.gz) HTTP/1.1
Host: archive.ubuntu.com
Cache-Control: max-age=0
User-Agent: Debian APT-HTTP/1.3


GET [http://archive.ubuntu.com/ubuntu/dists/dapper/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/dapper/main/source/Sources.gz) HTTP/1.1
Host: archive.ubuntu.com
Cache-Control: max-age=0
User-Agent: Debian APT-HTTP/1.3


Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Sources
  Connection failed [IP: 85.133.25.7 80]
56% [Working]GET [http://archive.ubuntu.com/ubuntu/dists/dapper/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/dapper/restricted/source/Sources.gz) HTTP/1.1
Host: archive.ubuntu.com
Cache-Control: max-age=0
User-Agent: Debian APT-HTTP/1.3

---

### Post by TigerWolf on 2006-07-02
Please post your sources.list

---

### Post by snowdogdb on 2006-07-02
Here ya go... this is my sources.list

============================

#
# deb cdrom:[Ubuntu 6.06 _Dapper Drake_ - Release i386 (20060531.2)]/ dapper main restricted


deb cdrom:[Ubuntu 6.06 _Dapper Drake_ - Release i386 (20060531.2)]/ dapper main restricted

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-updates main restricted

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


# Line commented out by installer because it failed to verify:
#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# Line commented out by installer because it failed to verify:
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

---

### Post by nickpaton on 2006-07-02
Try this sources list from another post - thanks to Elamericano:

[http://http://www.ubuntuforums.org/showthread.php?t=185971]("http://http://www.ubuntuforums.org/showthread.php?t=185971")

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

# Ubuntu supported packages (sources, GPG key: 437D05B5)
deb-src http://us.archive.ubuntu.com/ubuntu dapper main restricted
deb-src http://us.archive.ubuntu.com/ubuntu dapper-updates main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted

# Ubuntu community supported packages (packages, GPG key: 437D05B5)
deb http://us.archive.ubuntu.com/ubuntu dapper universe multiverse
deb http://us.archive.ubuntu.com/ubuntu dapper-updates universe multiverse
deb http://security.ubuntu.com/ubuntu dapper-security universe multiverse

# Ubuntu backports
# deb http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

# Cipherfunk multimedia packages (packages, GPG key: 33BAC1B3)
deb ftp://cipherfunk.org/pub/packages/ubuntu/ dapper main

# kubuntu.org packages for the latest KDE version (packages, GPG key: DD4D5088)
deb http://kubuntu.org/packages/kde-latest dapper main

# Penguin Liberation Front (PLF)
deb http://theli.free.fr/packages/dapper/ ./

# Dapper PLF repository (not yet available)
# deb http://packages.freecontrib.org/ubuntu/plf/ dapper free non-free
# deb-src http://packages.freecontrib.org/ubuntu/plf/ dapper free non-free

# Compiz (packages, GPG key: 31A5F97FED8A569E)
deb http://www.beerorkid.com/compiz/ dapper main
deb http://xgl.compiz.info/ dapper main aiglx
deb http://compiztools.free.fr/debian unstable main

# Gaim 2 Beta 3
deb http://people.ubuntu.com/~seb128/deb ./

# Skype
deb http://download.skype.com/linux/repos/debian/ stable non-free

# Official Wine
# deb http://wine.sourceforge.net/apt/ binary/

# Wine Dapper
deb http://wine.lowvoice.nl/apt dapper main
```

Also have a look at Psychocats site, which as well as having a great repository list, also has some good help topics:

[http://http://www.psychocats.net/ubuntu/sources]("http://http://www.psychocats.net/ubuntu/sources")

---

### Post by snowdogdb on 2006-07-02
Thanks for trying to help!
That sources.list still produces tons of "Connection Failed"
Could this be a bug in the server version?  
I also tried som of the sources from the link you gave me.

---

### Post by nickpaton on 2006-07-03
I'm not too sure why the Psychocats repo isn't working for you, since it's what I use every day.

I've just done an update with no errors using the following repo based on Psycho with Automatix added at the end:

```
## Uncomment the following two lines to fetch updated software from the network
deb-src http://archive.ubuntu.com/ubuntu dapper main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://archive.ubuntu.com/ubuntu dapper-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb-src http://archive.ubuntu.com/ubuntu dapper universe

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted

deb http://security.ubuntu.com/ubuntu dapper-security universe
deb-src http://security.ubuntu.com/ubuntu dapper-security universe

deb http://archive.ubuntu.com/ubuntu/ dapper multiverse universe main restricted
deb-src http://archive.ubuntu.com/ubuntu dapper multiverse

deb http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse

deb http://packages.freecontrib.org/ubuntu/plf/ dapper free non-free
deb-src http://packages.freecontrib.org/ubuntu/plf/ dapper free non-free

deb http://www.beerorkid.com/automatix/apt dapper main

```

Let me know how you get on & good luck!

---

