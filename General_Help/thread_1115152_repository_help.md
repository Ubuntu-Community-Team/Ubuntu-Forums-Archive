---
title: "repository help"
date: 2009-04-03
forum: General Help
---

### Post by PRCalDude on 2009-04-03
Guys and Gals,

Long story short, I've been trying to install the supported version of Audacity to record some voice from a microphone and save it as a .mp3.  I couldn't get the Beta version to work (which was listed in Synaptic).  I uninstalled it and wanted to download the Dapper version of Audacity, but I can't seem to get Synaptic to recognize it.  

The line of code should be:

```
deb http://packages.ubuntu.com/dapper/audacity dapper universe security
```

but when I put the line in the 'Software sources->third party software -> add' command line and then 'update,' it gives the following error messages:

> 
GPG error: [http://packages.ubuntu.com](http://packages.ubuntu.com) dapper Release: The following signatures were invalid: NODATA 1 NODATA 2Failed to fetch [http://packages.ubuntu.com/dapper/audacity/dists/dapper/universe/binary-i386/Packages.bz2](http://packages.ubuntu.com/dapper/audacity/dists/dapper/universe/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://packages.ubuntu.com/dapper/audacity/dists/dapper/security/binary-i386/Packages.bz2](http://packages.ubuntu.com/dapper/audacity/dists/dapper/security/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)
Some index files failed to download, they have been ignored, or old ones used instead.

What's more, my 'sources.list' file isn't updating with the lines I just entered through 'Software sources.'  

Does anyone know what's happening?

---

### Post by taurus on 2009-04-03
Which release are you using?  Open a terminal and post your /etc/apt/sources.list.

Applications -> Accessories -> Terminal
```
cat /etc/apt/sources.list
```

---

### Post by PRCalDude on 2009-04-03
Here it is:

> # deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb [http://packages.ubuntu.com/dapper/audacity](http://packages.ubuntu.com/dapper/audacity) dapper universe security


I can't find anything in there about the Dapper release of Audacity

---

### Post by mb_webguy on 2009-04-03
You *really* shouldn't mix and match repositories from different versions of Ubuntu.  That way lies madness.

Audacity should work just fine *if* you have the appropriate codecs installed.  Try installing the ubuntu-restricted-extras package.  If that doesn't help, try adding the [Medibuntu]("https://help.ubuntu.com/community/Medibuntu") repository and the approprate codecs package for your architecture (i.e. w32codecs, w64codecs, or ppc-codecs).  You *may* be able to simply install the non-free-codecs package, which automatically selects the appropriate package for your system.

---

### Post by PRCalDude on 2009-04-03
> **mb_webguy said:**
> You *really* shouldn't mix and match repositories from different versions of Ubuntu.  That way lies madness.

Audacity should work just fine *if* you have the appropriate codecs installed.  Try installing the ubuntu-restricted-extras package.  If that doesn't help, try adding the [Medibuntu]("https://help.ubuntu.com/community/Medibuntu") repository and the approprate codecs package for your architecture (i.e. w32codecs, w64codecs, or ppc-codecs).  You *may* be able to simply install the non-free-codecs package, which automatically selects the appropriate package for your system.

I'm a retard.  The dapper Audacity line is at the very bottom of the file.  I've been looking at it too long.  

Anyways, how am I mixing repositories?  The Dapper Audacity repo isn't Dapper Ubuntu, is it?

Are you suggesting I install the beta version of Audacity and just get the codecs and it'll work fine?  I'll give it a shot...

---

### Post by taurus on 2009-04-03
Just delete the last entry, dapper, from your /etc/apt/sources.list.  Then, save it and run

```
sudo apt-get update
sudo apt-get upgrade
```

---

