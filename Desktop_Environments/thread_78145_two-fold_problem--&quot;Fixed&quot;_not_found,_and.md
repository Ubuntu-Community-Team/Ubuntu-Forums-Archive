---
title: "two-fold problem--&quot;Fixed&quot; not found, and 404 package errors..."
date: 2005-10-17
forum: Desktop Environments
---

### Post by questionasker on 2005-10-17
everything was just peachy, working like a dream, as ubuntu always does...

then came breezy, and everything fell apart...

im getting the seeming to be very common, error about not being able to stat X font "Fixed"... i searched, and found a thred with several ideas listed to try, and aparently, the poster got his prolem resolved.
however, when i try to install anything, (and even tried a dist-upgrade after updating all the repos to breezy), i get 404 errors that the files are not found...

and these are very common files, in the breezy main branch. in fetching rigth at 200 packages to upgrade earlier today, over half them were not found, and most of them were in the breezy main repo. i would think then, that i had edited my sources.list incorrectly, but some of the packages are still found and download fine...

im getting tired of XP, i need some help guys...


please, any suggestions greatly appriciated! :)

---

### Post by dbott67 on 2005-10-17
The US archives are down.  The answer is in [this thread]("http://www.ubuntuforums.org/showthread.php?p=411974").

This is the "official" sources.list file.  Your /etc/apt/sources.list file needs to be edited so that it looks like this (basically, you have to remove any of the 'US' parts of the URLs):

```
## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu breezy main universe multiverse restricted
deb-src http://archive.ubuntu.com/ubuntu breezy main universe multiverse restricted

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe
```

-Dave

---

### Post by questionasker on 2005-10-17
lol, i figured this out about three mins ago, and now im posting from the very comp that was broken.! 

works like a charm now, hopefully itll find those other 100+ packages that were missing, and ill be cutting edge again :D



by the way- the codes 
```
sudo apt-get install xfs
```
```
sudo apt-get --reinstall install xfonts-base
```

got it running for me (after i took the "US" off my repo lists...)

i guess this post can be deleted now, or saved for future reference... :)

---

