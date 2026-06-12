---
title: "Depency hell? / handbrake"
date: 2009-03-16
forum: General Help
---

### Post by cd-r80 on 2009-03-16
Trying to install Handbrake depencies:
sudo apt-get install subversion jam yasm build-essential \
autoconf intltool libtool zlib1g-dev libbz2-dev libglib2.0-dev \
libdbus-glib-1-dev libgtk2.0-dev libhal-dev libhal-storage-dev \
libgtkhtml3.14-dev libgstreamer0.10-dev libgstreamer-plugins-base0.10-dev

But I got: ?
 
The following packages have unmet dependencies:
  autoconf: Depends: m4 (>= 1.4.8) but it is not going to be installed
            Recommends: automake but it is not going to be installed or
                        automaken
  build-essential: Depends: g++ (>= 4:4.3.1) but it is not going to be installed
                   Depends: dpkg-dev (>= 1.13.5) but it is not going to be installed
  handbrake: Depends: libgtkhtml3.14-19 (>= 3.24.1.1) but it is not going to be installed
  intltool: Depends: gettext (>= 0.10.36-1) but it is not going to be installed
snip...

What I should do? It is not going to be installed.

---

### Post by taurus on 2009-03-16
The first thing I would do is to take a real quick look at /etc/apt/sources.list.

```
cat /etc/apt/sources.list
```

---

### Post by cariboo on 2009-03-16
If you download the Handbrake .deb from [here]("http://handbrake.fr/?article=download"), all you have to double click the file, and gdebi will take care of the dependencies.

Jim

---

### Post by cd-r80 on 2009-03-16
No it wont? :

 dpkg -i HandBrake-0.9.3-Ubuntu_GUI_amd64.deb 
(Reading database ... 136372 files and directories currently installed.)
Preparing to replace handbrake 0.9.3-1 (using HandBrake-0.9.3-Ubuntu_GUI_amd64.deb) ...
Unpacking replacement handbrake ...
dpkg: dependency problems prevent configuration of handbrake:
 handbrake depends on libgtkhtml3.14-19 (>= 3.24.1.1); however:
  Package libgtkhtml3.14-19 is not installed.
dpkg: error processing handbrake (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 handbrake

I think that I have all sources enabled (apt)? I have not used any greasy programs to mess it.

---

### Post by oldos2er on 2009-03-16
Can you please post the output of
```
cat /etc/apt/sources.list
```
?

---

### Post by cd-r80 on 2009-03-16
Here it comes with "xy" , country code replaced.

# deb cdrom:[Xubuntu 8.10 _Intrepid Ibex_ - Release amd64 (20081028)]/ intrepid main multiverse restricted universe

#deb cdrom:[Xubuntu 8.10 _Intrepid Ibex_ - Release amd64 (20081028)]/ intrepid main multiverse restricted universe
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://xy.archive.ubuntu.com/ubuntu/](http://xy.archive.ubuntu.com/ubuntu/) intrepid main restricted
deb-src [http://xy.archive.ubuntu.com/ubuntu/](http://xy.archive.ubuntu.com/ubuntu/) intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://xy.archive.ubuntu.com/ubuntu/](http://xy.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted
deb-src [http://xy.archive.ubuntu.com/ubuntu/](http://xy.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://xy.archive.ubuntu.com/ubuntu/](http://xy.archive.ubuntu.com/ubuntu/) intrepid universe
deb-src [http://xy.archive.ubuntu.com/ubuntu/](http://xy.archive.ubuntu.com/ubuntu/) intrepid universe
deb [http://xy.archive.ubuntu.com/ubuntu/](http://xy.archive.ubuntu.com/ubuntu/) intrepid-updates universe
deb-src [http://xy.archive.ubuntu.com/ubuntu/](http://xy.archive.ubuntu.com/ubuntu/) intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://xy.archive.ubuntu.com/ubuntu/](http://xy.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb-src [http://xy.archive.ubuntu.com/ubuntu/](http://xy.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb [http://xy.archive.ubuntu.com/ubuntu/](http://xy.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse
deb-src [http://xy.archive.ubuntu.com/ubuntu/](http://xy.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://xy.archive.ubuntu.com/ubuntu/](http://xy.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
deb-src [http://xy.archive.ubuntu.com/ubuntu/](http://xy.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse

deb [http://moblock-deb.sourceforge.net/debian](http://moblock-deb.sourceforge.net/debian) intrepid main
deb-src [http://moblock-deb.sourceforge.net/debian](http://moblock-deb.sourceforge.net/debian) intrepid main

deb [http://www.pvv.ntnu.no/~knuta/xmms/intrepid](http://www.pvv.ntnu.no/~knuta/xmms/intrepid) ./
deb-src [http://www.pvv.ntnu.no/~knuta/xmms/intrepid](http://www.pvv.ntnu.no/~knuta/xmms/intrepid) ./
deb [http://ppa.launchpad.net/baudm/ubuntu](http://ppa.launchpad.net/baudm/ubuntu) intrepid main

deb [http://ppa.launchpad.net/fabricesp/ppa/ubuntu](http://ppa.launchpad.net/fabricesp/ppa/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/fabricesp/ppa/ubuntu](http://ppa.launchpad.net/fabricesp/ppa/ubuntu) intrepid main

---

### Post by cd-r80 on 2009-03-16
Going down. But I found a repository that solved my problems:

deb [http://ppa.launchpad.net/handbrake-ubuntu/ubuntu](http://ppa.launchpad.net/handbrake-ubuntu/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/handbrake-ubuntu/ubuntu](http://ppa.launchpad.net/handbrake-ubuntu/ubuntu) intrepid main

apt-get update
apt-get install handbrake-common
apt-get install handbrake-gtk

I wonder if there was any hope with that .deb & missing libgtkhtml3.14-19 ?

---

