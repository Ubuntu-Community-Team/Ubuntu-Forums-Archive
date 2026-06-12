---
title: "Xubuntu migration broke Gnome"
date: 2013-05-07
forum: Desktop Environments
---

### Post by KeithO on 2013-05-07
I switched from Ubuntu 13.04 to Xubuntu to get away from unity. However Xfce has been unstable for me and I wish to return to Unity. The issue is I am unable to restore the Gnome files. My problem arises with pulseaudio not being able to get installed

I run
```

sudo apt-get install ubuntu-gnome-desktop ubuntu-gnome-default-settings

```
however it errors out with 
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 ubuntu-gnome-desktop : Depends: pulseaudio but it is not going to be installed
                        Recommends: pulseaudio-module-bluetooth but it is not going to be installed
                        Recommends: pulseaudio-module-x11 but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
keith@Keith-Linux:~$ sudo apt-get install pulseaudio-module-bluetooth
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 pulseaudio-module-bluetooth : Depends: pulseaudio but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
keith@Keith-Linux:~$ sudo apt-get install pulseaudio
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 pulseaudio : Depends: libpulse0 (= 1:3.0-0ubuntu6) but 1:3.0-0ubuntu6+1~webupd8~raring is to be installed
              Recommends: pulseaudio-module-x11 but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

```

Here is the list of the repos I am pulling from 
```

