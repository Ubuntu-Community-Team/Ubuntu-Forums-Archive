---
title: "install mplayer"
date: 2005-05-19
forum: Desktop Environments
---

### Post by testingubuntu on 2005-05-19
I would like to install mplayer Preferablly gmplayer (gui version) 

Synaptic shows that it is there but won't install because of 
> mplayer-386:
 Depends: libavcodeccvs but it is not going to be installed
  Depends: libc6 (>=2.3.2.ds1-21) but 2.3.2.ds1-20ubuntu13 is to be installed
  Depends: libfontconfig1 (>=2.3.0) but 2.2.3-4ubuntu7 is to be installed
 Depends: libpostproc0 but it is not going to be installed
  Depends: libvorbis0a (>=1.1.0) but 1.0.1-1 is to be installed
 Depends: libxvidcore4 but it is not going to be installed
 Depends: xmms but it is not going to be installed 

other than installing all of these 1 at a time,  What is the easyest way to accomplish installing gmplayer? 

Thanks

---

### Post by nascent16 on 2005-05-19
I am having the same problem..... I'll see what I can do and post back if I find anything. If anybody knows how a little help would be appreciated.

Justin

---

### Post by NeoChaosX on 2005-05-19
If you have the marillat repositories in your sources.list, remove them or comment them out. The mplayer on those repos rely on Debian-only packages, which is where the problem comes from. The default Ubuntu repos have an MPlayer version that does work with Ubuntu packages.

---

### Post by kuap on 2005-05-19
do: sudo apt-get install -t hoary mplayer

That's it.

---

### Post by testingubuntu on 2005-05-19
which repo does it come from ? 

here is my sources.list 

> deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted


## Uncomment the following two lines to fetch updated software from the network
 deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted
 deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted

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

#deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) stable main
#deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) unstable main
#deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) testing main

---

### Post by testingubuntu on 2005-05-19
[QUOTE=kuap]do: sudo apt-get install -t hoary mplayer

That's it.[/QUOTE]

jim@jNOTEBOOK:~$ sudo apt-get install -t hoary mplayer
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package mplayer
jim@jNOTEBOOK:~$  


could you copy and paste your  /etc/apt/sources.list So that i can compare?

---

### Post by testingubuntu on 2005-05-20
Could some one tell me which repo houses mplayer so that I may add it?

---

### Post by lorap on 2005-05-22
hi friend!
install this player - VLC, and you'll be out of troubles, trust me.
but before you install it via synaptic you've to add it to the repositories's list.
let's do it right now so after i get home the only thing you'd have to do just install the only package.
first of all open System-->Computer Management-->Synaptic Package Manager.
after you get it open go to the Setting-->Repositories.
once you get the repositories window open press Advanced button and mark all checkboxes possible except "download only upgradable packages" then press Ok.
after what you'll need to wait until the update process completes. the repositories' window'll close at the end of the process so you'll be prompted again the synaptic window.
press the Reload button and wait until the reload process completes.
now you're able to install the VLC player.
press the Search button and write in VLC then press Ok.
once you have the package fount out mark it for install and then press Apply button. wait until install process completes after what close the synaptic.
have a nice day.
pavel

---

### Post by christooss on 2005-05-22
[QUOTE=testingubuntu]Could some one tell me which repo houses mplayer so that I may add it?[/QUOTE]

Uncomment ones with word marillat

---

