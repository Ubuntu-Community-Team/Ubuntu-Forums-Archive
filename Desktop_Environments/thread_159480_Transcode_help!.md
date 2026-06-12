---
title: "Transcode help!"
date: 2006-04-13
forum: Desktop Environments
---

### Post by aptsonic on 2006-04-13
I've updated Dvd::rip, and now I need to update Transcode, I've added its repository to my source list but I also need these following dependencies.

Please help me find them so that i can simply add them to my source list.


transcode:
  Depends: libasound2 (>1.0.10) but 1.0.9-2 is to be installed
 Depends: libavcodeccvs51 but it is not going to be installed
  Depends: libgcc1 (>=1:4.1.0) but 1:4.0.1-4ubuntu9 is to be installed
  Depends: libglib2.0-0 (>=2.10.0) but 2.8.3-0ubuntu1 is to be installed
 Depends: libmagick9  but it is not installable
  Depends: libogg0 (>=1.1.3) but 1.1.2-1 is to be installed
 Depends: libpostproccvs51 but it is not going to be installed
  Depends: libstdc++6 (>=4.1.0) but 4.0.1-4ubuntu9 is to be installed
  Depends: libvorbis0a (>=1.1.2) but 1.1.0-1ubuntu1 is to be installed
  Depends: libvorbisfile3 (>=1.1.2) but 1.1.0-1ubuntu1 is to be installed
  Depends: libxml2 (>=2.6.23) but 2.6.21-0ubuntu1 is to be installed

---

### Post by nemequ on 2006-04-13
Please paste your sources.list here.

---

### Post by aptsonic on 2006-04-13
(the bottom three are the ones which apply to dvd::rip)


deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
## deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
## deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy universe main restricted multiverse

deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/

deb [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) breezy free non-free
deb-src [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) breezy free non-free

deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) etch non-free

deb [http://kubuntu.org/packages/kde351](http://kubuntu.org/packages/kde351) breezy main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb [http://koti.mbnet.fi/~ots/ubuntu/](http://koti.mbnet.fi/~ots/ubuntu/) breezy/
deb-src [http://koti.mbnet.fi/~ots/ubuntu/](http://koti.mbnet.fi/~ots/ubuntu/) breezy/

deb [http://people.ubuntu.com/~doko/OOo2](http://people.ubuntu.com/~doko/OOo2) ./

## created by arniefreeadded

deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) sarge main
deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) etch main
deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) sid main

---

### Post by nemequ on 2006-04-13
You've got a lot of weird sources in there. Try using [http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic) then add in the extras you really need. IIRC there is a dvdrip package in multiverse that you should be using instead of those ones on the bottom. Make sure you run a dist-upgrade... my guess is you have old packages that depend on older versions of those libraries, which prevents them from being upgraded to the versions you need for transcode.

---

### Post by aptsonic on 2006-04-13
a number of them were added by automatix

the last three are the ones that [www.exit1.org/dvdrip/](www.exit1.org/dvdrip/) recomends to install the debian packages.

I think it is obivious why I need constant updates of a program called dvd::rip, so will this sorcelist maker add the sources to fulfill my need?

---

### Post by aptsonic on 2006-04-13
new source.list

# Automatically generated sources.list
# [http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)
#
# If you get errors about missing keys, lookup the key in this file
# and run these commands (replace KEY with the key number)
#
# gpg --keyserver subkeys.pgp.net --recv KEY
# gpg --export --armor KEY | sudo apt-key add -

# Ubuntu supported packages (packages, GPG key: 437D05B5)
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

# Ubuntu supported packages (sources, GPG key: 437D05B5)
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

# Ubuntu community supported packages (packages, GPG key: 437D05B5)
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe multiverse
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe multiverse

# Ubuntu community supported packages (sources, GPG key: 437D05B5)
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe multiverse

# Seveas' packages (packages, GPG key: 1135D466)
deb [http://mirror.ubuntulinux.nl](http://mirror.ubuntulinux.nl) breezy-seveas all

# Seveas' packages (sources, GPG key: 1135D466)
deb-src [http://users.lichtsnel.nl/~seveas](http://users.lichtsnel.nl/~seveas) breezy-seveas all

# Ubuntu backports project (packages, GPG key: 437D05B5)
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

# Ubuntu backports project (sources, GPG key: 437D05B5)
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

# Cipherfunk multimedia packages (packages, GPG key: 33BAC1B3)
deb [ftp://cipherfunk.org/pub/packages/ubuntu/](ftp://cipherfunk.org/pub/packages/ubuntu/) breezy main

# Cipherfunk multimedia packages (sources, GPG key: 33BAC1B3)
deb-src [ftp://cipherfunk.org/pub/packages/ubuntu](ftp://cipherfunk.org/pub/packages/ubuntu) breezy main

# Penguin Liberation Front (packages)
deb [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) breezy free non-free

# Penguin Liberation Front (sources)
deb-src [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) breezy free non-free

# Bleeding edge wine packages (packages)
deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/

# Bleeding edge wine packages (sources)
deb-src [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) source/

# OpenOffice.org 2 final packages (packages)
deb [http://people.ubuntu.com/~doko/OOo2/](http://people.ubuntu.com/~doko/OOo2/) ./

# Osmo Salomas CVS amule packages (packages, GPG key: 70188C3B)
deb [http://koti.mbnet.fi/~ots/ubuntu](http://koti.mbnet.fi/~ots/ubuntu) breezy/

# Osmo Salomas CVS amule packages (sources, GPG key: 70188C3B)
deb-src [http://koti.mbnet.fi/~ots/ubuntu](http://koti.mbnet.fi/~ots/ubuntu) breezy/

# Bazaar-NG development (packages, GPG key: 1F44842D)
deb [http://people.ubuntu.com/~jbailey/snapshot/bzr](http://people.ubuntu.com/~jbailey/snapshot/bzr) ./

# Bazaar-NG development (sources, GPG key: 1F44842D)
deb-src [http://people.ubuntu.com/~jbailey/snapshot/bzr](http://people.ubuntu.com/~jbailey/snapshot/bzr) ./

---

### Post by aptsonic on 2006-04-13
on the update check these failed

W: GPG error: [http://mirror.ubuntulinux.nl](http://mirror.ubuntulinux.nl) breezy-seveas Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 49A120FD1135D466
W: GPG error: [http://people.ubuntu.com](http://people.ubuntu.com) ./ Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY B0B7481B1F44842D
W: GPG error: [ftp://cipherfunk.org](ftp://cipherfunk.org) breezy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 4CF19C3233BAC1B3
W: GPG error: [http://users.lichtsnel.nl](http://users.lichtsnel.nl) breezy-seveas Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 49A120FD1135D466
W: GPG error: [ftp://ftp.nerim.net](ftp://ftp.nerim.net) sarge Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 07DC563D1F41B907
W: GPG error: [ftp://ftp.nerim.net](ftp://ftp.nerim.net) etch Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 07DC563D1F41B907
W: GPG error: [ftp://ftp.nerim.net](ftp://ftp.nerim.net) sid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 07DC563D1F41B907

---

