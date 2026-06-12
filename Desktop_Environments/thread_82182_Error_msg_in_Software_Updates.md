---
title: "Error msg in Software Updates"
date: 2005-10-26
forum: Desktop Environments
---

### Post by Neeko on 2005-10-26
Hi there,
can someone tell me what this error message is and what I do to fix it?

Software Updates notification has a red cross through it. Clicking it opens the Software Updates window as usual, but when I click on the "Install" button I get this error message:

```
E: The package index files are corrupted. No Filename: field for package autoconf.
E: Unable to lock the download directory
```

Thx

---

### Post by endersshadow on 2005-10-26
Can you paste your /etc/apt/sources.list file here for us to see?

Thanks!

---

### Post by Neeko on 2005-10-26
Sure thing, here you go:
```
john@ubuntu:~$ cat /etc/apt/sources.list
deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main r estricted

#deb ftp://ftp.nerim.net/debian-marillat/ etch main

deb-src http://nz.archive.ubuntu.com/ubuntu breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://nz.archive.ubuntu.com/ubuntu breezy-updates main restricted
#deb-src http://nz.archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://nz.archive.ubuntu.com/ubuntu breezy universe main restricted multiver se
deb-src http://nz.archive.ubuntu.com/ubuntu breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe
john@ubuntu:~$

```
thx

---

### Post by Neeko on 2005-10-27
*bump*

Can anyone help me with this?

I get this same error if I try to install any software packages via "Add Applications" or the "Synaptec Package Manager". 

I have been on ubuntu only a week or so and dont know where to look...

---

