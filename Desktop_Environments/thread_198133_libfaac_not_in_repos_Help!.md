---
title: "libfaac not in repos? Help!"
date: 2006-06-16
forum: Desktop Environments
---

### Post by johso on 2006-06-16
Hiya!

I was just trying to install ffmpeg from cvs, in order to convert some movies to mp4. Long story short, 'make' failed, and I somehow screwed up my repos!
I've tried with a clean sources.list, but libfaac and gstreamer0.8-faac are still gone.
The end result of this is that mplayer is now uninstalled. Yay. That really sucks!
Help, someone? I'm panicking!

---

### Post by Ramses de Norre on 2006-06-16
What are your repos? Do you have universe and multiverse? I see a package libfaac0 here.

---

### Post by johso on 2006-06-16
I've got everything other than the CD enabled! And yes, I did also have a libfaac0 earlier this evening, but now it's gone. At first it was not installable, then I tried a complete removal (I guess it mean that literally ;)), and now it's totally gone.
If I try to install from a terminal, this is the output:

```

Reading package lists... Done
Building dependency tree... Done
Package libfaac0 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libfaac0 has no installation candidate

```

---

### Post by Ramses de Norre on 2006-06-16
Try with this sources: ```
# If you get errors about missing keys, lookup the key in this file
# and run these commands (replace KEY with the key number)
#
# gpg --keyserver subkeys.pgp.net --recv KEY
# gpg --export --armor KEY | sudo apt-key add -
##deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted

## Uncomment the following two lines to fetch updated software from the network
deb http://archive.ubuntu.com/ubuntu dapper main restricted
deb-src http://archive.ubuntu.com/ubuntu dapper main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu dapper universe
deb-src http://archive.ubuntu.com/ubuntu dapper universe

deb http://archive.ubuntu.com/ubuntu dapper multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper multiverse

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted

deb http://security.ubuntu.com/ubuntu dapper-security universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security universe multiverse

deb http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse

# Penguin Liberation Front (PLF)
deb http://theli.free.fr/packages/dapper/ ./

# Dapper PLF repository (not yet available)
# deb http://packages.freecontrib.org/ubuntu/plf/ dapper free non-free
# deb-src http://packages.freecontrib.org/ubuntu/plf/ dapper free non-free

##
## Use the following repos only if you need them.
## To use one remove the "##"  from the line that starts with "## deb".
##

## wine
deb http://wine.budgetdedicated.com/apt dapper main
deb-src http://wine.budgetdedicated.com/apt dapper main

## opera web browser
##deb http://deb.opera.com/opera/ etch non-free

# Cipherfunk multimedia (GPG key: 33BAC1B3)
deb ftp://cipherfunk.org/pub/packages/ubuntu/ dapper main
deb-src ftp://cipherfunk.org/pub/packages/ubuntu dapper main

```

---

### Post by johso on 2006-06-16
Of course, it was the backports that was missing! Typical mistake...
Don't know how that happened though, it pretty weird. I haven't been playing around with the sources.list tonight (not before something was wrong, anyway).
Thanks a bunch! :-)

---

