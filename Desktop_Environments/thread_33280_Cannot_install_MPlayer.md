---
title: "Cannot install MPlayer"
date: 2005-05-10
forum: Desktop Environments
---

### Post by mstralka on 2005-05-10
I'm trying to install MPlayer using Synaptic but it keeps getting dependency errors.  Here's the message when I try to install mplayer-586:
mplayer-586:
 Depends: libavcodeccvs but it is not going to be installed
  Depends: libc6 (>=2.3.2.ds1-21) but 2.3.2.ds1-20ubuntu13 is to be installed
  Depends: libfontconfig1 (>=2.3.0) but 2.2.3-4ubuntu7 is to be installed
 Depends: libpostproc0 but it is not going to be installed
  Depends: libvorbis0a (>=1.1.0) but 1.0.1-1 is to be installed
 Depends: libxvidcore4 but it is not going to be installed
  Depends: xmms (>=1.2.10+cvs20050209) but 1.2.10-2ubuntu1 is to be installed

Here is my sources.lst (I upgraded from warty to hoary)

# deb cdrom:[Ubuntu 4.10 _Warty Warthog_ - Preview i386 Binary-1 (20041020)]/ unstable main restricted  


deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary main restricted   
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary main restricted    

## Uncomment the following two lines to fetch updated software from the network
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse

deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) stable main
deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) unstable main
deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) testing main

#[http://ubuntuforums.org/showthread.php?t=27369](http://ubuntuforums.org/showthread.php?t=27369)
deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/

#[http://beaglewiki.org/index.php/UbuntuInstall](http://beaglewiki.org/index.php/UbuntuInstall)
deb [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports) hoary-backports-staging main universe multiverse restricted
deb [http://manno.name/debian/](http://manno.name/debian/) breezy cvs

---

### Post by brickbat on 2005-05-10
Try following the directions here:

[Ubuntu Guide](http://ubuntuguide.org/#mplayer) 

ciao
bb

---

### Post by Lowe on 2005-05-10
I'm serious, screw mplayer it's fugly anyway.

apt-get install vlc and don't forget the gui wxvlc. Looks 10x better and does everything mplayer does and more.

---

### Post by jcooper on 2005-05-10
MPlayer is covered by the guide posted further up the thread.

What's wrong with Totem, does it not play a particular file? I've installed the win32codecs, libdvdcss and a few others, and I can play pretty much anything in Totem.

VLC, as mentined before, is also good, just not a "gnome app" if you like your consistency ;)

---

