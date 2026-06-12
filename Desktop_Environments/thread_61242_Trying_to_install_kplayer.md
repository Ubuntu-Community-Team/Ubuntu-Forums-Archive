---
title: "Trying to install kplayer"
date: 2005-08-30
forum: Desktop Environments
---

### Post by jhuff on 2005-08-30
I just changed my sources.list file as described in “KUDOS Unofficial Kubuntu FAQ” [http://kudos.berlios.de/kf/kf.html](http://kudos.berlios.de/kf/kf.html) .  Now When I try and install kplayer I get the following error:

xxx@xxxxxx:~/Downloads$ sudo apt-get install kplayer
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  kplayer: Depends: libidn11 (>= 0.5.13) but 0.5.2-3 is to be installed
E: Broken packages
xxx@xxxxxx:~/Downloads$

Does anyone have any suggestions on how to resolve this problem?

Has anyone else started using the “KUDOS Unofficial Kubuntu FAQ”?

---

### Post by incinerator on 2005-08-31
kplayer is not an official part of ubuntu. The package apt-get wants to install is probably designed for debian. Now, ubuntu is not debian, and certain packages have other names, other version numbers or are missing. That's why adding external package repositories to /etc/apt/sources.list doesn't always work.

In fact, I don't like that sources.list from the kudos website at all. I fail to see the reason why e.g. the marillat repo should be in there, everything important is in universe/multiverse or hoary-backports/hoary-extras. I fail to see the reason why marillat is enabled by default when hoary-extras is disabled by default.

I followed the saner approach as seen [here](http://ubuntuguide.org/#extrarepositories). Plus the repo for kubuntu kde 3.4.2, and you're settled. Dunnow if that enables kplayer though, as I use kaffeine.

---

### Post by jhuff on 2005-08-31
I put back my old sources.list.  Now I'm wondering if I caused any compatibility problems.  I guess time will tell.  The kudos instructions have you install /etc/apt/preferences.  Should I delete this file?  I don't remember having it before.

The file contains the following:
Package: *
Pin: release a=hoary, v=5.04
Pin-Priority: 1000

Package: *
Pin: release a=hoary-security, v=5.04
Pin-Priority: 1000

Package: *
Pin: release a=hoary-updates, v=5.04
Pin-Priority: 1000

---

### Post by incinerator on 2005-09-01
Well, I've never used apt-pinning, and I don't see what benefits the contents of your  preferences file should have. Rename that file (e.g. to preferences.backup) and see what happens. If something breaks you can always revert it to its old name.

My understanding of apt-pinning is that is mainly to be used to resolve version conflicts when different repos contain different versions of the same package. I think it mainly got invented in debian for people to be able to install packages from different releases, e.g. mixing "stable" and "testing". Usually users stayed with one release but installed newer versions of packages from "testing" when they deemed it important to have a newer version.

With ubuntu, these version conflicts are unlikely to appear, unless you try mixing hoary with breezy or you add some 3rd party repositories. As an example, the old unofficial hoary-backports repo contains firefox-1.0.6, but the official hoary-upates repo also contains that version. apt-pinning can then provide an easy way for apt-get to figure out from what repo it should prefer for updates.

Anywas, I think this pinning stuff is not really needed in most of the cases, I have never set it up with kubuntu and things seem to work fine for me.

---

### Post by gnutux on 2005-09-01
Try using the universe or multiverse repositories.

(K)ubuntu IS NOT Debian, only based.

gnutux

---

### Post by incinerator on 2005-09-01
> Try using the universe or multiverse repositories.
Yup, I think jhuff got that idea three days ago. Nice that you mention it, though.


> (K)ubuntu IS NOT Debian, only based.
Shocking, I am speechless, REALLY?

---

### Post by gnutux on 2005-09-01
well, if the packages from Debian are renamed and remodified, then the system has differed. Plus, Ubuntu's kernel has been remodified as far as what I heard.

gnutux

---

### Post by jhuff on 2005-09-01
Would someone mind taking a look at my sources.list file and let me know if it looks OK?

## deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted


## Uncomment the following two lines to fetch updated software from the network
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse

## Backports
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted

deb [http://kubuntu.org/hoary-kde342](http://kubuntu.org/hoary-kde342) hoary-updates main
deb-src [http://kubuntu.org/hoary-kde342](http://kubuntu.org/hoary-kde342) hoary-updates main

---

### Post by incinerator on 2005-09-01
hoary-updates -> no multiverse, no universe ???
hoary-security -> no multiverse ???

offical hoary-backports are missing, too.

gnutux: nonono, you've got it all wrong. ubuntu is just a re-labeled version of debian devised by microsoft as a means to make gnu/linux users go back to la-la-land. Debian is soooooo difficult to install and soooooo difficult to administer, surely nobody except these 1000 debian developers would really want to use it. That's the perfect distro to lure newbies to install, only to get them disappointed by .deb hell and make them switch back to la-la-virus. I tell you, canonical is knee-deep in this, too. Look at this Shuttleworth guy, he is a South African, and WHITE. He cannot possibly be a decent person. Only decent person in South Africa is Nelson Mandela! Besides, what would be the benefit of make ubuntu different from debian? any change would only make it better, some people could actually like it. 50% of the forum members here are actually con artists paid by ms do lure the n00bz even deeper into the excrement. Me too, byraway.

---

### Post by gnutux on 2005-09-01
Ubuntu is definitely not supported by Microsoft.

gnutux

---

