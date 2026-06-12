---
title: "Gnomebaker K3B installation problems"
date: 2005-06-25
forum: Desktop Environments
---

### Post by cotcot on 2005-06-25
I installed Ubuntu 5.04 from CD and added the universe and multiverse repositories in /etc/apt/sources.list.
Installing Gnomebaker failed (mpg321, sox, vorbis not installable because libid3tag0 and libmad0 are missing; cannot find these)

I tried k3B as an alternative but I could not find any repository for it. 

Can anybody help me ? Has anybody recently installed Gnomebaker or k3b ?

Thank you

---

### Post by cutOff on 2005-06-25
Can you post your sources.list please?

---

### Post by cotcot on 2005-06-26
Here is my sources.list :

deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted


deb-src [http://be.archive.ubuntu.com/ubuntu](http://be.archive.ubuntu.com/ubuntu) hoary main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://be.archive.ubuntu.com/ubuntu](http://be.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://be.archive.ubuntu.com/ubuntu](http://be.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://be.archive.ubuntu.com/ubuntu](http://be.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://be.archive.ubuntu.com/ubuntu](http://be.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse

deb [http://download.videolan.org/pub/videolan/debian](http://download.videolan.org/pub/videolan/debian) sid main
deb-src [http://download.videolan.org/pub/videolan/debian](http://download.videolan.org/pub/videolan/debian) sid main

deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted

---

### Post by titmouse on 2005-06-26
[QUOTE=cotcot]I installed Ubuntu 5.04 from CD and added the universe and multiverse repositories in /etc/apt/sources.list.
Installing Gnomebaker failed (mpg321, sox, vorbis not installable because libid3tag0 and libmad0 are missing; cannot find these)

I tried k3B as an alternative but I could not find any repository for it. 

Can anybody help me ? Has anybody recently installed Gnomebaker or k3b ?

Thank you[/QUOTE]
 I installed gnomebaker recently with this in /etc/apt/sources.list:
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse

deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) stable main
deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) unstable main
deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) testing main

deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted

Just reload all repositories information completely (click on show details during repositories update in synaptic and reload till all is complete)

---

### Post by cutOff on 2005-06-26
[QUOTE=cotcot]Here is my sources.list :

deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted


deb-src [http://be.archive.ubuntu.com/ubuntu](http://be.archive.ubuntu.com/ubuntu) hoary main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://be.archive.ubuntu.com/ubuntu](http://be.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://be.archive.ubuntu.com/ubuntu](http://be.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://be.archive.ubuntu.com/ubuntu](http://be.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://be.archive.ubuntu.com/ubuntu](http://be.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse

deb [http://download.videolan.org/pub/videolan/debian](http://download.videolan.org/pub/videolan/debian) sid main
deb-src [http://download.videolan.org/pub/videolan/debian](http://download.videolan.org/pub/videolan/debian) sid main

deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted[/QUOTE]

Gnomebaker is in [universe](http://us.archive.ubuntu.com/ubuntu/pool/universe/g/gnomebaker/)  repository.

BTW you lack one line in your sources.list

```
deb [http://be.archive.ubuntu.com/ubuntu](http://be.archive.ubuntu.com/ubuntu) hoary main restricted
```

---

### Post by cotcot on 2005-06-27
Thanks titmouse and cutOff. I could install gnomebaker after adding the repositories, installing gftp-gtk and apt-get update. 
I got some error messages for the ftp's from debian :
W: GPG error: [ftp://ftp.nerim.net](ftp://ftp.nerim.net) stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 07DC563D1F41B907
W: GPG error: [ftp://ftp.nerim.net](ftp://ftp.nerim.net) unstable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 07DC563D1F41B907
W: GPG error: [ftp://ftp.nerim.net](ftp://ftp.nerim.net) testing Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 07DC563D1F41B907

The missing packages were downloaded from :
Ophalen:1 [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) hoary/universe cdda2wav 4:2.0+a38-1ubuntu4 [153kB]
Ophalen:2 [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) hoary/main libid3tag0 0.15.1b-3 [34,2kB]
Ophalen:3 [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) hoary/main libmad0 0.15.1b-1 [73,1kB]
Ophalen:4 [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) hoary/universe mpg321 0.2.10.3 [34,5kB]
Ophalen:5 [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) hoary/universe sox 12.17.5-4 [264kB]
Ophalen:6 [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) hoary/main liboggflac1 1.1.1-4 [30,0kB]
Ophalen:7 [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) hoary/main vorbis-tools 1.0.1-1.1ubuntu1 [190kB]
Ophalen:8 [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) hoary/universe gnomebaker 0.3-3 [394kB]
I have quickly tested gnomebaker with a CD-RW and it was OK (after a mounting error i have to look after).

---

