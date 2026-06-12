---
title: "apt-get problems"
date: 2006-01-07
forum: General Help
---

### Post by chubsmalone on 2006-01-07
I've been working on this problem for a couple of weeks now and I am getting really frustrated.  I have kubuntu breezy and when I do apt-get update, apt-get upgrade, I get this:
```
root@Ballard:~# apt-get upgrade
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up debtags (1.4+svn20050912-0ubuntu1) ...
Get:1 http://people.debian.org/~enrico/tags/tags-current.gz
Get:2 http://people.debian.org/~enrico/tags/vocabulary.gz
Fetched 6228B in 0s (9255B/s)
Reading tag data and vocabulary for http://people.debian.org/~enrico/tags/...
ParserException: /var/cache/debtags/people.debian.org_%7eenrico_tags_vocabulary.gz:1: invalid character `<' expecting `:'.  Ignoring source http://people.debian.org/~enrico/tags/
debtags: ConsistencyCheckException: Unable to use any data source (not even previously cached ones)

dpkg: error processing debtags (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of adept:
 adept depends on debtags; however:
  Package debtags is not configured yet.
dpkg: error processing adept (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 debtags
 adept
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I want adept, and adept requires debtags, so I need to fix this.  I have tried manually removing debtags then installing it with apt-get install -f debtags.  I have tried removing and purging it with apt, then reinstalling it.  I've even apt-get dist-upgrade 'd.  I'm at a complete loss for what to do next.  I appreciate any help I can get here...

---

### Post by chubsmalone on 2006-01-09
I still haven't been able to fix this one...just bringing it to the top hoping for the best.  Thanks.

---

### Post by Billquinn1 on 2006-01-10
I guess I am confused. I seem to remember adept being installed when I installed Breezy Kubuntu. When you installed Kubuntu, did you install KDE or the kubuntu-desktop? (they are not the same)
Either way there is an Adept ubuntu package so if you have your repo sources in good shape, you should be able to sudo apt-get install adept. I see some strange repo in your post. Maybe you should comment out those deb repos, apt-get update, apt-get upgrade then install adept. Post your repo list if it still barks at you.
One more thing. You may like synaptic better anyway. If you can't get adept through command line, apt-get install synaptic and use synaptic to install adept. Well you get the idea.

Hope something there helps.

---

### Post by chubsmalone on 2006-01-14
I installed breezy Kubuntu from a CD.  I did not do kubuntu-desktop.  Adept has never worked...ever since my initial install, apt complained about debtags, kubuntu-desktop and adept.  I don't really use adept anyways, I just don't like that I can't fix this problem.  So, here is my sources.list file:

```

#deb cdrom:[Kubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


## Uncomment the following two lines to fetch updated software from the network
deb ftp://mirror.mcs.anl.gov/pub/ubuntu breezy main restricted
deb-src ftp://mirror.mcs.anl.gov/pub/ubuntu breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb ftp://mirror.mcs.anl.gov/pub/ubuntu breezy-updates main restricted
deb-src ftp://mirror.mcs.anl.gov/pub/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb ftp://ubuntu.mirrors.tds.net/ubuntu breezy universe multiverse
deb-src ftp://ubuntu.mirrors.tds.net/ubuntu breezy universe multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb ftp://ubuntu.mirrors.tds.net/ubuntu breezy-backports main restricted universe multiverse
deb-src ftp://ubuntu.mirrors.tds.net/ubuntu breezy-backports main restricted universe multiverse

deb ftp://mirror.mcs.anl.gov/pub/ubuntu breezy-security main restricted
deb-src ftp://mirror.mcs.anl.gov/pub/ubuntu breezy-security main restricted

deb ftp://mirror.mcs.anl.gov/pub/ubuntu breezy-security universe
deb-src ftp://mirror.mcs.anl.gov/pub/ubuntu breezy-security universe


#deb ftp://mirror.mcs.anl.gov/pub/ubuntu breezy-security main restricted
#deb-src ftp://mirror.mcs.anl.gov/pub/ubuntu breezy-security main restricted

#deb http://security.ubuntu.com/ubuntu breezy-security universe
#deb-src http://security.ubuntu.com/ubuntu breezy-security universe

#Extra Junks...
#deb ftp://cipherfunk.org/pub/packages/ubuntu/ breezy main

#deb http://ubuntu-backports.mirrormax.net/ breezy-extras-staging main restricted universe multiverse

##jedit

#deb http://dl.sourceforge.net/sourceforge/jedit ./
#deb-src http://dl.sourceforge.net/sourceforge/jedit ./

##hoary-extras
#deb http://public.planetmirror.com/pub/ubuntu-backports/ hoary-extras main universe multiverse restricted

#deb ftp://ftp.nerim.net/debian-marillat/ sid main

## FTP mirror from http://free.fr (french ISP)
#deb ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/ breezy free non-free
#deb-src ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/ breezy free non-free


```

---

