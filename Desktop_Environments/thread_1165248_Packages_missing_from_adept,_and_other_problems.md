---
title: "Packages missing from adept, and other problems"
date: 2009-05-20
forum: Desktop Environments
---

### Post by Hark3n on 2009-05-20
Hi,

Over the weekend I finally got myself a new computer.  Along with that I decided it would be a good time to install 9.04.  Unfortunately I realised soon thereafter that it was probably not a good idea.  I only have a Hauwei E220 for internet access, and with Jaunty not capable of using the modem I decided to install Intrepid again.

Now this is where the fun starts.  Firstly, my install didn't exactly go smoothly.  I had frequent freezes during the install, and in the end it took about 2 hours to get the thing up and running.

Then I realized that Kubuntu would randomly freeze during startup and shutdown.  The startup freezes have now been resolved, but the shutdown freeze is still there.  It is not that big a problem, but is quite irritating.

Now, my big problem.  Having had to do a new install on my new computer, I had to re-install quite a lot of programs.  Some of them aren't that important, but one is vital for my wife's business.  After adding all the necessary repos I started noticing that certain packages didn't show up in adept, specifically digikam and screensavers.  I also noticed that the option to keep Kubuntu at 8.10 has disappeared, leaving me with no option but to upgrade to 9.04.  Obviously I don't want to do that as I would loose function of my modem.

I have been trying to find similar problems on the forums and google, but am still unable to find any.

Does anybody know what might be the problem with my installation and how I can remedy it.  I have included my sources.list.

> # deb cdrom:[Kubuntu 8.10 _Intrepid Ibex_ - Release amd64 (20081029.1)]/ intrepid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) intrepid main restricted
deb-src [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted
deb-src [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) intrepid universe
deb-src [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) intrepid universe
deb [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) intrepid-updates universe
deb-src [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb-src [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse
deb-src [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
# deb-src [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner

deb [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) intrepid-security main restricted
deb-src [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) intrepid-security main restricted
deb [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) intrepid-security universe
deb-src [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) intrepid-security universe
deb [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) intrepid-security multiverse
deb-src [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) intrepid-security multiverse
deb [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) intrepid main
deb [http://ppa.launchpad.net/kubuntu-ppa/experimental/ubuntu](http://ppa.launchpad.net/kubuntu-ppa/experimental/ubuntu) intrepid main
deb [http://ppa.launchpad.net/kubuntu-members-kde4/ppa/ubuntu](http://ppa.launchpad.net/kubuntu-members-kde4/ppa/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/kubuntu-members-kde4/ppa/ubuntu](http://ppa.launchpad.net/kubuntu-members-kde4/ppa/ubuntu) intrepid main
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) intrepid free non-free
deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) intrepid free non-free


---

### Post by Hark3n on 2009-05-21
Bump, and can someone please tell me why my posts are generally ignored?

---

