---
title: "i need help :("
date: 2009-02-07
forum: General Help
---

### Post by Nikes on 2009-02-07
i'm trying to install a program called kdenlive but when i try to install it, it gives me this message:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  kdenlive: Depends: kdebase-runtime (>= 4:4.1.2) but it is not going to be installed
            Depends: kdelibs5 (>= 4:4.1.3) but it is not going to be installed
            Depends: libmlt++1 but it is not going to be installed
            Depends: libmlt1 but it is not going to be installed
            Depends: libqt4-dbus (>= 4.4.3) but it is not installable
            Depends: libqt4-svg (>= 4.4.3) but it is not installable
            Depends: libqt4-xml (>= 4.4.3) but it is not installable
            Depends: libqtcore4 (>= 4.4.3) but it is not installable
            Depends: libqtgui4 (>= 4.4.3) but it is not installable
            Depends: inigo but it is not going to be installed
            Depends: ffmpeg but it is not going to be installed
E: Broken packages


what does it mean by "broken package" and if it's another way to install it, can somebody give me step by step on how to do it....please!!:(

---

### Post by taurus on 2009-02-07
Post your /etc/apt/sources.list.

```
cat /etc/apt/sources.list
```

---

### Post by Sycron on 2009-02-07
Go to Applications-Accesories and open up a terminal. Then type ```
sudo apt-get install -f
``` and try again.

---

### Post by Nikes on 2009-02-07
> **Sycron said:**
> Go to Applications-Accesories and open up a terminal. Then type ```
sudo apt-get install -f
``` and try again.


still didn't work

---

### Post by Nikes on 2009-02-07
> **taurus said:**
> Post your /etc/apt/sources.list.

```
cat /etc/apt/sources.list
```


what is that? i'm a noob in ubuntu sorry....

---

### Post by Sycron on 2009-02-07
Open up a terminal and type:```
cat /etc/apt/sources.list
``` then copy paste the output here.

---

### Post by Nikes on 2009-02-07
> **Sycron said:**
> Open up a terminal and type:```
cat /etc/apt/sources.list
``` then copy paste the output here.

ok:


# 
# deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080701)]/ hardy main restricted

# deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080701)]/ hardy main restricted
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

# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) edgy main
deb [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) edgy main
deb [http://ppa.launchpad.net/baudm/ubuntu](http://ppa.launchpad.net/baudm/ubuntu) intrepid main
deb [http://ppa.launchpad.net/baudm/ubuntu](http://ppa.launchpad.net/baudm/ubuntu) intrepid main

---

### Post by oldos2er on 2009-02-07
Open your sources.list in Text Editor (gedit):
```
gksu gedit /etc/apt/sources.list
```
and remove the comment marks (#) from these two lines:
 ```
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
 deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
```
 
 Delete these lines:

```
deb [http://ubuntu.beryl-project.org]("http://ubuntu.beryl-project.org/") edgy main
 deb [http://ubuntu.beryl-project.org]("http://ubuntu.beryl-project.org/") edgy main
 deb [http://ppa.launchpad.net/baudm/ubuntu](http://ppa.launchpad.net/baudm/ubuntu) intrepid main
 deb [http://ppa.launchpad.net/baudm/ubuntu](http://ppa.launchpad.net/baudm/ubuntu) intrepid main
```

 Save the file and exit. Then in a terminal, run
```
sudo apt-get update && sudo apt-get upgrade
```

 Now try installing kdenlive again.

---

### Post by Nikes on 2009-02-09
> **oldos2er said:**
> Open your sources.list in Text Editor (gedit):
```
gksu gedit /etc/apt/sources.list
```
and remove the comment marks (#) from these two lines:
 ```
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
 deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
```
 
 Delete these lines:

```
deb [http://ubuntu.beryl-project.org]("http://ubuntu.beryl-project.org/") edgy main
 deb [http://ubuntu.beryl-project.org]("http://ubuntu.beryl-project.org/") edgy main
 deb [http://ppa.launchpad.net/baudm/ubuntu](http://ppa.launchpad.net/baudm/ubuntu) intrepid main
 deb [http://ppa.launchpad.net/baudm/ubuntu](http://ppa.launchpad.net/baudm/ubuntu) intrepid main
```

 Save the file and exit. Then in a terminal, run
```
sudo apt-get update && sudo apt-get upgrade
```

 Now try installing kdenlive again.


ok it installed but where does the app go to? i can't find it.

---

