---
title: "Does my sources.list look OK?  Just upgraded to Hardy"
date: 2009-05-19
forum: Dell Ubuntu Support (CLOSED)
---

### Post by mysoda on 2009-05-19
Hi

I've just gone from gutsy to hardy (yes, I know I'm slow!) and I used the GUI option.  The update re-wrote my sources.list (which I assumed just meant changed gutsy to hardy) but could someone put my mind at rest that it looks as it should please??  Do I need to tidy it up??  Do I need the restricted repos?

Big thank you!  I know people are always asking this, but forgive me I'm new ;)

mysoda

```
deb http://archive.ubuntu.com/ubuntu hardy main restricted universe
deb-src http://archive.ubuntu.com/ubuntu hardy main restricted universe

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb http://archive.ubuntu.com/ubuntu gutsy universe
# deb-src http://archive.ubuntu.com/ubuntu gutsy universe

deb http://security.ubuntu.com/ubuntu hardy-security main restricted universe
deb-src http://security.ubuntu.com/ubuntu hardy-security main restricted universe

## deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted

deb http://ppa.launchpad.net/dell-team/ppa/ubuntu hardy main
deb http://archive.ubuntu.com/ubuntu hardy-updates restricted main universe
deb-src http://archive.ubuntu.com/ubuntu hardy-updates restricted main universe
deb-src http://ppa.launchpad.net/dell-team/ppa/ubuntu hardy main
```

---

### Post by kostkon on 2009-05-19
Looks ok to me.

---

