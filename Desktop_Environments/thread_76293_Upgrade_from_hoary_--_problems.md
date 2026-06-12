---
title: "Upgrade from hoary -- problems"
date: 2005-10-14
forum: Desktop Environments
---

### Post by reuben on 2005-10-14
I did the upgrade. The first time around synaptic failed, so I had it reload, mark all upgrades, and applied again. The second time it works. 

Here are the apps I cannot get working:

mplayer -- worked badly (slo mo), removed, now won't install (screwed up deps)
vlc -- didn't work, removed, now won't install (screwed up deps)
ffplay -- reinstalled manually; no sound (can't open /dev/dsp1)
mozilla-calendar -- won't install (wrong version of mozilla-browser in repository)

older versions of things:
digikam -- 7.2?? NOOOO (7.4 fixes some bugs that I need; guess I have to roll forward on that at least)




In case you're wondering, here's my sources.list

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy-updates main restricted 
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy-updates main restricted 

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy main restricted universe multiverse 
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy main restricted universe multiverse 

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) breezy-security main restricted 
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) breezy-security main restricted 

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) breezy-security universe 
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) breezy-security universe

---

### Post by reuben on 2005-10-15
Ah, I worked this out -- there was a bunch of shite that installed when I tried out e17 a while back. Mplayer said it required something that wasn't going to be installed (lib... I forget). Solution was to look for the lib of the same name but different version, and completely remove it. It took all of the e17 crap with it. All is good now.

---

### Post by skyboy on 2005-10-15
when you have troubles after miss installation, do the commmand sudo apt-get -f install
it usually fix the problems

---

