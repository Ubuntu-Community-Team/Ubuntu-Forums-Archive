---
title: "konqueror disappeared"
date: 2005-07-18
forum: Desktop Environments
---

### Post by DonVla on 2005-07-18
something strange occured...

yesterday i opened kde and clicked on the home button, but konqueror didn't start. instead cervisia started (what's that?????). i searched konqueror, but konqueror isn't installed at all. last time i started kde, it was three or four weeks ago, konqueror was there. i never uninstalled or removed it !!! actually i do not even use kde. i only use it when friends work on my computer, like yesterday. 
ok, then i tried to apt-get install konqueror, but then came this:


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
  konqueror: Depends: kdebase-kio-plugins but it is not going to be installed
E: Broken packages


then i tried to  apt-get install kdebase-kio-plugins and following happened:

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
  kdebase-kio-plugins: Depends: dbus-1 (>= 0.23.4) but it is not going to be installed
                       Depends: dbus-qt-1 (>= 0.23.4) but it is not going to be installed
                       Depends: libhal-storage0 but it is not going to be installed
                       Depends: libhal0 (>= 0.4.0) but it is not going to be installed
E: Broken packages

ok, i figured out, that  there is a conflict between dbus-1 and dbus (dbus is installed an my machine), but i never installed or changed dbus. i even don't really know what dbus is good for. i also haven't install any exotic programs that could uninstall or change konqueror or related libraries.
so what the heck happened.

can anyone help me or perhaps explain what happened???

thank you 

vlad

---

### Post by hod139 on 2005-07-29
Not too sure what to say.  Here is what my /etc/apt/sources.list looks like
> 
#deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted


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

deb [http://kubuntu.org/hoary-kde342](http://kubuntu.org/hoary-kde342) hoary-updates main

## Backports
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary-backports main universe multiverse restricted

## Extras
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted
 

Maybe you can set yours to my working list, try apt-get update followed by sudo apt-get upgrade

Good luck.

---

