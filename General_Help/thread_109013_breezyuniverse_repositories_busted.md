---
title: "breezy/universe repositories busted?"
date: 2005-12-27
forum: General Help
---

### Post by ren wins on 2005-12-27
every time i log into synaptic, i get this error

> W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)

i tried re-adding all the repositories in synaptic (settings > repositories > add) and it told me a had a bunch of new updates available, i downloaded those and got this error

> W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory

and this one
> [http://us.archive.ubuntu.com/ubuntu/dists/breezy/universe/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/breezy/universe/binary-i386/Packages.gz:) Sub-process gzip returned an error code (1)

i just installed the k7 kernel, but i'm not using it at the moment (the internet only works in the 386 kernel), but maybe that's the problem?
but all the other repositories seem to be working fine

sudo apt-get update gets the same sort of errors...
am i missing something?

---

### Post by One Quick Question on 2005-12-27
The universe repos are working fine for me.   
I can't think of why that is erroring (I haven't seen it before).
Check out /var/lib/apt/lists/.  Does it exist?

---

### Post by ren wins on 2005-12-27
it looks like it's there..?

> lock
partial
security.ubuntu.com_ubuntu_dists_breezy-security_main_binary-i386_Packages
security.ubuntu.com_ubuntu_dists_breezy-security_main_source_Sources
security.ubuntu.com_ubuntu_dists_breezy-security_multiverse_binary-i386_Packagessecurity.ubuntu.com_ubuntu_dists_breezy-security_Release
security.ubuntu.com_ubuntu_dists_breezy-security_Release.gpg
security.ubuntu.com_ubuntu_dists_breezy-security_restricted_binary-i386_Packagessecurity.ubuntu.com_ubuntu_dists_breezy-security_restricted_source_Sources
security.ubuntu.com_ubuntu_dists_breezy-security_universe_binary-i386_Packages
security.ubuntu.com_ubuntu_dists_breezy-security_universe_source_Sources
Ubuntu%205.10%20%5fBreezy%20Badger%5f%20-%20Release%20i386%20(20051012)_dists_breezy_main_binary-i386_Packages
Ubuntu%205.10%20%5fBreezy%20Badger%5f%20-%20Release%20i386%20(20051012)_dists_breezy_Release
Ubuntu%205.10%20%5fBreezy%20Badger%5f%20-%20Release%20i386%20(20051012)_dists_breezy_restricted_binary-i386_Packages
us.archive.ubuntu.com_ubuntu_dists_breezy-backports_main_binary-i386_Packages
us.archive.ubuntu.com_ubuntu_dists_breezy-backports_main_source_Sources
us.archive.ubuntu.com_ubuntu_dists_breezy-backports_multiverse_binary-i386_Packages
us.archive.ubuntu.com_ubuntu_dists_breezy-backports_multiverse_source_Sources
us.archive.ubuntu.com_ubuntu_dists_breezy-backports_Release
us.archive.ubuntu.com_ubuntu_dists_breezy-backports_Release.gpg
us.archive.ubuntu.com_ubuntu_dists_breezy-backports_restricted_binary-i386_Packages
us.archive.ubuntu.com_ubuntu_dists_breezy-backports_restricted_source_Sources
us.archive.ubuntu.com_ubuntu_dists_breezy-backports_universe_binary-i386_Packages
us.archive.ubuntu.com_ubuntu_dists_breezy-backports_universe_source_Sources
us.archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages
us.archive.ubuntu.com_ubuntu_dists_breezy_main_source_Sources
us.archive.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-i386_Packages
us.archive.ubuntu.com_ubuntu_dists_breezy_Release
us.archive.ubuntu.com_ubuntu_dists_breezy_Release.gpg
us.archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages
us.archive.ubuntu.com_ubuntu_dists_breezy_restricted_source_Sources
us.archive.ubuntu.com_ubuntu_dists_breezy_universe_source_Sources
us.archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-i386_Packages
us.archive.ubuntu.com_ubuntu_dists_breezy-updates_main_source_Sources
us.archive.ubuntu.com_ubuntu_dists_breezy-updates_multiverse_binary-i386_Packages
us.archive.ubuntu.com_ubuntu_dists_breezy-updates_Release
us.archive.ubuntu.com_ubuntu_dists_breezy-updates_Release.gpg
us.archive.ubuntu.com_ubuntu_dists_breezy-updates_restricted_binary-i386_Packages
us.archive.ubuntu.com_ubuntu_dists_breezy-updates_restricted_source_Sources
us.archive.ubuntu.com_ubuntu_dists_breezy-updates_universe_binary-i386_Packages


