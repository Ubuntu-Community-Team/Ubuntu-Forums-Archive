---
title: "Cant install kubuntu-desktop"
date: 2009-01-23
forum: Desktop Environments
---

### Post by mr_x408 on 2009-01-23
hey all, im having troubles installing kubuntu-desktop.
when i type in:
" sudo apt-get install kubuntu-desktop"
i get:
"Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting kubuntu-desktop instead of kubuntu-kde4-desktop
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  kubuntu-desktop: Depends: kdebase-workspace-bin but it is not going to be installed
                   Depends: language-selector-qt but it is not going to be installed
                   Depends: okular but it is not going to be installed
                   Depends: software-properties-kde but it is not going to be installed
                   Recommends: apport-qt but it is not going to be installed
                   Recommends: gdebi-kde but it is not going to be installed
                   Recommends: guidance-power-manager but it is not going to be installed
                   Recommends: hplip-gui but it is not going to be installed
                   Recommends: install-package but it is not going to be installed
                   Recommends: jockey-kde but it is not going to be installed
                   Recommends: kde-printer-applet but it is not going to be installed
                   Recommends: kdebluetooth but it is not going to be installed
                   Recommends: libqca2-plugin-ossl but it is not going to be installed
                   Recommends: openoffice.org-kde but it is not going to be installed
                   Recommends: system-config-printer-kde but it is not going to be installed
                   Recommends: update-notifier-kde but it is not going to be installed
E: Broken packages
"
any suggestions?

---

### Post by taurus on 2009-01-23
Post your /etc/apt/sources.list.

Applications -> Accessories -> Terminal
```
cat /etc/apt/sources.list
```

---

### Post by mr_x408 on 2009-01-23
i got
# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.


## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner


## Wine, Ubuntu Hardy Heron (8.04):
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) hardy main
deb-src [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) hardy main
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid main universe restricted multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid universe main multiverse restricted #Added by software-properties
deb [http://www.kiberpipa.org/~minmax/cinelerra/builds/sid/](http://www.kiberpipa.org/~minmax/cinelerra/builds/sid/) ./
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) intrepid main #WineHQ - Ubuntu 8.10 "Intrepid Ibex"

sory for the late reply i had to walk my dog

---

### Post by taurus on 2009-01-23
You don't have a whole lot of repos in your /etc/apt/sources.list.  And besides, there are two from hardy which shouldn't be in there.  

Make a backup of your original /etc/apt/sources.list in case you need it later.

```
sudo cp /etc/apt/sources.list  /etc/apt/sources.list.bak
```
Now, edit /etc/apt/sources.list

```
gksudo gedit /etc/apt/sources.list
```
and remove everything in there.  Then, paste in the new repos for intrepid.

```

#deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ intrepid main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid main restricted

deb http://us.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted

deb http://us.archive.ubuntu.com/ubuntu/ intrepid universe
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid universe
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-updates universe

deb http://us.archive.ubuntu.com/ubuntu/ intrepid multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid multiverse
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-updates multiverse

deb http://archive.canonical.com/ubuntu intrepid partner
deb-src http://archive.canonical.com/ubuntu intrepid partner

deb http://security.ubuntu.com/ubuntu intrepid-security main restricted
deb-src http://security.ubuntu.com/ubuntu intrepid-security main restricted
deb http://security.ubuntu.com/ubuntu intrepid-security universe
deb-src http://security.ubuntu.com/ubuntu intrepid-security universe
deb http://security.ubuntu.com/ubuntu intrepid-security multiverse
deb-src http://security.ubuntu.com/ubuntu intrepid-security multiverse

deb http://wine.budgetdedicated.com/apt intrepid main #WineHQ - Ubuntu 8.10 "Intrepid Ibex"

```
Save it and close down gedit editing window.  Now run

```
sudo apt-get update
sudo apt-get install kubuntu-desktop
```

---

### Post by mr_x408 on 2009-01-23
thankyou very much it worked

---