grep ^ /etc/apt/sources.list /etc/apt/sources.list.d/*
/etc/apt/sources.list:
/etc/apt/sources.list:# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Beta amd64 (20120328)]/ precise main restricted
/etc/apt/sources.list:
/etc/apt/sources.list:# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
/etc/apt/sources.list:# newer versions of the distribution.
/etc/apt/sources.list:deb http://us.archive.ubuntu.com/ubuntu/ raring main restricted
/etc/apt/sources.list:deb-src http://us.archive.ubuntu.com/ubuntu/ raring universe main multiverse restricted #Added by software-properties
/etc/apt/sources.list:
/etc/apt/sources.list:## Major bug fix updates produced after the final release of the
/etc/apt/sources.list:## distribution.
/etc/apt/sources.list:deb http://us.archive.ubuntu.com/ubuntu/ raring-updates main restricted
/etc/apt/sources.list:deb-src http://us.archive.ubuntu.com/ubuntu/ raring-updates universe main multiverse restricted #Added by software-properties
/etc/apt/sources.list:
/etc/apt/sources.list:## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
/etc/apt/sources.list:## team. Also, please note that software in universe WILL NOT receive any
/etc/apt/sources.list:## review or updates from the Ubuntu security team.
/etc/apt/sources.list:deb http://us.archive.ubuntu.com/ubuntu/ raring universe
/etc/apt/sources.list:deb http://us.archive.ubuntu.com/ubuntu/ raring-updates universe
/etc/apt/sources.list:
/etc/apt/sources.list:## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
/etc/apt/sources.list:## team, and may not be under a free licence. Please satisfy yourself as to 
/etc/apt/sources.list:## your rights to use the software. Also, please note that software in 
/etc/apt/sources.list:## multiverse WILL NOT receive any review or updates from the Ubuntu
/etc/apt/sources.list:## security team.
/etc/apt/sources.list:deb http://us.archive.ubuntu.com/ubuntu/ raring multiverse
/etc/apt/sources.list:deb http://us.archive.ubuntu.com/ubuntu/ raring-updates multiverse
/etc/apt/sources.list:
/etc/apt/sources.list:## N.B. software from this repository may not have been tested as
/etc/apt/sources.list:## extensively as that contained in the main release, although it includes
/etc/apt/sources.list:## newer versions of some applications which may provide useful features.
/etc/apt/sources.list:## Also, please note that software in backports WILL NOT receive any review
/etc/apt/sources.list:## or updates from the Ubuntu security team.
/etc/apt/sources.list:deb http://us.archive.ubuntu.com/ubuntu/ raring-backports main restricted universe multiverse
/etc/apt/sources.list:deb-src http://us.archive.ubuntu.com/ubuntu/ raring-backports main restricted universe multiverse #Added by software-properties
/etc/apt/sources.list:
/etc/apt/sources.list:deb http://security.ubuntu.com/ubuntu raring-security main restricted
/etc/apt/sources.list:deb-src http://security.ubuntu.com/ubuntu raring-security universe main multiverse restricted #Added by software-properties
/etc/apt/sources.list:deb http://security.ubuntu.com/ubuntu raring-security universe
/etc/apt/sources.list:deb http://security.ubuntu.com/ubuntu raring-security multiverse
/etc/apt/sources.list:
/etc/apt/sources.list:## Uncomment the following two lines to add software from Canonical's
/etc/apt/sources.list:## 'partner' repository.
/etc/apt/sources.list:## This software is not part of Ubuntu, but is offered by Canonical and the
/etc/apt/sources.list:## respective vendors as a service to Ubuntu users.
/etc/apt/sources.list:deb http://archive.canonical.com/ubuntu precise partner
/etc/apt/sources.list:deb-src http://archive.canonical.com/ubuntu precise partner
/etc/apt/sources.list:
/etc/apt/sources.list:## This software is not part of Ubuntu, but is offered by third-party
/etc/apt/sources.list:## developers who want to ship their latest software.
/etc/apt/sources.list:deb http://extras.ubuntu.com/ubuntu raring main
/etc/apt/sources.list:deb-src http://extras.ubuntu.com/ubuntu raring main
/etc/apt/sources.list:deb http://archive.canonical.com raring partner
/etc/apt/sources.list:deb-src http://archive.canonical.com raring partner
/etc/apt/sources.list.d/atareao-atareao-quantal.list.distUpgrade:deb http://ppa.launchpad.net/atareao/atareao/ubuntu quantal main
/etc/apt/sources.list.d/atareao-atareao-quantal.list.distUpgrade:deb-src http://ppa.launchpad.net/atareao/atareao/ubuntu quantal main
/etc/apt/sources.list.d/atareao-atareao-raring.list:# deb http://ppa.launchpad.net/atareao/atareao/ubuntu raring main
/etc/apt/sources.list.d/atareao-atareao-raring.list:# deb-src http://ppa.launchpad.net/atareao/atareao/ubuntu raring main
/etc/apt/sources.list.d/atareao-atareao-raring.list.save:# deb http://ppa.launchpad.net/atareao/atareao/ubuntu raring main
/etc/apt/sources.list.d/atareao-atareao-raring.list.save:# deb-src http://ppa.launchpad.net/atareao/atareao/ubuntu raring main
/etc/apt/sources.list.d/atareao-lenses-precise.list.distUpgrade:# deb http://ppa.launchpad.net/atareao/lenses/ubuntu quantal main # disabled on upgrade to quantal
/etc/apt/sources.list.d/atareao-lenses-precise.list.distUpgrade:# deb-src http://ppa.launchpad.net/atareao/lenses/ubuntu quantal main # disabled on upgrade to quantal
/etc/apt/sources.list.d/cairo-dock-team-ppa-precise.list.distUpgrade:# deb http://ppa.launchpad.net/cairo-dock-team/ppa/ubuntu quantal main # disabled on upgrade to quantal
/etc/apt/sources.list.d/cairo-dock-team-ppa-precise.list.distUpgrade:# deb-src http://ppa.launchpad.net/cairo-dock-team/ppa/ubuntu quantal main # disabled on upgrade to quantal
/etc/apt/sources.list.d/conky-companions-ppa-raring.list:deb http://ppa.launchpad.net/conky-companions/ppa/ubuntu quantal main
/etc/apt/sources.list.d/conky-companions-ppa-raring.list:# deb-src http://ppa.launchpad.net/conky-companions/ppa/ubuntu raring main
/etc/apt/sources.list.d/conky-companions-ppa-raring.list.save:deb http://ppa.launchpad.net/conky-companions/ppa/ubuntu quantal main
/etc/apt/sources.list.d/conky-companions-ppa-raring.list.save:# deb-src http://ppa.launchpad.net/conky-companions/ppa/ubuntu raring main
/etc/apt/sources.list.d/gnome3-team-gnome3-raring.list:deb http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu raring main
/etc/apt/sources.list.d/gnome3-team-gnome3-raring.list:# deb-src http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu raring main
/etc/apt/sources.list.d/gnome3-team-gnome3-raring.list:# deb-src http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu raring main
/etc/apt/sources.list.d/gnome3-team-gnome3-raring.list.save:deb http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu raring main
/etc/apt/sources.list.d/gnome3-team-gnome3-raring.list.save:# deb-src http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu raring main
/etc/apt/sources.list.d/gnome3-team-gnome3-raring.list.save:# deb-src http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu raring main
/etc/apt/sources.list.d/gnome-shell-extensions-ppa-raring.list:# deb http://ppa.launchpad.net/gnome-shell-extensions/ppa/ubuntu raring main
/etc/apt/sources.list.d/gnome-shell-extensions-ppa-raring.list:# deb-src http://ppa.launchpad.net/gnome-shell-extensions/ppa/ubuntu raring main
/etc/apt/sources.list.d/gnome-shell-extensions-ppa-raring.list.save:# deb http://ppa.launchpad.net/gnome-shell-extensions/ppa/ubuntu raring main
/etc/apt/sources.list.d/gnome-shell-extensions-ppa-raring.list.save:# deb-src http://ppa.launchpad.net/gnome-shell-extensions/ppa/ubuntu raring main
/etc/apt/sources.list.d/google-chrome.list:### THIS FILE IS AUTOMATICALLY CONFIGURED ###
/etc/apt/sources.list.d/google-chrome.list:# You may comment out this entry, but any other modifications may be lost.
/etc/apt/sources.list.d/google-chrome.list:deb http://dl.google.com/linux/chrome/deb/ stable main
/etc/apt/sources.list.d/google-chrome.list.distUpgrade:### THIS FILE IS AUTOMATICALLY CONFIGURED ###
/etc/apt/sources.list.d/google-chrome.list.distUpgrade:# You may comment out this entry, but any other modifications may be lost.
/etc/apt/sources.list.d/google-chrome.list.distUpgrade:deb http://dl.google.com/linux/chrome/deb/ stable main
/etc/apt/sources.list.d/google-chrome.list.save:### THIS FILE IS AUTOMATICALLY CONFIGURED ###
/etc/apt/sources.list.d/google-chrome.list.save:# You may comment out this entry, but any other modifications may be lost.
/etc/apt/sources.list.d/google-chrome.list.save:deb http://dl.google.com/linux/chrome/deb/ stable main
/etc/apt/sources.list.d/gwendal-lebihan-dev-cinnamon-stable-raring.list:deb http://ppa.launchpad.net/gwendal-lebihan-dev/cinnamon-stable/ubuntu raring main
/etc/apt/sources.list.d/gwendal-lebihan-dev-cinnamon-stable-raring.list:# deb-src http://ppa.launchpad.net/gwendal-lebihan-dev/cinnamon-stable/ubuntu raring main
/etc/apt/sources.list.d/jsevi83-unity-precise.list:# deb http://ppa.launchpad.net/jsevi83/unity/ubuntu precise main
/etc/apt/sources.list.d/jsevi83-unity-precise.list:# deb-src http://ppa.launchpad.net/jsevi83/unity/ubuntu precise main
/etc/apt/sources.list.d/jsevi83-unity-precise.list.distUpgrade:# deb http://ppa.launchpad.net/jsevi83/unity/ubuntu precise main
/etc/apt/sources.list.d/jsevi83-unity-precise.list.distUpgrade:# deb-src http://ppa.launchpad.net/jsevi83/unity/ubuntu precise main
/etc/apt/sources.list.d/jsevi83-unity-precise.list.save:# deb http://ppa.launchpad.net/jsevi83/unity/ubuntu precise main
/etc/apt/sources.list.d/jsevi83-unity-precise.list.save:# deb-src http://ppa.launchpad.net/jsevi83/unity/ubuntu precise main
/etc/apt/sources.list.d/kokoto-java-omgubuntu-stuff-quantal.list.distUpgrade:deb http://ppa.launchpad.net/kokoto-java/omgubuntu-stuff/ubuntu quantal main
/etc/apt/sources.list.d/kokoto-java-omgubuntu-stuff-quantal.list.distUpgrade:deb-src http://ppa.launchpad.net/kokoto-java/omgubuntu-stuff/ubuntu quantal main
/etc/apt/sources.list.d/markjtully-ppa-precise.list.distUpgrade:# deb http://ppa.launchpad.net/markjtully/ppa/ubuntu quantal main # disabled on upgrade to quantal
/etc/apt/sources.list.d/markjtully-ppa-precise.list.distUpgrade:# deb-src http://ppa.launchpad.net/markjtully/ppa/ubuntu quantal main # disabled on upgrade to quantal
/etc/apt/sources.list.d/medibuntu.list:## Please report any bug on https://bugs.launchpad.net/medibuntu/
/etc/apt/sources.list.d/medibuntu.list:deb http://packages.medibuntu.org/ raring free non-free #Medibuntu - Ubuntu 13.04 "raring ringtail"
/etc/apt/sources.list.d/medibuntu.list:# deb-src http://packages.medibuntu.org/ raring free non-free #Medibuntu (source) - Ubuntu 13.04 "raring ringtail"
/etc/apt/sources.list.d/medibuntu.list.save:## Please report any bug on https://bugs.launchpad.net/medibuntu/
/etc/apt/sources.list.d/medibuntu.list.save:deb http://packages.medibuntu.org/ raring free non-free #Medibuntu - Ubuntu 13.04 "raring ringtail"
/etc/apt/sources.list.d/medibuntu.list.save:# deb-src http://packages.medibuntu.org/ raring free non-free #Medibuntu (source) - Ubuntu 13.04 "raring ringtail"
/etc/apt/sources.list.d/nilarimogard-webupd8-precise.list.distUpgrade:# deb http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu quantal main # disabled on upgrade to quantal
/etc/apt/sources.list.d/nilarimogard-webupd8-precise.list.distUpgrade:# deb-src http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu quantal main # disabled on upgrade to quantal
/etc/apt/sources.list.d/noobslab-themes-precise.list.distUpgrade:# deb http://ppa.launchpad.net/noobslab/themes/ubuntu quantal main # disabled on upgrade to quantal
/etc/apt/sources.list.d/noobslab-themes-precise.list.distUpgrade:# deb-src http://ppa.launchpad.net/noobslab/themes/ubuntu quantal main # disabled on upgrade to quantal
/etc/apt/sources.list.d/otto-kesselgulasch-gimp-precise.list.distUpgrade:# deb http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu quantal main # disabled on upgrade to quantal
/etc/apt/sources.list.d/otto-kesselgulasch-gimp-precise.list.distUpgrade:# deb-src http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu quantal main # disabled on upgrade to quantal
/etc/apt/sources.list.d/paullo612-unityshell-rotated-quantal.list.distUpgrade:deb http://ppa.launchpad.net/paullo612/unityshell-rotated/ubuntu quantal main
/etc/apt/sources.list.d/paullo612-unityshell-rotated-quantal.list.distUpgrade:deb-src http://ppa.launchpad.net/paullo612/unityshell-rotated/ubuntu quantal main
/etc/apt/sources.list.d/private-ppa.launchpad.net_commercial-ppa-uploaders_steam_ubuntu.list:deb https://private-ppa.launchpad.net/commercial-ppa-uploaders/steam/ubuntu raring main #Added by software-center; credentials stored in /etc/apt/auth.conf disabled on upgrade to raring
/etc/apt/sources.list.d/private-ppa.launchpad.net_commercial-ppa-uploaders_steam_ubuntu.list.distUpgrade:deb https://private-ppa.launchpad.net/commercial-ppa-uploaders/steam/ubuntu quantal main #Added by software-center; credentials stored in /etc/apt/auth.conf
/etc/apt/sources.list.d/private-ppa.launchpad.net_commercial-ppa-uploaders_steam_ubuntu.list.save:deb https://private-ppa.launchpad.net/commercial-ppa-uploaders/steam/ubuntu raring main #Added by software-center; credentials stored in /etc/apt/auth.conf disabled on upgrade to raring
/etc/apt/sources.list.d/quantal-partner.list:deb http://archive.canonical.com/ubuntu raring partner #Added by software-center
/etc/apt/sources.list.d/quantal-partner.list.distUpgrade:deb http://archive.canonical.com/ubuntu quantal partner #Added by software-center
/etc/apt/sources.list.d/quantal-partner.list.save:deb http://archive.canonical.com/ubuntu raring partner #Added by software-center
/etc/apt/sources.list.d/scopes-packagers-ppa-precise.list.distUpgrade:# deb http://ppa.launchpad.net/scopes-packagers/ppa/ubuntu quantal main # disabled on upgrade to quantal
/etc/apt/sources.list.d/scopes-packagers-ppa-precise.list.distUpgrade:# deb-src http://ppa.launchpad.net/scopes-packagers/ppa/ubuntu quantal main # disabled on upgrade to quantal
/etc/apt/sources.list.d/steam.list.distUpgrade:deb http://repo.steampowered.com/steam/ precise steam
/etc/apt/sources.list.d/steam.list.distUpgrade:deb-src http://repo.steampowered.com/steam/ precise steam
/etc/apt/sources.list.d/tualatrix-ppa-raring.list:# deb http://ppa.launchpad.net/tualatrix/ppa/ubuntu raring main
/etc/apt/sources.list.d/tualatrix-ppa-raring.list:# deb-src http://ppa.launchpad.net/tualatrix/ppa/ubuntu raring main
/etc/apt/sources.list.d/tualatrix-ppa-raring.list.save:# deb http://ppa.launchpad.net/tualatrix/ppa/ubuntu raring main
/etc/apt/sources.list.d/tualatrix-ppa-raring.list.save:# deb-src http://ppa.launchpad.net/tualatrix/ppa/ubuntu raring main
/etc/apt/sources.list.d/webupd8team-gnome3-raring.list:# deb http://ppa.launchpad.net/webupd8team/gnome3/ubuntu raring main
/etc/apt/sources.list.d/webupd8team-gnome3-raring.list:# deb-src http://ppa.launchpad.net/webupd8team/gnome3/ubuntu raring main
/etc/apt/sources.list.d/webupd8team-gnome3-raring.list:# deb-src http://ppa.launchpad.net/webupd8team/gnome3/ubuntu raring main
/etc/apt/sources.list.d/webupd8team-gnome3-raring.list.save:# deb http://ppa.launchpad.net/webupd8team/gnome3/ubuntu raring main
/etc/apt/sources.list.d/webupd8team-gnome3-raring.list.save:# deb-src http://ppa.launchpad.net/webupd8team/gnome3/ubuntu raring main
/etc/apt/sources.list.d/webupd8team-gnome3-raring.list.save:# deb-src http://ppa.launchpad.net/webupd8team/gnome3/ubuntu raring main
/etc/apt/sources.list.d/webupd8team-sublime-text-2-raring.list:deb http://ppa.launchpad.net/webupd8team/sublime-text-2/ubuntu raring main
/etc/apt/sources.list.d/webupd8team-sublime-text-2-raring.list:# deb-src http://ppa.launchpad.net/webupd8team/sublime-text-2/ubuntu raring main
/etc/apt/sources.list.d/webupd8team-sublime-text-2-raring.list:# deb-src http://ppa.launchpad.net/webupd8team/sublime-text-2/ubuntu raring main
/etc/apt/sources.list.d/webupd8team-sublime-text-2-raring.list.save:deb http://ppa.launchpad.net/webupd8team/sublime-text-2/ubuntu raring main
/etc/apt/sources.list.d/webupd8team-sublime-text-2-raring.list.save:# deb-src http://ppa.launchpad.net/webupd8team/sublime-text-2/ubuntu raring main
/etc/apt/sources.list.d/webupd8team-sublime-text-2-raring.list.save:# deb-src http://ppa.launchpad.net/webupd8team/sublime-text-2/ubuntu raring main
/etc/apt/sources.list.d/xubuntu-dev-xfce-4_12-raring.list:# deb http://ppa.launchpad.net/xubuntu-dev/xfce-4.12/ubuntu raring main
/etc/apt/sources.list.d/xubuntu-dev-xfce-4_12-raring.list:# deb-src http://ppa.launchpad.net/xubuntu-dev/xfce-4.12/ubuntu raring main
/etc/apt/sources.list.d/xubuntu-dev-xfce-4_12-raring.list.save:# deb http://ppa.launchpad.net/xubuntu-dev/xfce-4.12/ubuntu raring main
/etc/apt/sources.list.d/xubuntu-dev-xfce-4_12-raring.list.save:# deb-src http://ppa.launchpad.net/xubuntu-dev/xfce-4.12/ubuntu raring main
/etc/apt/sources.list.d/yannubuntu-boot-repair-quantal.list.distUpgrade:deb http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu quantal main
/etc/apt/sources.list.d/yannubuntu-boot-repair-quantal.list.distUpgrade:deb-src http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu quantal main

```

Any guidance would be greatly appreciated.

---

### Post by dentaku65 on 2013-05-08
Seems that your software sources are mixed raring/quantal; you can try to disable all 3rd party PPA and use only official repositories in /etc/apt/source.list Then
```
sudo apt-get clean
sudo apt-get update
sudo apt-get dist-upgrade
```

On Psychocats [http://www.psychocats.net/ubuntu/pureubuntu](http://www.psychocats.net/ubuntu/pureubuntu) you can check how to switch in pure mode between *buntu, but at the moment only till quantal is the info available.

---

### Post by KeithO on 2013-05-08
Thanks for the suggestion. I looked and Psychocats has updated to 13.04 [http://www.psychocats.net/ubuntucat/pure-ubuntu-13-04/](http://www.psychocats.net/ubuntucat/pure-ubuntu-13-04/)

---

### Post by KeithO on 2013-05-08
I reset my sources to 
```

#############################################################
################### OFFICIAL UBUNTU REPOS ###################
#############################################################

###### Ubuntu Main Repos
deb http://us.archive.ubuntu.com/ubuntu/ raring main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ raring main restricted universe multiverse

###### Ubuntu Update Repos
deb http://us.archive.ubuntu.com/ubuntu/ raring-security main restricted universe multiverse
deb http://us.archive.ubuntu.com/ubuntu/ raring-updates main restricted universe multiverse
deb http://us.archive.ubuntu.com/ubuntu/ raring-proposed main restricted universe multiverse
deb http://us.archive.ubuntu.com/ubuntu/ raring-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ raring-security main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ raring-updates main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ raring-proposed main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ raring-backports main restricted universe multiverse

##############################################################
##################### UNOFFICIAL  REPOS ######################
##############################################################

###### 3rd Party Binary Repos

#### WebUpd8 PPA - http://www.webupd8.org/
deb http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu raring main


####### 3rd Party Source Repos

#### WebUpd8 PPA (Source) - http://www.webupd8.org/
deb-src http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu raring main

```

however I am still getting the error on pulseaudio 
```

gnome-shell is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 ubuntu-gnome-desktop : Depends: pulseaudio but it is not going to be installed
                        Recommends: pulseaudio-module-bluetooth but it is not going to be installed
                        Recommends: pulseaudio-module-x11 but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

```

---

### Post by KeithO on 2013-05-10
bump

---

### Post by dentaku65 on 2013-05-11
Try
```
sudo apt-get install -f
```

---

### Post by KeithO on 2013-05-13
It still doesn't like want to install even when forcing.

---

### Post by dentaku65 on 2013-05-14
I can suggest to use aptitute instead
```
sudo apt-get install aptitude
sudo aptitude update
sudo aptitude dist-upgrade
```
Aptitude should prompt you the option in order to fix the unmet dependencies

---

### Post by KeithO on 2013-05-14
Using aptitude did the trick. Installed what was necessary and downgraded the pulseaudio. this all allowed for gnome to be installed. I will report back if anything is screwy after rebooting later this evening.

Much appreciated dentaku65

---

### Post by KeithO on 2013-05-16
All is well. This is closed.

---

