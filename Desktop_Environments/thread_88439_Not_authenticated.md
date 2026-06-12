---
title: "Not authenticated"
date: 2005-11-10
forum: Desktop Environments
---

### Post by Pete051 on 2005-11-10
Another puzzle, when I try to install Knoda (or it appears any kde software) Synaptic give me the message "You are about to install software that can't be authenticated! ,etc.etc. Any ideas why Ubuntu suddenly has a grudge against kde anyone? Thanks 
Pete
Just out of Idle curiousity how do some posters manage to use their PGP signatures on their postings?

---

### Post by Pablo_Escobar on 2005-11-10
AFAIK Synaptic pops that message if You're installing something from the repos which aren't officialy supported by Ubuntu team.
If You have trust in repos You're using it's safe to use them.

---

### Post by Pete051 on 2005-11-10
So if I'd installed the kubuntu desktop instead of ubuntu I wouldn't have this problem?
Pete

---

### Post by Pablo_Escobar on 2005-11-10
No, it not something ubuntu <-> kubuntu. It's when You add some extra repos (I'm using one for Polish IM, and it gives me the same "Not authenticated" messages).
If You're worried, paste Your /etc/apt/sources.list file here, and we'll see which repos are not the standard ones.

---

### Post by Pete051 on 2005-11-10
Hmm ok, here's the sources list as you see the only non standard repos are for the cvs scribus. I commented out the back port repos because they give me a directory not found error. 
Pete

deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


## Uncomment the following two lines to fetch updated software from the network
deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy universe
deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
#deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
#deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb         [http://debian.scribus.net/debian/](http://debian.scribus.net/debian/) breezy main restricted
deb-src     [http://debian.scribus.net/debian/](http://debian.scribus.net/debian/) breezy main restricted

deb         [http://debian.tagancha.org/debian/](http://debian.tagancha.org/debian/) breezy main restricted
deb-src     [http://debian.tagancha.org/debian/](http://debian.tagancha.org/debian/) breezy main restricted

---

