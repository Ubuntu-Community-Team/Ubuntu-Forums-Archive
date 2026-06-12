---
title: "synaptic not loading / problems with apt-get"
date: 2005-10-22
forum: Desktop Environments
---

### Post by uzusan on 2005-10-22
im having some problems with synaptic and apt-get. i was installing FCEU (the nes emulator) and when it finished, it wasn't showing up in synaptic as being installed.

i tried re-installing it a few times but it wouldnt show up. i shutdown synaptic to try through apt-get but whenever i run apt-get it shows:

Reading package lists... Done
Segmentation faulty tree... 50%

the goes back to the prompt.

now also whenever i try to load synaptic it loads, then quits immediatly. ive tried resetting the machine but its still the same.

it only seems to be synaptic and apt-get that are affected.

any ideas?

---

### Post by KingBahamut on 2005-10-22
Whats your sources.list look like?

---

### Post by uzusan on 2005-10-22
here it is:
> 
deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted


deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) hoary main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) hoary-updates main restricted

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

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

## Backports
#deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
#deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted

i was having problems with some of them (especially the backports), so thats why they are commented out.

---

### Post by uzusan on 2005-10-22
i manged to fix it thanks to this post at the debian lists 
[http://lists.debian.org/deity/2001/04/msg00021.html](http://lists.debian.org/deity/2001/04/msg00021.html)

i emptied the cache for apt by doing 

rm /var/cache/apt/*.bin

and both worked fine after that.

---