i'm gonna look at that ubuntu guide... b/c i think it had directions on how to add repositories in gedit
which i trust more than gui

---

### Post by One Quick Question on 2005-12-28
Hm.  Could you post your sources.list?

---

### Post by kurokikaze on 2005-12-28
Hi. I've exactly the same problem as ren_wins. I'm using Ubuntu 5.10 AMD with K8 kernel and here it is my sources.list:

> #deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release amd64 (20051012)]/ breezy main restricted

## INTERNATIONAL HOSTS ##

# Ubuntu supported packages (packages)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

# Ubuntu supported packages (sources)
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

# Ubuntu community supported packages (packages)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe multiverse

# Ubuntu community supported packages (sources)
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe multiverse

# Ubuntu backports project (packages)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

# Ubuntu backports project (sources)
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

It worked for about five minutes, but now it is impossible for me to get the packages.

---

### Post by Unicast on 2005-12-28
Having major problems here too in Breezy:

> W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)

---

### Post by kurokikaze on 2005-12-28
Well, actually they work. I think there has been some problems with the ubuntu packages server. I've found that checking the site [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) is quite a guarantee: if you can see it, then apt-get update will work !

For Unicast: I think the urls of the repositories are wrong. Try changing in your sources.list file, for example:

> [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/main --> [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

This should work.

---

### Post by Unicast on 2005-12-28
Hmmm....

My sources.list
> #deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted

## Uncomment the following two lines to fetch updated software from the network
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse 

deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) etch non-free
deb [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) breezy free non-free
deb-src [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) breezy free non-free


kurokikaze - my "backports" is already configured as you suggested. Is the backport server down?

---

### Post by kurokikaze on 2005-12-29
Unicast - The url for backports is [http://archive.ubuntu.com/ubuntu/dists/breezy-backports/](http://archive.ubuntu.com/ubuntu/dists/breezy-backports/) and actually I found it running. If you can see it in your browser, probably it will work with apt-get update too.

---

### Post by Ruskie on 2005-12-29
There definitely must be some problem with the package server: I couldn't see any of my repositories, and I didn't change anything for a month, at least. I tried 3 times, then I set off for help and came into this thread. Didn't change nothing, retried synaptic... and it's got its repositories!
It only does not found wine specific repositories and another one... but official repositories are ok. I thinks something is not working properly....

---

### Post by kurokikaze on 2005-12-29
I think Ubuntu server has been attacked by hackers. In fact, if you open [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) with your browser you'll see a clearly fake google page with 404 error on it. Plus, if you just open [http://archive.ubuntu.com](http://archive.ubuntu.com) you'll see a well designed but again fake page of google.

---

### Post by One Quick Question on 2005-12-29
Whoa.  Is that true?   Those pages seem to have been restored now, anyway.

---

### Post by kurokikaze on 2005-12-29
[QUOTE=One Quick Question]Whoa.  Is that true?   Those pages seem to have been restored now, anyway.[/QUOTE]

Yes, now they work but for five minutes they've been completely crazy!!

---

### Post by ren wins on 2005-12-29
sorry it took me a while to get back with this

here's my sources.list
> 
## Uncomment the following two lines to fetch updated software from the network
 deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted universe multiverse
 deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe main restricted multiverse
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

 deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe main restricted multiverse
 deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe


---

