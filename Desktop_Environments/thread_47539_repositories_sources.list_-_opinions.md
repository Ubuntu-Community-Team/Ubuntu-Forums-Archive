---
title: "repositories sources.list - opinions?"
date: 2005-07-09
forum: Desktop Environments
---

### Post by Rory on 2005-07-09
Hi,  

I loaded Ubuntu but then added the last source, on the list below, in order to load kubuntu-desktop.  But, I'm not sure how the Ubuntu and Kubuntu source lists should differ.  

Can anyone make any suggestions for additions/deletions/improvements to this sources.list?

Thanks,
Rory


```

## Uncomment the following two lines to fetch updated software from the network
deb http://archive.ubuntu.com/ubuntu hoary main restricted
deb-src http://archive.ubuntu.com/ubuntu hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://archive.ubuntu.com/ubuntu hoary-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu hoary universe
deb-src http://archive.ubuntu.com/ubuntu hoary universe

deb http://security.ubuntu.com/ubuntu hoary-security main restricted
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted

deb http://security.ubuntu.com/ubuntu hoary-security universe
deb-src http://security.ubuntu.com/ubuntu hoary-security universe

deb http://archive.ubuntu.com/ubuntu hoary multiverse
deb-src http://archive.ubuntu.com/ubuntu hoary multiverse

## Backports
deb http://ubuntu-backports.mirrormax.net/ hoary-backports main universe multiverse restricted bleeding
deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted bleeding

#Kubuntu
deb http://kubuntu.org/hoary-kde341 hoary-updates main


```

---

### Post by t2kburl on 2005-07-09
that is exactly the same as mine

I've seen some threads that mention the merrilat repos ... haven't yet tried them myself

---

### Post by t2kburl on 2005-07-09
I found them

## Marillat
#deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) stable main
#deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) testing main

# OpenOffice
#deb [http://borft.student.utwente.nl/openoffice/debian/](http://borft.student.utwente.nl/openoffice/debian/) stable main contrib
#deb [http://borft.student.utwente.nl/openoffice/debian/](http://borft.student.utwente.nl/openoffice/debian/) unstable main contrib

---

### Post by t2kburl on 2005-07-09
I just tried the merrilat repos I listed and they didn't work ....   apt-get update error ...blah blah  ](*,)

---

### Post by André on 2005-07-09
AFAIK you don't need the marillat repos anymore.

The only thing i used it for was w32codecs but that came with the hoary-extras backport repo.

Marillat's repo, which i used for some time, is based on Debian unstable, again AFAIK :-) And so there are sometimes dependency problems. Try to find w32codecs but just using the backports and you should find them.

Otherwise tell me ;-)

Greetings
André

P.S.: You didn't include the repos for KDE 3.4.1 and koffice 1.4. You can find these on the Kubuntu homepage: [www.kubuntu,org](www.kubuntu,org)

---

