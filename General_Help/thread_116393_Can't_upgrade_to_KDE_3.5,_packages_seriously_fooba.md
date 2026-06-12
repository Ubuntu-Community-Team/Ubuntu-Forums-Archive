---
title: "Can't upgrade to KDE 3.5, packages seriously foobar'd"
date: 2006-01-12
forum: General Help
---

### Post by eqisow on 2006-01-12
I recently tried to upgrade to KDE 3.5 via the instructions [here]("http://kubuntu.org/announcements/kde-35.php"). After updated my sources.list and adding the gpg key I attempted to upgrade via synaptic. I received the following error:

```
E: /var/cache/apt/archives/kdm_4%3a3.5.0-0ubuntu0breezy1_i386.deb: subprocess new pre-removal script returned error exit status 1

```

I was going to upload my sources.list but so many packages are broken due to this that I can't even run most KDE apps now. At any rate, I don't see how that could be causing the problem.

---

### Post by Kadin2048 on 2006-01-12
I got the upgrade to work, I believe by following the same instructions.

Pretty much all I did was add the kubuntu server to my sources.list file, add the PGP key, apt-get update, and then dist-upgrade.  

I will append my sources.list file onto the end of my post. I would maybe try running apt-get update once or twice (sometimes I need to run it twice for it to not give me any errors) and then try dist-upgrade again.

Good luck.

```
deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


## Uncomment the following two lines to fetch updated software from the network
 deb-src http://us.archive.ubuntu.com/ubuntu breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
 deb http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted
# deb-src http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu breezy universe main restricted
# deb-src http://us.archive.ubuntu.com/ubuntu breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
 deb http://us.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

 deb http://security.ubuntu.com/ubuntu breezy-security main restricted
# deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

 deb http://security.ubuntu.com/ubuntu breezy-security universe
# deb-src http://security.ubuntu.com/ubuntu breezy-security universe

# Packages relating to the BOINC Project
deb http://pkg-boinc.alioth.debian.org/ubuntu/ breezy universe

# KDE 3.5 Packages
deb http://kubuntu.org/packages/kde35 breezy main
```

---

### Post by ollesbrorsa on 2006-01-13
Hello,

I also followed the announcements directions for the repo and the gpg-key. 

When I upgraded via 

```
sudo apt-get update
sudo apt-get dist-upgrade
```

I had to do

```
sudo apt-get -f dist-upgrade
```

in order for it to work.

Good luck!

/ollesbrorsa

---

### Post by sharke on 2006-01-13
I think when you upgrade via synaptic it uses smart upgrade not dist-upgrade.
Follow ollesbrorsa instructions and you should be okay.
Regards
Sharke

---

