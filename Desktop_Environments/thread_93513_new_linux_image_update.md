---
title: "new linux image update?"
date: 2005-11-22
forum: Desktop Environments
---

### Post by missmoondog on 2005-11-22
I am getting the following compnents listed as being able to be updated from my update manager this morning. However, when I click install, I get a warning that says it can't be authenticated.  The only difference between those packages and mine are the .1 at the end of the version number. Get almost the exact same thing going through Synaptic, except there are only 4 items in the upgradeable list, there are 8 in update manager. I believe I am using just the default repositories. What should I do?

Thank you

linux-386 (version 2.6.12.16) will be upgraded to version 2.6.12.16.1
linux-image-386 (version 2.6.12.16) will be upgraded to version 2.6.12.16.1
linux-restricted-modules-386 (version 2.6.12.16) will be upgraded to version 2.6.12.16.1
linux-restricted-modules-common (version 2.6.12.4-11) will be upgraded to version 2.6.12.4-11.1
linux-image-2.6.12-10-386 (version 2.6.12-10.24) will be installed
linux-restricted-modules-2.6.12-10-386 (version 2.6.12.4-11.1) will be installed

---

### Post by Pablo_Escobar on 2005-11-22
Post Your /etc/apt/sources.list here so we can troubleshoot :)

---

### Post by missmoondog on 2005-11-22
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
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
##deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
##deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy universe

---

### Post by Pablo_Escobar on 2005-11-22
I'd recommend applying the sources.list provided by ubuntu_daemon here:
[http://www.ubuntuforums.org/showthread.php?t=92672]("http://www.ubuntuforums.org/showthread.php?t=92672")

---

### Post by missmoondog on 2005-11-22
Just edited the src list and reloaded. same results as far as getting the warning message about those file not being authenticated.

---

### Post by Pablo_Escobar on 2005-11-22
Not authenticated is nothing to worry about IMHO that is.

---

### Post by missmoondog on 2005-11-22
reloaded a couple times and now get more updates than i had to begin with! not getting the warning message though. went ahead and got all the upgrades there were available to me. i made it back here, so everything seems to be good for now. i do have 2 references to the linux kernel when booting up again. from previous experience in that matter from a couple of days ago, i know how to fix that.

---

