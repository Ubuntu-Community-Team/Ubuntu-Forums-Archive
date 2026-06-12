---
title: "Commented out the CD-ROM Repositories"
date: 2005-08-02
forum: Desktop Environments
---

### Post by eelozano on 2005-08-02
Hello,

I have commented out the CD-ROM for repositories due to the fact that I am running a laptop and the modular bay is normally occupied by the additional battery.  I noticed that I am still able to get all of the same updates and my question is whether or not this is a 'safe' practice.  Are these files the same ones that I would have gotten off the CD had I kept it uncommented.

```
## deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted


## Uncomment the following two lines to fetch updated software from the network
deb http://us.archive.ubuntu.com/ubuntu hoary main restricted
deb-src http://us.archive.ubuntu.com/ubuntu hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu hoary universe
deb-src http://us.archive.ubuntu.com/ubuntu hoary universe

deb http://security.ubuntu.com/ubuntu hoary-security main restricted
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted

deb http://security.ubuntu.com/ubuntu hoary-security universe
deb-src http://security.ubuntu.com/ubuntu hoary-security universe

deb http://archive.ubuntu.com/ubuntu hoary multiverse
deb-src http://archive.ubuntu.com/ubuntu hoary multiverse

## Backports
deb http://ubuntu-backports.mirrormax.net/ hoary-backports main universe multiverse restricted
deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted

```

---

### Post by GavinX on 2005-08-02
[QUOTE=eelozano]Hello,

I have commented out the CD-ROM for repositories due to the fact that I am running a laptop and the modular bay is normally occupied by the additional battery.  I noticed that I am still able to get all of the same updates and my question is whether or not this is a 'safe' practice.  Are these files the same ones that I would have gotten off the CD had I kept it uncommented.[/QUOTE]
It would not affect your system. The short reason why is that updates are obtained via the internet. As a result, the CD would NOT have updates on it. The 'practice' is quite normal and would not yield and negative results.  :)

---

### Post by eelozano on 2005-08-02
Awesome I finally am doing something on my own that people would 'normally' do :)

Step in the right direction.

---

