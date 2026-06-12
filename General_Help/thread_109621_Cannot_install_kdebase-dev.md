---
title: "Cannot install kdebase-dev"
date: 2005-12-29
forum: General Help
---

### Post by roach of discord on 2005-12-29
Hello.  I am trying to compile a program...which gives me this error:

checking for KDE... configure: error:
in the prefix, you've chosen, are no KDE headers installed. This will fail.
So, check this please and use another prefix!

I figured I needed kdebase-dev?  I tried to install that via kynaptic..but it does not work due to a dependency error.  Could anyone possibly help me?  Thanks!

-Joe

---

### Post by Hobbsee on 2005-12-29
I'm thinking you would need to install kde-devel, to get the kde headers...

If you could paste the dependancy error, that would probably be helpful, too.

---

### Post by roach of discord on 2005-12-29
**Here is the error I get trying to install kde-devel:**

[i]posthuman@ubuntu:~/Desktop/target$ sudo apt-get install kde-devel
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
  kde-devel: Depends: kdesdk but it is not going to be installed
             Depends: kdelibs4-dev but it is not going to be installed
             Depends: kdebase-dev but it is not going to be installed
             Depends: libkonq4-dev but it is not going to be installed
E: Broken packages[/i]

**Here is the error I get trying to install kdebase-devel:**

[i]posthuman@ubuntu:~/Desktop/target$ sudo apt-get install kdebase-dev
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
  kdebase-dev: Depends: kdelibs4-dev (>= 4:3.5-rc1) but it is not going to be installed
E: Broken packages[/i]

That is trying to install both kde-dev and kdebase-dev :(.

Here is my sources.list

```
  GNU nano 1.3.8                                           File: /etc/apt/sources.list

deb-src http://archive.ubuntu.com/ubuntu breezy main restricted

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
deb-src http://archive.ubuntu.com/ubuntu breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
## deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
## deb-src http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe

deb http://archive.ubuntu.com/ubuntu/ breezy universe main restricted multiverse

deb http://wine.sourceforge.net/apt/ binary/

deb http://public.planetmirror.com/pub/plf/ubuntu/plf/ breezy free non-free

deb ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/ breezy free non-free
deb-src ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/ breezy free non-free

deb http://deb.opera.com/opera/ etch non-free
## deb http://seveas.ubuntulinux.nl/ breezy-seveas breezy-backports breezy-custom breezy-extras freenx madwifi
## deb-src http://seveas.ubuntulinux.nl/ breezy-seveas breezy-backports breezy-custom breezy-extras freenx madwifi

deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
deb http://ubuntu-backports.mirrormax.net/ breezy-extras main restricted universe multiverse
## created by arniebackports

deb http://kubuntu.org/packages/kde35 breezy main
deb http://kubuntu.org/packages/amarok-1.3.7 breezy main
deb http://kubuntu.org/packages/kde-latest/ breezy main

deb-src http://kubuntu.org/packages/kde35 breezy main

```

---

### Post by mlomker on 2005-12-29
I'd recommend commenting out all of the non-Ubuntu and Kubuntu items in your sources.list and then:

```

sudo apt-get update
sudo apt-get -f upgrade

```

The third-party repos could be creating an impossible combination for apt to deal with.  I always recommend disabling third-party repos as soon as you are done with them.

---

### Post by limit223 on 2005-12-29
[QUOTE=roach of discord]Hello.  I am trying to compile a program...which gives me this error:

checking for KDE... configure: error:
in the prefix, you've chosen, are no KDE headers installed. This will fail.
So, check this please and use another prefix!

I figured I needed kdebase-dev?  I tried to install that via kynaptic..but it does not work due to a dependency error.  Could anyone possibly help me?  Thanks!

-Joe[/QUOTE]

The most important KDE header would be kdelibs4-dev (kdelibs-dev)..don't forget to install this package as well.

---

