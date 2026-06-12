---
title: "libpng3"
date: 2004-10-18
forum: General Help
---

### Post by dasfiend on 2004-10-18
serveral packages (cedega, linux-image-2.6.8.1-3-686-smp, etc) have listed as a dependancy the package libpng3.  This does not appear in my apt list (I searched via apt-cache search png and nothing came up).  My error is:

The following packages have unmet dependencies:
  cedega: Depends: libpng3 but it is not installable
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

I was scared to force the install of a kernel image.

is there anyway to get a libpng3 for ubuntu?

---

### Post by jeremy on 2004-10-18
I have it on mine, here's my /etc/apt/soureces.lst -
```
deb cdrom&#58;&#91;Ubuntu 4.10 _Warty Warthog_ - Preview i386 Binary-1 &#40;20041013&#41;&#93;/ unstable main restricted 


deb http&#58;//archive.ubuntu.com/ubuntu/ warty main restricted 
deb-src http&#58;//archive.ubuntu.com/ubuntu/ warty main restricted 

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http&#58;//archive.ubuntu.com/ubuntu/ warty universe 
deb-src http&#58;//archive.ubuntu.com/ubuntu/ warty universe 

deb http&#58;//security.ubuntu.com/ubuntu/ warty-security main restricted 
deb-src http&#58;//security.ubuntu.com/ubuntu/ warty-security main restricted 

## Added by me
deb http&#58;//archive.ubuntu.com/ubuntu/ warty multiverse 
deb ftp&#58;//ftp.nerim.net/debian-marillat/ unstable main 
# deb http&#58;//ftp.carnet.hr/pub/debian/ sid main non-free contrib
```

---

