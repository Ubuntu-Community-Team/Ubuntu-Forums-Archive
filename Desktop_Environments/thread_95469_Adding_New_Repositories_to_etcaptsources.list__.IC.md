---
title: "Adding New Repositories to /etc/apt/sources.list?  .ICE_Authority Issues?"
date: 2005-11-26
forum: Desktop Environments
---

### Post by skitzot on 2005-11-26
Hey all,

Just wondering if they are any conflicts/issues with ucommenting some repositories and adding some non-standard ones for libdvdcss and w32codecs?

Just wondering if this would cause package conflicts or unnessesary upgrades to occur.  After I edited /etc/apt/sources.list, to reflect what I pasted below, I turned my computer on this moring only to find that Gnome and KDE weren't working, .ICE_ Authority didn't have the right permissions somehow, which was easy enough to fix.  I'm wondering if me screwing with the repositories or "sudo su, passwd" to have a root password, cou;d have done it?  Thoughts, comments?

Thanks.

> 
deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

## DVD and Win32codecs
# deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) etch main


---

### Post by Rob2687 on 2005-11-26
load the failsafe terminal and do:

sudo chown [your username] .ICEauthority

---

### Post by skitzot on 2005-11-26
Yeah, thats what I did to get back to GNOME, but I was wondering if the repositories could be the cause, or rather, the edits I did?

---

### Post by migueljacq on 2005-11-26
I don't know if that's the cause of yourproblems. But I do know that when adding the unofficial backports for things like w32codecs and whatnot, those instructions often advise to comment out the repositories you had used after installing the packages, and running apt-get update again, to avoid messing your system up. So you are right in that regard. But I don't know if it caused the problem.

---

### Post by skitzot on 2005-11-26
[QUOTE=migueljacq]I don't know if that's the cause of yourproblems. But I do know that when adding the unofficial backports for things like w32codecs and whatnot, those instructions often advise to comment out the repositories you had used after installing the packages, and running apt-get update again, to avoid messing your system up. So you are right in that regard. But I don't know if it caused the problem.[/QUOTE]

Ya, I copied my original repository list so I just replaced it after backing up my newish one.  So I got my ass covered on both ends.  Thanks all.

---

