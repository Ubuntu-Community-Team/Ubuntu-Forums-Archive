---
title: "Amarok Problem: Libxine-extracodecs appears in synaptic but won't install"
date: 2009-06-13
forum: General Help
---

### Post by tklaus on 2009-06-13
I am trying to get amarok to work but I can't get libxine-extracodecs to install. I am almost sure I have the correct repositories added, and I can see it inside synaptic, but when I mark it for installation it says the package has unresolved dependencies.

---

### Post by synapsys on 2009-06-13
Try typing:

```
sudo apt-get install libxine-extracodecs
```

at terminal and see what the output says.

---

### Post by mc4man on 2009-06-13
The libxine1-extracodecs is atm only available for dapper, 8.04 -> 9.04 use a different name. What version of ubuntu are you using?

---

### Post by tklaus on 2009-06-13
I am using 9.04 jaunty jackalope. This is what the output for sudo apt-get install libxine-extracodecs is:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libxine-extracodecs: Depends: libxine-main1 but it is not installable
E: Broken packages

---

### Post by mc4man on 2009-06-13
Here is a listing of all the libxine1 plugins, codecs for 8.04 > 9.04
[http://packages.ubuntu.com/jaunty/libxine1-all-plugins](http://packages.ubuntu.com/jaunty/libxine1-all-plugins)

What do you see if you search libxine1 in synaptic

(typically installing libxine1-ffmpeg or libxine1-all-plugins will take care of everything you'll need

Did you do an upgrade to jaunty?
if so maybe take a look at your sources.list
```
cat /etc/apt/sources.list
```

---

### Post by tklaus on 2009-06-13
# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) jaunty main restricted
deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted
deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) jaunty universe
deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) jaunty universe
deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) jaunty-updates universe
deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse
deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
# deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse
# deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) jaunty free non-free
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) jaunty free non-free






this is the output for the source. I actually just upgraded today so I don't know if that is a problem. When I searched for libxine1 a whole bunch of options came up. Am I supposed to use one of those instead? Thanks for the help!

---

### Post by mc4man on 2009-06-13
> # deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse
[COLOR="Blue"]deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse[/COLOR]
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) jaunty free non-free
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) jaunty free non-free


Make the 2 lines in blue look like the ones above them (# +space

 ```
gksudo gedit /etc/apt/sources.list
```

As such
```
# deb http://archive.ubuntu.com/ubuntu dapper multiverse
# deb-src http://archive.ubuntu.com/ubuntu dapper multiverse
# deb http://archive.ubuntu.com/ubuntu dapper multiverse
# deb-src http://archive.ubuntu.com/ubuntu dapper multiverse
deb http://packages.medibuntu.org/ jaunty free non-free
deb http://packages.medibuntu.org/ jaunty free non-free 
```

Then run ```
sudo apt-get update
```
and 
```
sudo apt-get install libxine1-ffmpeg phonon-backend-xine
```

do note that jaunty uses the new amarok that many people hate. (there are posts on how to get the 1.4 version going (amarok 14

also what if any issues you may have from an upgrade to jaunty I'm not sure (versus a 'fresh' install


(what version of amarok is shown as being installed (the upgrade should of updated to 2.x


Edit: if at any point after editing the sources you get a 'broken package' error then open synaptic, click on 'custom filters', choose 'broken' and see what package it is. If it's 'libxine-extracodecs' then remove it.

---

### Post by tklaus on 2009-06-14
Thanks for the help! I think its working ok. I just have to get the sound working now....

---

